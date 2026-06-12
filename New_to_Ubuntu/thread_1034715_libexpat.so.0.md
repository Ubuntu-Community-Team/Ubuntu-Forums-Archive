---
title: "libexpat.so.0"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by gak67 on 2009-01-09
I am a real NOOB at Ubuntu.  I  have recently installed 8.10.  I have downloaded and installed Gyach Enhanced - a Yahoo Messenger client.  When i try and run it it comes up with the following message:

gyach: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory

How do I fix this please - and please explain it in simple terms, cos as I said i am new at this.

---

### Post by geforce123 on 2009-01-09
When you're looking for a packge, you can use this command:
```
apt-cache search *KeyWord*
```

So I ran the following command:
```
apt-cache search libexpat
```

which returned me the following output:
```
~# apt-cache search libexpat
libexpat1 - XML parsing C library - runtime library
libexpat1-dev - XML parsing C library - development kit
libexpat-ocaml - ocaml expat bindings
libexpat-ocaml-dev - ocaml expat bindings
liblua5.1-expat-dev - libexpat development files for the lua language version 5.1
liblua5.1-expat0 - libexpat bindings for the lua language version 5.1
ser-jabber-module - contains the Jabber module (SIP-Jabber message translation)

```

Now I know you need the package "libexpat1".
You can install the package using the following command:

```
apt-get install libexpat1
```

---

### Post by onelife151 on 2009-02-19
ok now that i have that package install. i am still getting an error that libexpat.so.1 lib can not be found.

---

### Post by Bachstelze on 2009-02-19
This program is old and requires an old version of the libexpat library. You cannot use it with Ubuntu.

---

### Post by chcip on 2010-03-24
For resolve this problem you can try to link the new library with the old tiping in terminal:

sudo -i
cd /lib
ln libexpat.so.1 libexpath.so.0



in this way I have resolved my problem.

---

### Post by fundoonick on 2010-07-15
Hey,
Thx chcip for sharing your solution.
I have tried it, but its not working for me. I still get the same error.
Can anyone suggest something else which I can try.

Also, I am nt sure about where it is looking for the file, so I have copied it to /usr/local/lib, /usr/lib and even /lib.
The file was originally at /usr/lib. But I copied it to /usr/local/lib because it has happened to me many times that a program I am running is not able to find a library which is present at /usr/lib. I copy it to /usr/local/lib and it works.
But here, chcip had mentioned /lib, so I even tried that, but none of it is working.
Any help will be highly appreciated!

---

### Post by scsever on 2010-07-16
I'm having the same problem trying to install Wink.  I have the latest version of libexpat1 but can not find any libexpat* in Lucid Lynx.  Any other suggestions?

```
sudo apt-get install libexpat1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libexpat1 is already the newest version.
```


```
/usr/lib$ locate libex*
/usr/lib/libexif.so.12
/usr/lib/libexif.so.12.3.1
/usr/lib/libexiv2.so.6
/usr/lib/libexiv2.so.6.0.0
/usr/lib/libexslt.so.0
/usr/lib/libexslt.so.0.8.15
```

Thanks,

---

### Post by scsever on 2010-07-16
My bad... in my previous post I was searching /usr/lib following the instructions from another help site but I should have been searching /lib which is where libexpat.so.1 is.  Then I notice that there was an error in one of the previous posts that stated to do:

```
sudo ln libexpat.so.1 libexpath.so.0
```


The correct command would be:

```
sudo ln libexpat.so.1 libexpat.so.0
```

This worked to get Wink installed.

Thanks,

---

### Post by tonywhelan on 2011-08-26
> **scsever said:**
> My bad... in my previous post I was searching /usr/lib following the instructions from another help site but I should have been searching /lib which is where libexpat.so.1 is. .....

**I'm using Ubuntu Natty (32 bit) and libexpat is installed somewhere altogether different, in /lib/i386-linux-gnu**

so: ```
sudo ln /lib/i386-linux-gnu/libexpat.so.1 libexpat.so.0
```

---

