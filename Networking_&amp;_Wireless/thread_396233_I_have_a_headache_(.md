---
title: "I have a headache :("
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by timcs on 2007-03-29
I have spent a day and a half trying to get the infamous Belkin F5d7050. knowing to look before posting I read nearly all posts which to me either advised to use the ndiswrapper or the native driver from that seamonkey link and there is another link from this forum I had found also (can;t remember it now, its all a blur)

I did the lsusb command and got the 050d:705a id . I then looked on this forum for this and found pretty much the same pointers as when I just searched for the F5D7050.

I am running Ubuntu Edgy BTW before I forget to mention. Strange thing is that when I booted it as a live CD it showed the wireless driver in the GUI network section. However on installing it that disappeared. 

I am confused now as the ndiswrapper claims all is okay when following its instructions but ifconfig does not find it has a device.

This is also true when I compile the driver from the seamonkey site and then try and get it running. I have also looked via google for another guides, found these which I have tried.

The bad thing is, I really do not want to use Windows but the way this is going its looking tempting :frown: 

I am run this all on a low spec pc which is a celeron 633 256mb ram . I can use the net on this at the moment with its built in NIC but I need the wireless working in its place.

The only errors I got when I try the compile on the drivers were warnings. Sorry for the vague info at the moment but the machine is off and I am thinking to re-install however I do not know if this will be in vain.

HELP!!!

---

### Post by teaker1s on 2007-03-29
first make sure you have latest "ndiswrapper-utils" installed (either it will be 1.8 or 1.9)
reboot
```
sudo modprobe ndiswrapper
```
```
sudo ndiswrapper -l
```
```
iwconfig
```

post output

---

### Post by timcs on 2007-03-29
> **teaker1s said:**
> first make sure you have latest "ndiswrapper-utils" installed (either it will be 1.8 or 1.9)
reboot
```
sudo modprobe ndiswrapper
```
```
sudo ndiswrapper -l
```
```
iwconfig
```

post output

Thanks for your reply teaker1s , I can remember that when I did the sudo modprobe ndiswrapper there was not error or output. When I did the sudo ndiswrapper -l it did report that the driver was there. 

However when running iwconfig there was no wireless adapter listed :(. On the other hand I had already driver the native driver and strangely enough instead of it been listed just as rausb0 it showed it as rausb0_irename (or something similar). BTW do I need ro un sudo ndiswrapper -m first before running iwconfig?

Also I did used the 1.8 version of ndiswrapper via downloading it using apt-get.

At the moment because I have tried so many different variations on this, I am re-installing ubuntu as we speak and once done, I will use the ndiswrapper route again and come back with the output for you.

It will take a little while however on this spec PC so don't worry I won't forget :)

---

### Post by timcs on 2007-03-29
As Requested :

> 
sudo ndiswrapper -l
Installed drivers:
rt73            driver installed, hardware present 


and iwconfig :
> 
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr: off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr: off   Fragment thr=2346 B   
          
sit0      no wireless extensions.



Thing is, the wmaster0 and wlan0 were there before I used ndiswrapper. Before hand when I installed ubuntu the first time, these two never appeared :confused: 

Hope this helps

---

### Post by timcs on 2007-03-29
teaker1s

   Sorry to be impatient but I have given up on this device. I currently have a Netgear WG111 V2 ,which by luck I have got for nothing as my Mum bought a DG834g & it came with it free.


however hitting problems with that now. So I look around here and found no one with the same problem. Looks like a new post coming along

---

### Post by teaker1s on 2007-03-29
reference previous post with iwconfig try
```
sudo apt-get install network-manager-gnome
```

now on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key

---

### Post by timcs on 2007-03-30
> **teaker1s said:**
> reference previous post with iwconfig try
```
sudo apt-get install network-manager-gnome
```

now on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key

teaker1s would this program work with any Wireless adapter or does it just work with ndiswrapper drivers?

---

### Post by teaker1s on 2007-03-30
most adapters:KS

---

### Post by Austin_KW on 2007-03-30
If you use the serialmonkey drivers or the ndiswraper you will need to blacklist the driver that is in ubuntu. add 'blacklist rt73usb' to /etc/modprobe.d/blacklist. & reboot.

I use the native driver and it works ok for me,  but there is no reason why the you cant use the windows driver. Just make sure that you have blacklisted the rt73usb or you may have 2 drivers trying to manage the device.

---

### Post by timcs on 2007-03-31
Austin_KW thanks for your input, as I mentioned previously I have stopped looking into this device as I am trying to get the WG111 working at the moment. 

I did do as you suggested however as before I posted this thread I was reading all of the other threads relating to this unit.


Again thanks to both teaker1s and Austin_KW for their help. If I decide to go back to the beklin I will post here

---

### Post by timcs on 2007-03-31
Update!

  I have now got the Belkin to work, I had been struggling with the netgear and so decided to give this another shot.

Because the netgear was already installed as wlan0 the Belkin has been given the device of wlan1. As running sudo ndiswrapper -m puts alias wlan0 ndiswrapper as a file called ndiswrapper in /etc/modprobe.d/ I had to edit this and change the wlan0 to wlan1.

I also added to /etc/modprobe.d/blacklist the line blacklist rt73usb. However since doing all of this and having the netgear unplugged, when I have rebooted the system I get a internal error with HAL which is a bit worrying :confused: .

Also I did install wlassiant (I think thats its name) as gnome-network-manager ignored is presence. I have to say that wlassiant didn't make it work for me in the end.

What I had to do is force the key by typing:
sudo iwconfig wlan1 enc <key>

I am considering to re-install and start again now. However I would like to try Xubuntu because of the spec of this PC and that browsing the web is slower  than in Windows.

I am just wondering if Xubuntu will work as well as ubuntu for the driver support, any ideas anyone?

Anyway lets hope I can do this again without any problems ;)

