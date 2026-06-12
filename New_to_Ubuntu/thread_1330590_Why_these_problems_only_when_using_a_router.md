---
title: "Why these problems only when using a router?"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by resander on 2009-11-18
The problems are:

 1.  downloads stop (no activity) when using Firefox. Pressing Pause 
     and then Resume cause the download to continue. Smaller downloads
     may be ok, but usually not the larger ones (larger than 30MB).
     It is impractical to have to sit and pause and resume a hundred
     times for a large download.

 2.  opening a web page using Firefox, then leaving it and
     immediately going back to it sometimes causes the rotating 
     wait cursor to spin forever. 
     Going to some other page(s) and  going back to the page usually
     works (i.e. I can enter the page), but not always. Sometimes, 
     the only option is to restart the PC. 

Point 1 has been reported by someone as a Firefox bug, but other people have said this is a problem for Opera too on Ubuntu. Synaptic downloads never stop like this, though.

However, problems 1 and 2 are not present when I bypass the router (Belkin) and connect directly to the Virgin broadband ADSL modem.

I am not on Windows anymore, but as far as I can remember I never had these problems when using Firefox on Windows.

I have no knowledge of routers. Is there is anything I can do with router that may hint at what is wrong, or better still solve the problem?

---

### Post by QIII on 2009-11-18
If, by removing the router from the loop, your performance gets back to where you want it, the router itself is suspect.

How old is the router?  It may be that it was working fine long ago when you were using Windows, but is about to give up the ghost now.  (It happens.  Hardware breaks.  Some routers do not dissipate heat well and eventually bake themselves.)

What is the router model?  Have you done any research to find out if others are having similar problems with that model?

Does your router have firmware settings that can be reached by using your web browser?  (Most do.)  Can you tweak the settings?

---

### Post by doas777 on 2009-11-18
I don't trust anything belkin. except maybe a cable or adapter.

got to agree with Q, the problem does appear to be the router. did you mess with any packetfilter or firewall policies?

---

### Post by resander on 2009-11-19
Belkin G router (Model: F5D7230-4, number not on box, but on frontpage of manual)

It came with a CD containing an Easy Install Wizard for Windows and a user manual.
I was still using Windows when I bought it, so used the Easy Install Wizard.
About a year ago I showed Windows the door and installed Ubuntu 8.10. Plugged in printer (HP Deskjet) and scanner (Epson). They just worked. I left the router and Virgin modem cabling the way I had it for Windows and could connect to Internet from the computers in the house directly and via the router. I did not do any router installation/config, since the router appeared to work. Should I have done something?

The router also supports a browser-based alternative to the Easy Install Wizard. Entering 192.168.2.1 into Firefox's address bar brings up a router summary page:

```

Version Info
   Firmware Version	9.01.05
   Boot Version	0.01
   Hardware	01
   Serial No.	BE701158594
	  	
LAN Settings
   LAN/WLAN MAC	00-17-3F-E7-75-AB/
   IP address	192.168.2.1
   Subnet mask	255.255.255.0
   DHCP Server	Enabled


Internet Settings
   WAN MAC address	00-17-42-12-22-18
   Connection Type	Dynamic
   Subnet mask	255.255.252.0
   Wan IP	82.5.114.81
   Default gateway	82.5.112.1
   DNS Address	194.168.4.100
	  	
Features
   NAT	Enabled
   Firewall	Enabled
   SSID	belkin54g
   Security	Disabled

```


These settings are probably left-overs from the Windows Easy Install session. I guess they are defaults that should work with Ubuntu too. Correct?

The browser-based interface allows me to change router parameters, but I do not know which/how to change.

It may well be that the router is going bad, but I think software also plays a part, because large downloads do not stop for the Ubuntu Synaptic/Update Managers, Oracle's and DB2's download managers. My guess is that these programs in some way reset/reinitialise the connection periodically which causes the downloader program and router to be in sync, while Firefox does not. The Pause & Resume workaround on Firefox might cause a resync which lets the download progress for a while. The finger really points to Firefox being the culprit, but as far as I know Firefox has not been able to reproduce the problem. 

What is the best action now?

---

### Post by ukripper on 2009-11-19
your problem more seems like ipv6 issue. Can you disable ipv6.
try this first in firefox:

