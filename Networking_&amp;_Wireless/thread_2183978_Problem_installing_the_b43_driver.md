---
title: "Problem installing the b43 driver"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by Filip_Lundberg on 2013-10-27
Hi mates :) I have problem with getting internet through wireless. I got internet through a ethernet cable now .

First, I installed the b43-fwcutter as you can see here: [http://tinypic.com/r/kbyb8k/5](http://tinypic.com/r/kbyb8k/5)

But then, when I try to download the b43-firmware this happens: [http://tinypic.com/r/2s0y7a8/5](http://tinypic.com/r/2s0y7a8/5) . They say that I don't have the package b43-fwcutter but as you can see, I have it !


What is the problem? :) I would be very glad if someone could help me ;)

---

### Post by chili555 on 2013-10-27
You don't say what Ubuntu version you installed, but for most recent versions, this should work:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```Detach the ethernet and use your wireless to report your progress!

---

### Post by Filip_Lundberg on 2013-10-28
The first command works fine but then, when I do the 2nd command this happened: [http://tinypic.com/r/2qw26hd/5](http://tinypic.com/r/2qw26hd/5). I tested it 3 times, the first time I received what I think is a kernel panic. And the 2 other times nothing happened, as you see on the photo :/

I'm using Ubuntu 12.04 lts.

Do you know what's wrong?

---

### Post by chili555 on 2013-10-28
Not exactly, without examining the logs. Please try a reboot. If the wireless isn't working as expected, please show us:```
dmesg | grep b43
```

---

### Post by Filip_Lundberg on 2013-10-28
Reboot didn't help.

Typing: dmesg | grep b43

Gives:
[   13.761771] b43-phy0: Broadcom 4321 WLAN found (core revision 11)
[   13.803675] b43-phy0: Found PHY: Analog 5, Type 4 (N), Revision 1
[   19.228461] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   19.324934] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   19.324938] b43-phy0 ERROR: This device does not support DMA on your system. It will now be switched to PIO.
[   19.324940] b43-phy0: Controller RESET (DMA error) ...
[   19.540279] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   19.616274] b43-phy0 warning: Forced PIO by use_pio module parameter. This should not be needed and will result in lower performance.
[   19.636800] b43-phy0: Controller restarted

Picture: [http://tinypic.com/r/2pzl5wp/5](http://tinypic.com/r/2pzl5wp/5)

---

### Post by chili555 on 2013-10-28
Ahhhh! My (least) favorite problem! You asked how to install the firmware for your device and we did so successfully. However, that didn't get you a working connection, because b43 and firmware is probably incorrect for your device!> b43-phy0: [COLOR="#FF0000"]Broadcom 4321[/COLOR] WLAN found (core revision 11)Let's go back to step 0; let's identify the actual device:```
lspci -nn -d 14e4:
```There is no need for tinypic. You can either copy and paste the data into your reply or simply copy it with pencil and paper.

NOTE TO SELF: Always verify the pci.id.

---

### Post by Filip_Lundberg on 2013-10-28
Ignore this reply. Answer the reply below instead ;)

---

### Post by Filip_Lundberg on 2013-10-28
Ok mate  I will do it inte future 


Typing: lspci -nn -d 14e4:
Gives:02:07.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)


I'm glad that you are helping me with this problem

---

### Post by chili555 on 2013-10-28
>  Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329]Congratulations! This is our lucky day!! Woo hoo! You have one of the hardest devices to get going correctly in the Broadcom stable. We know, at least that b43 and firmware is troublesome. Before we discard it and try another option, let's try one thing:```
sudo modprobe -r b43
sudo modprobe b43 pio=1
```Any improvement?

Before we try anything else, let's also verify a few other details:```
arch
lsb_release -d
```Thanks.

---

### Post by Filip_Lundberg on 2013-10-29
Here's what I get after typing the comands:
filip@Username:~$ sudo modprobe -r b43
[sudo] password for filip: 
filip@Username:~$ sudo modprobe b43 pio=1
filip@Username:~$ 

What happened? Terminal didn't give me any ''answer''.

Typing: 
arch
lsb_release -d

Gives: 
filip@Username:~$ arch
x86_64
filip@Username:~$ lsb_release -d
Description:	Ubuntu 12.04.3 LTS
filip@Username:~$ 


**Do u know what to do next? :)**

---

### Post by chili555 on 2013-10-29
> filip@Username:~$ sudo modprobe -r b43
[sudo] password for filip:
filip@Username:~$ sudo modprobe b43 pio=1
filip@Username:~$

What happened? Terminal didn't give me any ''answer''.It did give you an answer. When the terminal simply returns to the prompt, that means, roughly, 'command executed and there are no errors or warnings to report.' That's exactly what we hoped for! However, the larger thing we hoped for, that your wireless would spring to life, did not occur. We know, therefor, that the driver b43 and its firmware is not the correct fix for your  Broadcom Corporation BCM4321 802.11b/g/n [[COLOR="#FF0000"]14e4:4329[/COLOR]]. We will try another fix. 

With a working wired ethernet connection, copy and paste these commands, each one at a time:```
wget http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb
sudo dpkg -i bcmwl*.deb
```Detach the ethernet, reboot and give us your report.

---

### Post by Filip_Lundberg on 2013-10-29
Wireless still don't working.
[IMG]http://tinypic.com/r/2hnz5hx/5[/IMG]
That's how terminal 'answered'. Do u see anything wrong?

EDIT: Do you see the photo?

---

### Post by chili555 on 2013-10-29
I don't see the photo.

---

### Post by Filip_Lundberg on 2013-10-29
Okay :/ Then, I need to link you the photo through tinypic, sry mate :( [http://tinypic.com/r/rr8qva/5](http://tinypic.com/r/rr8qva/5)

---

### Post by bishop__ on 2013-10-29
@Filip_Lundberg, broadcom prepared a driver for this and it can be found  here [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php). Follow the  instructions in README.txt. You will need to download the source code  package and compile them.

---

### Post by chili555 on 2013-10-29
> **bishop__ said:**
> @Filip_Lundberg, broadcom prepared a driver for this and it can be found  here [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php). Follow the  instructions in README.txt. You will need to download the source code  package and compile them.However, the most recent STA driver doesn't work so well with kernel version 3.8 which is what is included in 12.04.3. That's why I suggested, based on many similar cases, the next older version.

---

### Post by chili555 on 2013-10-29
> **Filip_Lundberg said:**
> Okay :/ Then, I need to link you the photo through tinypic, sry mate :( [http://tinypic.com/r/rr8qva/5](http://tinypic.com/r/rr8qva/5)Looks good to me. Now what is the result of:```
sudo modprobe wl
iwconfig
sudo iwlist eth1 scan
```

---

### Post by Filip_Lundberg on 2013-10-31
@bishop_
I had the STA driver before, but I had a lot of problems with it so that's why I want the b43 instead ;)

---

### Post by Filip_Lundberg on 2013-10-31
First command: 

filip@Username:~$ sudo modprobe wl
[sudo] password for filip: 
filip@Username:~$ 

After the first command, I got wireless connection. Thank you so much for the help :) But what did that command really do? Where can I see that is the b43 driver I'm using now?

---

### Post by Filip_Lundberg on 2013-10-31
After being on the computer for a whole, I receive a kernel panic. Should I send you a photo on the kernel panic?

---

### Post by chili555 on 2013-10-31
> **Filip_Lundberg said:**
> After being on the computer for a whole, I receive a kernel panic. Should I send you a photo on the kernel panic?Yes, please.> @bishop_
I had the STA driver before, but I had a lot of problems with it so that's why I want the b43 instead The problem with that is that the b43 driver doesn't work *at all* for your device.

---

### Post by Filip_Lundberg on 2013-10-31
Ok, after the kernel panic, I restarted the computer and then, my wireless didn't work again. Are you sure that the b43 driver work for me? If yes, why?

Should I test the steps that you gave me in a former post?

---

### Post by chili555 on 2013-10-31
> Are you sure that the b43 driver work for me? If yes, why?See post #5, from your own machine. You were using b43 and there were all sorts of complaints in the message logs and, worst of all, you had *NO* wireless connectivity. You didn't have momentary connectivity. You didn't see networks but then couldn't connect. You didn't connect but then drop. You had nothing, zero, nada and zippo. Is that what you are trying to get back to?> Should I test the steps that you gave me in a former post? Please try only:```
sudo modprobe wl
```Then tell us if it's working. If so, we can make it persistent.

---

### Post by Filip_Lundberg on 2013-10-31
Here's the kernel panic: [http://sv.tinypic.com/r/29xazdk/5](http://sv.tinypic.com/r/29xazdk/5).

But the wireless worked for me when I was running windows 7 so why shouldnt it work with ubuntu?
Maybe the internet don't work because when the wireless didn't work for me in the start. I tested many tips from this forum to get wireless connection, so maybe it's just made my computer worse. What do you think? And from the message log, isn't it errors that We could solve?

I got problems with the update manager to, maybe that's the problem. 

I'm very glad for all your help and I hope you can answer this questions so I can get my wireless work :)

---

### Post by chili555 on 2013-10-31
> But the wireless worked for me when I was running windows 7 so why shouldnt it work with ubuntu?Because Windows and Linux are two completely different things. The drivers are completely different, the networking process is completely different, and...really, everything. All you've shown is that the hardware is not defective.

The picture you linked is very hard for me to read; however, I'd assume that a switch to a text console is because the graphics driver, nVidia, ATI or Intel or whomever, stopped working properly. I do see an error at x86/kernel/smp.c. That is Intel SMP support routines. As far as I know, that is not related directly to wireless.

When you modprobbed wl, did the wireless start up? If so, we can certainly run updates from the command line.

---

### Post by Filip_Lundberg on 2013-10-31
Yes, when I modprobbed wl, the wireless started up ;)

For a time ago, I was updating my nVidia driver, but then it just stopped and I restarted the computer, can it was the problem?

---

### Post by chili555 on 2013-10-31
> **Filip_Lundberg said:**
> For a time ago, I was updating my nVidia driver, but then it just stopped and I restarted the computer, can it was the problem?Oh, yes, probably so. With a working connection, try:```
sudo apt-get update
sudo apt-get upgrade
```Are there any errors, warnings, etc.?

---

### Post by Filip_Lundberg on 2013-10-31
filip@Username:~$ sudo apt-get update
[sudo] password for filip: 
Läs:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal Release.gpg                           
Läs:2 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates Release.gpg [933 B]  
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports Release.gpg                 
Läs:3 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal Release                               
Läs:4 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates Release [49,6 kB]
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release      
Läs:5 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49,6 kB]            
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports Release                     
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/main Sources                          
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/restricted Sources                    
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/universe Sources 
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/multiverse Sources                    
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/main amd64 Packages                   
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources         
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/restricted amd64 Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/universe amd64 Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/multiverse amd64 Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/main i386 Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/restricted i386 Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/universe i386 Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/multiverse i386 Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/main TranslationIndex
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/multiverse TranslationIndex
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/restricted TranslationIndex
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages  
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main TranslationIndex
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/universe TranslationIndex         
Läs:6 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/main Sources [120 kB] 
Läs:7 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [63,7 kB]       
Läs:8 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/restricted Sources [2 564 B]
Läs:9 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/universe Sources [91,9 kB]  
Läs:10 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [1 833 B]
Läs:11 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [21,3 kB]  
Läs:12 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [1 175 B]
Läs:13 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages [180 kB]
Läs:14 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/multiverse Sources [4 813 B]
Läs:15 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/main amd64 Packages [308 kB]
Läs:16 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages [3 469 B]
Läs:17 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages [63,1 kB]
Läs:18 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/restricted amd64 Packages [4 804 B]
Läs:19 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/universe amd64 Packages [207 kB]
Läs:20 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages [1 489 B]
Läs:21 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [178 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-sv_SE                    
Läs:22 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [11,9 kB]
Läs:23 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/main i386 Packages [306 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-sv                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Läs:24 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [3 531 B]
Läs:25 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [63,7 kB]
Läs:26 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/restricted i386 Packages [4 841 B]
Läs:27 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/universe i386 Packages [207 kB]
Läs:28 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [1 718 B]
Läs:29 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main TranslationIndex [73 B]
Läs:30 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse TranslationIndex [71 B]
Läs:31 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted TranslationIndex [72 B]
Läs:32 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe TranslationIndex [73 B]
Läs:33 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [12,1 kB]
Bra [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en            
Läs:34 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/main TranslationIndex [74 B]
Läs:35 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/multiverse TranslationIndex [72 B]
Läs:36 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/restricted TranslationIndex [72 B]
Läs:37 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/universe TranslationIndex [74 B]
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/main Sources                
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/restricted Sources          
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/universe Sources            
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/multiverse Sources          
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/main amd64 Packages         
Bra [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en 
Bra [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en 
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/restricted amd64 Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/universe amd64 Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/main i386 Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/restricted i386 Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/universe i386 Packages
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
Bra [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/main TranslationIndex
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/multiverse TranslationIndex
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/restricted TranslationIndex
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/universe TranslationIndex
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/main Translation-sv
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/main Translation-en
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/multiverse Translation-sv
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/multiverse Translation-en
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/restricted Translation-sv
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/restricted Translation-en
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/universe Translation-sv
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal/universe Translation-en
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/main Translation-en
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/restricted Translation-en
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-updates/universe Translation-en
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/main Translation-en
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/restricted Translation-en
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) quantal-backports/universe Translation-en
Hämtade 1 965 kB på 2s (752 kB/s)
Läser paketlistor... Färdig
filip@Username:~$ sudo apt-get upgrade
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Följande paket har hållits tillbaka:
  apport apport-gtk apt-utils aptdaemon bamfdaemon brasero brasero-cdrkit
  brasero-common compiz compiz-core compiz-gnome compiz-plugins-default
  coreutils cups-filters dbus dconf-gsettings-backend dconf-service
  evolution-data-server evolution-data-server-common firefox gcc-4.6-base:i386
  gedit gedit-common gir1.2-gtk-3.0 gir1.2-javascriptcoregtk-3.0 gir1.2-rb-3.0
  gir1.2-totem-1.0 gir1.2-unity-5.0 gir1.2-webkit-3.0 gnome-control-center
  gnome-control-center-data gnome-games-data gnome-keyring gnome-nettool
  gnome-online-accounts gnome-orca gnome-screensaver gnome-session
  gnome-session-bin gnome-session-common gnome-settings-daemon gnome-sudoku
  gnome-system-log gnomine gwibber gwibber-service gwibber-service-facebook
  gwibber-service-identica gwibber-service-twitter ifupdown imagemagick
  indicator-appmenu indicator-datetime initramfs-tools initramfs-tools-bin
  jockey-common language-selector-common language-selector-gnome
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libbamf0 libbamf3-0 libbrasero-media3-1 libcairo2 libcomerr2:i386
  libcompizconfig0 libcupsfilters1 libdb5.1:i386 libdconf-dbus-1-0
  libdecoration0 libexif12:i386 libexpat1:i386 libffi6:i386
  libfontconfig1:i386 libgail-3-0 libgcc1:i386 libgd2-xpm:i386 libgif4:i386
  libglib2.0-0 libglib2.0-0:i386 libglib2.0-bin libglu1-mesa:i386
  libgnome-control-center1 libgoa-1.0-0 libgoa-1.0-common libgpg-error0:i386
  libgphoto2-2:i386 libgphoto2-port0:i386 libgpm2:i386 libgpod-common libgpod4
  libgssapi-krb5-2:i386 libgstreamer0.10-0:i386 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libice6:i386 libieee1284-3:i386 libjavascriptcoregtk-3.0-0
  libjpeg-turbo8:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms1:i386 libldap-2.4-2:i386 libltdl7:i386
  libncurses5:i386 libopenal-data libopenal1 libopenal1:i386 liborc-0.4-0:i386
  libp11-kit0:i386 libpam-winbind libpciaccess0:i386 libpcre3:i386
  libpng12-0:i386 libpoppler-glib8 libpulse0 libpython2.7 libqt4-dbus
  libqt4-declarative libqt4-network libqt4-opengl libqt4-script libqt4-sql
  libqt4-sql-sqlite libqt4-svg libqt4-xml libqt4-xmlpatterns libqtbamf1
  libqtcore4 libqtgui4 libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math
  libreoffice-style-tango libreoffice-writer libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libselinux1:i386 libsm6:i386 libsqlite3-0:i386
  libstdc++6:i386 libtasn1-3:i386 libtiff4 libtiff4:i386 libtinfo5:i386
  libtotem0 libunity9 libusb-0.1-4:i386 libuuid1:i386 libv4l-0:i386
  libv4lconvert0:i386 libwbclient0 libwebkitgtk-3.0-0 libxau6:i386
  libxcomposite1:i386 libxdamage1:i386 libxdmcp6:i386 libxml2 libxml2:i386
  libxpm4:i386 lsb-release mahjongg nautilus nautilus-data nux-tools
  nvidia-common overlay-scrollbar poppler-utils printer-driver-postscript-hp
  procps python-apt python-aptdaemon python-aptdaemon.gtk3widgets python-gi
  python-gi-cairo python-gobject python-libproxy python-libxml2
  python-packagekit python-uno python2.7 python2.7-minimal qdbus rhythmbox
  rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  samba-common seahorse shotwell smbclient software-center
  software-properties-common software-properties-gtk telepathy-gabble
  telepathy-idle thunderbird thunderbird-gnome-support totem totem-common
  totem-mozilla totem-plugins transmission-common transmission-gtk ufw unity
  unity-common unity-greeter unity-lens-applications unity-lens-files
  unity-lens-video unity-scope-video-remote unity-services update-manager
  update-manager-core usbmuxd whoopsie winbind xdiagnose zlib1g:i386
Följande paket kommer att uppgraderas:
  accountsservice activity-log-manager-common
  activity-log-manager-control-center adium-theme-ubuntu alsa-base alsa-utils
  app-install-data-partner apparmor appmenu-gtk appmenu-gtk3 apt
  apt-transport-https apt-xapian-index aptdaemon-data at-spi2-core base-files
  bind9-host busybox-initramfs busybox-static cabextract
  compiz-plugins-main-default compizconfig-backend-gconf consolekit cups
  cups-bsd cups-client cups-common cups-ppdc dbus-x11 deja-dup dkms dmsetup
  dnsutils dosfstools duplicity ecryptfs-utils file-roller
  firefox-gnome-support firefox-locale-en fonts-droid fonts-horai-umefont
  fonts-opensymbol ginn gir1.2-atspi-2.0 gir1.2-dee-1.0
  gir1.2-gst-plugins-base-0.10 gir1.2-launchpad-integration-3.0 gnome-terminal
  gnome-terminal-data gnupg gpgv gstreamer0.10-alsa gstreamer0.10-gconf
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-x hplip
  hplip-data icoutils im-switch imagemagick-common iptables isc-dhcp-client
  isc-dhcp-common jockey-gtk launchpad-integration libaccountsservice0
  libapt-pkg4.12 libasn1-8-heimdal libasn1-8-heimdal:i386 libasound2
  libasound2:i386 libatspi2.0-0 libaudio2 libbind9-80 libc-bin libc-dev-bin
  libc6 libc6:i386 libc6-dev libcairo-gobject2 libck-connector0 libcroco3
  libcups2 libcups2:i386 libcupscgi1 libcupsimage2 libcupsmime1 libcupsppdc1
  libcurl3 libcurl3-gnutls libcurl3-nss libdbus-1-3 libdbus-1-3:i386
  libdbus-glib-1-2 libdee-1.0-4 libdevmapper-event1.02.1 libdevmapper1.02.1
  libdns81 libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau1a
  libdrm-nouveau2:i386 libdrm-nouveau2 libdrm-radeon1:i386 libdrm-radeon1
  libdrm2 libdrm2:i386 libecryptfs0 libfreetype6 libfreetype6:i386 libfs6
  libgcrypt11 libgcrypt11:i386 libgeis1 libglib2.0-data libgnutls26
  libgnutls26:i386 libgssapi3-heimdal libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base0.10-0:i386
  libhcrypto4-heimdal libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimbase1-heimdal libheimntlm0-heimdal libheimntlm0-heimdal:i386
  libhpmud0 libhx509-5-heimdal libhx509-5-heimdal:i386 libicu48 libisc83
  libisccc80 libisccfg82 libjack-jackd2-0 libkrb5-26-heimdal
  libkrb5-26-heimdal:i386 liblaunchpad-integration-3.0-1
  liblaunchpad-integration-common liblcms2-2 liblvm2app2.2 liblwres80
  libmpg123-0 libmpg123-0:i386 libnautilus-extension1a libnss3 libnss3-1d
  libpam-ck-connector libpam-gnome-keyring libperl5.14 libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpulse-mainloop-glib0
  libpulsedsp libpurple-bin libpurple0 libraw5 libreoffice-emailmerge
  libreoffice-style-human libroken18-heimdal libroken18-heimdal:i386
  libsane-hpaio libsmbclient libssh-4 libssl1.0.0 libssl1.0.0:i386
  libtelepathy-logger2 libtxc-dxtn-s2tc0:i386 libunity-2d-private0
  libwebkitgtk-3.0-common libwind0-heimdal:i386 libwind0-heimdal libx11-6
  libx11-6:i386 libx11-data libx11-xcb1 libx11-xcb1:i386 libxcb-dri2-0:i386
  libxcb-dri2-0 libxcb-glx0:i386 libxcb-glx0 libxcb-render0 libxcb-shape0
  libxcb-shm0 libxcb1 libxcb1:i386 libxcursor1 libxcursor1:i386 libxext6
  libxext6:i386 libxfixes3 libxfixes3:i386 libxi6 libxi6:i386 libxinerama1
  libxinerama1:i386 libxp6 libxrandr2 libxrandr2:i386 libxrender1
  libxrender1:i386 libxres1 libxslt1.1 libxslt1.1:i386 libxt6 libxt6:i386
  libxtst6 libxv1 libxvmc1 libxxf86dga1 libxxf86vm1 libxxf86vm1:i386
  linux-firmware linux-libc-dev linux-sound-base lsb-base memtest86+ mountall
  multiarch-support openssl perl perl-base perl-modules policykit-1
  printer-driver-hpcups printer-driver-hpijs pulseaudio
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python python-apport python-apt-common python-dbus
  python-dbus-dev python-httplib2 python-keyring python-minimal python-openssl
  python-problem-report python-pyatspi2 python-software-properties
  python-virtkey rsyslog rtkit samba-common-bin sessioninstaller sudo
  telepathy-logger ttf-droid ttf-umefont ttf-unfonts-core tzdata
  ubuntu-system-service ubuntu-wallpapers-precise unity-2d unity-2d-common
  unity-2d-panel unity-2d-shell unity-2d-spread uno-libs3 unrar ure
  usb-creator-common usb-creator-gtk vim-common vim-tiny vino wine wine1.4
  wine1.4-amd64 wine1.4-common wine1.4-i386:i386 winetricks x11-apps
  xserver-common xul-ext-ubufox
282 to update , 0 to reinstall, 0 to delete and 235 to not update.
Behöver hämta 166 MB arkiv.
Efter denna åtgärd kommer 8 680 kB att frigöras på disken.
Vill du fortsätta [J/n]?


I have many updates, but when I go to update manager, this happens:

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks; this may be caused by held packages.'

---

### Post by chili555 on 2013-10-31
I assume J is for ja or yes. I would proceed (Ja!) and see if we can get this thing fixed.

---

### Post by Filip_Lundberg on 2013-10-31
I proceed yes, then after updating 2%, I received a kernel panic :(

Is it anyway to reinstall the whole Ubuntu 12.04 lts? Or do you have any idea how to solve this?
I am so thankful that you are helping me with this problem :)

I will not be able to test your tips before monday because I will
 Be away for three days and I can't Bring the computer with me :( But I will test your answer on this message  ASAP ;)

---

### Post by chili555 on 2013-10-31
I would reinstall. Just drop the DVD in the tray and select install 12.04 in place of 12.04.

---

### Post by Filip_Lundberg on 2013-11-04
The thing is that i have deleted ubuntu 12.04 lts from the USB that I booted from :/ But does it work to download it again?
Or do I need to burn it on a CD?

---

### Post by Filip_Lundberg on 2013-11-04
New problem :( I don't find the menu on the left side :( [http://tinypic.com/r/15rb0uq/5](http://tinypic.com/r/15rb0uq/5)
This happened after I updated the programs that was available to update. Do you know what this is? I'm sorry for posting so many problems :/

---

### Post by chili555 on 2013-11-04
> **Filip_Lundberg said:**
> New problem :( I don't find the menu on the left side :( [http://tinypic.com/r/15rb0uq/5](http://tinypic.com/r/15rb0uq/5)
This happened after I updated the programs that was available to update. Do you know what this is? I'm sorry for posting so many problems :/No problem at all. That's what we are here for; to solve problems, hopefully. Do the icons not appear after a reboot? Is there any clue here?```
dmesg | grep -i error
```

---

### Post by Filip_Lundberg on 2013-11-04
I don't see the terminal, just spotify. But maybe it's KDE I have now? Is it any short command to open terminal?

---

### Post by chili555 on 2013-11-04
> Is it any short command to open terminal? Ctrl+Alt+t

---

### Post by Filip_Lundberg on 2013-11-04
My alt-key doesn't work. But when I press alt gr + t it doesn't work. I will change to my other keyboard and see if it work with that instead ;)

---

