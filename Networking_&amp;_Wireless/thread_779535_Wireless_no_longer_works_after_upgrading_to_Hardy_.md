---
title: "Wireless no longer works after upgrading to Hardy Heron"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by TomThePhotographer on 2008-05-02
I upgraded from Gutsy Gibbon 7.10 to Hardy Heron 8.04 LTS last night, using the update manager in Gutsy Gibbon,  but after rebooting my wireless card no longer works.:( :confused: I have a D-link dwl-510 wireless card. It still shows up in the Device Manager, but I have nothing showing wireless connections on the upper right panel. What can I do to fix this? Have I missed something obvious? I am a new user of both Gutsy Gibbon and Hardy Heron.

Should I install NDISWrapper and use the windows driver that came with my d-link dwl-510 card as suggested here? 

[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

How can I do this when I can't even get online to download the ndisgtk package? :confused: Do I have to burn a Hardy Heron istallation CD and get it from there? :(  I was hoping to avoid having to do this. :(

---

### Post by c007c on 2008-05-02
Did you upgrade wirelessly? Not always, but sometimes wireless gets bumped during the reconfiguration, leaving you without the HAL/backport wireless drivers. Plug into ethernet, wait a few. If the update doesnt start on its own, do it manually.

---

### Post by CoeusTitan on 2008-05-02
> **TomThePhotographer said:**
> I upgraded from Gutsy Gibbon to Hardy Heron last night, but now my wireless card no longer works.:( :confused: I have a D-link dwl-510 wireless card. It still shows up in the Device Manager, but I have nothing showing wireless connections on the upper right panel. What can I do to fix this? Have I missed something obvious? I am a new user of both Gutsy Gibbon and Hardy Heron.

Should I install NDISWrapper and use the windows driver that came with my d-link dwl-510 card as suggested here? 

[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

How can I do this when I can't even get online to download the ndisgtk package? :confused: Do I have to burn a Hardy Heron installation CD and get it from there? :(  I was hoping to avoid having to do this. :(

I dealt with the same thing when upgrading to Hardy. When you upgrade, the OS "re-disengages" the restricted drivers, so you have to re-enable / re-install them again.

Like in my case, I had to re-enable the restricted fwcutter, plug an ethernet cable into my labtop so the fwcutter could download the firmware again, then it installed the firmware. It took about 30 seconds for networks to pop up in the list, but it worked.

Now this is just my experience, but from what happened to me, I gather that whatever you had to do to install the wireless drivers for Gutsy, you'll have to do for Hardy again.

It's a pain, but I did it anyways, because I love ubuntu =)

Sorry if this didn't help much, as I'm still new around here.

=)

---

### Post by TomThePhotographer on 2008-05-02
Yes, i upgraded wirelessly. Plug into the ethernet? I don't have any way to plug this old Pentium III direcly into my router, if that's what you mean. I guess I would have to install an ethernet card. :( I was hoping to avoid having to do that, too. How about just going backwards and re-installing Gutsy Gibbon? Would that solve my problem? :(

---

### Post by CoeusTitan on 2008-05-02
Oh, and burning a installation disk isn't going to help, as everything you'll need is from other online sources.

Are you not able to jack in to your router via an ethernet cable temporarily as you fix this? That's what I had to do.

Ah, nevermind, as I see you've got a Pentium III....ouch, lol =)

Well...you can either install a ethernet card, or you can use another computer and put the needed files on a burned CD, and then onto your little ol' P/III.

---

### Post by TomThePhotographer on 2008-05-02
When I originally installed Gutsy Gibbon, my Wireless card was recognized, no problem, it's only with the update to Hardy Heron that I can't use my wireless card. :( :confused:

---

### Post by c007c on 2008-05-02
> **TomThePhotographer said:**
> Yes, i upgraded wirelessly. Plug into the ethernet? I don't have any way to plug this old Pentium III direcly into my router, if that's what you mean. I guess I would have to install an ethernet card. :( I was hoping to avoid having to do that, too. How about just going backwards and re-installing Gutsy Gibbon? Would that solve my problem? :(

If thats how you were successful originally, yes. Then give the upgrade a second try. Sometimes it works. But before you do, check and see if the linux-restricted-modules and common 2.6.24 are loaded. try installing them

---

### Post by TomThePhotographer on 2008-05-02
I don't have any way of connecting an ethernet cable to my ubuntu installed computer. Couldn't I just do a complete re-installation of Gutsy Gibbon? ( a step backwards, it seems) :(

---

### Post by TomThePhotographer on 2008-05-02
This page seems to suggest a way of installing NDSWrapper without an internet connection...

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

Install "ndiswrapper" package with working internet connection (Ethernet):

Quote:
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9  

Install "ndiswrapper" package without working internet connection (alternatively, install it via Synaptic/Adept):

Quote:
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

---

### Post by TomThePhotographer on 2008-05-02
> **c007c said:**
> Check and see if the linux-restricted-modules and common 2.6.24 are loaded. try installing them

How do I do this?:confused:

---

### Post by c007c on 2008-05-02
System--->Administration--->Synaptic Package Manager. Then perform a search for "restricted". Mark for installation, apply. I'm hoping the package was downloaded, but not installed. or possibly you will see the former versions under installed or obsolete. they might get you by till you upgrade them

---

### Post by c007c on 2008-05-02
I have not done this...there is an option to add a cd under the Edit tab in the Synaptic Package Manager, whether it can see packages is unknown. You may want to try this as well, see if you can find the former restricted drivers, 

Here's some info

[https://wiki.ubuntu.com/AddLocalRepositorySpec](https://wiki.ubuntu.com/AddLocalRepositorySpec)

---

### Post by Ichido on 2008-05-02
> **c007c said:**
> If thats how you were successful originally, yes. Then give the upgrade a second try. Sometimes it works. But before you do, check and see if the linux-restricted-modules and common 2.6.24 are loaded. try installing them

I also lost my wireless connection.
I partitioned my hard drive then Installed 8.04 on sda6.
I still have the OEM,7.01, on sda3 with the Wifi working!

How do I check for "linux-restricted-modules" and "common 2.6.24?

How do I "re-enable the restricted fwcutter"?

---

### Post by Ayuthia on 2008-05-02
For those of you who are saying that they lost their wireless, can you post your lspci -nn?  If you are connecting from another computer, can you at least look at lspci -nn and post the information for anything that is either a Network Controller or an Ethernet Controller?  I just want to make sure that we give you the right information about your wireless.

Both the Linux native Intel and Broadcom drivers have changed in this new kernel (2.6.24).  Because of this, some iwl3xxx or iwl4xxx drivers have changed and those who where using the bcm43xx driver are now using the b43 driver.  Unfortunately, both of them will require a download of some sort if you want to use the native driver.  The Broadcom cards can also use NDISwrapper so if you were using NDISwrapper prior to Hardy, you might just need to reinstall NDISwrapper and use the driver that you used in the prior version.

---

### Post by Ichido on 2008-05-02
This is from my 7.10's lspci -nn:

0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

The 7.10 has the working wifi!

How do I set up this in my 8.04?

I checked the Restricted Drivers in my 7.10 and it states:
"Conexant modem engine" & "Intel(R) PRO/Wireless 3945 Network Connection driver for Linux"
Both of these show as "In Use".

---

### Post by Ayuthia on 2008-05-02
> **Ichido said:**
> This is from my 7.10's lspci -nn:

0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

The 7.10 has the working wifi!

How do I set up this in my 8.04?
You will need to install linux-backports-modules-hardy-generic.  If you have a wired connection, you can just do:
```
sudo aptitude install linux-backports-modules-hardy-generic
```or you can go into Synaptic and install it from there.  If you don't have a connection, you will need to get the following packages from packages.ubuntu.com([http://packages.ubuntu.com/hardy/linux-backports-modules-2.6.24-16-generic):](http://packages.ubuntu.com/hardy/linux-backports-modules-2.6.24-16-generic):)
```
linux-backports-modules-2.6.24-16-generic
```Download the amd64 version if you are using 64-bit and i386 if you are using 32-bit.  Assuming that you downloaded the file to the desktop you can do the following in the Terminal:
64-bit:
```
cd /home/user/Desktop
sudo dpkg -i linux-backports-modules-2.6.24-16-generic_2.6.24-16.14_amd64.deb
```
32-bit:
```
cd /home/user/Desktop
sudo dpkg -i linux-backports-modules-2.6.24-16-generic_2.6.24-16.14_i386.deb
```
Make sure that you replace user in /home/user/Desktop with your username.

Hope that helps and works for you.

---

### Post by silberj on 2008-05-02
Up front, I am the noobest of noobs regarding Linux, but I really like Hardy, and am using wubi to make the transition off of windows. I'm really liking it so far. I did get wireless working for my Atheros card, however it is a real pain in the rear, and I have tried all the remedies I have found here. The following is the only way I can get wireless access on my laptop. 

System->Administration->Network-> After you unlock, disable the enable roaming checkbox. Then select the wireless network you desire, and enter the appropriate information. It should start reconfiguring at this point. Do not hit close, but wait for it to reconfigure. Once that is complete,close, and you should be able to go to network tools and under the ath0 adapter you should have an IP address (provided you use DHCP). If you do, then wireless should be working. The problem is reenabling after a reboot. After a reboot, you will need to do the same above, except this time you need to enable roaming mode. Once this is done, close. Then go back in and repeat the steps above. Trust me, this is a good solution after having tried everything else and failing. If anyone knows a better way, I am all ears, but I'm typing this on my wireless network from my laptop using the steps above. Good luck.

---

### Post by Ayuthia on 2008-05-02
> **silberj said:**
> I did get wireless working for my Atheros cardsilberj, can you post your lspci -nn?  Here is a link for an Atheros AR5007 install: [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

---

### Post by Ichido on 2008-05-02
I tried the "lspci -nn" in Heron 8.04 and I got the same info as in Gibbon 7.10!
I compared all of my settings in both Heron 8.04 & Gibbon 7.10 including my Firestarter Firewall.
NO Difference _except_ in my Wireless Settings!?

I finally found that:
In Heron 8.04, Wifi ONLY works with my ESSID and DHCP filled in!
In Gibbon 7.10, Wifi Only works with "Roaming Enabled"!

Don't know why the difference matters, because it's the same Laptop, a new Dell 1525n, pre-installed with Gibbon 7.10, Same Mini-card, Dual Booting with Heron 8.04 & Gibbon 7.10.:confused:

Thanks to all for your ideas and suggestions, but it's working in both now.:)

---

### Post by silberj on 2008-05-03
As per request, here is my lspci -nn:

a19dret@a19dret-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
06:04.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
06:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
06:04.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
06:04.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]

FYI, I did try the method on that link with no luck.

---

### Post by Ayuthia on 2008-05-03
> **silberj said:**
> 04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)Here is another link to try.  Check out post 6.  That person seems to have a similar card.  Do you using 32-bit or 64-bit?  If you are not sure, try uname -m.

[http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)

---

### Post by silberj on 2008-05-03
[QUOTE=Do you using 32-bit or 64-bit?  If you are not sure, try uname -m.[/QUOTE]

a19dret@a19dret-laptop:~$ uname -m
i686

My system is 32 bit, and I don't see any links at all in post #6, sorry.

---