Disabling ipv6 in Firefox

 [B]  1. Type about:config in your address entry bar (in firefox)
   2. Type "ipv6" in the filter
   3. Change the value of "network.dns.disableIPv6" to true[/B]

if it works fine for you and you see no slowness issues or resume/pause problem then make permanent with below:

 by passing as a kernel parameter as below:

Edit /etc/default/grub file

 ```
   sudo gedit  /etc/default/grub
```

Change

>     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

   >  GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"

Save and exit.

Update the grub from the command line

  ```
sudo update-grub 
```

reboot

Also there has been a bug reported in relation to your router which also states the problem to ipv6. [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218)

---

### Post by 3rdalbum on 2009-11-19
I've seen this problem when there's bad signal strength on mobile broadband - just to confirm, is this wired ADSL or mobile broadband?

Also, a side note: Your router has not been set up with any security. Anyone can get in and use your internet connection, wirelessly. Tell the router to use WPA2 encryption with a passphrase ("Shared Key").

---

### Post by doas777 on 2009-11-19
> **resander said:**
> It may well be that the router is going bad, but I think software also plays a part, because large downloads do not stop for the Ubuntu Synaptic/Update Managers, Oracle's and DB2's download managers. 
that kind of sounds like a DNS problem, (perhaps a symptom of the IPv6 problem). with a large download, you only need check the remote IP once, and once it is discovered, you don;t have to query for it again. the dl just keeps running. with many smaller downloads though, you have to query for each domain that you want, usually on an object by object basis.

---

### Post by resander on 2009-11-20
UKRipper:

Many thanks!

I changed "network.dns.disableIPv6" to true on Firefox on my PC and:

```

 - larger downloads do not stop anymore (problem 1)
    (cannot remember 100MB or bigger downloads ever completing by themselves
     before without spoon feeding Pause and Resume)
 - can go back to a web page (after leaving) without Firefox hanging (problem 2)
     (tried entry/reentry to pages for about 10 minutes without Firefox looping, 
       needs more testing so will keep this under observation)
 - youTube runs to completion every time (forgot to mention this problem)
     (before it always stopped after about a minute)   

```

All PCs connected to the router via cable or wirelessly had these problems.

The ADLS modem connects to the router via the original modem cable. My desktop PC and another PC connect via cable to two of the four ports at the back of the router and two more (laptops) connect via USB wifi G adapters.

Without restarting, as an experiment I put the Firefox setting back to false and found that the problems that had been so persistent before did not show up on my PC and the other computers (which had not issued any Firefox disableIPv6=true yet). It seems changing the Firefox setting to true on my PC changed the state of the router to the better which lasted even when the setting of disableIPv6 was changed back to false. Why?

I then logged out and turned off power of PC, ADSL modem and router. After restart Internet did not work at all. The PCs got 'web address unknown' for everything even google.com and yahoo.com and the laptop got 'no signal' condition. I tried several times with disableIPv6 to false and true. I left the setting to true before turning off.

This morning I connected my PC directly to the modem and Internet worked fine. Then, after shut down and complete power-off I reconnected to the router and Internet worked! Don't understand.

Any ideas?

---

### Post by ukripper on 2009-11-20
> **resander said:**
> UKRipper:

After restart Internet did not work at all. The PCs got 'web address unknown' for everything even google.com and yahoo.com and the laptop got 'no signal' condition. I tried several times with disableIPv6 to false and true. I left the setting to true before turning off.


When you restarted router, did you check whether your green "**internet**/**WLAN**" light on your router was on, or was it turned orange/no-light indicating that your ISP having some problem at that instance?

---

### Post by resander on 2009-11-22
UKRipper:

I think the internet/WLAN light was on, but am not 100% sure.

However, problems 1,2,and 3 returned and yet I had not made any changes to the router. Tried toggling disableIPv6 back and forth, powered-on/off and so on to no avail. 

I then made my network secure by setting a password for the router as suggested by 3rdalbum. This cleared the problems. Don't understand why. Ideas?

It has now been up and working for about a day, so at this moment the recipe seems to be:

 - set disableIPv6 to true in Firefox
 - ensure the network is secure by setting a router password


I refrained from setting disableIPv6 via the grub loader as error prone self might have brought the system down.
  
Would really like to understand this a bit better....

---

