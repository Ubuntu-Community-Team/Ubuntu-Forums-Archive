---
title: "ubuntu not rebooting properly after failed update"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by thesaintlyone@live.com on 2011-04-04
Hi 
Following an attempt to install updates, I am now unable to boot into ubuntu as normal
I am running ubuntu 10.10 on an aspire one netbook!!!!


When I turn on the Netbook I am faced with a black screen with the following at the top
GNU GRUB Version 1.98+20100804-5ubuntu3
Below these are 4 options
1)Ubuntu, with Linux 2.6.35-22-generic (This goes to a normal desktop type screen but the mouse shown will not move nor click)
Plus 2 system monitoring options

2) Is the same as above but recovery mode, when I click on this it scrolls through text and ends on the following
begin: Running /scripts/init-bottom ... done

I am completely stuck!!!!

---

### Post by Hedgehog1 on 2011-04-05
Here is a possible solution:

Go ahead and boot to 'Ubuntu, with Linux 2.6.35-22-generic' (I know the mouse is stuck).

Once the GUI is up, press this key combo to get s terminal:

[ctrnl] + [alt] + 't'

If your keyboard is working, you will get the terminal and the type:

```
sudo apt-get update
```

and then:

```
sudo apt-get install
```

This will complete the update that was interrupted (we hope).

A reboot will then tell us if my *'Hedgie sense'* is working today...

***The Hedge***

:KS

---

### Post by matt_symes on 2011-04-05
Hi

> **thesaintlyone@live.com said:**
> Hi 
Following an attempt to install updates, I am now unable to boot into ubuntu as normal
I am running ubuntu 10.10 on an aspire one netbook!!!!


When I turn on the Netbook I am faced with a black screen with the following at the top
GNU GRUB Version 1.98+20100804-5ubuntu3
Below these are 4 options
1)Ubuntu, with Linux 2.6.35-22-generic (This goes to a normal desktop type screen but the mouse shown will not move nor click)
Plus 2 system monitoring options

2) Is the same as above but recovery mode, when I click on this it scrolls through text and ends on the following
begin: Running /scripts/init-bottom ... done

I am completely stuck!!!!

That sound very much to me like the last attempt to build initramfs failed badly for some reason. After some updates are when it gets rebuilt.

After unpacking one of my initramfs archives. Look familiar ?

```
matthew@matthew-laptop:~$ ls data/initramfs/scripts/
functions  init-bottom  init-top  local  local-bottom  local-premount  nfs  nfs-top  panic
matthew@matthew-laptop:~$
```

I think you need to rebuild your initramfs. This is the command you will need.

```
sudo update-initramfs -u
```

First try to boot into an older kernel and run the command. If that does not work you will need to chroot using a LiveCD/USB.

Assuming there is no corruption to your files in /usr/share/initramfs-tools or your system binaries then hopefully this will work.

Kind regards

---

