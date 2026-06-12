---
title: "Netgear WG511 v3"
date: 2005-10-15
forum: Networking &amp; Wireless
---

### Post by breakthestate on 2005-10-15
*** I have edited this post to incorporate some of gt24's comments *** 
 
I'm not sure how these instructions will work with other versions of Ubuntu. I used all of the following in Breezy 5.10.
 
1. Unload the prism54 module.
 
Before getting ndiswrapper, unload the prism54 module from your system. Ubuntu detects the WG511v3 on boot and loads the prism54 module. Although this card does have a Prism chipset (you can find out by typing "lspci" in the terminal), v3 is not currently supported by the prism54 project:
[FONT=Courier New]```
sudo modprobe -r prism54
```[/FONT]
 
Also, add a line containing the following to the /etc/hotplug/blacklist file using your favorite text editor (must have root privelages). 
 
```
prism54
```
 
That will prevent your system from loading the prism54 module at boot. (Thanks bimberi)
 
2. Install ndiswrapper.
 
[FONT=Courier New]```
sudo apt-get update
sudo apt-get install ndiswrapper-utils
```
[/FONT]
3. Download the driver. 
 
cd into a directory you prefer and type in terminal and:
[FONT=Courier New]```
wget http://www.smc.com/files/AV%5CDR_2802wV.2_WHQL.zip
```[/FONT]
Please let me know if the above step doesn't work. If you get a 404 error, it may just be that the file no longer exists at that location.
Unzip the file:
[FONT=Courier New]```
unzip AV\DR_2802wV.2_WHQL.zip
``` [/FONT]
 
[FONT=Courier New]4. Load the driver.[/FONT]
cd into the "Driver" directory and cd into the "WinXP" directory. In this directory, you should see a file named "2802W.inf". In the terminal, type:
[FONT=Courier New]```
sudo ndiswrapper -i 2802W.inf
```[/FONT]
Check to see if the last step went okay with:
[FONT=Courier New]```
sudo ndiswrapper -l
```[/FONT]
You should see:
```
[FONT=Courier New]Installed ndis drivers:
 2802w   driver present, hardware present[/FONT]
```
 
*** gt24 told me (see below) that the drivers on the CD worked just fine and that the link I've posted above no longer works. If anyone finds a working link for v3, let me know and I'll update this. ***
 
5. Load the ndiswrapper module.
 
[FONT=Courier New]```
sudo modprobe ndiswrapper
```[/FONT]
Make sure everything went okay. Type in the terminal:
[FONT=Courier New]```
dmesg
```[/FONT]
Hopefully, you will see the following at the end of this output:
```
[FONT=Courier New][4298557.630000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
 [4298557.760000] ndiswrapper: driver 2802w (SMC,04/29/2004, 3.0.11.1) loaded
 [4298557.771000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
 [4298557.771000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
 [4298557.772000] ndiswrapper: using irq 10
 [4298561.706000] wlan0: ndiswrapper ethernet device xx:xx:xx:xx:xx:xx using driver 2802w, configuration file 1260:3890.5.conf
 [4298561.706000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP[/FONT]
```
Your hardware should now be good to go. Please note that the x's above will be replaced by your NIC's MAC address. 
 
6. Connect to the internet.
 
Use the Network Adminstration Tool in Breezy to connect to your router. This should be the easiest part. If you run into trouble with this last step, please check other posts and the Wiki before posting here.
 
7. Make things easy.
If you are successful and don't want to have to modprobe ndiswrapper after every boot, simply do the following:
[FONT=Courier New]```
sudo ndiswrapper -m
```[/FONT]
Also, please let me know of any errors in this post. I'm not sure if what I pasted as far as the dmesg output goes, will be what you get, especially the #'s in the brackets, but you should see the text not bracketed. (If this is wrong, someone please let me know)

---

### Post by breakthestate on 2005-10-30
i got this as a private message from good soul, gt24:

ou can use the driver CD that came with your Netgear card if you want. Then, instead of downloading the zip file, you just browse on your CD to the Driver/WINXP directory.
 
 The zip file you linked to didn't work for me. Additionally, going to Netgear's site and downloading the driver was sorta a slap in the face, since they have an exe installer to install the driver (so you cannot see the inf file).
 
 Most of the commands don't work as typed because they need sudo in front of them. Here is what worked for me. (this list may be incomplete)
 
 * no change *
 
 sudo apt-get update
 sudo apt-get install ndiswrapper-utils
 
 * skip *
 
 * skip *
 
 netgear -i 2802W.inf <---- this command is wrong, corrected version below
 sudo ndiswrapper -i 2802W.inf <----- the inf filename will change depending on what driver version you are using
 
 * skip to last line *
 
 sudo ndiswrapper -m
 
 One last thing... for valuable information on how to make ndiswrapper work, there is a link for more information.
 [https://wiki.ubuntu.com/HowToSetUpNd...ndiswrapper%29]("https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29")
 
 Anyways, thought to fire off a PM instead of posting in that thread because I didn't want to "steal your thunder" as the quote goes. However, if you want to quote me in your thread, feel free to.
 
 Anyways, thanks for your article, it got me on the right track.  [IMG]images/smilies/icon_smile.gif[/IMG]

---

### Post by gt24 on 2005-10-30
An additional bit...  the inf that I used was netwg511.inf from the Netgear CD that came with my wifi card, which is version 1 and made in China (the version, and what country it comes from, are needed to troubleshoot issues with this card).  Also, if you want the card to work, make sure it is inserted before you boot your laptop, or else you need to execute the modprobe command before using the card.

To make this easier, you can make an entry in your Gnome menu.  You can do this using a program called smeg (which you need to initially run from terminal ironically enough... you might want to add that program to the menu while you are at it.  :)).  If it doesn't start, you might need to apt-get it.  Also, if you need more help, just say so.

As mentioned above, thanks for the article!

---

### Post by dwessell on 2006-02-19
Hey guys,,, I've been using this guide (Thanks for it).. 

I've followed the steps above.. Using dmesg I have the appropriate information.. nidswrapper -l shows that they are loaded...

But when I go into the Network settings (Using Kubuntu) and attempt to enable the device it fails.. It enables for a second, and then goes back to disabled..

I have the following in /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
wireless-mode managed
wireless-essid xxxxx
wireless-key xxxxxx

As well.. It doesn't load the card up at boot.. I did the  sudo ndiswrapper -m but didn't seem to maky a difference.. Any help would be appreciated.



Thanks
David

---

### Post by dwessell on 2006-02-19
Addendum:

At boot, the light on the NIC flashes for a few seconds.. Then quits.. After that I cannot activate the card from inside the Netwrk area in System settings.


Thanks
David

---

### Post by breakthestate on 2006-02-21
david,
 
just to try and see if we can get to the bottom of this, are you in a position where you could disable the encryption on your wireless router for a few minutes and try things without encryption?  If so, try it and let me know what happens.

---

### Post by dwessell on 2006-02-21
Hey breakthestate... Sorry I hadn't gotten a chance to come back and update this. I've had an ASM project due in, and it's been a time killer..

I did exactly what you suggested last night, and it works fine without the encryption... Perhaps there's an issue with the ndiswrapper and communicating with the Win drivers when using encryption... I didn't see anything while reading the Wiki, but I might have missed it...

Have you run into this before?

Thanks
David


[QUOTE=breakthestate]david,
 
just to try and see if we can get to the bottom of this, are you in a position where you could disable the encryption on your wireless router for a few minutes and try things without encryption?  If so, try it and let me know what happens.[/QUOTE]

---

### Post by reidi on 2006-02-22
Bravo! breakthestate's well-documented HOWTO just plain worked on an old Gateway Solo, with a Netgear WG511 card which showed up as a prism54.

Thanks for taking the time to make it easier for all.

---

### Post by breakthestate on 2006-02-26
reidi- glad I could help

