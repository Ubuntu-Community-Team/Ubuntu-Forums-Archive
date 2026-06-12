---
title: "Belkin F5D6050 in Breezy"
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by murkin on 2005-10-18
I hate to do a repost of sorts, but the original thread is listed under the Warty Warthog --> networking section, and it's gotten all of one view since i posted a question there.
so...mods, please forgive me!

[http://www.ubuntuforums.org/showthread.php?t=5164](http://www.ubuntuforums.org/showthread.php?t=5164)

The original quote is as follows:
[INDENT]"I've just got my Belkin F5D6050 working with hoary.  To do so, I followed this simple 17 step process:

I added the hoary/multiverse to my /etc/apt/sources.list, then did:

```
apt-get install at76c503a-source atmel-firmware
```

(and made sure that I had the linux-headers installed, in my case linux-headers-k7).  Then:

```

cd /usr/src
tar xvzf at76c503a.tar.gz
cd modules/at76c503a
debian/rules binary-modules KVERS=2.6.10-5-k7
cd ..
dpkg -i <modulename.deb>
depmod -a

```[/INDENT]


i've gotten all the way to:

/usr/src/modules/at76c503a$

sudo debian/rules binary-modules KVERS=2.6.12-9-386  (i used i386 rather than k7 for obvious reasons)

at this point the "rules" file runs a script which searches for and copies files from:

/lib/modules/2.6.12-9-386/build/.tmp_versions/*.mod

maybe this could be found in previous versions of the kernel or warty/hoary, but I can't find these folders or directories anywhere on my system. to be more specific, i get to /lib/modules/2.6.12-9-386 but can't find the /build directory.

i've tried searching for hidden files and folders; am i missing a package?

this is driving me crazy!!

Thanks in advance! :confused:

---

### Post by murkin on 2005-10-18
ok, it seems i've gotten slightly closer to success.
i needed to install the build-essential package. this, however created a /build directory under /lib/modules/2.6.12-9-386/ but the full linux-headers folder (under /usr/src) did not include the "-386" in the folder name. the only folder there with "-386" in its name appeared to have a whole bunch of shortcuts (forgive the M$ lingo). i created a duplicate linux-headers folder and renamed the new one with "-386" at the end of the directory name.

now the issue i ran into was that upon runing the script, i was getting a few new error messages. among them a "not found" error for gcc-3.4 and also a missing file called Module.symvers. after some searching online, i found out that this file is created during a compile of the linux kernel from source. i don't actually intend to use the recompiled kernel, but i need that file!!

so... i got downloaded all the files onto my laptop, transferred to my flash drive, and installed them on my desktop using dpkg... (the one having all these problems). the packages needed were gcc-3.4, gcc-3.4 base, and cpp-3.4.

latest error..."no rule to make target 'init/main.o', needed by 'init/built-in.o'.

---

### Post by murkin on 2005-10-19
well, it's working now. god only knows how. i'm trying to piece it all together. after giving up briefly, i looked under my linux-headers folder (there had been one folder named 2.6.12-9 and one named 2.6.12-9-386). The second one was just a bunch of links/references to the folder without the "-i386" in the name. anyway, within the "-i386" folder i found the Module.symvers file. strange.

i ran the "rules" script again and got yet another error. this time, it was related to the debhelper package. i installed that off the cd, ran the script again. and it actually went through! a .deb was created. i installed it by following the instructions on the original post. 

finally, to activate the hardware, i typed in a command similar to the one listed in the original post. instead of:
modprobe -v at76c503a-rfmd-acc

i typed:
modprobe -v at76c503-rfmd-acc  (notice the missing a).

i really don't know why the differences, but there just wasn't a file named at76c503a... in my modules folder.

anyway, i'm online! i hope to come back to this post and clean it up a bit some time. this was such a headache to get up and running and i'd hope that no one else has such a hard time with this!

---

### Post by Billy_McSkintos on 2006-05-07
Could anybody help me get this working via an XP PC? I'd like to download the files and then transfer them to the ubuntu box and then get it running...

---

