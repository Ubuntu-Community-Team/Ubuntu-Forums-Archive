---
title: "&quot;No such file or directory&quot; when trying to Execute files"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by Keinan on 2010-08-02
I'm using Ubuntu 10.4 Lucid



I'm working on setting up a game server, and need to execute some files to start up the various parts of the servers.


I used the following command in the terminal:

cd /location of my database server files
./db_server

First I received a permissions error


I went to the file, and checked the box so that it would be executable


I retried and received the error "No such file or directory" despite it clearly recognizing it a moment ago in order to display the permissions error...


Any ideas about how to fix this?

---

### Post by Bachstelze on 2010-08-02
You are probably running a 64-bit system and the executable is 32-bit.  Install [font=monospace]ia32-libs[/font].

---

### Post by Keinan on 2010-08-02
Ok, installed those libs... now I have a different but similar error

error while loading shared libraries: libmysqlclient.so.15 : cannot open shared object file : no such file or directory

---

### Post by Keinan on 2010-08-02
I've read that you can't get libmysqlclient.so.15 on Ubuntu 10.4? Is that true, or is there a way to get around this? 



I really don't want to have to call my host and make them re-install a different version of Ubuntu, because even though they SAID that they would install Ubuntu 9.10 and they didn't, they'll probably still charge me ._. .

They said they'd install 9.10 server edition... when I check what I'm running it says Ubuntu 10.4...is that regarding the GUI only? I installed a GUI on top of the server, does the GUI automatically give me 10.4 or should it give me 9.10 because that is what should probably be compatible if I had been running .910 server edition? I used install ubuntu desk-top command to install the GUI...

---

### Post by Bachstelze on 2010-08-02
> **Keinan said:**
> I've read that you can't get libmysqlclient.so.15 on Ubuntu 10.4? Is that true, or is there a way to get around this? 


It is true that libmysqlclient15 is not in the Lucid repos, but you can just install the package from another version of Ubuntu (you can get it at [http://packages.ubuntu.com](http://packages.ubuntu.com)).  However, if the app is 32 bit, you will need the 32 bit version of the library.  I don't think ia32-libs has it, so you will probably have to manually extract the package and copy the lib into /lib32.

---

### Post by Keinan on 2010-08-02
I'm not sure how to go about doing that? How do I find it and extract it? Sorry, I'm quite new. :(


Would it be easier if I just installed 9.10 instead? If so...should I make it 32bit or 64bit?

---

### Post by sandyd on 2010-08-02
> **Keinan said:**
> I'm not sure how to go about doing that? How do I find it and extract it? Sorry, I'm quite new. :(


Would it be easier if I just installed 9.10 instead? If so...should I make it 32bit or 64bit?
```

wget -c http://mirrors.kernel.org/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb
mkdir mysql32
dpkg --extract libmysqlclient*deb mysql32
sudo mv mysql32/usr/lib/* /usr/lib32/

```

---

### Post by Bachstelze on 2010-08-02
> **Keinan said:**
> 
Would it be easier if I just installed 9.10 instead? If so...should I make it 32bit or 64bit?

If you want minimal fuss, install the 32-bit version of a distro that has libmysqlclient15, so either 9.10 or 8.04 if you want LTS.

---

### Post by Keinan on 2010-08-02
> **carlee said:**
> ```

wget -c http://mirrors.kernel.org/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb

dpkg --extract libmysqlclient*deb
```

 dpkg --extract libmysqlclient*deb
dpkg-deb: --extract needs a target directory.


Sorry :( How do I specify a target directory in that line?

---

### Post by Bachstelze on 2010-08-02
```
mkdir mysql32
dpkg -x libmysql*deb mysql32
```

---

### Post by Keinan on 2010-08-02
> **Bachstelze said:**
> ```
mkdir mysql32
dpkg -x libmysql*deb mysql32
```

I should literally be putting mysql32? It doesn't seem to do anything....

or something else? the directory the files are in isn't /usr/lib?

---

### Post by Bachstelze on 2010-08-02
You can put whatever, the package will be extracted there.  It means that the library files will be in mysql32/usr/lib, you need to copy them into /lib32 (*not* into /usr/lib, you would overwrite the 64-bit version).

---

### Post by sandyd on 2010-08-02
> **Bachstelze said:**
> ```
mkdir mysql32
dpkg -x libmysql*deb mysql32
```
oops... fixed.

just try the commands I initially posted... again

---

### Post by Keinan on 2010-08-02
You guys and this forum are heavenly! Thank you so much for your patience and assistance!

---

### Post by bratsos on 2012-04-22
mistake reply

---

### Post by bratsos on 2012-04-22
Re: "No such file or directory" when trying to Execute files
Quote:
Originally Posted by sandyd View Post
Code:

wget -c [http://mirrors.kernel.org/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/m/mysql-dfsg-5.0/libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb)
mkdir mysql32
dpkg --extract libmysqlclient*deb mysql32
sudo mv mysql32/usr/lib/* /usr/lib32/

And asnwer me:

bratsos@bratsos-desktop:~/db$ wget -c [http://mirrors.kernel.org/ubuntu/poo...untu3_i386.deb](http://mirrors.kernel.org/ubuntu/poo...untu3_i386.deb)
--2012-04-21 00:33:00-- [http://mirrors.kernel.org/ubuntu/poo...untu3_i386.deb](http://mirrors.kernel.org/ubuntu/poo...untu3_i386.deb)
Resolving mirrors.kernel.org... 149.20.4.71
Connecting to mirrors.kernel.org|149.20.4.71|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-04-21 00:33:01 ERROR 404: Not Found



I have the same issue "



bratsos@bratsos-desktop:~/db$ ./db_server
./db_server: error while loading shared libraries: libmysqlclient.so.15: cannot open shared object file: No such file or directory


What i must do now ?


:confused:


Why in new versions of ubuntu remove needed files ?

In Coala server 9.10 all ok (but no londer supported, need manually find all updates)

I think i go google "libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb" maybe some ftp server, have it (i hope :S )



Ubuntu Server 10.04 proved to be a real pain in the as*. Somehow the MySQL server in the Ubuntu repository differs from the version required by old database. I looked the internet for solutions but found only people asking the same questing without finding a solution.
I must install mysql-server from the older Ubuntu Server 9.10 (karmic) manually before installing my old database schema ??


Why ubuntu do such things ?


Mine ububtu is Release 10.04 (lucid) 32bit

---

