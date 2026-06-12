---
title: "ndiswrapper help"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by se2schul on 2007-04-07
I`m having trouble getting my wireless card to work.

I did a fresh install of ubuntu 6.10 using the alternate CD, then downloaded the XFCE desktop. I just enabled the extra repositories, and installed ndiswrapper using synaptic.

My wireless card is a d-link, DWL-G122 ver A1.
From what I`ve read, I think I need to use ndiswrapper to get this card to work.

Can someone please tell me what I did wrong, or what I need to tweak to get this to work. I`m still relatively new with Linux.

This is what I did:

```
steve@ubuntu:~$ ndiswrapper -l
No drivers installed
steve@ubuntu:~$ cd dlinkdriver/dwlg122_driver_113/
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ ls
PRISMA02.cat  PRISMA02.inf  PRISMA02.sys  setup.exe
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ 
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ 
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ sudo ndiswrapper -i PRISMA02.inf 
Installing prisma02
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ sudo ndiswrapper -l
Installed ndis drivers:
prisma02        driver present 
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ sudo modprobe ndiswrapper 
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-server/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

---

### Post by aysiu on 2007-04-07
I'm not sure if there's a big difference between A and B, but this page seems to indicate you don't need *ndiswrapper*:
[https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_(Rev_B](https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_(Rev_B))

---

### Post by Floppyjoe on 2007-04-07
> **se2schul said:**
> I`m having trouble getting my wireless card to work.

I did a fresh install of ubuntu 6.10 using the alternate CD, then downloaded the XFCE desktop. I just enabled the extra repositories, and installed ndiswrapper using synaptic.

My wireless card is a d-link, DWL-G122 ver A1.
From what I`ve read, I think I need to use ndiswrapper to get this card to work.

Can someone please tell me what I did wrong, or what I need to tweak to get this to work. I`m still relatively new with Linux.

This is what I did:

```
steve@ubuntu:~$ ndiswrapper -l
No drivers installed
steve@ubuntu:~$ cd dlinkdriver/dwlg122_driver_113/
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ ls
PRISMA02.cat  PRISMA02.inf  PRISMA02.sys  setup.exe
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ 
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ 
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ sudo ndiswrapper -i PRISMA02.inf 
Installing prisma02
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ sudo ndiswrapper -l
Installed ndis drivers:
prisma02        driver present 
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ sudo modprobe ndiswrapper 
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-server/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

I have this card and have thus far not been able to get it to work without using ndiswrapper. I think you may need to use a newer version of ndiswrapper. I was getting a similar error when I upgraded the kernel and it broke ndiswrapper. I also blacklisted three modules that follow:
```
sudo gedit /etc/modprobe.d/blacklist
```
Add these to that file:
```
blacklist islsm_usb
blacklist islsm_device
blacklist islsm
```
Here is a link to install the latest version of ndiswrapper.
[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3)
Good luck!

---

### Post by se2schul on 2007-04-08
Well, I have good news and bad news.

The good news is that I got the wireless card to work briefly following FloppyJoe's tips. I'm actually thrilled that my wireless adapter works. I thought that I'd have to buy a different one.  

The bad news is that upon rebooting, when I log into XFCE, I no longer have my taskbar and I'm unable to use the desktop manager. I also no longer have a network connection when plugged directly into my router.

I'm not exactly sure what I did to break it. It's a very new install, and I haven't really installed any software yet.  Basically, I used Synaptic to uninstall my old version of ndiswrapper, and I installed the latest ndiswrapper.  I blacklisted 3 modules as listed in this thread and I configured my wireless card.  I was able to connect to my WAP without WEP, but I couldn't get it to work with WEP. I decided to reboot (yes, it's a Windows reflex) to see if that would help.  Now my XFCE doesn't work. 

So, since I'm still relatively new to linux, I'm not sure how to diagnose/repair this problem. Is it best to try to fix it, or to reinstall and start all over?  Any advice is appreciated.

---

### Post by se2schul on 2007-04-08
It turns out that the crash was my XFCE desktop. I was able to restart it. Now I can get back to figuring out how to get WEP to work. If I need further help, I'll post in this thread.  Thanks.

---

### Post by se2schul on 2007-04-10
Floppyjoe, or anyone who uses the DWL-G122 revA,

Were you able to get WEP to work? 
I can only connect to my AP when I disable WEP. 
Any suggestions appreciated...

Thanks.

---

### Post by stchman on 2007-04-10
> **se2schul said:**
> I`m having trouble getting my wireless card to work.

I did a fresh install of ubuntu 6.10 using the alternate CD, then downloaded the XFCE desktop. I just enabled the extra repositories, and installed ndiswrapper using synaptic.

My wireless card is a d-link, DWL-G122 ver A1.
From what I`ve read, I think I need to use ndiswrapper to get this card to work.

Can someone please tell me what I did wrong, or what I need to tweak to get this to work. I`m still relatively new with Linux.

This is what I did:

```
steve@ubuntu:~$ ndiswrapper -l
No drivers installed
steve@ubuntu:~$ cd dlinkdriver/dwlg122_driver_113/
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ ls
PRISMA02.cat  PRISMA02.inf  PRISMA02.sys  setup.exe
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ 
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ 
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ sudo ndiswrapper -i PRISMA02.inf 
Installing prisma02
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ sudo ndiswrapper -l
Installed ndis drivers:
prisma02        driver present 
steve@ubuntu:~/dlinkdriver/dwlg122_driver_113$ sudo modprobe ndiswrapper 
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-server/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

I do not know what chipset that wireless card is but I have procedures to install Atheros or Broadcom 43xx wireless cards.

Visit my website [http://www.stchman.com](http://www.stchman.com) and I have the procedures listed at the bottom.

---

### Post by thebluejay on 2007-04-12
It seems I not the only one to have the WEP problem. I installed Xubuntu and it recognized my linksys wireless connection at once with no problems so long as I disabled WEP. But when I enable WEP on my main computer, my wireless computer with Xubuntu will not connect to the router.It says it can't find the IP address. I have tried Network Manager and have just installed Wifi-Radar but same results no matter what settings I try in these.

Any ideas? I really don't want to work on unsecured wireless even if WEP is not foolproof - still better than nothing at all!

---

### Post by TheSandman on 2007-04-12
> **thebluejay said:**
> It seems I not the only one to have the WEP problem. I installed Xubuntu and it recognized my linksys wireless connection at once with no problems so long as I disabled WEP. But when I enable WEP on my main computer, my wireless computer with Xubuntu will not connect to the router.It says it can't find the IP address. I have tried Network Manager and have just installed Wifi-Radar but same results no matter what settings I try in these.

Any ideas? I really don't want to work on unsecured wireless even if WEP is not foolproof - still better than nothing at all!


No. You're not the only one.
I've spent two days now trying to figure this out.

Using ndiswrapper is was able to get my BC adapter to work fine.
But no matter what i do i can't get any form of encryption to work.
Neither WEP/WPA work, with or without the manager.

In terminal i was actually able to connect to the router both with WEP and WPA when the essid, key and adress was supplied. But for some reason i couldn't get an IP.
Didn't matter if i tried to use dhcp or reserve an adress in the router and get a static one.

Both my computer and the router claimed i was connected and listed the MAC adress, but no IP adress... huh?

Disabling encryption and wlan works perfectly regardless of method of connecting.

Using fresh install of Fiesty. So... same problem there even if you chose to wipe the new manager.

---

### Post by ittiam on 2007-04-12
I use WPA and it didnt work for me through the network  manager.

But this [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136) worked for me.

---

### Post by thebluejay on 2007-04-12
are you kidding? I looked at that thread and got dizzy!!! No wonder people aren't using Linux! Besides, it seems to apply to WPA whereas I am using WEP. Does it still apply? I think not.

---

### Post by ittiam on 2007-04-12
ofcourse it applies only for wpa, since i found ppl in this thread asking abt wpa..i gave that howto

---

### Post by Floppyjoe on 2007-04-12
> **se2schul said:**
> Floppyjoe, or anyone who uses the DWL-G122 revA,

Were you able to get WEP to work? 
I can only connect to my AP when I disable WEP. 
Any suggestions appreciated...

Thanks.
I have never attempted to use wep with this device but it does work with WPA very well.
WPA encryption is a bit more complicated to set up but it is much more secure than WEP.  

This Url Has details on setting up WPA:
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by thebluejay on 2007-04-12
seems nobody can connect using WEP - bummer!

---

### Post by thebluejay on 2007-04-13
Here is a tip I got from Chili which got my WEP connection going after many days of discouraging failure. Before making any changes to the properties of the connection, first open System>Networking which opens the network administrator. Select the wireless connection  and click on Properties. Then disable the connection by removing the check mark so that the wireless card is no longer enabled. Close and log off. After restart, open the network administrator, select the network and click Properties, check enable this connection again and enter the relevant information:

SSID: the ESSID which is case sensitive
The WEP hex key - also case sensitive
Set the configuration to DHCP

Click OK.  Worked for me. It seems that it is important to first disable the whole thing to get it going again. Good luck to all!

thebluejay

---

### Post by alex_anthony on 2007-04-13
I use MAC filtering. Once you have it set up, it's very secure as long as you don't tell anyone your MAC address and your connection just works like open security for the MAC addresses allowed

---

### Post by TheSandman on 2007-04-16
I use MAC filtering in addition, but it's not a viable alternative that sorts the problem.
It won't change the fact that other networks i move to WILL require encryption and i can't exactly ask them to turn it off for me.
It should just work.

But i digress.

I had some sucess using WPA_supplicant.
I got it to connect to the access point and get an IP release.
But it's very... very slow and it drops the connection after a while. I'll try to read the output and see if there are any issues i can do something about.

Network manager still only manages to connect if there's no encryption at all.
Even with all of the needed settings added to interfaces it just sets the encryption key: off :confused: 

Maybe its a driver issue. I can set the needed parameters for WPA though supplicant (and... it uses them...) but not properly to the driver through iwpriv.
Iwconfig can set the proper settings and reports them back, but of course won't connect to the encrypted networks without supplicant since iwpriv doesn't give me the options to set what it needs.
But applicant apparently can...?
Can't help but thinking maybe it's as simple as the Network-manager being unable to use the driver supplied by ndiswrapper properly.

Getting tired of this. I dug out a 50m cable from the closet :P

Won't solve my issues when i'm not at home though. More and more access points require wlan and don't even offer you a cable.
Hotspots, trains, cafe&#347;, lobbys etc.

WPA_applicant seems to be the only "working" solution for me atm. I guess i'll toy around with it some more and try to get it to work properly.

This, of course, means that if an access point requires me to use WEP i'm still fracked even if i get the WPA at home working better. :(
Maybe i'll go back to GSM modem...

---

### Post by J Snyder on 2007-04-16
Okay, here's what I did to get my Linksys card working- maybe it will help on yours:

FIRST, make sure you have ndiswrapper installed: You said you used the Synaptic manager to get it in place, so it should be okay.

SECOND, make sure you have Linux drivers for your hardware (or, failing that, a driver compatible with WinXP). Unzip the driver into a dedicated folder where you can get to it easily.

THIRD, open terminal and enter the following:

$ cd /home/USER NAME/NAME OF FOLDER CONTAINING YOUR DRIVER

$ sudo ndiswrapper -i (NAME OF DRIVER .INF FILE)

$ sudo ndiswrapper -l

You should see:

Installed ndis drivers:

(DRIVER NAME) driver present, hardware present

Follow up with:

$ sudo depmod ndiswrapper

If there is no error message:

$ sudo modprobe ndiswrapper

Don't ask me what to do if you DO get an error mesage- I had no problems and didn't have to go there.

Hopefully all will be well and you will be able to open a connection through your Network Manager (my PCI card showed up as 'wlan0'; I just enabled the connection and went from there)

---

