---
title: "install files with old dependencies ... how?"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by BananaPeal on 2011-02-19
Hello,

I'm trying to install software that requires libstdc++5 and v6 is installed on 10.04. I downloaded and installed v5 from [http://packages.debian.org/squeeze/libstdc++5](http://packages.debian.org/squeeze/libstdc++5)

it now lists a bunch of libstdc++5 files in the usr/lib folder, as shown in image.

When I try the install script it produces error:

```
root@alexDesk:/mnt# /mnt/dsrc/i486_linux/obj/redirect: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```
However, take a look at my usr/lib screenshot:

libstdc++.so.5 is indeed there as a sym link to libstdc++.so.5.0.7 on line 2.

How might I fix this? 

FYI, The filesystem in mnt is a looped iso. (mount -o loop -t iso9660)

Please let me know what to do next, I'm rather stuck and can't even think of what to look up next...

Thanks for your help!

---

### Post by BananaPeal on 2011-02-19
Screenshot of usr/lib:

---

### Post by n-n-nebbl on 2011-02-19
already tried the ubuntu (and not the debian) version of libstc++5?

[http://packages.ubuntu.com/hardy/libstdc%2B%2B5](http://packages.ubuntu.com/hardy/libstdc%2B%2B5)

maybe you search for a newer one than hardy ;)

---

### Post by gmargo on 2011-02-19
If you have the **lucid-backports** repository enabled, you can install it from there.

