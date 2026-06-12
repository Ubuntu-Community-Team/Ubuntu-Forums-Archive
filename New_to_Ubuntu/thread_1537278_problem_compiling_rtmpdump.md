---
title: "problem compiling rtmpdump"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by lg_undeadorc on 2010-07-23
In the following url
[http://stream-recorder.com/forum/rtmpdump-freeware-rtmp-stream-downloader-macos-x-t3838p3.html](http://stream-recorder.com/forum/rtmpdump-freeware-rtmp-stream-downloader-macos-x-t3838p3.html)

I got 4 step procedure to install rtmpdump on ubuntu
**1)First of all install the tools needed for accessing the code and compilation**.
code:sudo apt-get install build-essential gcc make subversion libssl0.9.8 libssl-dev libssl0.9.8

**2)Now check out the latest code from the Subversion repository:**
code:svn co svn://svn.mplayerhq.hu/rtmpdump rtmpdump
**3)cd rtmpdump**
**4)make linux**

The steps 1-3 went well
but when moving to step 4
*the following error occured*
**make: *** No rule to make target `linux'.  Stop.**

Beside this url , i also looked at other and none of them helped me
How could i compile rtmpdump on ubuntu 10.4 and use it to download videos from videolectures.net

---

### Post by qoqodu75 on 2010-07-23
just type make, maybe ?

---

### Post by lg_undeadorc on 2010-07-23
> **qoqodu75 said:**
> just type make, maybe ?

It didn't work. Anyway thanks for replying. I got solution from similar kind of thread and procedure is as follows :[suggested by ron999]
These were the   steps that I used:-
1) I downloaded source tarball **rtmpdump-2.3.tgz** from here:-[http://rtmpdump.mplayerhq.hu/](http://rtmpdump.mplayerhq.hu/)
2) Then I extracted it.
3) Then I changed directory:-  **cd /home/ron/Downloads/rtmpdump-2.3**
4) Then used:-  **make SYS=posix**

And one more step:-
5) Copied the **rtmpdump** file from the **rtmpdump-2.3** folder  into **usr/bin/local** folder.

---

### Post by dave2008713 on 2010-08-12
> **lg_undeadorc said:**
> It didn't work. Anyway thanks for replying. I got solution from similar kind of thread and procedure is as follows :[suggested by ron999]
These were the   steps that I used:-
1) I downloaded source tarball **rtmpdump-2.3.tgz** from here:-[http://rtmpdump.mplayerhq.hu/](http://rtmpdump.mplayerhq.hu/)
2) Then I extracted it.
3) Then I changed directory:-  **cd /home/ron/Downloads/rtmpdump-2.3**
4) Then used:-  **make SYS=posix**

And one more step:-
5) Copied the **rtmpdump** file from the **rtmpdump-2.3** folder  into **usr/bin/local** folder.

BTW
If you see this error:  *error while loading shared libraries*: libexpat.*so*.*0*, you may also need to copy or link  librtmp.so.0 into /lib.
librtmp.so.0 can be found in directory librtmp which is in your source tree.

---

### Post by matthewbpt on 2010-08-16
> **dave2008713 said:**
> BTW
If you see this error:  *error while loading shared libraries*: libexpat.*so*.*0*, you may also need to copy or link  librtmp.so.0 into /lib.
librtmp.so.0 can be found in directory librtmp which is in your source tree.
Easier just to do
```
sudo make install
```
instead of the last step, and all the compiled binaries and libraries get copied into the system.

---

### Post by ron999 on 2010-08-17
> **matthewbpt said:**
> Easier just to do
```
sudo make install
```
instead of the last step, and all the compiled binaries and libraries get copied into the system.

Thanks for that information.:D
I've been back and edited my post.
Here:-[http://art.ubuntuforums.org/showpost.php?p=9626752&postcount=6]("http://art.ubuntuforums.org/showpost.php?p=9626752&postcount=6")

---

### Post by andrew.46 on 2010-08-27
Hi,

I have just done a little work with compiling rtmpdump with MPlayer so perhaps the following single command might be helpful:

```

sudo apt-get -y install build-essential checkinstall libssl-dev && \
wget http://rtmpdump.mplayerhq.hu/download/rtmpdump-2.3.tgz && \
tar xvf rtmpdump-2.3.tgz && cd rtmpdump-2.3 && \
make SYS=posix && \
sudo checkinstall && sudo ldconfig

```

This of course deals with the release version rather than the development version.

Andrew

---

### Post by temp3 on 2010-12-05
> **andrew.46 said:**
> 
```

sudo apt-get -y install build-essential checkinstall libssl-dev && \
wget http://rtmpdump.mplayerhq.hu/download/rtmpdump-2.3.tgz && \
tar xvf rtmpdump-2.3.tgz && cd rtmpdump-2.3 && \
make SYS=posix && \
sudo checkinstall && sudo ldconfig

```


yeeeeeees it worked !
u know, i'm new to Linux. i just registered here to say THANKS MAN.

---

### Post by andrew.46 on 2011-01-31
> **temp3 said:**
> yeeeeeees it worked !
u know, i'm new to Linux. i just registered here to say THANKS MAN.

My pleasure :)

---

### Post by ron999 on 2011-05-10
Hi

There have been several patches applied to RTMPDump.:)
Following Andrew's method above, this is how I compiled RTMPDump from SVN:-

```
sudo apt-get -y install build-essential checkinstall libssl-dev && \
svn co svn://svn.mplayerhq.hu/rtmpdump/trunk rtmpdump && cd rtmpdump && \
make VERSION="v2.3\ SVN-r$(svn info 2> /dev/null | grep Revision | cut -d' ' -f2)" && \
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname rtmpdump \
--pkgversion "2.3-SVN-r$(svn info 2> /dev/null | grep Revision | cut -d' ' -f2)" \
--backup=no --deldoc=yes --default && sudo ldconfig
```

**rtmpdump_2.3-SVN-r568-1_i386.deb**

```
ron@ubuntu:~$ rtmpdump
RTMPDump v2.3 SVN-r568
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
```

---

### Post by temp3 on 2011-05-10
thanks. i think the HANDSHAKE (for rtmpe 9) problem isn't fixed yet. am i right ?

---

### Post by ron999 on 2011-05-10
> **temp3 said:**
> am i right ?
Yes :mad:

---

