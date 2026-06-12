---
title: "No Wireless Dell Inspiron 1521 Laptop"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by swimstarguy on 2010-02-14
I just switched to 9.10 and am, once again, having wireless issues with my laptop.

I cannot get a wireless or a wired connection. Nothing. I went to System>Administration>Hardware Drivers and there's nothing in there to select/update.

I have tried to reinstall as well.

I have also been searching for ever in old threads and have found nothing that works. 

I would greatly appreciate any help. 

Here are some things that I've tried and info on the machine:

```
david@david-laptop:~$ uname -m 
i686 
david@david-laptop:~$ 
david@david-laptop:~$ ndiswrapper -l 
The program 'ndiswrapper' is currently not installed.  You can install it by typing: 
sudo apt-get install ndiswrapper-common 
ndiswrapper: command not found 
david@david-laptop:~$ sudo apt-get install ndiswrapper-comm 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
E: Couldn't find package ndiswrapper-comm 
david@david-laptop:~$  
david@david-laptop:~$ lsmod | grep ndis 
ndiswrapper           185404  0  
david@david-laptop:~$  

```

```
david@david-laptop:~$ dmesg | grep -e ndis -e wlan 
[ 3554.829120] ndiswrapper version 1.55 loaded (smp=yes, preempt=no) 
[ 3554.832154] usbcore: registered new interface driver ndiswrapper 
david@david-laptop:~$  

```

```
david@david-laptop:~$ lshw -C Network 
WARNING: you should run this program as super-user. 
  *-network UNCLAIMED      
       description: Network controller 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0b:00.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=0 
       resources: memory:fe8fc000-fe8fffff 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: BCM4401-B0 100Base-TX 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=64 
       resources: memory:fe5fe000-fe5fffff 
david@david-laptop:~$ 
```

```
david@david-laptop:~$ dmesg | grep -e ndis -e wlan 
[ 3554.829120] ndiswrapper version 1.55 loaded (smp=yes, preempt=no) 
[ 3554.832154] usbcore: registered new interface driver ndiswrapper 
david@david-laptop:~$  
blah blah blah...
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02) 
blah blah blah...
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
```


I do see where lshw -C Network has a few things marked as "unclaimed" I saw in a previous thread where you set the driver to claim the card, something about blacklisting the unneeded drivers. It didn't work, though I may have been doing it wrong.

I'm lost and I know I'm missing something simple that has already been solved for someone else.

Please, any help would be welcomed. I'm pounding my face against my desk.

---

### Post by swimstarguy on 2010-02-14
Hate to do this...
bump...

---

### Post by lemmy999 on 2010-02-14
```
product: BCM4311 802.11b/g WLAN 

```

Suggests that the wireless card has a Broadcom B43 chipset. You'll need to go to hardware drivers ( can't tell you where as I'm using CBL ATM) and click on that.It should detect your card and offer toinstall the driver for you ( need a wired connection to do this ) Reboot and voila- should be good to go

---

### Post by Megaptera on 2010-02-14
I know this talks about Dell Mini but this simple fix worked on my Dell Inspiron -

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

I think this is as suggested by lemmy999?

---

### Post by oldefoxx on 2010-02-14
I dug through a rat's nest online for weeks before I got my wireless to work.  It can depend very much on finding out which chipset and interface is being used, especially in laptops/notebooks.  Based on that info, you ought to be able to track down fixes for other machines that happen to use the same, and that can be important.

I know enough about ndiswireless to say it is not necessarily the only solution, and many say it may not be the best solution.  I could have at least tried to go with ndiswrapper, but to me that was a last ditch effort.  And guess what:  I am not using it, the solution for wireless finally fell into place after numerous approaches.

What most don't recognize, and I didn't myself, is that despite appearance and name brands, internally the wireless adapters out there only fit into a few categories, these being certain chip families.  And for each category, there are some choices as to drivers, and we may be talking about drivers for different OSes, drivers provided by different venders, and of course drivers that support different features when it comes to the three Wireless protocols, B, G, and N.

If you search, it would be a poor idea to include ndiswrapper as a part of the search term, because at this point, you just want something that works for you.  If you include Windows in the search term, then you are going right back to ndiswrapper, aren't you?

I'm afraid I can't help you further, except to make use of Linux where you can in discovering what you really have and how it is being treated.  You seem to be doing that.  I've yet to encounter a comprehensive guide on what to do or how to do it when setting up a wireless connection.  No idea what the story is with your wired adapter either.  It may be related, it may not.

One thing I can say is that if you used 9.04 and it worked pretty good, then you could use the Update Manager and try to install 9.10 over it.
That can have a different result than just installing 9.10 direct.  I can't say that it is always a good result, but if your connections work under 9.04, then there is the prospect that they might still work under 9.10.  What's to lose?

---

### Post by bkratz on 2010-02-14
> **swimstarguy said:**
> I just switched to 9.10 and am, once again, having wireless issues with my laptop.

I cannot get a wireless or a wired connection. Nothing. I went to System>Administration>Hardware Drivers and there's nothing in there to select/update.

I have tried to reinstall as well.

I have also been searching for ever in old threads and have found nothing that works. 

I would greatly appreciate any help. 

Here are some things that I've tried and info on the machine:


I do see where lshw -C Network has a few things marked as "unclaimed" I saw in a previous thread where you set the driver to claim the card, something about blacklisting the unneeded drivers. It didn't work, though I may have been doing it wrong.

I'm lost and I know I'm missing something simple that has already been solved for someone else.

Please, any help would be welcomed. I'm pounding my face against my desk.

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02) 
blah blah blah...
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)



Here is a thread that may help with both your problems (B44 and B43).

[http://ubuntuforums.org/showthread.php?t=1396940&highlight=b44](http://ubuntuforums.org/showthread.php?t=1396940&highlight=b44)

---

### Post by sandyd on 2010-02-14
download this onto your desktop
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
```

mkdir ~/dev
mv ~/Desktop/hybrid*gz ~/dev
cd ~/dev
tar xvfz hybrid*.gz
cd hybrid*
sudo apt-get install dkms
make
sudo make install
sudo modprobe wl

```

or, if you have internet, you can simply click [here]("apt://bcmwl-kernel-source")

---