[http://packages.ubuntu.com/lucid-backports/libstdc++5](http://packages.ubuntu.com/lucid-backports/libstdc++5)

---

### Post by BananaPeal on 2011-02-19
> **gmargo said:**
> If you have the **lucid-backports** repository enabled, you can install it from there.

[http://packages.ubuntu.com/lucid-backports/libstdc++5](http://packages.ubuntu.com/lucid-backports/libstdc++5)

OK so after downloading, I tried these commands:
```
alex@alexDesk:~/Downloads$ ls
ati-driver-installer-11-2-x86.x86_64.run
fglrx-install.OwaZLn
flashplayer10_2_p3_64bit_linux_111710.tar.gz
libstdc++5_3.3.6-20~lucid1_amd64.deb
alex@alexDesk:~/Downloads$ dpkg -i libs*
dpkg: requested operation requires superuser privilege
alex@alexDesk:~/Downloads$ sudo dpkg -i libs*
[sudo] password for alex: 
(Reading database ... 124988 files and directories currently installed.)
Preparing to replace libstdc++5 1:3.3.6-20~lucid1 (using libstdc++5_3.3.6-20~lucid1_amd64.deb) ...
Unpacking replacement libstdc++5 ...
Setting up libstdc++5 (1:3.3.6-20~lucid1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
alex@alexDesk:~/Downloads$ 

```

However, the lib folder still looks like:

```
lrwxrwxrwx  1 root root       18 2011-02-19 16:35 libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r--  1 root root   829320 2010-11-02 18:16 libstdc++.so.5.0.7
lrwxrwxrwx  1 root root       19 2011-02-18 08:44 libstdc++.so.6 -> libstdc++.so.6.0.13
-rw-r--r--  1 root root  1044112 2010-03-26 20:16 libstdc++.so.6.0.13

```

same error:
```
root@alexDesk:/mnt# /mnt/dsrc/i486_linux/obj/redirect: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


```

So is it just a matter of finding a libstdc++.so.5 file exactly, like not one that points to libstdc++.so.5.0.7 as shown in the ls output?

Thanks for your time,

---

### Post by n-n-nebbl on 2011-02-19
what are you trying to install?

and do you really have an i486 cpu?
even if you have one, try to install a i386 version of the programm.
maybe it searches for an i486 version of libstdc++5 and gets an error while trying to load the i386 version

---

### Post by slakkie on 2011-02-19
wat does ldd say?

ldd /mnt/dsrc/i486_linux/obj/redirect

Because your setup looks good..

---

### Post by BananaPeal on 2011-02-19
Hello,

I think i486 is just a folder name that they thought was appropriate for their linux stuff...

Didn't know about ldd!! anyways, results:

```
root@alexDesk:/mnt# ldd /mnt/dsrc/i486_linux/obj/redirect
	linux-gate.so.1 =>  (0xf77c5000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf77b1000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7798000)
	librt.so.1 => /lib32/librt.so.1 (0xf778e000)
	libstdc++.so.5 => not found
	libm.so.6 => /lib32/libm.so.6 (0xf7768000)
	libc.so.6 => /lib32/libc.so.6 (0xf760e000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf75ef000)
	/lib/ld-linux.so.2 (0xf77c6000)
root@alexDesk:/mnt# 
```

So it apparently doesn't like libstdc++.so.5 linking to libstdc++.so.5.0.7 ... am I interpreting that correctly?

thing is i can't find another copy. looks like it's 5.0.7 everywhere...

---

### Post by slakkie on 2011-02-19
That's a wrong interpretation. I think it is weird that it doesn't work. But as a quick fix:

export LD_LIBRARY_PATH=/usr/lib

and then run the ldd command again, it should now find it. Why it doesn't find it in the first place, beats me.

You run 64 bit Ubuntu right? (if not sure, run: getconf LONG_BIT, 32 is 32 bit, 64 is 64 bit ;))

---

### Post by BananaPeal on 2011-02-19
Yessir this is 64bit linux. With a 64 bit video card. Hopefully will be able to use the two for math one day.

my commands were fruitless... :( but not quite:

also, using the lucid-backports version of libstc++5. Figured its more appropriate than hardy version.

```

root@alexDesk:/# export LD_LIBRARY_PATH=/usr/lib

root@alexDesk:/mnt# /mnt/dsrc/i486_linux/obj/redirect: error while loading shared libraries: libstdc++.so.5: wrong ELF class: ELFCLASS64

root@alexDesk:/mnt# ldd /mnt/dsrc/i486_linux/obj/redirect
	linux-gate.so.1 =>  (0xf770a000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf76f6000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf76dd000)
	librt.so.1 => /lib32/librt.so.1 (0xf76d3000)
	libstdc++.so.5 => not found
	libm.so.6 => /lib32/libm.so.6 (0xf76ad000)
	libc.so.6 => /lib32/libc.so.6 (0xf7553000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7534000)
	/lib/ld-linux.so.2 (0xf770b000)

root@alexDesk:/mnt# echo LD_LIBRARY_PATH
LD_LIBRARY_PATH
root@alexDesk:/mnt# echo $LD_LIBRARY_PATH
/usr/lib



```

So what do you think the elf class thing is about now? Does it not like 64 bits?

---

### Post by gmargo on 2011-02-19
Your unnamed software is 32-bit, so you need the 32-bit compatibility library.  It would probably be called lib32stdc++5, but I don't know of a source at this time.

Update: here's a probable source:
[https://launchpad.net/~jason-scheunemann/+archive/ppa/+buildjob/1458644]("https://launchpad.net/%7Ejason-scheunemann/+archive/ppa/+buildjob/1458644")

---

### Post by BananaPeal on 2011-02-20
HOwdy folks,

I'm now getting a 64bit libXm.so.3 error. After prodding online it seems like i need a lib32 version of openMotief ... is it possible to do this by taking the proper openMotief version in i386 form and simply dropping the usr/ files into lib32 then sym linking from the lib to the lib32 files in each case?

Has anyone else ever had to do this? Would I have to actually "build" it on my system as 32 bit then drop it in the lib32 folder?

ugh. sorry for the barrage of questions... installing software's vastly different than anything I've had to do in the past. Quite honestly I'm getting scared of trying anything that doesn't come thru the synaptic package manager again...

Thanks for your support,

---

### Post by gmargo on 2011-02-20
> **BananaPeal said:**
> I'm now getting a 64bit libXm.so.3 error. 

Install the **ia32-libs** package.  It contains **libXm.so** (and many other libraries) compiled appropriately for 32-bit support on a 64-bit system.

---

### Post by BananaPeal on 2011-02-20
> **gmargo said:**
> Install the **ia32-libs** package.  It contains **libXm.so** (and many other libraries) compiled appropriately for 32-bit support on a 64-bit system.

Done.

Now error turns to: 
```
root@alexDesk:/mnt# /mnt/dsrc/i486_linux/obj/redirect: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

```

Out of desperation, i renamed the libXm.so.3 that exists in lib to libXmOLD.so.3 then I backed out to filesystem and used command:

```
root@alexDesk:/# ln -s usr/lib32/libXm.so.3 usr/lib/libXm.so.3

```

to force it to go to the lib32 version. still no luck. both files exist in their respective lib and lib32 directories. 

any thoughts?

Thanks.

---

### Post by slakkie on 2011-02-20
Haha, there is no lib64stdc++5 available, afaics

Try to install one of these:
[http://packages.ubuntu.com/search?suite=all&arch=amd64&searchon=names&keywords=libstdc%2B%2B5](http://packages.ubuntu.com/search?suite=all&arch=amd64&searchon=names&keywords=libstdc%2B%2B5)

---

### Post by BananaPeal on 2011-02-20
> **slakkie said:**
> Haha, there is no lib64stdc++5 available, afaics

Try to install one of these:
[http://packages.ubuntu.com/search?suite=all&arch=amd64&searchon=names&keywords=libstdc%2B%2B5](http://packages.ubuntu.com/search?suite=all&arch=amd64&searchon=names&keywords=libstdc%2B%2B5)

Mr. Slakkie, lib32stdc++ is no longer the problem, ldd finds it, just now libXm.so.3 is giving trouble and I don't understand why I can find all the libXm.so.3 on the system just fine but it can't. How does it look for these anyways? Certainly exist in the directories all other so's are hanging out in...

fyi, lib32stdc++ from lucid-backports is installed, as is uhm. ... the lib32 equivalent. er/ see attachment.

There's a sym link going from the lib directory that has libstdc++5 and points to the equiv. lib32 file, lib32c++5.

libXm.so.3 is now not found. How/why, not sure. this is gnawing at my soul.

---

