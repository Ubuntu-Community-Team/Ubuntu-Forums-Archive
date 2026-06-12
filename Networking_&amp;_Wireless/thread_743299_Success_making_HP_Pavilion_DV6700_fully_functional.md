---
title: "Success making HP Pavilion DV6700 fully functional!!!"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by paraplegicpanda on 2008-04-02
Okay, I have been over hundreds of threads in multiple forums and done WAY too many clean installs over the past three days, but now this laptop is up and running in 64 bits of glory!!! The only two things that didn't work for me straight out of the box were the video and the built in wireless card (the hardest part to fix).

Here's what I did for the wireless:
I can't figure out where I found this tutorial as I found it before my last clean install and saved it in an office file on my storage partition... If you know where this tutorial came from, please pm me so I can add accreditation.
So, first I did an absolute clean install. I hooked my LiveDrive and an ethernet cable to my laptop and went straight into the install (LiveDrives work only in Safe Graphics mode on these computers). Once it was finished and I got bored with my game of nibbles, I restarted my computer and logged in. I DID NOT install any updates or programs whatsoever. I think this may be the key. As soon as my desktop loaded, I opened the terminal and followed these instructions:

> 
1. Open your terminal

2. Get this version of madwifi:
```
wget -c http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
```

3. Untar the downloaded package:
```
tar xvf madwifi-ng-r2756+ar5007.tar.gz
```

4. Get inside the unpacked directory:
```
cd madwifi-ng-r2756+ar5007
```

5. If you haven&#8217;t compiled anything from source before on your linux then you propably need the build essential package:
```
sudo apt-get update && sudo aptitude install build-essential
```
//*NOTE: This will be necessary because you SHOULD NOT install ANYTHING before you follow these instructions.*//

6. Now you can build your madwifi and install the modules:
```
make
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
```
The last 2 commands can cause some complications on some systems. If they do check your System >> Administration >> Restricted Drivers Manager and disable atheros here. Then try again.

7. Now restart your computer and you should be able to see any available networks in your Network Manager.

I did end up having to disable the HAL in the Restricted Drivers Manager because it is enabled by default. You'll have to restart after you disable HAL, then just run the last two "sudo modprobe" commands again.

Now that I have my wifi fixed, I can fix my video card. To do so, go into your Restricted Drivers Manager again and enable the NVIDIA accelerated graphics driver (latest cards) and restart your computer again. Now that your drivers are installed, you just have to fix your resolution. Open a terminal and type:
```
sudo nvidia-settings
```
If you don't run this with sudo then it won't allow you to save your new video settings to the X config file. I am going to be very specific about the placement of this window because the computer defaults to a resolution that won't allow you to see all of the buttons you need to unless you follow these instructions exactly. Move the NVIDIA X Server Settings window to the top left corner of your screen. In the list on the left of the window, click on "X Server Display Configuration." There will be an option that says Resolution: 800x600. Click on the 800x600 and change it to 1280x800 (max settings for our screen, go lower if you like but I don't suggest it). Now press the "tab" key 7 times. This will focus you on a button that you cannot see. Hit Enter and your screen should adjust to your new resolution! Now just click the "Save to x Configuration File" button and you're good to go!!!

YAY!!! Working wireless and video!!! YIPPEE!!!

Anyways, now that your wifi and video and video are working, feel free to install all of your favorite applications and go on with your new linux laptop. I believe I have all of the hardware working on my laptop so if you have a DV6700 and are having problems, feel free to pm me and ask for help. I am barely a novice Linux user, but I'll do my best to help you out. I really hope this saves somebody the three days of trouble that I went through to get everything working. Enjoy!!!


EDIT: The light on my wireless switch DOES NOT turn blue. It stays orange regardless of whether the switch is on or off. If you try this method and your switch is working but your light remains orange, try either another laptop or moving to a place where you absolutely know there will be wireless signal... The light may but most likely will not be an indicator of whether or not your box is fixed.

