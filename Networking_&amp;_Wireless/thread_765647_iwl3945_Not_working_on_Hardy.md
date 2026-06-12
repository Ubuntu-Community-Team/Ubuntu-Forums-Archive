---
title: "iwl3945 Not working on Hardy"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by JHumphrey on 2008-04-24
I tried to access the Internet off my Intel  Pro/Wireless 3945 ABG (Centrino) card after upgrading from gutsy to hardy, and I cannot connect to my wireless router with any method.

The card worked under gutsy with the ipw3945 driver, but with hardy, after switching to iwl3945, it no longer works.

[Heres](http://pastebin.com/f1d1b9686) a txt file with some data on the card. (Like iwconfig, etc)  My AP name is 2WIRE882.

Also, when I go to network tools, and try push the configure button  on any network interface, it says that the Interface does not exist.

So, what can I do, besides going back to gutsy?

---

### Post by ScottY86 on 2008-04-24
Bump, same problem.  Intel wireless 3945... no dice.

---

### Post by JHumphrey on 2008-04-24
I tried a different distro based on Ubuntu, and it used iwl3945 as well, and it didn't work either.

---

### Post by JHumphrey on 2008-04-24
> **ScottY86 said:**
> Bump, same problem.  Intel wireless 3945... no dice.


Do you happen to have a 2Wire router? I've found one other documented case where the iwl3945 driver does not work with a 2wire router. 

I would say this is a huge bug in the wireless part.

---

### Post by poobal on 2008-04-24
I have a similar issue with hardy on x61s with intel 3495. I can connect to open wireless networks that broadcast but I loose connection after few minutes. The networkmanager indicates that its still connected to a wireless network but I don't have connectivity. The ipw3495 seems to be loaded but its not showing up on restricted drivers manager. 

Karthik

---

### Post by JHumphrey on 2008-04-24
> **poobal said:**
> I have a similar issue with hardy on x61s with intel 3495. I can connect to open wireless networks that broadcast but I loose connection after few minutes. The networkmanager indicates that its still connected to a wireless network but I don't have connectivity. The ipw3495 seems to be loaded but its not showing up on restricted drivers manager. 

Karthik

i tried modprobe ipw3945, and it didnt work, do i have to modprobe -r iwl3945 first?

---

### Post by poobal on 2008-04-24
Possible solution?
[http://ubuntuforums.org/showthread.php?t=731024](http://ubuntuforums.org/showthread.php?t=731024)

Looks like its the network manager that is the problem here.

Karthik

---

### Post by sirclaudio on 2008-04-25
Install linux-backports-modules-hardy, it has the most recent versions of iwlwifi and rt2x00

---

### Post by Teklock on 2008-04-25
> **JHumphrey said:**
> I tried to access the Internet off my Intel  Pro/Wireless 3945 ABG (Centrino) card after upgrading from gutsy to hardy, and I cannot connect to my wireless router with any method.

The card worked under gutsy with the ipw3945 driver, but with hardy, after switching to iwl3945, it no longer works.

[Heres](http://pastebin.com/f1d1b9686) a txt file with some data on the card. (Like iwconfig, etc)  My AP name is 2WIRE882.

Also, when I go to network tools, and try push the configure button  on any network interface, it says that the Interface does not exist.

So, what can I do, besides going back to gutsy?


Same problem here with my Dell D620 and Intel Pro/Wireless 3945 ABG.  Worked fine with 7.10.  Has anyone ben able to get anywhere with this issue?

---

### Post by Hieronymus on 2008-04-25
This problem is still not solved but you can get wireless working by using ndiswrapper.

```

lsmod | grep iwl

```

this will give you an output of the modules loaded to get iwl3945 working. The modules it shows are: iwl3945, iwlwifi_mac80211, cfg80211.
Then we must make sure that these are not loaded again

```

sudo nano /etc/modprobe.d/blacklist

```

and add:

#iwl
blacklist iwl3945
blacklist iwlwifi_mac80211
blacklist cfg80211

then remove the modules:

```

sudo rmmod iwl3945
sudo rmmod iwlwifi_mac80211
sudo rmmod cfg80211

```

then install ndiswrapper

```

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

```

install the windows driver

```

sudo ndiswrapper -i drivername.inf

```

make sure it starts at boottime, add ndiswrapper to /etc/modules

```

sudo nano /etc/modules

```

Now reboot and all should be fine

Jeroen

---

### Post by chili555 on 2008-04-25
On my Thinkpad T60, my 3945ABG works perfectly in Hardy with iwl3945 and without Network Manager. So, it seems this is not a Hardy vs. iwl3945 issue.

---

### Post by DO55 on 2008-04-25
i have same problem
[http://ubuntuforums.org/showthread.php?t=765615](http://ubuntuforums.org/showthread.php?t=765615)

---

### Post by areteichi on 2008-04-25
As far as I know, this is the problem of the linux kernel. The current version in Hardy (2.6.24) has some issues with 3945G wireless card, so it is necessary to revert back to 2.6.22.

One can do so by editing the repos:
```
sudo gedit /etc/apt/sources.list
```
and change the following "hardy" to **gutsy**
```
deb http://us.archive.ubuntu.com/ubuntu/ **hardy** main restricted
```

Once you have done that, update the package list with synaptic manager and install/remove the following:

```

Completely removed the following packages:
linux-backports-modules-2.6.24-16-generic
linux-backports-modules-hardy
linux-backports-modules-hardy-generic
linux-generic
linux-image-2.6.24-16-generic
linux-image-generic
linux-restricted-modules-2.6.24-16-generic
linux-restricted-modules-generic
linux-ubuntu-modules-2.6.24-16-generic
linux-headers-2.6.24-16
linux-headers-2.6.24-16-generic
linux-headers-generic

Installed the following packages:
linux-backports-modules-2.6.22-14-generic (2.6.22-14.10)
linux-image-2.6.22-14-generic (2.6.22-14.46)
linux-restricted-modules-2.6.22-14-generic (2.6.22.4-14.9)
linux-ubuntu-modules-2.6.22-14-generic (2.6.22-14.37)
linux-restricted-modules-2.6.22-14-generic (2.6.22.4-14.9)
linux-headers-2.6.22-14 (2.6.22-14.46)
linux-headers-2.6.22-14-generic (2.6.22-14.46)

```

Make sure that after doing all of that, the version of linux-restricted-modules-generic is correctly reverted to 2.6.22, otherwise it will not work. Once you confirm that everything works, revert back the sources.list the way it was (change back "gutsy" to "hardy").

---

### Post by JHumphrey on 2008-04-25
I'll be trying this method when I get home tonight:  [http://ubuntuforums.org/showthread.php?t=766864](http://ubuntuforums.org/showthread.php?t=766864)

And I'll try the ndiswrapper as a last resort.

---

### Post by areteichi on 2008-04-25
Sorry I had to wipe out my entire post while I made sure my method properly worked.

But yeah, the above method should work (2 posts above). Let me know if there is any unclarity.

---

### Post by JHumphrey on 2008-04-25
> **byagietera said:**
> Sorry I had to wipe out my entire post while I made sure my method properly worked.

But yeah, the above method should work (2 posts above). Let me know if there is any unclarity.


I love catch-22s

I can't connect to the internet because my wireless card is down, and I can't fix my card unless I connect to the internet.

A wired internet is not a solution, my router only has wireless.

---

### Post by itsacoaster on 2008-04-25
I am having a problem with the same card.

I am trying to connect to a wireless router with WEP 64 Bit Hex encryption.  The connection takes forever to figure out that it needs a password, and once it prompts me, it takes forever to ask me for the password again.  The password is not wrong, I swear, and I have no problem connecting to routers without encryption.

Any ideas?

---

### Post by JHumphrey on 2008-04-25
> **itsacoaster said:**
> I am having a problem with the same card.

I am trying to connect to a wireless router with WEP 64 Bit Hex encryption.  The connection takes forever to figure out that it needs a password, and once it prompts me, it takes forever to ask me for the password again.  The password is not wrong, I swear, and I have no problem connecting to routers without encryption.

Any ideas?


I would try the methods in this thread. Should probably keep the ndiswrapper one as a last resort, and maybe do in virtualization or back up everything, just in case it doesn't work

---

### Post by areteichi on 2008-04-25
> **JHumphrey said:**
> I love catch-22s

I can't connect to the internet because my wireless card is down, and I can't fix my card unless I connect to the internet.

A wired internet is not a solution, my router only has wireless.

You could put in your gutsy cd and search for packages there :)
Those packages must be included in the default cd.

---

### Post by cartisdm on 2008-04-25
> **byagietera said:**
> As far as I know, this is the problem of the linux kernel. The current version in Hardy (2.6.24) has some issues with 3945G wireless card, so it is necessary to revert back to 2.6.22.

One can do so by editing the repos:
```
sudo gedit /etc/apt/sources.list
```
and change the following "hardy" to **gutsy**
```
deb http://us.archive.ubuntu.com/ubuntu/ **hardy** main restricted
```

Once you have done that, update the package list with synaptic manager and install/remove the following:

```

Completely removed the following packages:
linux-backports-modules-2.6.24-16-generic
linux-backports-modules-hardy
linux-backports-modules-hardy-generic
linux-generic
linux-image-2.6.24-16-generic
linux-image-generic
linux-restricted-modules-2.6.24-16-generic
linux-restricted-modules-generic
linux-ubuntu-modules-2.6.24-16-generic
linux-headers-2.6.24-16
linux-headers-2.6.24-16-generic
linux-headers-generic

Installed the following packages:
linux-backports-modules-2.6.22-14-generic (2.6.22-14.10)
linux-image-2.6.22-14-generic (2.6.22-14.46)
linux-restricted-modules-2.6.22-14-generic (2.6.22.4-14.9)
linux-ubuntu-modules-2.6.22-14-generic (2.6.22-14.37)
linux-restricted-modules-2.6.22-14-generic (2.6.22.4-14.9)
linux-headers-2.6.22-14 (2.6.22-14.46)
linux-headers-2.6.22-14-generic (2.6.22-14.46)

```

Make sure that after doing all of that, the version of linux-restricted-modules-generic is correctly reverted to 2.6.22, otherwise it will not work. Once you confirm that everything works, revert back the sources.list the way it was (change back "gutsy" to "hardy").

I just tried this method and after a reboot and I don't even have the wireless networks show up anymore.....what happened?

---

### Post by areteichi on 2008-04-25
> **cartisdm said:**
> I just tried this method and after a reboot and I don't even have the wireless networks show up anymore.....what happened?

Did you make sure that you're basically replacing what you have for 2.6.24 with 2.6.22? What you basically want to do is to select the equivalent one for 2.6.22 in place of what you to remove for 2.6.24.

```
Completely removed the following packages:
linux-generic
linux-headers-2.6.24-16
linux-headers-2.6.24-16-generic
linux-headers-generic
linux-image-2.6.24-16-generic
linux-image-generic
linux-restricted-modules-2.6.24-16-generic
linux-restricted-modules-common
linux-restricted-modules-generic
linux-ubuntu-modules-2.6.24-16-generic

Installed the following packages:
linux-headers-2.6.22-14 (2.6.22-14.46)
linux-headers-2.6.22-14-generic (2.6.22-14.46)
linux-image-2.6.22-14-generic (2.6.22-14.46)
linux-ubuntu-modules-2.6.22-14-generic (2.6.22-14.37)
```

```
Installed the following packages:
linux-restricted-modules-2.6.22-14-generic (2.6.22.4-14.9)
linux-restricted-modules-common (2.6.22.4-14.9)
```

I simply had to take those two steps. Can you tell me if you have all of those installed?

---

### Post by DO55 on 2008-04-25
can anyone try this
[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

i found the link here [http://ubuntuforums.org/showthread.php?t=765379](http://ubuntuforums.org/showthread.php?t=765379)

---

### Post by cartisdm on 2008-04-25
> **DO55 said:**
> can anyone try this
[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

i found the link here [http://ubuntuforums.org/showthread.php?t=765379](http://ubuntuforums.org/showthread.php?t=765379)

Yea man I tried it earlier today, it didn't work for me:(

______________________________________________________________

> I simply had to take those two steps. Can you tell me if you have all of those installed?

I just double checked and I'm pretty sure I have everything you listed. However I can't find this version of linux-restricted-modules-common (2.6.22.4-14.9)  I only see the .16 version.  Here's a screenshot...

---

### Post by chili555 on 2008-04-25
> **DO55 said:**
> can anyone try this
[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

i found the link here [http://ubuntuforums.org/showthread.php?t=765379](http://ubuntuforums.org/showthread.php?t=765379)I tried this and got my LED working! Woooo hoooo! I still believe this is a Network Manager issue, not a kernel or driver issue. I have NM removed and before and since I upgraded to Hardy last night, my 3945ABG has worked perfectly.

Also, I think you can safely ignore *wmaster0.*

---

### Post by Tulsapoke on 2008-04-25
I have the same problem on my Dell laptop after searching the forums I finally saw that the new kernel is messed up for our ipw3945 setup.  This led me to the solution to revert to the older kernel, and I am now back in business. 

How could they actually revert to common hardware like this not working in a new kernel?  This seems like a really big screwup!  I have 2 other friends running Ubuntu with Intel wifi, now I am going to advise them to layoff of Hardy until this is fixed.

---

### Post by areteichi on 2008-04-25
> **Tulsapoke said:**
> I have the same problem on my Dell laptop after searching the forums I finally saw that the new kernel is messed up for our ipw3945 setup.  This led me to the solution to revert to the older kernel, and I am now back in business. 

How could they actually revert to common hardware like this not working in a new kernel?  This seems like a really big screwup!  I have 2 other friends running Ubuntu with Intel wifi, now I am going to advise them to layoff of Hardy until this is fixed.

I'm glad you got your Hardy working. May I ask if you followed any of my procedure or you found your own way of reverting the kernel?

I think it will help those who are still having problems if you could tell us how you got it done.

---

### Post by Khalis7 on 2008-04-26
I wonder why the wireless connection has becomes an issue because this problem shouldn't happened at first place and this has caused trouble to many people who are using Hardy.:mad: I call upon Ubuntu developer people to take action on this problem and come out with the solution ASAP.

My Intel 3945abg card has worked wonderfully in Gutsy and it broke down in Hardy. To solve this, I installed linux-restricted-modules-generic and I got the Wifi LED working but still couldn't get automatically connected to the wireless network. Then I resorted to use Wifi-Radar and connect to the network manually and I'm connected.

Is there any way for me connect to the wireless network automatically rather than to use Wifi-Radar? Ndiswrapper is not an option to me because I didn't get it worked. Any ideas??

---

### Post by DO55 on 2008-04-26
i have report the bug 
[https://bugs.launchpad.net/ubuntu/+bug/221633](https://bugs.launchpad.net/ubuntu/+bug/221633)

---

### Post by Blingin2Mingin on 2008-04-26
This was definitely a Network Manager problem for me on a Dell Inspiron 9400. Dropping back to older kernels made no difference at all for me.

After upgrading to Hardy I had no connection and no led.

So I upgraded the iwl driver

```
sudo apt-get install linux-backports-modules-hardy-generic
```

This cured the led, but I was still struggling to connect to any WEP or WPA encrypted network. 

So I took the plunge and ditched Network Manager and installed Wicd.

Bingo!

Wicd works very well indeed for me. So well that I don't see me going back to Network Manager when this bug is finally fixed.

In order to get Wicd you will need the following line requires adding to your third party repositories 

```
deb http://apt.wicd.net hardy extras
```

---

### Post by Blackdrive on 2008-04-26
It was posted here too:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190346](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190346)

Installing Wicd didn't do the job for me :(.

I'm going to install the backports-modules now.
If that doesn't work, I'll try reverting the kernel.

Edit:

Omg, it works!
Only thing I did was installing the backports-modules.
btw, I'm still using network-manager.

---

### Post by billis on 2008-04-26
Blackdrive, can you describe exactly what you did, please?

---

### Post by cartisdm on 2008-04-26
> **billis said:**
> Blackdrive, can you describe exactly what you did, please?

Yea please do, I am still restricted to the length of my LAN cable!!!

---

### Post by Blackdrive on 2008-04-26
> **billis said:**
> Blackdrive, can you describe exactly what you did, please?

I enabled the Hardy Backports repository in 'Software Sources' (tab Updates). When I hit 'close' it asked to reload the repositories, I did that.
After that I opened Terminal and entered:
```
sudo apt-get install linux-backports-modules-hardy-generic
```

That's all really, after the backports-modules were installed I tried logging in again with nm-applet and it worked.

Basically I followed the [guide]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/") mentionned before.


I hope this helps for you guys.
good luck!

---

### Post by _aluminium23 on 2008-04-26
I have the same problem. I tried the "backports" but don't work. I tried with wicd and network-manager.

Sorry about my english. :)

---

### Post by billis on 2008-04-26
Me neither :(

---

### Post by cartisdm on 2008-04-26
> **_aluminium23 said:**
> I have the same problem. I tried the "backports" but don't work. I tried with wicd and network-manager.

Sorry about my english. :)

Same here.  I'm really starting to get annoyed with my hardy upgrade.  Feisty to Gutsy was great but I'm not so thrilled about 8.04....

---

### Post by Mr_Congeniality on 2008-04-26
I miss my gutsy.  I'm going back.

---

### Post by evolutionspeak on 2008-04-26
BlackDrive's instructions worked for me using wicd (which is far superior to network manager).

---

### Post by cartisdm on 2008-04-26
> **Mr_Congeniality said:**
> I miss my gutsy.  I'm going back.

You got it man, I'm on the liveCD now downgrading to Gutsy.  I'll check back frequently and upgrade again once they get this issue taken care of

---

### Post by David Ostrom on 2008-04-26
> Originally Posted by Blackdrive. I enabled the Hardy Backports repository in 'Software Sources' (tab Updates). When I hit 'close' it asked to reload the repositories, I did that.
After that I opened Terminal and entered:
Code:

sudo apt-get install linux-backports-modules-hardy-generic

That's all really, after the backports-modules were installed I tried logging in again with nm-applet and it worked.

Basically I followed the guide mentionned before.


I hope this helps for you guys.
good luck!


Thanks Blackdrive! I'm running off the CD and like what I see, now that I've got wireless working I just might go ahead and do a clean install.

---

### Post by Khalis7 on 2008-04-27
> **Blingin2Mingin said:**
> 
Wicd works very well indeed for me. So well that I don't see me going back to Network Manager when this bug is finally fixed.

In order to get Wicd you will need the following line requires adding to your third party repositories 

```
deb http://apt.wicd.net hardy extras
```


Hey, that works for me. I had linux-backport-backport-module generic and wicd installed. Everything is working fine and smooth now. Thank you!!
:)

---

### Post by Blingin2Mingin on 2008-04-27
Warning.

The backports iwl driver is an improvement on the original driver but its a long way from perfect. 

I turned wifi off with Fn + F2 and it turned off fine, but I couldn't get it back on for love nor money.

The only answer was to reboot into Windoze (I've not been there for weeks honest) Restart wifi there and reboot again into Hardy.


I honestly don't know what I would have done if I didn't still have a dual boot setup.

---

### Post by manugap on 2008-04-27
> **poobal said:**
> I have a similar issue with hardy on x61s with intel 3495. I can connect to open wireless networks that broadcast but I loose connection after few minutes. The networkmanager indicates that its still connected to a wireless network but I don't have connectivity. The ipw3495 seems to be loaded but its not showing up on restricted drivers manager. 

Karthik

I have exactly the same problem after the update, (Intel Corporation PRO/Wireless 3945ABG). 

manu

---

### Post by warreng on 2008-04-27
I had the same problem after upgrading a Dell D830. The backports method resolved it for me.

---

### Post by jackcy on 2008-04-27
Enabling the backports and installing the backports generic modules worked for me. After reloading the module, I was able to connect.
What I am wondering is why there was the switch from ipw3945 to iwl3945. Probably a license issue.

---

### Post by canerunner on 2008-04-27
I fought with the 3945ABG problem on an X60s Thinkpad. I tried a lot of things, but what worked was removing the Network Manager.

I just ran:

sudo apt-get remove network-manager

After a reboot, I had wireless with no issues, and the wired connection continued working fine. 

There is some issue between Network Manager and the drivers. I hear a number of people having the same issue with various WiFi devices. Is Network Manager the thing that's really broken??

---

### Post by ctpaterson on 2008-04-27
Just wanted to report:

"sudo apt-get install linux-backports-modules-hardy-generic"

got my wireless working again on a Dell Inspiron 1520 - running 32-bit Hardy with the alternate disc.  Tested with an open network, and a network encrypted with 128-bit WEP.

Much obliged.

---

### Post by themusicwave on 2008-04-27
> **Blackdrive said:**
> I enabled the Hardy Backports repository in 'Software Sources' (tab Updates). When I hit 'close' it asked to reload the repositories, I did that.
After that I opened Terminal and entered:
```
sudo apt-get install linux-backports-modules-hardy-generic
```

That's all really, after the backports-modules were installed I tried logging in again with nm-applet and it worked.

Basically I followed the [guide]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/") mentionned before.


I hope this helps for you guys.
good luck!

That worked perfectly for me!

I have a Dell E1505 Hardy Release.
Also using a Linksys WRTGS Router with SSID broadcast off and WEP Hex encrptytion.

Thanks!

---

### Post by Tulsapoke on 2008-04-27
> **byagietera said:**
> I'm glad you got your Hardy working. May I ask if you followed any of my procedure or you found your own way of reverting the kernel?

I think it will help those who are still having problems if you could tell us how you got it done.

I just select an earlier Kernel when I boot up from the Grub menu.  

Although now I am thinking about trying out this backports solution so I can use the new kernel.  However so far using the older kernel has been flawless as it has been since the last 3 or so upgrades.

Can I still use the default network manager with this backports solution or do you have to change to something new?

---

### Post by tanis.mezzelfo on 2008-04-27
I had the some problem on my DELL LATITUDE D520. I have used the old 2.6.22-14 linux kernel and now my intel wireless connection works fine!

I hope that the problem on the new 2.6.24-16 kernel'll resolved early :-( sigh

Bye, bye

Tanis

---

### Post by billis on 2008-04-27
I made it work on my Thinkpad x60s!

I just uninstalled following packages through synaptic (search for "network manager"):

```
network-manager
network-manager-dev
network-manager-gnome
```

Afterwars I've installed them again!

Then i chose to connect to another network, entered my settings and bingo!

Hope this helps you guys!

billi

---

### Post by bluewizard on 2008-04-28
My friend just switched from Vista to Hardy yesterday, and he seems to have the same problem as everyone else in this thread (wireless eth1 interface doesn't show up). We're both very new to Ubuntu, but we can follow directions and run terminal commands. Hopefully one of these fixes (hopefully the backport drivers one, since it seems easy) will work.

---

### Post by Medo42 on 2008-04-28
Installing the backports-package did the job for me, too (using a Toshiba Satellite A100 PSAA9E). I was having trouble connecting to my university's open wlan, a network admin told me my device was only trying to connect in 54mbit-mode, which the APs here don't support. Is the issue maybe with 11mbit-wlans only?

---

### Post by yrenster on 2008-04-28
I struggled with that in Hardy. I finally got it working by simply commenting out all the lines relates to it in the file /etc/network/interfaces. After that, you need to reboot the system for the NetworkManager to gain control over the Intel 3945. You, then can set up the network settings for the card in the nm applet.

---

### Post by SadaraX on 2008-04-29
Does anyone know where I can get authentication keys for apt for WiCD? I don't like downloading from some place that is not verified.

---

### Post by syko21 on 2008-04-29
> **Hieronymus said:**
> This problem is still not solved but you can get wireless working by using ndiswrapper.

```

lsmod | grep iwl

```this will give you an output of the modules loaded to get iwl3945 working. The modules it shows are: iwl3945, iwlwifi_mac80211, cfg80211.
Then we must make sure that these are not loaded again

```

sudo nano /etc/modprobe.d/blacklist

```and add:

#iwl
blacklist iwl3945
blacklist iwlwifi_mac80211
blacklist cfg80211

then remove the modules:

```

sudo rmmod iwl3945
sudo rmmod iwlwifi_mac80211
sudo rmmod cfg80211

```then install ndiswrapper

```

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

```install the windows driver

```

sudo ndiswrapper -i drivername.inf

```make sure it starts at boottime, add ndiswrapper to /etc/modules

```

sudo nano /etc/modules

```Now reboot and all should be fine

Jeroen

Worked great for me, thanks! This should get a sticky to the front page for the time being since there are a fair amount of users having trouble with their 3945abg cards.

---

### Post by SadaraX on 2008-04-29
I installed WiCD and it solved my problem. I connect to any wireless network now.

I also installed the package 'linux-backports-modules-hardy-generic' but I removed it before I tested with WiCD. I don't know if it left anything on my system, since I know it modified my initrd.img.* files.

I am not surprised that network manager is somewhat buggy. I had Knetwork-manager crash on my numerous times in Edgy. I hope they fix the bugs because, since it is the program shipped with Kubuntu, it is important to have it working.

---

### Post by NeSportz on 2008-04-29
try disabling IPV6 it worked for my IBM t60 laptop!

I could see the networks before but not connect or stay connected. After disabling IPV6 Its worked flawlessly for days.

[https://help.ubuntu.com/7.10/internet/C/troubleshooting.html](https://help.ubuntu.com/7.10/internet/C/troubleshooting.html)

JwAcK

PS I LOVE 8.04 its working AWESOME ON my IBM t60 with 4gb of RAM

---

### Post by cartisdm on 2008-04-29
> **NeSportz said:**
> try disabling IPV6 it worked for my IBM t60 laptop!

I could see the networks before but not connect or stay connected. After disabling IPV6 Its worked flawlessly for days.

[https://help.ubuntu.com/7.10/internet/C/troubleshooting.html](https://help.ubuntu.com/7.10/internet/C/troubleshooting.html)


I was experiencing the exact same problem where I could see the networks but unable to establish a connection.  I downgraded to Gutsy again but can anyone else verify if this helped them before I try Hardy again?

---

### Post by Tulsapoke on 2008-04-29
I did the backports update (recommended here) and that seemed to fix it.  I am using the current kernel and don't see any problems now.

---

### Post by 3nt on 2008-04-30
I am running Hardy on a Dell 9400. Initially the wireless 3945 was not working and I have installed the backports, uninstalled network-manager, applied the latest HAL release and re-installed network-manager. I also had to comment out the wireless lines in /etc/network/interfaces and then use nm to re-install.( the lines are quite different). However I can still only get either the wireless or the wired network working. As soon as I turn on the wired network then the wireless ceases to work, turn it off and the wireless works again. I am not sure what info to post to best assist in fixing this.

---

### Post by brazh on 2008-05-01
I use Kubuntu Hardy on my HP Pavilion dv6185ea (dv6000) notebook. Of course, it has intel 3945 adapter ("Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)"). I was unable to connect to my Linksys WRT54GL wireless router, using WPA-security settings.
First of all, I tried to install linux-backports-modules-hardy-generic package, as it was advised above. After that, I could connect to the internet, but every minute I was disconnected for about 5 seconds and then connected again automatically:
[I]
wlan0: authenticated
...
wlan0: RX deathentication from <router_mac_address> (reason=15)
wlan0: deathenticated
...
wlan0: authenticated[/I]

This behaviour of my system was very annoying. So, I uninstalled network-manager and installed wicd. Then I commented all the lines in /etc/network/interfaces except

[I]auto lo
iface lo inet loopback[/I]

and got my wi-fi internet connection working perfectly, using Wicd.

So, linux-backports-modules-hardy-generic + Wicd is the solution for me. Thank you all, I couldn't do anything without your help!!! :)

---

### Post by amarcha on 2008-05-01
After sorting long and hard for the solution I found this:


Code:

modprobe -r iwl3945

Code:

modprobe iwl3945

Code:

ifconfig wlan0  up

create a file name iwl3945 in /etc/modprobe.d/
in the file type the following and save:
Quote:
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
now reboot.

got from: [http://ubuntuforums.org/showthread.php?t=733054](http://ubuntuforums.org/showthread.php?t=733054)

This worked very well for me.

If after this you cannot get your led working, install linux-backports-modules-hardy

---

### Post by chili555 on 2008-05-01
> However I can still only get either the wireless or the wired network working. As soon as I turn on the wired network then the wireless ceases to work, turn it off and the wireless works again.This is exactly how Network Manager is designed to work. Unless you are setting up a network bridge, why would you need two interfaces and two IP addresses?

---

### Post by SadaraX on 2008-05-02
Has anyone created an article in the Ubuntu wiki with steps to fix this problem? It seems to be established pretty thoroughly this is a wide spread problem, and that installing the backports + WiCD is a solid solution.

---

### Post by pjfl on 2008-05-02
It gets worse. Once you've got the LED working again, got the thing to connect at startup, tweaked the wifi-radar config so that works with the new wlan0 there is still more bad news. The iwl3945 v1.2.25 from the backports module still randomly drops connections. An explanation of why the old driver was dropped is here [http://james.colannino.org/downloads.html](http://james.colannino.org/downloads.html). Has anyone tried this? I mean someone who doesn't mind being left with brick of course.

---

### Post by DO55 on 2008-05-02
because the problem is still not solve .. id like to continue using 7.10 
but is it supported from ubuntu ? can I still received update ?

---

### Post by chili555 on 2008-05-02
> **pjfl said:**
> It gets worse. Once you've got the LED working again, got the thing to connect at startup, tweaked the wifi-radar config so that works with the new wlan0 there is still more bad news. The iwl3945 v1.2.25 from the backports module still randomly drops connections. An explanation of why the old driver was dropped is here [http://james.colannino.org/downloads.html](http://james.colannino.org/downloads.html). Has anyone tried this? I mean someone who doesn't mind being left with brick of course.
This is clearly, both in the name and in the first several lines of the patch, for ipw3945, not iwl3945. Are you asking if someone has written a similar patch for iwl3945?> it just adds the missing #define statementsAre the #define statements missing and needed in iwl3945?

---

### Post by jetsam on 2008-05-03
> **DO55 said:**
> because the problem is still not solve .. id like to continue using 7.10 
but is it supported from ubuntu ? can I still received update ?

Gutsy 7.10 will be supported with security updates until April 2009.  See here:
[http://www.ubuntu.com/products/whatIsubuntu/releases]("http://www.ubuntu.com/products/whatIsubuntu/releases") 

You only need to update to a new release if it has features your really need or want.  It's nice to be up to date, but there's no harm in delaying an upgrade, or skipping a release.

---

### Post by grantonstar on 2008-05-03
I'm a new Ubuntu after having switched from Gentoo. I've been very impressed with everything but the wifi issues detailed in this thread.

Basically, I'm having the same dreaded problem. I'm using a Dell XPS M1710 and after installing the backports can now get the wifi light on and connect to wlan's without any security. However, whenever I try to connect to a network using WEP or WPA security it fails.

I've tried wicd and network-manager. My currently loaded modules are:

> iwl3945                93940  0 
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211
led_class               6020  1 iwl3945


/var/log/messages contains:

> ADDRCONF(NETDEV_UP): wlan0: link is not ready


Any ideas? Back in the ipw3945 days you had to also load the ieee security modules too. Is this now included in the iwl3945 driver?

Thanks,

grantonstar

---

### Post by bkly-dog on 2008-05-03
I installed the backports package as instructed above, rebooted, and wireless now seems to work fine for me. 

Thanks!

---

### Post by jkilgrow on 2008-05-04
Well....I accidentally fixed my problem by following your advice.

There were a couple of things that I modified. Editing the /etc/apt/sources.list didn't do a thing for me. I ended up using the synaptic package manager and I just checked all of the possible sources that it could suggest (including my Ubuntu installation CD). So, I ended up having all possible packages to choose from.

So, the very first thing that I noticed when I started following your instructions was that I did not have *ANY* of the "linux-backports*" modules. I figured that, since I didn't have them, I probably did not need to remove them.

I removed the rest of the packages and installed the packages you suggested and restarted my system only to find that I was somehow on Gutsy Gibbon! NOTHING worked at that time (no sound, no video, and no wireless card). So I just reversed the instructions. Removed the stuff I just installed and installed the stuff I previously removed. Now, when I installed the stuff I previously removed, I *ALSO* installed the linux-backports packages. This may be what I was missing to begin with because when I restarted my system, I tried my wireless card and it worked!

So, before you go and remove/install all of that stuff, you may want to check your installed packages list and see if you have the backports installed. If not, I would try installing them first.

One more thing that happened is that there were some updates to Ubuntu that I installed. But I did not see anything to do with wireless card drivers or the network manager. So, I *doubt* that doing that update solved anything. I really believe that installing the backports packages was the solution.

I hope that helps.

---

### Post by esj on 2008-05-15
thanks for the guidance on this.  one thing I'm missing is openvpn support.  I really liked the way the network manager made starting and stopping a vpn very easy.  Ive tried kvpnc bit it seems to get confused between openvpn and ipsec.  any suggestions for openvpn management tools until network manager gets fixed?

thanks

---

### Post by syko21 on 2008-05-15
You could try the development branch of network-manager, the new 0.7. Instructions can be found here [http://ubuntuforums.org/showthread.php?t=676992](http://ubuntuforums.org/showthread.php?t=676992) and the repository can be found here [https://launchpad.net/~asac/+archive](https://launchpad.net/~asac/+archive)

---

### Post by esj on 2008-05-17
> **syko21 said:**
> You could try the development branch of network-manager, the new 0.7. Instructions can be found here [http://ubuntuforums.org/showthread.php?t=676992](http://ubuntuforums.org/showthread.php?t=676992) and the repository can be found here [https://launchpad.net/~asac/+archive](https://launchpad.net/~asac/+archive)

works great (sort of) wifi and ethernet switching are swell.  open vpn, not so good

May 17 11:51:12 first-triad kernel: [  209.021896] nm-vpn-properti[7117]: segfault at 00000000 eip b6e33507 esp bfa7d330 error 6

---

### Post by regonzal on 2008-05-30
Using Syko21's method I was able to confirm that the ndiswrapper installation was indeed able to work for me on my Intel PRO/Wireless 3945abg card. I also added two steps at the end of my post in this thread 
[http://ubuntuforums.org/showthread.php?p=5075751#post5075751]("http://ubuntuforums.org/showthread.php?p=5075751#post5075751") and it is working flawlessly! Thank you all!

---

### Post by cartisdm on 2008-06-08
Forgive me for being lazy but I haven't caught up on this thread in a long time and didn't want to backtrack all the pages.  Last time I tried to upgrade to Hardy it was on the release date.  From a quick browse I see there are still some issues obviously but everyone's case is a little different.  I'd like to try to upgrade again.  Have there been any official patches/updates for the 3945 card issues?

---

### Post by Praill on 2008-07-11
linux-backport-modules-hardy-generic worked like a charm for me.
now lets see if we can packet injection :)

---

### Post by KingNeil on 2008-07-12
I'm running a Dell XPS M1530 and the wireless works fine, but if I leave it for prolonged period of time, it switches off and thus I have to restart the computer. Mine is the Intel ABG3945 btw, with the iwl driver

I think this must be something to do with power management, like when I was running Vista on this same machine.

Does anyone have any ideas on how I can prevent this problem. Pretty much whenever I start up the computer, the wireless is down and I have to reboot. It's damn annoying.

This is a bit of extra info if it helps (after I entered sudo lshw -C network into the terminal):

> 
 *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:17:92:51
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.67 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g


---

### Post by tdeprato on 2008-08-11
Please join my discussion . 
[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/253697"]
https://bugs.launchpad.net/ubuntu/+source/linux/+bug/253697
[/URL]
This is were the Ubuntu developers actually research problems.  

Thanks

---

### Post by tdeprato on 2008-08-11
I just did this and now WPA2 connection is working 

[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/")

---

### Post by asac on 2008-08-12
right, one idea is to install the backport modules.

In any case, for others it helped to disable hardware scanning.

To test you can sudo rmmod iwl3945

and load it with sudo modprobe -v iwl3954 disable_hw_scan=1

---

### Post by EatMorePie on 2008-08-26
My experience with iwl3945 under Hardy:
[B]
The good:[/B]
[LIST]
[*]Got it to work, with a little effort.
[*]WPA-TKIP worked fine, but only with a handcrafted iface stanza in /etc/network/interfaces
[*]Would resume from suspend.
[/LIST]
**The bad:**
[LIST]
[*]Didn't come up automatically on boot.  With the right values in /etc/network/interfaces, I could at least start it with ifdown followed by ifup.
[*]  Throughput dropped through the floor after a little heavy network use.  Forget about watching video over the network or having a responsive VNC connection, we're talking dialup-like speeds here.  Stopping the interface and starting it again brought it back 
[/LIST]
**What I tried:**
  Everything in this forum.
[LIST]
[*]ndiswrapper didn't work for me.  Maybe I didn't work at it enough but I've used it successfully with other cards and what worked for me there didn't work for me here.
[*]   loading the backports modules didn't change a thing.
[*]   disable_hw_scan didn't either.
[/LIST]
**What worked:**
  Building the old ipw3945 driver and daemon, as described here: [http://ubuntuforums.org/showpost.php?p=4932500&postcount=2](http://ubuntuforums.org/showpost.php?p=4932500&postcount=2).  These instructions worked perfectly.

I'm content with this solution.  The only downside is that the connection doesn't come back on resume, but I'd rather have to stop and start the interface when resuming than every five minutes in use.

---

### Post by em4mapson on 2008-08-29
I solved my problem! 

kernels 2.6.24 and up have the iwlwifi driver included (instead of ipw3945, which is and was working for some)

[http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi) says
"Using kernels 2.6.24 and up
These kernels have the iwlwifi driver included and the released drivers (available from this site under download page) do not work with these kernels. If you want to run the latest (or very close to it) development code with your kernel then you should use the compat-wireless project"

compat-wireless project = [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

As a result, I compiled the latest drives and it worked!

You can find nice instructions in there, but in short:
take the latest from 
[http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)
(at the moment compat-wireless-2008-08-06.tar.bz2)

extract it, tar jxvf compat-wireless-2008-08-06.tar.bz2

go to the folder, $cd compat-wireless-2008-08-06

build it, $make 

install, $sudo make install

unload old modules, $make unload

load new modules, $make load

You are done, and everything should be fine!

Nice thing about this package is that you can (or at least you should be able to) go back to using your old drivers, $sudo make uninstall [I did not try this one]

This packages is said to support the following drivers
adm8211, at76_usb, ath5k, b43, b43legacy, iwl3945, iwl4965, ipw2100, ipw2200, ub8xxx, libertas_cs, p54_pci, p54_usb, rndis_wlan, rt2400pci, rt2400pci, rt2500pci, rt2500usb, rt61pci, rt73usb, rtl8180, rtl8187, zd1211rw 

P.S. 
-installing linux-backports-modules-hardy-generic did not help
-$sudo rmmod iwl3945 and $sudo modprobe -v iwl3954 disable_hw_scan=1 not working either

---

