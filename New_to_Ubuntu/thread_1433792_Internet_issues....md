---
title: "Internet issues..."
date: 2010-03-19
forum: New to Ubuntu
---

### Post by Flaredancer on 2010-03-19
I've posted questions in other forums but one of them redirected me here.
I'll copy and paste my original question...

[noob]
Okay. So I've just recently installed my first Linux OS, Ubuntu Studio. I don't have the wireless card driver and I can't get it with the regular Driver Manager, so a friend recommended I get the restricted drivers manager.

He said the command to get that went like this:

sudo apt-get install jockey-gtk

But when I did that it just said I already had that. So, me beilng weird, I switched jockey-gtk to restricted-manager and got this output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package restricted-manager is a virtual package provided by:
  jockey-gtk 0.3.3-0ubuntu8.2
You should explicitly select one to install.
E: Package restricted-manager has no installation candidate


What do I do to get the manager? 

(It isn't in the 'Add/Remove' section either.)

[/noob]
---
BY THE WAY!

As a reply I was told to tell the output to :
[FONT=monospace]sudo lshw -C network

Here it is:
  *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:46:ff:f2
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.2.102 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s


Sorry for the huge post.. Thanks for any help!

-Flaredancer
[/FONT]

---

### Post by yeats on 2010-03-19
Go to System -> Administration -> Synaptic Package Manager, put in your password, then type "jockey" in the Quick search bar.  jockey-gtk will be one of the options.  Right-click on it and select "Mark for Installation", then Apply.  This should do it for you.

---

### Post by Flaredancer on 2010-03-19
> **chrissharp123 said:**
> Go to System -> Administration -> Synaptic Package Manager, put in your password, then type "jockey" in the Quick search bar.  jockey-gtk will be one of the options.  Right-click on it and select "Mark for Installation", then Apply.  This should do it for you.


That's the thing.
I've already got this, so the only options are:

Mark for reinstallation
Mark for removal
Mark for complete removal

Should I just reinstall it?

-BTW.
When I type:
sudo jockey-gtk

into terminal, the Hardware Drivers manager comes up; but there are no available drivers.
"No proprietary drivers are in use on this system."

Someone on my other question asked what the output was for that; I forgot to post it here.

---

### Post by yeats on 2010-03-19
> Should I just reinstall it?

Nah - I was misunderstanding your request (thinking you could not install jockey-gtk).  What is your main issue? Your wireless card isn't working?

---

### Post by Flaredancer on 2010-03-19
> **chrissharp123 said:**
> Nah - I was misunderstanding your request (thinking you could not install jockey-gtk).  What is your main issue? Your wireless card isn't working?

Right.

EDIT:

Forgot to mention. I don't have the driver for my wireless card and don't know how to get it; I believe this is the problem.

---

### Post by yeats on 2010-03-19
If you will, please post the output of:

```
lspci
```

and wrap it in CODE tags (use the # button when composing).  That will give a little more specifics about your model wireless card.

---

### Post by Flaredancer on 2010-03-19
> **chrissharp123 said:**
> If you will, please post the output of:

```
lspci
```and wrap it in CODE tags (use the # button when composing).  That will give a little more specifics about your model wireless card.

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)
```

Like that?

---

### Post by bkratz on 2010-03-19
> **Flaredancer said:**
> Right.

EDIT:

Forgot to mention. I don't have the driver for my wireless card and don't know how to get it; I believe this is the problem.




From what I have read in several other threads, Ubuntu Studio doesn't come with network manager installed--see this thread

[http://ubuntuforums.org/showpost.php?p=8964462&postcount=2](http://ubuntuforums.org/showpost.php?p=8964462&postcount=2)

And has to be installed before wireless can be made to work

---

### Post by yeats on 2010-03-19
Exactly!

```
0c:00.0 Network controller: Atheros Communications Inc. **Unknown device** 002a (rev 01)
```

Do you know your card's model number?

---

### Post by Flaredancer on 2010-03-19
> **chrissharp123 said:**
> Exactly!

```
0c:00.0 Network controller: Atheros Communications Inc. **Unknown device** 002a (rev 01)
```Do you know your card's model number?

Sorry to say, I don't. I could find out for you if you let me know how..

@bkratz..
I have network manager installed. It does not come up with any wireless networks because I don't have the driver.

---

### Post by bkratz on 2010-03-19
> **Flaredancer said:**
> Sorry to say, I don't. I could find out for you if you let me know how..

@bkratz..
I have network manager installed. It does not come up with any wireless networks because I don't have the driver.

This thread gives a command to update the pci id's, maybe that would help. It also says that often the device will show up as unknown if not enabled in the bios.

[http://ubuntuforums.org/showthread.php?t=528985](http://ubuntuforums.org/showthread.php?t=528985)

---

### Post by Flaredancer on 2010-03-19
> **bkratz said:**
> This thread gives a command to update the pci id's, maybe that would help. It also says that often the device will show up as unknown if not enabled in the bios.

[http://ubuntuforums.org/showthread.php?t=528985](http://ubuntuforums.org/showthread.php?t=528985)

Did that. The new output is this:
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

---

### Post by Flaredancer on 2010-03-19
OH. ALSO.

I had recently downloaded and installed a rather unpopular version of Linux - Musix.
This version worked just fine with my wireless card, I didn't need to do anything after starting it up to get it working. It auto-connected to my wireless internet at home and I was good to go. I switched to Ubuntu Studio (which I still like a lot better) because it was old and slow..

I don't know if that information is helpful or not but figured it was worth mentioning.

EDIT:
Sorry for the double post D;

---

### Post by bkratz on 2010-03-19
> **Flaredancer said:**
> OH. ALSO.

I had recently downloaded and installed a rather unpopular version of Linux - Musix.
This version worked just fine with my wireless card, I didn't need to do anything after starting it up to get it working. It auto-connected to my wireless internet at home and I was good to go. I switched to Ubuntu Studio (which I still like a lot better) because it was old and slow..

I don't know if that information is helpful or not but figured it was worth mentioning.

EDIT:
Sorry for the double post D;

Here is a pretty good thread for your card

[http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X](http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X)

---

### Post by Flaredancer on 2010-03-19
> **bkratz said:**
> Here is a pretty good thread for your card

[http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X](http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X)

Please remember that I am an absolute beginner :(

I don't know what any of this stuff means.. All I need is to get the driver and install it and I don't know how to do that :(

---

### Post by cchhrriiss121212 on 2010-03-22
> All I need is to get the driver and install it and I don't know how to do thatGetting a wireless device to work is often not much to do with installing a driver due to the way linux is set up. Anyway, there seems to be a simple solution in that thread:
> I commented the ath_pci blacklist in /etc/modprobe.d/blacklist-ath_pci.conf.

You check if ath9k (or ath5k) is loaded in /etc/modules

echo ath9k | sudo tee -a /etc/modules

Then you install

linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic (and linux-backports-modules-wireless-karmic-generic-pae if you can but I didn't need it)

Reboot and all should be fine! :wink:To translate:
Open a terminal and paste this: ```
sudo gedit /etc/modprobe.d/blacklist-ath_pci.conf
``` which allows you to edit a system file. Enter a ```
#
``` at the start of the line with ath_pci on it, so that it looks like this: ```
#blacklist ath_pci
```
The # symbol is used at the start of a line in a sytem file to denote a comment for the user, it will be ignored by any process using the file. Save and exit.

Paste ```
echo ath9k | sudo tee -a /etc/modules
``` into a terminal.

Search for those backport modules in synaptic. If you want anything installed use synaptic.

---

### Post by gordintoronto on 2010-03-22
> **Flaredancer said:**
> Please remember that I am an absolute beginner :(

I don't know what any of this stuff means.. All I need is to get the driver and install it and I don't know how to do that :(

That is how you would do it in Windows, but Linux is not Windows.

Linux includes a huge number of drivers which are automatically loaded as needed, but sometimes there are too many loaded, which is what blacklisting is all about.

---

### Post by Flaredancer on 2010-03-27
@cchhrriiss121212
Thanks for translating that for me. I saw the solution but didn't know what to do with it. Unfortunately when I paste the last line that you gave me I get the following output:

```

aveenhof@kiwi-laptop:~$ echo ath9k | sudo tee -a /etc/modules
sudo: unable to resolve host kiwi-laptop
ath9k

```What do I do from here?

EDIT: I quoted you and then realized that the quote was really long and didn't really add to my post, so I deleted it.

---

### Post by cchhrriiss121212 on 2010-03-27
Thats an new error for me, but I found a fix here on the forums:
[http://ubuntuforums.org/showthread.php?t=723361&highlight=sudo%3A+unable+resolve+host](http://ubuntuforums.org/showthread.php?t=723361&highlight=sudo%3A+unable+resolve+host) 
If you ever get an error like this in terminal just paste it into the search box or google and 9/10 times you can find a fix in 5 mins.

In case you cannot follow the link just do this:
gksudo gedit /etc/hostsFor the line that begins 127.0.1.1, delete any text that appears after kiwi-laptop.
Then save and exit like before and carry on with the wireless fix.

---

### Post by Flaredancer on 2010-03-27
> **cchhrriiss121212 said:**
> Thats an new error for me, but I found a fix here on the forums:
[http://ubuntuforums.org/showthread.php?t=723361&highlight=sudo%3A+unable+resolve+host](http://ubuntuforums.org/showthread.php?t=723361&highlight=sudo%3A+unable+resolve+host) 
If you ever get an error like this in terminal just paste it into the search box or google and 9/10 times you can find a fix in 5 mins.

In case you cannot follow the link just do this:
gksudo gedit /etc/hostsFor the line that begins 127.0.1.1, delete any text that appears after kiwi-laptop.
Then save and exit like before and carry on with the wireless fix.

The code you gave me gave me an error message so I looked on the link you posted. The text file that came up didn't even have a line like the one you spoke of so I added it to resemble the one it should have looked like after erasing the text... And it worked. 
But.
The output for the last command was:
```

ath9k

```
But I searched for this in Synaptic with no search results.

Suggestions?

---

### Post by cchhrriiss121212 on 2010-03-28
The last command to put in was this:
```
echo ath9k | sudo tee -a /etc/modules
```
Which should just add a line to /etc/modules.

After that open synaptic and search for all the packages mentioned one at a time: 
> linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic (and linux-backports-modules-wireless-karmic-generic-pae if you can but I didn't need it)

You don't need to search for ath9k.

---

### Post by Flaredancer on 2010-03-28
> **cchhrriiss121212 said:**
> The last command to put in was this:
```
echo ath9k | sudo tee -a /etc/modules
```Which should just add a line to /etc/modules.

After that open synaptic and search for all the packages mentioned one at a time: 


You don't need to search for ath9k.

Ohh. Okay.

Er, I installed those packages and restarted like it told me to and I don't know / don't think wireless is working.

I'm a little clueless as to how to set this up because I'm stupid :(

How can I find out if it's working? Will it just automatically connect or something?

---

### Post by cchhrriiss121212 on 2010-03-28
You are not stupid for not knowing how to do something, your knowledge of things like this will increase as you use Linux more often.

It won't automatically connect unless you have done so before. You need to left click on the network manager on the top right side of the toolbar and look for your available connections. There should be wired and wireless options headings in bold text. If you just see these as greyed-out, or "wireless connections" is missing then I would double check the modules you installed in synaptic by looking in file>history.

---

### Post by Flaredancer on 2010-03-28
> **cchhrriiss121212 said:**
> You are not stupid for not knowing how to do something, your knowledge of things like this will increase as you use Linux more often.

It won't automatically connect unless you have done so before. You need to left click on the network manager on the top right side of the toolbar and look for your available connections. There should be wired and wireless options headings in bold text. If you just see these as greyed-out, or "wireless connections" is missing then I would double check the modules you installed in synaptic by looking in file>history.

When I click this icon (network MONITOR, I believe?) It comes up with a window titled 'Connection properties: eth0'. Nothing about wireless. The packages I installed were correct.

Also. I tried installing the network MANAGER from my add/remove applications applet and when I tried it gave me this error:
---
This application conflicts with other installed software. To install 'network-manager-gnome' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.
---
Earlier it also gave me an error installing this (this is a different error for the same thing) telling me to insert a disc of some sort.

I have the wicd network manager but that does not recognize any wireless networks.

---

### Post by Flaredancer on 2010-03-28
ALSO.

The wireless driver for my card, Atheros AR928x, is something like MadWifi (I believe that is what it is called). My friend downloaded and compiled all of that for me but he had a problem with a final part (creating an interface, I believe.)

If that information's helpful at all.

---

### Post by cchhrriiss121212 on 2010-03-28
You have wicd installed which is a network manager. If you go to preferences after clicking on the wicd icon you can set the wpa driver to madwifi or others. What is it set on now?

I have not installed madwifi before, and the other fixes do not mention it, so I've got these two suggestions. 1. Switch wpa driver to wext in wicd 2. Install gnome network manager from synaptic.
Based on other users reports here on the forums, all most people need is to install the backport modules.

---

### Post by Flaredancer on 2010-03-28
It was set on wext. I changed it to madwifi and that didn't make it work, so I put it back to wext for the time being.
As for the network manager; I searched gnome network manager in synaptic and the closest thing I saw was just 'network manager'. That's it, right?

Well, while downloading this I got the error..
Ubuntu-Studio 9.10 _Karmic Koala_ - Release amd64 (20091027)
in drive /cdrom/

And while installing it I got 
W: Failed to fetch cdrom:[Ubuntu-Studio 9.10 _Karmic Koala_ - Release amd64 (20091027)]/pool/main/n/network-manager/libnm-util1_0.8~a~git.20091013t193206.679d548-0ubuntu1_amd64.deb
  
/facepalm

---

### Post by cchhrriiss121212 on 2010-03-28
It's trying to install from the studio dvd for some reason so just put it in the drive and try again.

---

### Post by Flaredancer on 2010-03-28
> **cchhrriiss121212 said:**
> It's trying to install from the studio dvd for some reason so just put it in the drive and try again.

Well that's the thing.
I had trouble installing 9.1... Got errors during the GRUB portion and the Software portion of installation.
So I decided to install 9.04 and upgrade; I don't have the 9.1 disc.

I'm not gonna try with the 9.04 disc without your knowing this because it may be different.

EDIT. I found the disc I tried to install 9.1 with and even though I had errors during installation it seemed to work when installing the Network Manager.

This being said, my problem isn't fixed.. I can't see any wireless networks and if I could I wouldn't know how to...

---

### Post by cchhrriiss121212 on 2010-03-29
You should have an icon for network manager instead of wicd on the taskbar which will give you network availability. To be honest, the problem might have occurred from you upgrading to karmic which is not a wireless friendly release, and a fresh install is always preferable to an upgrade.

I would try a fresh install of regular karmic with the backports fix. Or try installing these drivers:
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

---

### Post by Flaredancer on 2010-03-29
> **cchhrriiss121212 said:**
> You should have an icon for network manager instead of wicd on the taskbar which will give you network availability. To be honest, the problem might have occurred from you upgrading to karmic which is not a wireless friendly release, and a fresh install is always preferable to an upgrade.

I would try a fresh install of regular karmic with the backports fix. Or try installing these drivers:
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)


How do I tell if I have my kernel headers installed? I don't remember doing it but it may have come with Ubunto or my friend may have done it while working on my laptop.

Also.
I tried the clean install a few times but as I said before I kept getting errors during..
A) The select and install software stage; it got to 80% and then the screen went red but gave me the option to skip. When I did, it gave me another one..
B) The GRUB installer part after like 10%. The rest finished just fine but obviously I can't start without the GRUB.

Thanks for all the help you're giving me, by the way. I **really** appreciate it.

---

### Post by cchhrriiss121212 on 2010-03-29
You can check for installed packages by searching in synaptic.
The trouble with studio is that the installation is not that great for a lot of people. What I suggest is that you try installing a regular version of Ubuntu karmic, then try getting wireless going. Or try another linux distro if you are up to it.
Once you have that you can install the studio package from synaptic. Alternatively you can dual boot with a shared /home partition so that you have one OS for pure studio work and another for internet use and entertainment. This is what I do and it works great, I can explain how to do that if you like.

---

### Post by Flaredancer on 2010-03-29
> **cchhrriiss121212 said:**
> You can check for installed packages by searching in synaptic.
The trouble with studio is that the installation is not that great for a lot of people. What I suggest is that you try installing a regular version of Ubuntu karmic, then try getting wireless going. Or try another linux distro if you are up to it.
Once you have that you can install the studio package from synaptic. Alternatively you can dual boot with a shared /home partition so that you have one OS for pure studio work and another for internet use and entertainment. This is what I do and it works great, I can explain how to do that if you like.

That would probably be the best way to go; I was considering that and my friend suggested it. I've tried another linux distro, Musix, and I kinda liked it (wireless started up instantly, by the way ;P) but it was old and slow.

What should I use for my 'entertainment' OS? Windows 7? If so I'll need a while to get a.. Legitimate copy because the BS ones have timebombs now :(

---

### Post by cchhrriiss121212 on 2010-03-30
> What should I use for my 'entertainment' OS? Windows 7?

I would only look at windows if you play a lot of games, linux based OS's can handle everything else that windows can. I'm currently using crunchbang for mine, which is lightweight, very stable and useable. It's based around ubuntu (new release, 10, will switch to debian) so you would find it easy to get along with. I'm using the alpha version of 10 right now, and it is very good.

---

### Post by Flaredancer on 2010-03-30
> **cchhrriiss121212 said:**
> I would only look at windows if you play a lot of games, linux based OS's can handle everything else that windows can. I'm currently using crunchbang for mine, which is lightweight, very stable and useable. It's based around ubuntu (new release, 10, will switch to debian) so you would find it easy to get along with. I'm using the alpha version of 10 right now, and it is very good.

Thankfully I don't play a lot of games anymore. I played WoW for a bit but I lost passion for it. :3

I'll take a look at that OS. I'd love to get wireless working on Studio so I will still work on that (not as avidly as I am right now..), and if I ever do I'll dump the other OS, because the main things I need internet for aren't intensive; IM clients and Facebook, lol.

Thanks for all your help! Legitimately.

-FD :popcorn:

---

