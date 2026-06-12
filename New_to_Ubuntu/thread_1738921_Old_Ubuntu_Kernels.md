---
title: "Old Ubuntu Kernels"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by user_linux on 2011-04-25
Hello, I am trying to remove the old ubuntu kernels from my desktop. I  tried deleting it when it starts, but it re-appears again. Help anyone? 
Thanks!

---

### Post by matt_symes on 2011-04-25
Hi

Install ubuntu-tweak and do it from there.

```
sudo apt-get install ubuntu-tweak
```

Kind regards

---

### Post by Atrumow on 2011-04-25
I believe this thread will help you

[http://ubuntuforums.org/showthread.php?t=1513200](http://ubuntuforums.org/showthread.php?t=1513200)

I just fixed the same problem using Ubuntu Tweak :)

---

### Post by 3177 on 2011-04-25
you will probably want to just edit grub.cfg
that way if something goes wrong its just a ```
sudo update grub
```away.

---

### Post by Karlchen on 2011-04-25
Hi, folks.

I do not quite see why any additional software like Ubuntu-tweak may be needed in order to 
[LIST]
[*]remove old kernels from the disk and
[*]remove entries referencing these old kernels from the grub boot menu
[/LIST]
It may be convenient to use Ubuntu-tweak for this purpose. But it is not really necessary to do so.
Synaptic Package Manager is perfectly capable of fulfilling these two tasks for you. :)

_**Beware:**_
No matter which way you go in order to remove old kernels from the disk and from the grub boot menu, make *triple* sure you know what your current kernel number is and that you do not touch the current kernel by accident. :!:

_**Example on how to proceed:**_
Let us assume we want to remove the kernel having the version number **2.6.32-29**.
(v2.6.32-31 is the current kernel on Lucid Lynx, and personally I will keep the previous kernel, i.e. v2.6.32-30, just in case ...)
So did remove kernel v**2.6.32-29** only yesterday.

[LIST]
[*]Go to System => System Administration => Synaptic Package Manager.
[*]Enter you password when prompted.
[*]Select the section "Installed" in order to reduce the list of displayed packages.
[*]In the quick filter field enter "linux-". (without the double quotes)
[*]In the list mark each of the following 3 items, right click it and select "Mark for complete removal":
[+] linux-headers-**2.6.32-29**
[+] linux-headers-**2.6.32-29**-generic
[+] linux-image-**2.6.32-29**-generic
It is always these 3 packages, only the version numbers will vary.
[*] Click on the "Apply" button
[*] Confirm your selection.
[*] Synaptic will uninstall the selected kernel packages first and make sure next that the grub menu is modified accordingly.
[*]Job done.
[/LIST]
To be honest, it is the same procedure that is explained in [the thread linked to two posts above]("http://ubuntuforums.org/showthread.php?t=1513200"). ;)

HTH,
Karl

---

### Post by matt_symes on 2011-04-25
Hi

> I do not quite see why any additional software like Ubuntu-tweak may be needed in order to
remove old kernels from the disk and
remove entries referencing these old kernels from the grub boot menu

You are correct. Ubuntu tweak just makes it very easy. It's a useful application to have installed as well.

Kind regards

---

### Post by collisionystm on 2011-04-25
sudo apt-get autoremove

---

### Post by domu on 2011-04-26
sudo apt-get autoremove does not remove old kernels

ubuntu-tweak is good, also you can use my remove-kernel script which can be run (with sudo) from a terminal window, or if you are using Ubuntu Server. See [TimeDicer]("http://www.timedicer.co.uk/") - in the 'My Programs' section. It's easier than synaptic, here is the help:
```

Shows installed Linux kernels in a Debian-based distro, and can remove
superfluous ones, including related packages, updating Grub appropriately. Does
not require a GUI. You are prompted before any dangerous stuff happens, and it
will not allow removal of the kernel that is currently in use, but should still
be used with care: once a kernel is gone, it's gone!

Tested under Ubuntu 10.04 and 10.10. Does not work under Lubuntu (because
kernel packages are differently named).

Usage    : remove-kernel [options] [kernelnumbertoremove-filter]
Example 1: ./remove-kernel              # list kernel packages and exit
Example 2: ./remove-kernel 2.6.32-24    # remove 2.6.32-24 kernel
Example 3: ./remove-kernel 2.6.32       # remove all 2.6.32-* kernels

```

---

### Post by 73ckn797 on 2011-04-26
The simple way that I do it is to go into Synaptic Package manager and  look for the linux-* kernel listings. Then select those for complete  removal that are not what you want, such as: linux-headers-(version  number), linux-image-(version number) & linux-image-(version  number)-generic (or also pae).

