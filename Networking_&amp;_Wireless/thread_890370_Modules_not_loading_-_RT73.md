---
title: "Modules not loading - RT73"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by Espionage on 2008-08-15
I'm currently running Ubuntu 7.10 PowerPC from a PS3.  I'm still a VERY fresh linux user, and can't quite remember everything I did when I first installed it, but I'm running an edited 2.6.24 to make the PS3's wifi work correctly, and the default kernel is 2.6.22-14-cell.  

Even with wifi fixed, the PS3's wireless card drops my connection too often, so I want to use an Asus WL-167G USB adapter, and I keep receiving problem after problem.

I've followed the guide here:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Everything works fine until I get to this part:

```
sudo modprobe rt73
```

I get an error saying that the module could not be found.

I then looked at the make install log, and it is using "linux-headers-2.6.22-14-powerpc" and the kernel that I'm running on is 2.6.24.  I did a quick googlesearch and a "solution" that somebody posted gave this:

```
sudo cp /lib/modules/2.6.22-14-powerpc/extra/rt73.ko /lib/modules/2.6.24/extra/rt73.ko
```

I then tried that method and did sudo modprobe rt73 again.  It gives this error now:

```
FATAL: Error inserting rt73 (/lib/modules/2.6.24/extra/rt73.ko): Invalid module format
```

The only thing I can think of is that it's using the headers of the original kernel, and I don't have any 2.6.24 headers.  I tried looking for 2.6.24 headers, but each one said "Error: Dependency is not satisfiable"

I then did:
```
aptitude search linux-headers
``` 
and all that came up in the list were 2.6.22.

I have no clue what to do now, and it's driving me insane.  Is there ANY way that it'll work?

---

### Post by Ayuthia on 2008-08-15
> **Espionage said:**
> I'm currently running Ubuntu 7.10 PowerPC from a PS3.  I'm still a VERY fresh linux user, and can't quite remember everything I did when I first installed it, but I'm running an edited 2.6.24 to make the PS3's wifi work correctly, and the default kernel is 2.6.22-14-cell.  
What do you mean by an edited 2.6.24?  Did you compile the kernel by source?  If so, you will have to check and see if the rt73 module is in the kernel and add it if it is.  If it is not there, you will have to compile the module.

As for the missing headers, you should check /usr/src and see what is out there for 2.6.24.

If not of this makes any sense, please post the results of:
```
uname -a
ls -l /usr/src
```
This will help us see what kernel you are using along with what headers are out there.

---

### Post by Espionage on 2008-08-15
> **Ayuthia said:**
> What do you mean by an edited 2.6.24?  Did you compile the kernel by source?  If so, you will have to check and see if the rt73 module is in the kernel and add it if it is.  If it is not there, you will have to compile the module.

As for the missing headers, you should check /usr/src and see what is out there for 2.6.24.

If not of this makes any sense, please post the results of:
```
uname -a
ls -l /usr/src
```
This will help us see what kernel you are using along with what headers are out there.
Hi, thanks for the response.

I BELIEVE that I followed a tutorial to compile my own 2.6.24 to allow the wireless to work on the PS3, It was a year and a half ago so I can't really remember.

In /usr/src I have the following:
```
linux-headers-2.6.22-14
linux-headers-2.6.22-13-powerpc
linux-headers-2.6.22-14-powerpc64-smp
linux-headers-2.6.22-15
linux-headers-2.6.22-15-powerpc
```

In /lib/modules I have:
```
2.6.22.14-cell
2.6.22-14-powerpc
2.6.22-14-powerpc64-smp
2.6.22-15-cell
2.6.22-15-powerpc
2.6.24
```

Doing uname -a I receive:
Linux ubuntu-ps3 2.6.24 #1 SMP Thu Jan 31 16:25:19 JST 2008 ppc64 GNU/Linux

Oh, right.  There was one other thing I had forgotten to mention.  When I tried compiling the rt73 source, it gave an error..umm.. think it was
```
File/directory build not found, cannot proceed
```
Or something along those lines.  So I just decided to cp the build folder from 2.6.22-powerpc into 2.6.24 in /lib/modules.  Totally forgot about that, but that might be the problem..