dwessell - I actually haven't used encryption with this card, but according to this thread: [http://www.ubuntuforums.org/showthread.php?t=28731&highlight=wg511+v3](http://www.ubuntuforums.org/showthread.php?t=28731&highlight=wg511+v3)
at least someone has gotten it to work with WEP.  Depending on what type of encryption you want to use, you should definitely post there if you wish to pursue this, because I'm afraid I won't be able to help.  I am however interested to see if you can get it working with encryption.  if so, maybe post a super mini-howto on this thread if you think it might help out others.  i hope your project went well.

peace,

- jeff

---

### Post by tafsen on 2006-03-17
I got the message: 2802w  driver pressent

But I don't get the hardware pressent.  How do I fix this?

---

### Post by kix on 2006-04-04
This thread has made my day.  I did not know there was a V3 WG511, now I do, and it works.

Many thanks!

Edited to mention, this works perfectly in Breezy but not so on Dapper.

---

### Post by Bhante Santi on 2006-04-10
[QUOTE=breakthestate]
 
Also, add a line containing the following to the /etc/hotplug/blacklist file using your favorite text editor (must have root privelages). 
 
```
prism54
```
 
That will prevent your system from loading the prism54 module at boot. (Thanks bimberi)
 [/QUOTE]

Hi, I'm new to Ubuntu. I'm having trouble with the step above - when I do /etc/hotplug/blacklist it says : permission denied. Does this mean I do not have 'root priveleges', how can that be when I'm the only user on the laptop?

Thanks, Bhante Santi.

---

### Post by Bhante Santi on 2006-04-10
[QUOTE=Bhante Santi]Hi, I'm new to Ubuntu. I'm having trouble with the step above - when I do /etc/hotplug/blacklist it says : permission denied. Does this mean I do not have 'root priveleges', how can that be when I'm the only user on the laptop?

Thanks, Bhante Santi.[/QUOTE]

I was previously trying to open it with terminal, then I found it and tried opening it in gedit but it is read only. How can I add the line prism54 to it?

Bhante Santi.

---

### Post by breakthestate on 2006-04-15
hey sorry it took me so long to get back to you.  to open files needing root permission, just type "sudo gedit <filename>" in the terminal where <filename> is the file you want to open.

---

### Post by pkk2a on 2006-05-20
[QUOTE=breakthestate]*** I have edited this post to incorporate some of gt24's comments *** 
 
I'm not sure how these instructions will work with other versions of Ubuntu. I used all of the following in Breezy 5.10.
 
1. Unload the prism54 module.
 
Before getting ndiswrapper, unload the prism54 module from your system. Ubuntu detects the WG511v3 on boot and loads the prism54 module. Although this card does have a Prism chipset (you can find out by typing "lspci" in the terminal), v3 is not currently supported by the prism54 project:
[FONT=Courier New]```
sudo modprobe -r prism54
```[/FONT]
 
Also, add a line containing the following to the /etc/hotplug/blacklist file using your favorite text editor (must have root privelages). 
 
```
prism54
```
 
That will prevent your system from loading the prism54 module at boot. (Thanks bimberi)
 
2. Install ndiswrapper.
 
[FONT=Courier New]```
sudo apt-get update
sudo apt-get install ndiswrapper-utils
```
[/FONT]
3. Download the driver. 
 
cd into a directory you prefer and type in terminal and:
[FONT=Courier New]```
wget http://www.smc.com/files/AV%5CDR_2802wV.2_WHQL.zip
```[/FONT]
Please let me know if the above step doesn't work. If you get a 404 error, it may just be that the file no longer exists at that location.
Unzip the file:
[FONT=Courier New]```
unzip AV\DR_2802wV.2_WHQL.zip
``` [/FONT]
 
[FONT=Courier New]4. Load the driver.[/FONT]
cd into the "Driver" directory and cd into the "WinXP" directory. In this directory, you should see a file named "2802W.inf". In the terminal, type:
[FONT=Courier New]```
sudo ndiswrapper -i 2802W.inf
```[/FONT]
Check to see if the last step went okay with:
[FONT=Courier New]```
sudo ndiswrapper -l
```[/FONT]
You should see:
```
[FONT=Courier New]Installed ndis drivers:
 2802w   driver present, hardware present[/FONT]
```
 
