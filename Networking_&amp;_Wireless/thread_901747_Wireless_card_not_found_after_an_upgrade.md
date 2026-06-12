---
title: "Wireless card not found after an upgrade"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by ansichart on 2008-08-26
I am using Ubuntu 8.04 i386 desktop.  I have an Atheros wireless card, and it has worked fine on Ubuntu for years.  Recently, I added a new source to apt-get:

deb [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) gutsy main

Later, my update manager said it found some new updates.  I downloaded those updates.  The next day, I rebooted my computer and now my wireless card can't be found.  I tried finding it with ifconfig -a and iwconfig and ath0 doesn't show up.

Not sure what to do, any help is appreciated.

---

### Post by Scott M. Sanders on 2008-08-26
I'm having almost exactly the same problem: Ubuntu just today updated three "linux-" packages of sorts, I had to restart Ubuntu, and now I've had to post this from Vista because Ubuntu can no longer find my wifi adapter.

I have a Toshiba Satellite A205-S5859 with the Intel 4965AGN factory-installed network adapter.

I'm fairly new to Linux but have tinkered with computers for 20-some years and had just recently fully "switched" to Ubuntu at home. Now this happened, but I really want to use a wireless Ubuntu again.

:(

---

### Post by irishbreakfast on 2008-08-26
Me too. I can't get my wireless working since the last upgrade. 


I posted 12 hours (upgrade to 19.41 now can't connect to router) but have not yet received any replies.
[http://ubuntuforums.org/showthread.php?t=901230](http://ubuntuforums.org/showthread.php?t=901230)

---

### Post by cybrsaylr on 2008-08-26
Same thing happened to me. I posted this here a few hours ago.

My couple month old Toshiba laptop is back on a wired connection.
After installing today's 4 updates it required a PC reboot.
I reboot and lost my wireless connection.

It was running great as I used for about a half hour, prior to noticing the 'updates are available' prompt. I decided to update and install those 4 updates, then rebooted as instructed and now have no wireless. 

Anyone know what happened and can someone help me get the wireless working again as it was before?

---

### Post by irishbreakfast on 2008-08-26
I had three updates:

Upgraded the following packages:
linux-headers-2.6.24-19 (2.6.24-19.36) to 2.6.24-19.41
linux-headers-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41
linux-image-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41


just curious if this is the same as yours

I hope to try a wired connection after dinner (8 hour from now)

---

### Post by AndySaunders on 2008-08-26
I'm having the exact same problem as well (Atheros card running on an Acer Aspire 4320 laptop)

---

### Post by cybrsaylr on 2008-08-26
My hard wired connection works fine.
It's wireless that doesn't work anymore since doing them upgrades today.

Noticed others having the same problem on other recent threads posted today.

---

### Post by Brickrat on 2008-08-26
My daughter's Acer Aspire 3680 with Atheros wireless card also lost wireless after running today's update.   I spent about 8 or 10 hours going through the forums and getting the Atheros fix installed, and can only say that it is disappointing to have it fail on the first update.   I switched here from Vista, due to poor performance on the Acer and she liked it fine.  I hope there is a simple fix.

---

### Post by ansichart on 2008-08-27
Thanks leo_rockw in irc.freenode.net /#ubuntu for helping me troubleshoot this problem.

SOLUTION: Install the madwifi drivers (if you had them already, you will need to reinstall them since the upgrade overwrote the module)

I used the devel (beta) version.
[http://madwifi.org/wiki/UserDocs/GettingMadwifi](http://madwifi.org/wiki/UserDocs/GettingMadwifi)

Of course you will need to restart your system afterwards.

---

### Post by Twotoes on 2008-08-27
I had the same problem on Ubuntu 8.04, the fix is very easy if the wireless connection was OK before the upgrade:-

cd ~/madwifi-hal-0.10.5.6
make clean
sudo make install

---

### Post by irishbreakfast on 2008-08-27
I missed that I have a different card then you all. I have the Intel(R) PRO/Wireless 3945ABG/BG.

any ideas?

---

### Post by cybrsaylr on 2008-08-27
> **Twotoes said:**
> I had the same problem on Ubuntu 8.04, the fix is very easy if the wireless connection was OK before the upgrade:-

cd ~/madwifi-hal-0.10.5.6
make clean
sudo make install

It didn't work for me.
After putting it in terminal I got this:

tt@tt-laptop:~$ cd ~/madwifi-hal-0.10.5.6
bash: cd: /home/tt/madwifi-hal-0.10.5.6: No such file or directory
tt@tt-laptop:~$ make clean
make: *** No rule to make target `clean'.  Stop.
tt@tt-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
tt@tt-laptop:~$

---

### Post by bbrownatl on 2008-08-27
> **ansichart said:**
> Thanks leo_rockw in irc.freenode.net /#ubuntu for helping me troubleshoot this problem.

SOLUTION: Install the madwifi drivers (if you had them already, you will need to reinstall them since the upgrade overwrote the module)

I used the devel (beta) version.
[http://madwifi.org/wiki/UserDocs/GettingMadwifi](http://madwifi.org/wiki/UserDocs/GettingMadwifi)

Of course you will need to restart your system afterwards.

As a newbie to Ubuntu, I go to the link above and see many choices.  Can you help me in being specific.  My wireless was working fine until the upgrade. 

I appreciate the assistance.

Brian

---

### Post by GrandpaLeaman on 2008-08-27
I ran into the same problem so I went back to the _HowTo_ that I first used to set up my wireless. I have a Broadcom BCM4311 802.11b/g card and used this thread to set it up.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I went through the steps again for the "Hardy Bug Fix" and I was up and running in 5 minutes. 

This worked for my card, but as for some of the others cards noted on this thread I'm sorry but I really can't help you. But you might want to go back to whatever you had to do to get your wireless to work in the beginning.

By the way, I think the upgrade noted by Irishbreakfast in post #5 as the culprit is the one that caused my problem:

> Upgraded the following packages:
linux-headers-2.6.24-19 (2.6.24-19.36) to 2.6.24-19.41
linux-headers-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41
linux-image-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41Hope this at least helps those with Broadcom cards.

---

### Post by bpl07 on 2008-08-27
> **irishbreakfast said:**
> 

Upgraded the following packages:
linux-headers-2.6.24-19 (2.6.24-19.36) to 2.6.24-19.41
linux-headers-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41
linux-image-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41



Next time wait for the [linux-restricted-modules]("http://packages.ubuntu.com/hardy/linux-restricted-modules-2.6.24-19-generic") to be ready for upgrade, which contains your wifi modules.  This should be less of an issue in intrepid, where most of the wireless drivers come included in the kernel.

For those without wire connection, try booting in to an older kernel (2.6.24-18 for example) which hasn't had the restricted modules overwritten yet.  You should still have wireless there, where you can download the restricted modules update.

---

### Post by luckyrog on 2008-08-27
> **irishbreakfast said:**
> I had three updates:

Upgraded the following packages:
linux-headers-2.6.24-19 (2.6.24-19.36) to 2.6.24-19.41
linux-headers-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41
linux-image-2.6.24-19-generic (2.6.24-19.36) to 2.6.24-19.41


just curious if this is the same as yours

I hope to try a wired connection after dinner (8 hour from now)
Exactly the same problem, as soon as I updated the kernel it vanished - wired still works though. What makes it worse is that it took me about 2 hours to get the thing working in the first place.  Oh well.

---

### Post by luckyrog on 2008-08-27
> **cybrsaylr said:**
> It didn't work for me.
After putting it in terminal I got this:

tt@tt-laptop:~$ cd ~/madwifi-hal-0.10.5.6
bash: cd: /home/tt/madwifi-hal-0.10.5.6: No such file or directory
tt@tt-laptop:~$ make clean
make: *** No rule to make target `clean'.  Stop.
tt@tt-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
tt@tt-laptop:~$
First you need to find the directory and cd into it, in my case it was

cd /home/roger/Desktop/madwifi-hal-0.10.5.6-r3835-20080801

Then do this:

make

sudo make install

sudo reboot

Worked like a charm for me, hope it works for you as well!

---

### Post by PhineasP on 2008-08-28
Well I'm afraid none of these solutions worked for me. I've pretty much decided to uninstall Hardy and go back to Gutsy which recognised my wireless adapter out of the box. A wired connection is not an option in the computer's current location.

Now how to uninstall? Look for another thread I suppose.

---

### Post by bpl07 on 2008-08-28
> **PhineasP said:**
> Well I'm afraid none of these solutions worked for me. 

Did you try booting in to an older kernel like I suggested?  They should still have the restricted modules.

---

### Post by skybro on 2008-08-28
> **Twotoes said:**
> I had the same problem on Ubuntu 8.04, the fix is very easy if the wireless connection was OK before the upgrade:-

cd ~/madwifi-hal-0.10.5.6
make clean
sudo make install

This is what fixed it for me, just remember to reboot.  Thanks!!!!

The linux header update killed me ;-)

Thanks.

---

### Post by irishbreakfast on 2008-08-29
Still not working for me. None of the suggestions suit the Intel(R) PRO/Wireless 3945ABG/BG.

Thanks to bpl0 for the advice about restricted modules. I have had a look at the link but, frankly, don't understand how to use the information that is there.

And booting to the previous versions I have does NOT work!

I have run out of ideas of what to try.

Anyone have time to help me sort this out?

---

### Post by cybrsaylr on 2008-08-29
> **luckyrog said:**
> First you need to find the directory and cd into it, in my case it was

cd /home/roger/Desktop/madwifi-hal-0.10.5.6-r3835-20080801

Then do this:

make

sudo make install

sudo reboot

Worked like a charm for me, hope it works for you as well!
Tried to do that with no luck.
Maybe I'm doing something wrong, I don't know and still have no wireless networks.

You said to "First you need to find the directory and cd into it,"
Just how do you do that? maybe I'm doing it the wrong way.

---

### Post by PhineasP on 2008-08-30
> **bpl07 said:**
> Did you try booting in to an older kernel like I suggested?  They should still have the restricted modules.
bp107, you are a lifesaver. After fiddling around a lot I found 8.04 2.6.22.14 on offer at system startup as an alternative to the 2.6.22.16 I had been using, and just booted into it. Shazam! I am now back online. I've rigged up a little mirror so I can watch the wireless adapter LED on the back of the box. Now all I need is some way of monitoring the wireless signal on screen.

The computer in question is my wife's desktop and I would like to set it up so she can boot strait into the 14 module without selecting from the list. Does anyone have any suggestions on how that can be set up? I have tried deleting the 16 module from the options at startup but without success. We need to keep the Windows XP double boot option as she will have to transfer quite a lot of stuff from there when she gets comfortable with Ubuntu.

Jim

---

### Post by cybrsaylr on 2008-08-30
> **bpl07 said:**
> Did you try booting in to an older kernel like I suggested?  They should still have the restricted modules.

I tried doing that and nothing.
It didn't help get wireless back.

---

### Post by awry on 2008-10-07
I had this problem.  Aptitude updated linux-image-2.6.24-19-generic from 2.6.24-19.36 to 2.6.24-19.41.  After rebooting, the madwifi modules would no longer load (unresolved symbols reported in dmesg output).  

The fix for me was to run depmod (depmod calculates kernel module dependencies and records them to the modules.dep file):

```
sudo depmod -ae
sudo modprobe ath_pci
```

After that, the madwifi modules loaded successfully, and I was in business.  There should be no need to compile from source if you have the relevant linux-restricted-modules pkg installed.
 
I thought that depmod was run automatically via a dpkg post-install script for kernel images, but apparently it didn't happen this time.  Probably something missing in the packaging script.  If others confirm this behavior I'll file a bug.

---

### Post by mwacky on 2008-10-08
Thanks this is exactly what helped me when I did an upgrade from Hardy to Interpid beta!

```
sudo depmod -ae
sudo modprobe ath_pci
```

Easy Fix!

---