!!!UPDATES!!!
Okay, I just upgraded to the 8.04 Hardy Heron Beta. Our computers DO NOT have out-of-the-box compatibility for wireless with 8.04 (at least not in the beta, I'll let everybody know what happens as soon as I get my hands on the full release). I am working on getting my wireless working again with Hardy because this tutorial is apparently no good for it. I'll update again once I get things up and running.

---

### Post by kevross_33 on 2008-04-04
Hey. I have been trying guide on getting it working for about a day now for the wireless. I hope not installing update isn't the key as I have my ubuntu as I want it lol. Apart from the wireless not working. 

anyway did yours automatically detect the wireless and the wireless switch turns blue? Mines just stays orange, I have tried all the ndiswrapper methods I have found but to no avail. i might try a kernel update see if that helps but only as a last resort as I prefer sticking with the ubuntu kernel releases. On the other hand I may just update to the development release of hardy herron that is to be released soon. 

Any other things you came across, thanks

---

### Post by linuxuser187 on 2008-04-05
i also have a hp dv6424 and have had nothing but problems for setting up my broadcom wireless using ndiswrapper and have tried many tutorials to no avail, Can't use the bcm43xx firmware from the restricted drivers as it doesn't work. i had this broadcom working under ubuntu 7.04 32bit but the upgraded to 7.10 64bit, at this stage right now i formated the ubuntu partion and will try this method and report back to see if it was of any good, Edit just realized this is for a atheros chipset!

---

### Post by kevross_33 on 2008-04-05
Hey, apparantly madwifi does not support the chipset and there seems to only be a patch for the 32 bit version of ubuntu :S Not good as I am using a 64 bit system. I have heard that the 2.2.24 kernel has better support for wireless and the wireless switches now found on laptops to turn it on and off, I may upgrade the distro to hardy heron as it uses that kernel tree. I did take the atheros folder from vista and installed in with ndiswrappers but even though it then said the hardware was present it still never worked or showed up anything in ifconfig, iwconfig etc..

I will keep trying as I am sure there is a way. If not i will just buy a removable wireless card that works lol.

---

### Post by paraplegicpanda on 2008-04-07
Actually the tutorial installs the newer MadWiFi drivers that DO support our card... I tried this method before I ran another install and it did not work, but after a clean install all was well... I hate to suggest to anybody to get rid of everything that they have already got the way they want it, but it's the only way I've found success so far.

My wireless does work, including the switch, but the light stays orange no matter what, on or off. Personally I don't mind it because the card works, but that is probably something to add...

---

### Post by paraplegicpanda on 2008-04-07
One more thing... if you absolutely cannot get your card working but you are willing to make the upgrade early, you may want to try the Hardy Heron (8.04) beta out, like kevross mentioned.

---

### Post by tab0u on 2008-04-13
Hi guys!I have the pavilion 6760ev and i cant install ubuntu 8.04!In the boot screen when i choose "try ubuntu.." or "install" it freezes!I try to change the boot parameters as in others posts (noacpi nolacpi etc) but with no result. :(    any ideas or suggestions?

ps.sorry for my english.

---

### Post by 67GTA on 2008-04-15
Thanks for the how-to. Wireless was the only thorn I had left. The only problem was the modules wouldn't survive a reboot, so I put the two modules in /etc/modules. Now wireless is there after rebooting.

---

### Post by dwdude on 2008-04-17
Thank you VERY much for this how to!

It works perfect for me, using Gutsy right now, i386 Ubuntu.

I have the Atheros AR5006EG 802. 11b/g PCI wireless card, and I have been to SEVERAL different threads to get this working to no avail.

This was my desperation attempt and BAM! Perfection.

Well... The little red LED saying that the wireless card isn't enabled is supposed to be blue... But whatever, I dont care, wireless is working now!

Thanks again for posting. :)

EDIT: I lied, it's not perfect.

It says I'm connected to a wireless signal, but I'm not receiving anything from it. *sighs and plugs the ethernet back in*

---

### Post by The_Lost_World on 2008-04-23
[COLOR="DarkRed"]Hey, does this work on 23bit computers as well? 

If not, does anyone know how to get it working on my 32bit machine?

Thanks![/COLOR]

---

### Post by VijayakumarK on 2008-04-24
After trying madwifi + Atheros 5006EG on my dv6700z with Kubuntu 8.04(32bit), I used ndiswrapper, and got wireless working. 

Here is what I did
1. Blacklist ath_pci first
As root
> 
echo &#8220;blacklist ath_pci&#8221; >> /etc/modprobe.d/blacklist

2. Install ndiswrapper
> sudo apt-get install ndiswrapper-common
3. Download driver for Atheros 5006. You can either copy it from your driver CD or download it from the link [http://www.atheros.cz/download.php?atheros=AR5006EG&system=1](http://www.atheros.cz/download.php?atheros=AR5006EG&system=1)
what worked for me is the XP 32 bit version. 
4. extract the zip file to a folder
5. Install the driver in ndiswrapper
> 
sudo ndiswrapper -i net5211.inf
sudo ndiswrapper -m

6. Reboot

On HP dv6700z(kernel 2.6.24), I the wireless LED didn't turn blue. However wireless works quite well ( I use WEP ). I'm not sure if Radiokill ( wireless switch ) works with this install.

P.S I had problems making ndiswrapper / driver work in 64bit version

---

### Post by mills on 2008-05-17
> **67GTA said:**
> Thanks for the how-to. Wireless was the only thorn I had left. The only problem was the modules wouldn't survive a reboot, so I put the two modules in /etc/modules. Now wireless is there after rebooting.

i wanna try this but dont know what 2 modules your talking about,

any help is appreciated

---

### Post by linux-tortoise on 2008-06-03
Does anyone know where I can get the HP version of the Atheros ar5007 card for an HP dv6500z? On the drivers and downloads page there are drivers for this card, which tells me that the card is included on HP's very short list of authorized hardware. However, I am assuming that it will have the bios on the card modified by HP in order for it to work on an HP computer. If I am wrong, and any card with that chip will work, then let me know. If you have one in your computer, I would appreciate it a lot if you could look at it and see what the HP part number is. I might be able to find it that way. All searches for the card on HP's site and through google have not turned up the card. Calling HP does not work. They can't find it either. But obviously, some people have it, so it does exist.

ANYONE???

---

### Post by racie on 2008-07-09
paraplegicpanda, my brother and i did the entire thing you said in the how-to, but it still doesn't work.  wireless internet isn't even an option, just wired or ppoe.  no wireless.  any suggestions?  i'm really desperate.

*edit* sorry for the bump

---

### Post by ufnoise on 2008-07-16
I have the driver working.  However you must always do something to the hardware to get it to respond.  For example:

/sbin/ifconfig wlan0 hw ether  00:1f:e1:6c:65:a8   
/sbin/iwconfig wlan0 key off essid "blah"

Until I do the first command, the second will not work.

---