*edit* here's the error that I had received:
```
make: *** /lib/modules/2.6.24/build: No such file or directory.  Stop.
```

Which is weird, because I do apt-get install build-essential and it says it's already up-to-date.

---

### Post by Ayuthia on 2008-08-15
> **Espionage said:**
> Hi, thanks for the response.

I BELIEVE that I followed a tutorial to compile my own 2.6.24 to allow the wireless to work on the PS3, It was a year and a half ago so I can't really remember.

In /usr/src I have the following:
```
linux-headers-2.6.22-14
linux-headers-2.6.22-13-powerpc
linux-headers-2.6.22-14-powerpc64-smp
linux-headers-2.6.22-15
linux-headers-2.6.22-15-powerpc
```

Oh, right.  There was one other thing I had forgotten to mention.  When I tried compiling the rt73 source, it gave an error..umm.. think it was
```
File/directory build not found, cannot proceed
```
Or something along those lines.  So I just decided to cp the build folder from 2.6.22-powerpc into 2.6.24 in /lib/modules.  Totally forgot about that, but that might be the problem..

*edit* here's the error that I had received:
```
make: *** /lib/modules/2.6.24/build: No such file or directory.  Stop.
```

Which is weird, because I do apt-get install build-essential and it says it's already up-to-date.

Yes, the two problems that you are encountering is that you are missing the headers and module folders for 2.6.24.  Generally when a kernel is compiled, it is helpful to keep the header files and the modules.  You might want to see if you still have the kernel source when you compiled the code.  Otherwise, you might have to get the kernel source again and compile the kernel.

The build-essential package only allows you to compile code.  It only provides the necessary compiling headers (the C, C++ headers), but it does not provide the kernel headers.

---

### Post by Espionage on 2008-08-15
Quick question.

This link isn't what I originally followed for my version of 2.6.24, but could you look over the steps and tell me if it'll result in the 2.6.24 headers?