Then run in terminal:
```
 sudo update-grub
```

Works every time for me.

---

### Post by user_linux on 2011-04-26
> **Karlchen said:**
> Hi, folks.

I do not quite see why any additional software like Ubuntu-tweak may be needed in order to 
[LIST]
[*]remove old kernels from the disk and
[*]remove entries referencing these old kernels from the grub boot menu
[/LIST]
It may be convenient to use Ubuntu-tweak for this purpose. But it is not really necessary to do so.
Synaptic Package Manager is perfectly capable of fulfilling these two tasks for you. :)

_**Beware:**_
No matter which way you go in order to remove old kernels from the disk and from the grub boot menu, make *triple* sure you know what your current kernel number is and that you do not touch the current kernel by accident. :!:

_**Example on how to proceed:**_
Let us assume we want to remove the kernel having the version number **2.6.32-29**.
(v2.6.32-31 is the current kernel on Lucid Lynx, and personally I will keep the previous kernel, i.e. v2.6.32-30, just in case ...)
So did remove kernel v**2.6.32-29** only yesterday.

[LIST]
[*]Go to System => System Administration => Synaptic Package Manager.
[*]Enter you password when prompted.
[*]Select the section "Installed" in order to reduce the list of displayed packages.
[*]In the quick filter field enter "linux-". (without the double quotes)
[*]In the list mark each of the following 3 items, right click it and select "Mark for complete removal":
[+] linux-headers-**2.6.32-29**
[+] linux-headers-**2.6.32-29**-generic
[+] linux-image-**2.6.32-29**-generic
It is always these 3 packages, only the version numbers will vary.
[*] Click on the "Apply" button
[*] Confirm your selection.
[*] Synaptic will uninstall the selected kernel packages first and make sure next that the grub menu is modified accordingly.
[*]Job done.
[/LIST]
To be honest, it is the same procedure that is explained in [the thread linked to two posts above]("http://ubuntuforums.org/showthread.php?t=1513200"). ;)

HTH,
Karl

Hi Karl,
Thanks for this detailed procedure, but when I type in linux-, I only get **2.6.32.31.37**[B] and even then it asks for its installation, i dont see the three items u mentioned above for installation. Oh and btw, I didn't clarify this. I don't have old ubuntu kernels but duplicate kernels of same ubuntu version. Any thoughts on this?
Thanks.
[/B]

---

### Post by Dondermans on 2011-04-26
> **Karlchen said:**
> 
(...)
_**Beware:**_
No matter which way you go in order to remove old kernels from the disk and from the grub boot menu, make *triple* sure you know what your current kernel number is and that you do not touch the current kernel by accident. :!:
(...)

Just a minor addition: the kernel you are using at the moment can be viewed using:

System -> Administration -> System Monitor

Choose the 'System' tab.

---

### Post by dniMretsaM on 2011-04-26
How do I know what my current kernel number is?

EDIT: Never mind. Just saw the post above mine.

---

### Post by babybean on 2011-04-26
If you are planing on upgrading to 11.04 any time soon then you could leave them. Updating tends to auto remove the old ones for you.

---

### Post by dniMretsaM on 2011-04-26
> **matt_symes said:**
> Hi

Install ubuntu-tweak and do it from there.

```
sudo apt-get install ubuntu-tweak
```Kind regards

Is Ubuntu Tweak incompatible with 10.10? When I try apt-get install ubuntu-tweak I get:```
E: Unable to locate package ubuntu-tweak
```> **babybean said:**
> If you are planing on upgrading to 11.04 any  time soon then you could leave them. Updating tends to auto remove the  old ones for you.

Oh cool. I guess I can live with them for another few days. I still would like Ubuntu Tweak though...

---

### Post by matt_symes on 2011-04-26
Hi

> Is Ubuntu Tweak incompatible with 10.10? When I try apt-get install ubuntu-tweak I get:

You need to add  the Ubuntu tweak ppa

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

Kind regards

---

### Post by dniMretsaM on 2011-04-26
Awesome thanks.

---

### Post by user_linux on 2011-04-26
Hi,
I have 2.6.28-19 kernel. BUt I dont see this in my list of kernels?
> **domu said:**
> sudo apt-get autoremove does not remove old kernel
s