*** gt24 told me (see below) that the drivers on the CD worked just fine and that the link I've posted above no longer works. If anyone finds a working link for v3, let me know and I'll update this. ***
 
5. Load the ndiswrapper module.
 
[FONT=Courier New]```
sudo modprobe ndiswrapper
```[/FONT]
Make sure everything went okay. Type in the terminal:
[FONT=Courier New]```
dmesg
```[/FONT]
Hopefully, you will see the following at the end of this output:
```
[FONT=Courier New][4298557.630000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
 [4298557.760000] ndiswrapper: driver 2802w (SMC,04/29/2004, 3.0.11.1) loaded
 [4298557.771000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
 [4298557.771000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
 [4298557.772000] ndiswrapper: using irq 10
 [4298561.706000] wlan0: ndiswrapper ethernet device xx:xx:xx:xx:xx:xx using driver 2802w, configuration file 1260:3890.5.conf
 [4298561.706000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP[/FONT]
```
Your hardware should now be good to go. Please note that the x's above will be replaced by your NIC's MAC address. 
 
6. Connect to the internet.
 
Use the Network Adminstration Tool in Breezy to connect to your router. This should be the easiest part. If you run into trouble with this last step, please check other posts and the Wiki before posting here.
 
7. Make things easy.
If you are successful and don't want to have to modprobe ndiswrapper after every boot, simply do the following:
[FONT=Courier New]```
sudo ndiswrapper -m
```[/FONT]
Also, please let me know of any errors in this post. I'm not sure if what I pasted as far as the dmesg output goes, will be what you get, especially the #'s in the brackets, but you should see the text not bracketed. (If this is wrong, someone please let me know)[/QUOTE]
I've ubuntu installed and trying to install netgear wg511 v3 and followed all above mentioned steps so now my netgear card shows flashing green light but yellow light ?

---

### Post by breakthestate on 2006-07-24
If you have a Toshiba Satellite Pro A10, please see the think below.  It is mainly the same although it tells you about a few extra modules you need to  add to your /etc/modprobe.d./blacklist file:

[http://www.ubuntuforums.org/showthread.php?t=156228](http://www.ubuntuforums.org/showthread.php?t=156228)

I am back on Dapper and back to using this card again (Stole this laptop from my roommate) so hopefully i can answer any questions if they come up again.  

Does anyone know if the fact that this workaround is necessary would be considered a bug?

---

### Post by Retnuh on 2006-09-04
> **tafsen said:**
> I got the message: 2802w  driver pressent

But I don't get the hardware pressent.  How do I fix this?


This happend to me too.
I have the Netgear WG511v2, not the v3.
So far I have tried every single inf file out there as a driver that I have found,but nothing is recognized when I do: ndiswrapper -l.

The one that is the 2808w shows up and is recognized but it has no answer for the hardware. Doenst even say Hardware.
Anyone?

---

### Post by nevurthls on 2007-04-27
Great post and howto!

I'm running the scripts one by one, it seems feisty fawn doesn't think it's a prism anymore, so that saves a bit of configuring. 

Anyways it did not end up working for me as I got the following error when doing the modprobe ndiswrapper:

```
[ 1160.644208] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[ 1160.671631] ndiswrapper (check_nt_hdr:153): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 1160.671646] ndiswrapper (load_sys_files:216): couldn't prepare driver 'wg311v3'
[ 1160.672781] ndiswrapper (load_wrap_driver:118): couldn't load driver wg311v3; check system log for messages from 'loadndisdriver'
[ 1160.675602] usbcore: registered new interface driver ndiswrapper
```

What can I do to solve this problem?

thanks,

maarten

---

### Post by omarcarr on 2007-05-15
Hello,

I've just insralled my first Linux (Ubunto v 7); does anyone knows how to have ubuntu recongnize my netgear wg511 v2 wireless card?.

network manager does not see any wireless connection, obviously because there appears not to be a card, but I gather there is a way to have ubuntu recognized it. In addition i also have the setup files from Netgear to install the app, but is for windows; i understand if i am able to copy both the .sys and .inf files to unbutu and have the network app find it and install it, it may work. Problem is i can't find the .sys and .inf files in the netgear  setup files...
anyone can help?....

omarcarr

---

### Post by omarcarr on 2007-05-18
Hello everyone;
I resently installed Ubuntu Feisty v 7, which i find it extremely satisfying to say the least; here is my problem so far.
I have 2 wireless cards one is a sony brand which runs at 10mb and it is supported by ubuntu out of the box, however, I would perfer to us my Netgear WG511 v2 (made in china) which runs at a higher rate).