[http://psubuntu.com/wiki/Setup](http://psubuntu.com/wiki/Setup)
*edit* Nope..that didn't solve the problem.  Turns out, that IS the guide I followed last year.  Which is why I don't have these folders >_<.

Could you please tell me if this is what I'm supposed to do?

I download linux-2.6.24.tar.bz2 and extract it.

I then did the following:
```
cd Desktop/linux-2*
make oldconfig
make
```

make oldconfig works fine, but once I type in 'make' it begins to go smooth, but then freezes up on one of the files each time.

---

### Post by Ayuthia on 2008-08-16
> **Espionage said:**
> Quick question.

This link isn't what I originally followed for my version of 2.6.24, but could you look over the steps and tell me if it'll result in the 2.6.24 headers?

[http://psubuntu.com/wiki/Setup](http://psubuntu.com/wiki/Setup)
*edit* Nope..that didn't solve the problem.  Turns out, that IS the guide I followed last year.  Which is why I don't have these folders >_<.

Could you please tell me if this is what I'm supposed to do?

I download linux-2.6.24.tar.bz2 and extract it.

I then did the following:
```
cd Desktop/linux-2*
make oldconfig
make
```

make oldconfig works fine, but once I type in 'make' it begins to go smooth, but then freezes up on one of the files each time.

Where did you get the .config file from?  You might need to use one of the most recent 2.6.22 powerpc linux-headers folder.  I would make a backup copy of the .config file that is in Desktop/linux-2* first.  Then I would copy the .config file from /usr/src/linux-2.6.22-15-powerpc to ~/Desktop/linux-2*.  You can then try the make oldconfig commands again.

I will say that I have never compiled on a PS3 before so I don't know what needs to be configured in the kernel for it (Because I don't know the hardware in it).  However, if you are able to use the 2.6.22-*-powerpc kernels, that .config file should be a good start.  I have always copied my linux-2.6.* folder into /usr/src (I don't know if that is the recommended place) and then ran
```
sudo make oldconfig
sudo make && sudo make modules_install
```
If that all compiles correctly, it should create a bzImage file in /usr/src/linux-2.6.24*/arch/powerpc/boot.

Hope that helps.

You might also read the README file in the linux-2.6.24 folder.

EDIT:
You might even try copying the linux-2.6.24 folder over to /usr/src and see if you can compile the rt73 module.  That might just be all you need.  I am not 100% sure about this though, but I would think that the linux-2.6.24 folder would have the headers you need.  I am just not for sure if anything else is missing though.

---

### Post by Espionage on 2008-08-16
I'm not sure where I got the oldconfig from, the guide just said to try "make xconfig" and if that didn't work, to use "make oldconfig"

I'll try out what you said later today, thanks.

Even with the headers, don't I still need a build folder inside lib/modules/2.6.24?  Right now /lib/modules/build says something like this:
Target: Link (broken)
instead of a folder.

---

### Post by Ayuthia on 2008-08-16
> **Espionage said:**
> I'm not sure where I got the oldconfig from, the guide just said to try "make xconfig" and if that didn't work, to use "make oldconfig"

I'll try out what you said later today, thanks.

Even with the headers, don't I still need a build folder inside lib/modules/2.6.24?  Right now /lib/modules/build says something like this:
Target: Link (broken)
instead of a folder.
From what I can tell, /lib/modules/build shoud point to the /usr/src/linux-2.6.24.  To see what it is pointing to:
```
ls -l /lib/modules/2.6.24/build
```
If it is not pointing to /usr/src/linux-2.6.24, then you will need to update it.  Of course, this is assuming that you copied linux-2.6.24 over to /usr/src:
```
sudo rm /lib/modules/build
sudo ln -s /usr/src/linux-2.6.24 /lib/modules/2.6.24/build
```

---

### Post by Espionage on 2008-08-16
> **Ayuthia said:**
> From what I can tell, /lib/modules/build shoud point to the /usr/src/linux-2.6.24.  To see what it is pointing to:
```
ls -l /lib/modules/2.6.24/build
```
If it is not pointing to /usr/src/linux-2.6.24, then you will need to update it.  Of course, this is assuming that you copied linux-2.6.24 over to /usr/src:
```
sudo rm /lib/modules/build
sudo ln -s /usr/src/linux-2.6.24 /lib/modules/2.6.24/build
```
Did the ls -l command, it said that build was pointing to /export3/snapshot/.work/linux-2.6.24.  Just fixed it using your method.  Thanks.

Now I'm trying to compile the kernel, each time it freezes up here:
```

LD     .tmp_vmlinux1
KSYM   .tmp_kallsyms1.5
AS     .tmp_kallsyms1.0
LD     .tmp_vmlinux2
```
And then I receive this:
```

The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".
Do you want to delete the applet from your configuration?
```

Just kept trying to compile it, now I receive:
```
LD     vmlinux.o
ld: final link failed: Memory exhausted
```

Great, it runs out of RAM.  I'll try making a swap file..

*edit* Greatx2.  sudo make modules && sudo make modules_install worked, but now 2.6.24 won't boot.

```
* Setting the system clock    [OK]
* Loading kernel modules...
* Loading manual drivers...

```
It goes through a list of a few things, then just quits doing anything, just a blinking underscore.

---

### Post by Ayuthia on 2008-08-16
> **Espionage said:**
> 
*edit* Greatx2.  sudo make modules && sudo make modules_install worked, but now 2.6.24 won't boot.

```
* Setting the system clock    [OK]
* Loading kernel modules...
* Loading manual drivers...

```
It goes through a list of a few things, then just quits doing anything, just a blinking underscore.

I don't have a good answer here.  If the last thing that was logged was loading manual drivers, it might be an issue with modules in /etc/modules but that is a guess.  You might check dmesg.0.log (in /var/log) and see if there are any messages that might help tell you where it is getting stuck. If you can find the part that is getting stuck, you might be able to disable it in the kernel compile (via make menuconfig).

---

### Post by Espionage on 2008-08-17
> **Ayuthia said:**
> I don't have a good answer here.  If the last thing that was logged was loading manual drivers, it might be an issue with modules in /etc/modules but that is a guess.  You might check dmesg.0.log (in /var/log) and see if there are any messages that might help tell you where it is getting stuck. If you can find the part that is getting stuck, you might be able to disable it in the kernel compile (via make menuconfig).

I've just decided that my kernel was too screwed up to continue.  I've formatted and installed ubuntu 7.04 feisty, and am currently updating.  Will get back to you on status of the rt73 drivers.

---