ubuntu-tweak is good, also you can use my remove-kernel script which can be run (with sudo) from a terminal window, or if you are using Ubuntu Server. See [TimeDicer]("http://www.timedicer.co.uk/") - in the 'My Programs' section. It's easier than synaptic, here is the help:
```

Shows installed Linux kernels in a Debian-based distro, and can remove
superfluous ones, including related packages, updating Grub appropriately. Does
not require a GUI. You are prompted before any dangerous stuff happens, and it
will not allow removal of the kernel that is currently in use, but should still
be used with care: once a kernel is gone, it's gone!

Tested under Ubuntu 10.04 and 10.10. Does not work under Lubuntu (because
kernel packages are differently named).

Usage    : remove-kernel [options] [kernelnumbertoremove-filter]
Example 1: ./remove-kernel              # list kernel packages and exit
Example 2: ./remove-kernel 2.6.32-24    # remove 2.6.32-24 kernel
Example 3: ./remove-kernel 2.6.32       # remove all 2.6.32-* kernels

```

---

### Post by matt_symes on 2011-04-26
Hi  

From a terminal type 

```
uname -r
```

to get your current kernel

```
dpkg -l | grep linux-image*
```

(small L after dpkg) will give you your list of installed kernels.

```
dpkg -l | grep $(uname -r)
```

will show you the installed packages for your current kernel.

Kind regards

---

### Post by domu on 2011-04-27
> **user_linux said:**
> Hi,
I have 2.6.28-19 kernel. BUt I dont see this in my list of kernels?

Hi user_linux, that seems weird. What version of Ubuntu are you using?

Please try this:

```
dpkg --get-selections|egrep "^(linux|kernel)"
```

and let us know what it shows. It should bring up a number of packages including your kernel images and headers.

---

### Post by user_linux on 2011-04-27
I'm using ubuntu 10.04 LTS but when I log in I see 2.6.28-18/19(generic) in my boot menu. By the way, my old ubuntu versions don't work either, so that's why I want to get rid of it. Here's my output:
kerneloops-daemon                install
linux-firmware                    install
linux-generic                    install
linux-headers-2.6.32-28                install
linux-headers-2.6.32-28-generic            install
linux-headers-2.6.32-31                install
linux-headers-2.6.32-31-generic            install
linux-headers-generic                install
linux-image-2.6.32-21-generic            install
linux-image-2.6.32-28-generic            install
linux-image-2.6.32-29-generic            deinstall
linux-image-2.6.32-31-generic            install
linux-image-generic                install
linux-libc-dev                    install
linux-sound-base                install

---

### Post by oldsoundguy on 2011-04-27
Once again, we have had several responses to this thread  insisting that everything has to be done the hard way.  
Ubuntu Tweak is a reliable program with a GUI and is much easier for a noob to use rather than cutting and pasting commands in terminal.

I have been using Linux since Mandrake 4 and ANYTHING that makes it easier is welcome in my book.  We do not have to prove we are geeks to use the system.  That is what scares off the noobs and continues to foster the "Linux is not for you because you are stupid" FUD!

---

### Post by domu on 2011-04-27
> **user_linux said:**
> I'm using ubuntu 10.04 LTS but when I log in I see 2.6.28-18/19(generic) in my boot menu. By the way, my old ubuntu versions don't work either, so that's why I want to get rid of it. Here's my output:
kerneloops-daemon                install
linux-firmware                    install
linux-generic                    install
linux-headers-2.6.32-28                install
linux-headers-2.6.32-28-generic            install
linux-headers-2.6.32-31                install
linux-headers-2.6.32-31-generic            install
linux-headers-generic                install
linux-image-2.6.32-21-generic            install
linux-image-2.6.32-28-generic            install
linux-image-2.6.32-29-generic            deinstall
linux-image-2.6.32-31-generic            install
linux-image-generic                install
linux-libc-dev                    install
linux-sound-base                install

hmm, I don't think you actually have 2.6.28-18/19(generic) because if you had it/they would have to appear in the list above. Something must have gone wrong at some point because the grub menu should only contain references to kernels you actually have. These seem to be 2.6.32-21, 2.6.32-28, 2.6.32-29 and 2.6.32-31. Which kernel does remove-kernel say you are using?

If you run ```
sudo update-grub
``` this should clean up the grub menu for you. Alternatively, if you delete a kernel (say 2.6.32-21, unless this is the one you are using) with remove-kernel this should have the same effect, I think.

---

### Post by user_linux on 2011-04-27
Ok, I see what u mean. My other ques is if I have to remove duplicate kernels of same ubuntu version from the boot menu, how can I do that? This is in reference to the other computer I have.
Thx a lot!
> **domu said:**
> hmm, I don't think you actually have 2.6.28-18/19(generic) because if you had it/they would have to appear in the list above. Something must have gone wrong at some point because the grub menu should only contain references to kernels you actually have. These seem to be 2.6.32-21, 2.6.32-28, 2.6.32-29 and 2.6.32-31. Which kernel does remove-kernel say you are using?
 