---

### Post by teaker1s on 2007-03-31
drivers will be the same, only your desktop will change with xubuntu:lolflag:

---

### Post by Austin_KW on 2007-03-31
Why not just install the xubuntu desktop and set it as your default when you configure. I have the ubuntu & kubuntu desktops and I am planning to get xubuntu to try it out.
sudo apt-get install  xubuntu-desktop
Saves a reinstall and you can just run the quicker desktop, plus you an go back if you dont like it...

---

### Post by timcs on 2007-03-31
> **Austin_KW said:**
> Why not just install the xubuntu desktop and set it as your default when you configure. I have the ubuntu & kubuntu desktops and I am planning to get xubuntu to try it out.
sudo apt-get install  xubuntu-desktop
Saves a reinstall and you can just run the quicker desktop, plus you an go back if you dont like it...

Austin_KW do you mean load it on as a separate install? if so the HDD I am using is too small to fit it all on :( .

At the moment I am trying to get Xubuntu to work with that OTHER wireless adapter. Boy am I having fun this week what with ubuntu and finding out new things in this house of mine ;).

> drivers will be the same, only your desktop will change with xubuntu

Well thats a sigh of relief was not sure if Xubuntu had the same kernel thats why i asked. Thanks for that teaker1s , you have to ask these questions otherwise you will never know ;)

---

### Post by teaker1s on 2007-03-31
if you install xubuntu it's just existing ubuntu install with option of xfce or you can have kde or gnome all on one ubuntu install

---

### Post by Austin_KW on 2007-03-31
As teaker1s says you just install the xubuntu-desktop into your existing ubuntu install. You will then have the option of selecting the xfce window manager for your session. You can play around with it and see if you prefer it, if not then you can always select gnome or kde when you next log in. Or different users can uses different window managers ....

---

### Post by timcs on 2007-03-31
sorry now you have confused me, do I install xubuntu off its CD while booting up from it or can I run Ubuntu and then install it from there?

It really doesn't bother me if I install it a fresh. However I was wondering if it is possible to install xubuntu on a usb hdd and then use grub on my internal HDD to boot it (my BIOS doesn't support boot from USB)

This is becoming more of an install query now. I do not want to start a new set of questions on this thread unless it is okay.

---

