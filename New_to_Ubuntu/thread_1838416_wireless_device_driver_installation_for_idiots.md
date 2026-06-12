---
title: "wireless device driver installation for idiots"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by ex windows on 2011-09-03
When my old laptop crashed I decided it was a good time to try Ubuntu so I downloaded it, wiped the disk and installed the new software. It will now not connect to the wireless network as it has no device driver so I downloaded it from Dell. That's where someone like me comes unstuck as I am used to double clicking and letting the wizard do its work. Everything I look at for advice goes right over my head so is there anyone out there who could give me an idiot's step-by-step guide to getting this driver loaded before I have to admit defeat and go back to Windows. Arggh :cry:
Not sure which version I have of Ubunto as I can't even find that info (am I useless or what!!) but I think it's the latest as I only downloaded it a month ago.

---

### Post by sanderd17 on 2011-09-03
can you give us the output of 

```

lspci

```

This will list all pci devices (including your network card). Please post the output between CODE tags (click on the #-icon).

---

### Post by ex windows on 2011-09-03
like I said - instructions for idiot's so I'm sorry but how do I do this??

---

### Post by josephmills on 2011-09-03
Hi there and welcome to the Ubuntu Fourm 

there are ways of checking and looking at wireless 

fist as noted above you look at your pci card aka wireless card with the command so open your terminal (ctrl+alt+t)
then type in ```
lspci -nn
``` and then paste the output here.   the -nn part puts in names and also numbers 
  

once you figure out your card you then start to install the mod aka drivers 

once we know the card we can look at other things 

in a nut shell wireless drivers are mods+firmware= wireless drivers 

you just need the right mods and right firmware loaded and that pertains to the card that you have.

---

### Post by sanderd17 on 2011-09-03
> **ex windows said:**
> like I said - instructions for idiot's so I'm sorry but how do I do this??

start the terminal (CTRL+ALT+T, or search it in a menu), type in the command (or copy-paste it, this is probably safer) and hit ENTER.

---

### Post by ex windows on 2011-09-03
Right, thanks, but not able to paste the output as I'm talking to you guys on my new laptop but if it's any help the wireless lan controller says [14e4:4318] (rev 02)
You can all see now what you are up against with me so when you are ready to give up please say so!!!!

---

### Post by ex windows on 2011-09-03
OK, with a bit of buggering around this is it:

colin@colin-ME051:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
colin@colin-ME051:~$ ^C
colin@colin-ME051:~$

---

### Post by josephmills on 2011-09-03
> **ex windows said:**
> Right, thanks, but not able to paste the output as I'm talking to you guys on my new laptop but if it's any help the wireless lan controller says [14e4:4318] (rev 02)
You can all see now what you are up against with me so when you are ready to give up please say so!!!!


Sweet I love new laptops. so you are rockin the the braodcom card. 
you need the b43fwcutters mods and its firmware. Here I wrote a little diddy about that a while ago 




 


**installing b43fwcutter with-out the internet ** 

download this file  [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)

Then transfer it over to your Ubuntu box 

Now in  your Ubuntu Box [computer]  please make your way to your **Home folder ** 

Once you are at your home folder right click on your home folder and ** make a new folder and call it Wireless**
[IMG]http://img862.imageshack.us/img862/8053/screenshotba.png[/IMG]





Now that you have made a new folder called wireless in your home directory. It is time to **move the downloaded file into the new folder called wireless** 
[IMG]http://img850.imageshack.us/img850/4563/screenshot1kl.png[/IMG]






Next we need to move that folder to the firmware directory to do this open your terminal and type in 
```
sudo cp -r ~/Wireless/* /lib/firmware/
```[IMG]http://img101.imageshack.us/img101/5329/screenshot5ei.png[/IMG]






Now lets double check to make sure the download made it to the firmware directory. Too do this type this into the terminal 
```
ls /lib/firmware
```Do you see it there ? Good if not it did not moved. Go back to the last step and try again. But if you do see it lets move on to the next step
[IMG]http://img151.imageshack.us/img151/5092/screenshot3ln.png[/IMG]





Ok so now that the download is in the firmware dir we are going to have to go there. To go there open your terminal and type in. 
```
cd /lib/firmware 
```Now that you have moved lets double check to make sure this next code tells us where we are in the computer file dir. This next code stands for "print working directory" ```
pwd
``` are you at /lib/firmware if so good if not go back one step 
[IMG]http://img143.imageshack.us/img143/3945/screenshot4zv.png[/IMG]





Now that we are in the firmware directory. We have to extract the download to do this type in 
```
sudo -s
``` then enter your password then 
```
tar -xzf b43-all-fw.tar_.gz
```then 
```
exit
```Now it is time to reboot 
```
sudo reboot 
```

---

### Post by ex windows on 2011-09-03
put in sudo etc then hit return. It asked for my sudo password which I assumed was ubuntu as that's the only one I've got and it replied 
cp: target 'lib/firmware' is not a directory
colin@colin-ME051:~$

---

### Post by sanderd17 on 2011-09-03
> **ex windows said:**
> put in sudo etc then hit return. It asked for my sudo password which I assumed was ubuntu as that's the only one I've got and it replied 
cp: target 'lib/firmware' is not a directory
colin@colin-ME051:~$

You probably forgot a / before lib. Is that true?

---

### Post by ex windows on 2011-09-03
Yep that was it, but I've tried 3 times since and it's not appearing. Will keep trying - don't have to extract it first do I?

---

### Post by josephmills on 2011-09-03
> **sanderd17 said:**
> You probably forgot a / before lib. Is that true?


you can copy and paste into the terminal also with 
shift+ctrl+c <--------------Copy 
shift+ctrl+v <--------------Paste 
shift+ctrl+t <-------------- New Tab 
You can see the hole list of keyboard shortcuts by going to terminal and seleting EDIt--->keyboard shortcuts    :)

---

### Post by ex windows on 2011-09-03
You guys are awesome!!!
Showing all available wireless networks now. Can't get it to connect yet - do I need to tap in the BSSID (whatever that is) and the MAC address? IPv4 settings are Automatic (DHCP) and IPv6 settings says Ignore.
Any more help would be appreciated

---

### Post by ex windows on 2011-09-03
I've managed to connect to a BT hotspot here in the UK but as I don't subscribe to BT it's no use to me. Obviously the problem is with the connection to my Belkin router. I obviously know my  internet security and SSID and the Mode is Infrastructure but what do I put in BSSID and Device MAC and Cloned MAC addresses. MTU is Automatic. What about IPv4 and IP6 settings?
So near yet so far!!

---

### Post by josephmills on 2011-09-03
you want to see bssid all of them that are around you open terminal 
```
sudo apt-get install aircrack-ng 
``` then ```
sudo su 
``` then ```
airmon-ng start wlan0 
``` then ```
airodump-ng mon0 
```  do you see the bssid numbers the channels that they are on the essid and all that jazz :popcorn:
after you have your info press ctrl+c then to drop out of root with the command ```
exit
```

---

### Post by Kreacher on 2011-09-03
Wireless device driver install. First move:

Look on the menu for the Network manager applet and right click on it (usually has an up and down arrow icon). Right click and note if the three "Enable" are checked. If not, check them. 

If the wireless one is not there, look on the menu for System>Administration>Hardware Drivers and click. Wait a few to see if your card is detected. If yes, then install. 

Otherwise, you need to follow the previous messages or search other areas for help. :)

Enjoy!

---