The problem is i've ran into several issues with this card all of which you'll probably know by now, I tried several methods of installing the wg511v2 xp driver and installing it via the ndiswrapper; ndiswrapper finds the xp driver and it seems that it installs it but it doesn't shows it in the window and when i try to install it again it tells me it is already installed; which it this point i insert my netgear card and try my luck to connect to the internet. Nothing... so i've come to you folks and see any one of you know how to fix this problem...

help..

much appricated
Omar

---

### Post by omarcarr on 2007-05-18
Hello everyone;
I resently installed Ubuntu Feisty v 7, which i find it extremely satisfying to say the least; here is my problem so far.
I have 2 wireless cards one is a sony brand which runs at 10mb and it is supported by ubuntu out of the box, however, I would perfer to us my Netgear WG511 v2 (made in china) which runs at a higher rate).

The problem is i've ran into several issues with this card all of which you'll probably know by now, I tried several methods of installing the wg511v2 xp driver and installing it via the ndiswrapper; ndiswrapper finds the xp driver and it seems that it installs it but it doesn't shows it in the window and when i try to install it again it tells me it is already installed; which it this point i insert my netgear card and try my luck to connect to the internet. Nothing... so i've come to you folks and see any one of you know how to fix this problem...

help..

much appricated
Omar

---

### Post by gerbel01 on 2007-07-18
hey guys.  I have a WG511 v3 and installed the drivers, everything checks out, and it will actually connect to networks without a password.  however, when i try to connect to my own router, it will give me a window saying "error connecting to wireless network.  the requested wireless network requires security capabilities unsupported by your hardware".  

if i try to manually configure, the connect icon wont blink green on either side, however the actual cards lights shows solid green and blinking yellow

---

### Post by stringt on 2007-08-30
I ran into an interesting issue setting up the WG511v2 (China version).  I was able to piece together bits and pieces of this post and managed to get ndiswrapper to work using the XP drivers from the CD.  

I have my Compaq laptop set up to dual boot between XP home and Ubuntu, with Ubuntu being the default.  

If I boot into Ubuntu inside my little office here, I'm able to connect to my Netgear wirelsess router with no problem.  I can also connect when I boot into XP.  

The weird part comes when I move outside this room.  

If I boot into Ubuntu while still inside the room, get a network connection, then move outside the room I remain connected.  If I try to boot into linux outside this room, it freezes when it gets to the point where it's "configuring network devices."

No problems anywhere in the house when booting into XP using the Netgear management software from the installation CD.  

Any ideas?  I would have thought signal strength would be more of a hardware function once software turned it on.

---

### Post by bliffle on 2007-09-10
I've got the WG511 installed in a Thinkpad 570 which has no RJ45 for conventional ethernet connection. I built the new 570 HDD as a dual boot with the XP system, and all that works fine. The WG511 works fine under XP.

But how do I do an 'apt-get' as instructed when I have no internet connection? I've pulled together all the code pieces mentioned and collected them in a "WG511" folder on the 570, but how do I install from there?

---

### Post by jdmoylan on 2007-12-05
[QUOTE=breakthestate;414837]*** I have edited this post to incorporate some of gt24's comments *** 
 
I'm not sure how these instructions will work with other versions of Ubuntu. I used all of the following in Breezy 5.10.
 
1. Unload the prism54 module.
 