If you run ```
sudo update-grub
``` this should clean up the grub menu for you. Alternatively, if you delete a kernel (say 2.6.32-21, unless this is the one you are using) with remove-kernel this should have the same effect, I think.

---

### Post by JKyleOKC on 2011-04-27
> **user_linux said:**
> Ok, I see what u mean. My other ques is if I have to remove duplicate kernels of same ubuntu version from the boot menu, how can I do that? This is in reference to the other computer I have.
Thx a lot!That ghost entry for 2.6.28 just might be a leftover from an old grub configuration. Do a "ls /boot/grub" to see whether you have Grub Legacy or Grub 2 installed. If it's Grub 2, there will be many files with names ending in ".mod" present; if it's not, there won't be any like that.

All new installs for quite some time now have installed Grub 2, but if you started out several years ago when Grub Legacy was still the one being used and have simply upgraded since then, you may still have Grub Legacy in use.

There's a simple tool called "Grub Customizer" that you can use to prevent the older or duplicate entries from being displayed, but it works only with Grub 2. For Grub legacy, you have to edit the /boot/grub/menu.lst file to remove them.

---

### Post by domu on 2011-04-27
Yes Jim may well be right and you may have old grub. remove-kernel will also tell you which version of grub you are using, or you can do:
```
grub-install -v
```
and if you see a version less than 1.96 you are using grub legacy and not grub2 (sorry I know it is confusing that version 1.96 is grub2).

If you have grub legacy it would be worth upgrading to grub2. I'm not sure how to do that but let us know if that is the case and then others here will surely advise.

---

### Post by Paqman on 2011-04-27
> **oldsoundguy said:**
> Once again, we have had several responses to this thread  insisting that everything has to be done the hard way.  
Ubuntu Tweak is a reliable program with a GUI and is much easier for a noob to use rather than cutting and pasting commands in terminal.


I'm sure Ubuntu Tweak is fine. Personally I just use Synaptic. It's pretty straightforward and it's already installed. I wouldn't bother messing around with the terminal for a bit of routine maintenance like this either.

---

### Post by user_linux on 2011-04-28
Hi Jim,
My only concern now is there are multiple entries of the same ubuntu like 2.6.32-31/30/28/27/25/21 (both generic and recovery mode). I'm not sure which ones would be deleted. I'm using version 10.4 kernel 2.6.32-31 (generic). Btw, I have grub 1.98. Would these instructions hold same still?

Many thx!

> **JKyleOKC said:**
> That ghost entry for 2.6.28 just might be a leftover from an old grub configuration. Do a "ls /boot/grub" to see whether you have Grub Legacy or Grub 2 installed. If it's Grub 2, there will be many files with names ending in ".mod" present; if it's not, there won't be any like that.

All new installs for quite some time now have installed Grub 2, but if you started out several years ago when Grub Legacy was still the one being used and have simply upgraded since then, you may still have Grub Legacy in use.

There's a simple tool called "Grub Customizer" that you can use to prevent the older or duplicate entries from being displayed, but it works only with Grub 2. For Grub legacy, you have to edit the /boot/grub/menu.lst file to remove them.

---

### Post by domu on 2011-04-28
user_linux, did you try doing from a terminal window:```
sudo update-grub
```because this should rebuild your grub menu correctly.

BTW, if your grub says 1.98 then it is grub2, so that's okay.

---

### Post by JKyleOKC on 2011-04-28
> **user_linux said:**
> Hi Jim,
My only concern now is there are multiple entries of the same ubuntu like 2.6.32-31/30/28/27/25/21 (both generic and recovery mode). I'm not sure which ones would be deleted. I'm using version 10.4 kernel 2.6.32-31 (generic). Btw, I have grub 1.98. Would these instructions hold same still?

Many thx!Those are not "the same" ubuntu; they are different versions of the same major release (2.6.32). If everything is working properly with 2.6.32-21, you'll be safe to "remove completely" every package for 2.6.32-28, also 27, 25, and 21. That would reclaim about half a gigabyte of disk space for you since each release uses about 125 MiB of disk. Just be sure not to remove the -30 and -31 releases, and to run "update-grub" after doing the cleanup, to rebuild your grub menu.

---

### Post by oldsoundguy on 2011-04-28
yep .. I keep the latest 3 .. but I have a ton of disk space.  The latest two makes sense as it gives you go back and repair points that you can use from Grub. (but have had to utilize repair ONCE since I first installed Ubuntu 6.04, and that was because of an error in the NVida driver!)
(I should emphasize that I do NOT dual boot. Only Linux on Linux boxes and Windows on Windows boxes.)

---

