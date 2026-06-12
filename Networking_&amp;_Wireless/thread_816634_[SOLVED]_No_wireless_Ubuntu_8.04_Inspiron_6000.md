---
title: "[SOLVED] No wireless Ubuntu 8.04 Inspiron 6000"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by Relysis on 2008-06-02
Hi, I have just installed Ubuntu 8.04 over windows xp.  I'm a first time linux user, and first time forum poster, so please be easy on me.  I read countless threads and websites and still can't get it fixed. That said...

I have a Dell Inspiron 6000 laptop with an intel PRO/wireless 2200BG network card according to lspci.  The installation went very smoothly, and everything otherwise (seems?) to be working normally. When the installation scanned for a wireless network, it could not find one and went on to the next step. I don't know why, my wireless card seems to be supported according to the wiki. The wifi light also does not come on, but it seems this problem does not indicate lack of connection, and is fixable.

Alright, in Network Settings I enabled the wireless connection, entered in the ESSID, and entered in the WPA2 personal network password.  Then I selected Automatic configuration (DHCP).  It is checked and looks to be enabled on the connections menu.

The output I am getting for iwconfig is as follows:
lo: no wireless extensions
eth0: no wireless extensions
eth1: unassociated ESSID:"Galactica"
mode:Managed Frequency=2.412 GHz Access Point: 00:18:F8:ED:B2:DA
Bit Rate:0 kb/s Tx-Power=20 dBm Sensitivity=8/0
Retry limit:7 RTS thr:off Fragment thr:off
Power Management: off
Link Quality:0 signal level:0 noise level:0
Rx invalid rwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx exessive retries:0 Invalid misc:0 Missed beacon:0

Radio is also enabled, but lshw -C network also shows that wireless is unassociated, even after configuring it in the network manager.

I've been working at this for hours and would appreciate any input as to the problem.  It hasn't turned me off to linux by any means, I love everything else about it so far.  As a working connection is mandatory though, I could greatly use some help.  I'll be checking back here frequently in case you need more information, but thanks to all who respond in advance.

~ Rely

---

### Post by clarkyscored on 2008-06-02
This sounds pretty much identicle to my problem with the RT61 card. I'm seriously considering deleting Ubuntu as I'm a first time user of Linux too...

---

### Post by twin798 on 2008-06-03
I am having the same problem on my Winbook. Same wirless card. Radio is on. Machine sees the wireless network and has good signal strenth.  When I click to connect and type in the wep password it will not conntect.

eth1      unassociated  ESSID:""  

          Mode:Managed  Frequency=2.417 GHz  Access Point: 00:15:05:02:29:0B   

          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  

          Retry limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:19  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:18   Missed beacon:0


I am a complete novice and just installed 8.04.  Help would be much appreciated!

---

### Post by Relysis on 2008-06-03
Hopefully somebody can shed some insight on this.  However, thanks twin798 for your report on the same wireless card using WEP security.  I thought at first my router's WPA2 personal security was the problem.  However, you both seem to be using the same card and getting the same problem regardless of security, so maybe this could help an expert who glances over this thread.  Hopefully?

---

### Post by vexingmodstwo on 2008-06-03
Instead of autoDHCP, try to manually configure the connection.

Are you dual booting?  If so, can you find out which IP address your router has assigned to the connection when you were using windows?

Get that IP address and the default gateway IP address and put that into the network manager for the wireless connection.

There seems to be an issue with DHCP so you'll have to force the card and router to talk by manually configuring them.

---

### Post by issih on 2008-06-03
Start from the basics, log into the router and disable all encryption, then see if you can connect...chances are you won't be able to as its not associating with the access point, but general rule of debugging wireless is start by removing possible problems.

If things still won't play after that, then in some way the wireless drivers are not actually working, they are close enough that the system recognises the hardware, but not good enough to actually make things work.

At this point you need to see if there are any other linux native drivers for your wireless chipset (e.g. search on these forums).

If not then your last chance is to look at using ndiswrapper, although that can be a fiddle. let us know how you get on or if you need more advice

---

### Post by Relysis on 2008-06-03
Thank you so much, vexingmodstwo.  You were exactly right about the automatic connection having problems.  After I used the static IP assignment, the connection works perfectly.  For anyone else having this problem, I booted a windows system on the network and entered ipconfig in command prompt, then entered in these given subnet mask and default gateway, as well as a new static IP for my ubuntu computer.  Thanks again.

---

### Post by vexingmodstwo on 2008-06-03
> **Relysis said:**
> Thank you so much, vexingmodstwo.  You were exactly right about the automatic connection having problems.  After I used the static IP assignment, the connection works perfectly.  For anyone else having this problem, I booted a windows system on the network and entered ipconfig in command prompt, then entered in these given subnet mask and default gateway, as well as a new static IP for my ubuntu computer.  Thanks again.

Awesome!

When you get back, make sure to mark this thread solved so people can search for solved issues easier.

---

### Post by sileliasdan on 2008-10-22
So it should work.

My Inspiron 6000 with Ubuntu 8.04 seems to recognize the card but when I try to enable the "Broadcom B43 wireless driver" I am not able to for some reason ... I do not get an error message or any indication of what has gotten wrong when I select the "enabled" check box. Status remain at "Not in use". 

I tried FN+F2 (can't really tell when it's on or off) but nothing changes. 

I've read forum after forum and was under the impression that when upgrading to 8.04 I was going to be up and running.

Thoughts?

Thanks

---

### Post by sileliasdan on 2008-10-22
Up and running thanks to

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