Before getting ndiswrapper, unload the prism54 module from your system. Ubuntu detects the WG511v3 on boot and loads the prism54 module. Although this card does have a Prism chipset (you can find out by typing "lspci" in the terminal), v3 is not currently supported by the prism54 project:
[FONT=Courier New]```
sudo modprobe -r prism54
```[/FONT]
 
Also, add a line containing the following to the /etc/hotplug/blacklist file using your favorite text editor (must have root privelages). 
 
```
prism54
```t 
 
That will prevent your system from loading the prism54 module at boot. (Thanks bimberi)
 
2. Install ndiswrapper.
 
[FONT=Courier New]```
sudo apt-get update
sudo apt-get install ndiswrapper-utils
```
[/FONT]
3. Download the driver. 
 
cd into a directory you prefer and type in terminal and:
[FONT=Courier New]```
wget http://www.smc.com/files/AV%5CDR_2802wV.2_WHQL.zip
```[/FONT]
Please let me know if the above step doesn't work. If you get a 404 error, it may just be that the file no longer exists at that location.
Unzip the file:
[FONT=Courier New]```
unzip AV\DR_2802wV.2_WHQL.zip
``` [/FONT]
 
[FONT=Courier New]4. Load the driver.[/FONT]
cd into the "Driver" directory and cd into the "WinXP" directory. In this directory, you should see a file named "2802W.inf". In the terminal, type:
[FONT=Courier New]```
sudo ndiswrapper -i 2802W.inf
```[/FONT]
Check to see if the last step went okay with:
[FONT=Courier New]```
sudo ndiswrapper -l
```[/FONT]
You should see:
```
[FONT=Courier New]Installed ndis drivers:
 2802w   driver present, hardware present[/FONT]
```
 
*** gt24 told me (see below) that the drivers on the CD worked just fine and that the link I've posted above no longer works. If anyone finds a working link for v3, let me know and I'll update this. ***
 
5. Load the ndiswrapper module.
 
[FONT=Courier New]```
sudo modprobe ndiswrapper
```[/FONT]
Make sure everything went okay. Type in the terminal:
[FONT=Courier New]```
dmesg
```[/FONT]
Hopefully, you will see the following at the end of this output:
```
[FONT=Courier New][4298557.630000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
 [4298557.760000] ndiswrapper: driver 2802w (SMC,04/29/2004, 3.0.11.1) loaded
 [4298557.771000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
 [4298557.771000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
 [4298557.772000] ndiswrapper: using irq 10
 [4298561.706000] wlan0: ndiswrapper ethernet device xx:xx:xx:xx:xx:xx using driver 2802w, configuration file 1260:3890.5.conf
 [4298561.706000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP[/FONT]
```
Your hardware should now be good to go. Please note that the x's above will be replaced by your NIC's MAC address. 
 
6. Connect to the internet.
 
Use the Network Adminstration Tool in Breezy to connect to your router. This should be the easiest part. If you run into trouble with this last step, please check other posts and the Wiki before posting here.
 
7. Make things easy.
If you are successful and don't want to have to modprobe ndiswrapper after every boot, simply do the following:
[FONT=Courier New]```
sudo ndiswrapper -m
```[/FONT]
Also, please let me know of any errors in this post. I'm not sure if what I pasted as far as the dmesg output goes, will be what you get, especially the #'s in the brackets, but you should see the text not bracketed. (If this is wrong, someone please let me know)[/QUOTE

-------------------------------------------------------------------------------------------------------
your directions seemed fine, except that i installed:

  ndiswrapper-common and
  ndiswrapper-utils-1.9

however, i followed all your steps and all seemed to go will until i got to the command:

  ndiswrapper -l

this gave me:

   2802w : driver installed

but no mention of hardware present

dmesg gives:

   [ 3082.068000] pccard: card ejected from slot 0
   [ 3087.168000] pccard: CardBus card inserted into slot 0

when i first remove and then insert the netgear wg511v2 (made in china) card.

this card has worked previously under fedora core 7, using some other
driver, though someone else installed the driver for me and i don't remember
the details.

in short, the card is there, but apparently not recognized.

any thoughts?

---

