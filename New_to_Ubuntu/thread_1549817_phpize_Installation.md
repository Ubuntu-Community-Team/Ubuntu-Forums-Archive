---
title: "phpize Installation"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by psharma17 on 2010-08-10
Hello All,
  I am trying to add [B][libssh2]("http://sourceforge.net/projects/libssh2/") PHP Extension in my ubuntu machine .
  My  webserver  has :- [/B]lighttpd/1.4.22 on ubuntu machine.
   PHP version :- php 5.3
  M new to lighttpd and server handling so while trying to add the libssh2 utility on ubuntu machine ,I found that I need to make it as an .so file by the following way


[LIST]
[*]Use these commands to download and compile the libssh2 PHP module.
[*]*wget [http://pecl.php.net/get/ssh2-0.10.tgz](http://pecl.php.net/get/ssh2-0.10.tgz)*
[*]*gunzip ssh2-0.10.tgz*
[*]*tar -xvf ssh2-0.10.tgz*
[*]*cd ssh2-0.10.tgz*
[*]*phpize && ./configure –with-ssh2 && make* **«** Generates ssh2.so, the compiled PHP extension.
[*](Note: If you encounter a make: *** [ssh2.lo] Error 1 error, run [Bill Pitz’s libssh2 patch]("http://www.billpitz.com/howto/php-libssh2.html").)
[*]*cp ./modules/ssh2.so /usr/lib/php/modules/ssh2.so*
[*]Open your PHP configuration file by typing *vi /etc/php.ini* and add *extension=ssh2.so* to the configuration, and save the file when you are complete.
[/LIST]



while compiling that i found the following issue:-

on command prompt :- phpize && ./configure .with-ssh2
phpize: command not found


Can you please tell me that how to install the phpize and compile the package into .so files.

Thanks in Advance :)

---

