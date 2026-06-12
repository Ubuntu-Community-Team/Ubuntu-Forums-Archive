---
title: "How to install Oracle,PHP and Apache and bring them up"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by tahahellion on 2006-10-13
I need both computers on our home network.I need to have Linux running,with Oracle,PHP,Apache all running on Linux.I need to be able to see the localhost website from Linux on my Windows IE browser-> meaning I need to be able to see my Linux website on my IE on my Windows box.

Urgent reply is needed :-?

---

### Post by marianom on 2006-10-17
I wrote down a few guidelines and if you want, just let me know for additional help:

1- first you need the db installed. Don't know what version you need so let me know and I point to the proper docs.
2- install apache (I did it directly from source code but you might install a version from the repositories). From source, eg (I compiled Apache with LDFLAGS="-lpthread" to prevent crashes at startup):

```

# LDFLAGS="-lpthread" ./configure --prefix=/opt/apache --enable-module=so
# make
# make install

```

3- download php source code and configure it from scratch for oci support. This is for example the command I executed (on the php conf., you'll see additional values used that you might not require -ttf, png, jpeg and related libraries- I need them to use JPGraph in my site):

```

# ./configure --prefix=/opt/php/php5.1.6
--exec-prefix=/opt/php/php5.1.6 --with-config-file-path=/opt/apache 
--with-libdir=lib64 --with-gd --with-zlib=/usr --with-xmlrpc 
--with-oci8=/opt/oracle/orase/oracle/product/10.2.0/db_1 
--with-apxs=/opt/apache/bin/apxs --enable-sigchild --with-ttf=/usr/lib64 
--enable-gd-native-ttf --enable-gd-imgstrttf --enable-gd-native-ttf
--with-ttf-dir=/usr/local/lib --with-freetype-dir=/opt/freetype 
--with-zlib-dir=/usr/local/lib --with-png-dir=/usr/local/lib 
--with-jpeg-dir=/usr/local/lib
# make
# make install

```

4- configure the php.ini file generated.
5- configure the httpd.conf to support php.

Check the db question and I point you to good docs.

---

### Post by creeds on 2008-04-20
Hello Sir, 
I want to configure Oracle 8i with php but procedding with few steps , 
it shows error...

i just made a tar of orcle currently being used in another server and make it untar in my new ubuntu box, after making a bash_profile i try to run it, but errors were shown as ...
 

libdl.so .2 is missing...also 
libc.so.6 is not found etc

i tried to apt-get them but is not  evn apt getable
so how can i procced

---

