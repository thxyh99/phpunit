安装Composer

    $ curl -sS https://getcomposer.org/installer | php
    $ sudo mv composer.phar /usr/local/bin/composer
    $ composer –version

安装PHPUnit

composer require --dev phpunit/phpunit ^5.7
配置autoload

    添加下面的代码到composer.json. PackageName是项目的名称，src是包含PHP class文件的文件夹地址，项目根目录下的子文件夹。
    "autoload": {
    "psr-4": {"PackageName\\": "src/"}
    },
    composer dump-autoload
    在使用代码库文件里添加require_once __DIR__ . '/path/to/vendor/autoload.php';
    使用代码库的class: $square = new PackageName\ParentDir\Square() （注：在src文件夹下有Square.php 这个文件)

使用PHPUnit
单元测试文件

    <?php
    # 文件位置 ProjectRoot/Test/SquareTest.php

    use PHPUnit\Framework\TestCase;                                                                                        
    require_once __DIR__ . '/../../vendor/autoload.php';   

    class SquareTest extends TestCase {
        public function testPushAndPop() {
            $square = new \PackageName\Ceshi\Square();
            $actual = $square->calc(10);
            $this->assertSame(100, $actual);
        }
    }


运行测试

../../vendor/bin/phpunit --color CeshiTest.php
