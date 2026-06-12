---
title: "Dialup user: &quot;connect chatscript failed&quot;"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by nix_user on 2010-01-20
Hello Everyone,   Newbie "nix_user" here. I need your help. Can't connect to the internet using dialup.   Acer Aspire 3680 laptop (512Mb ram, 51Gb hd running xp).   Need your expertise to help me configure pppconfig. I keep getting "connect chatscript failed" after entering:  sudo pon [myisp]  plog returns "connect chatscript failed"   I simply don't know what to do after this? Please send email with step-by-step instructions or let me know what else I need to provide for your expert instruction.    Warm regards,   Jin

---

### Post by lkraemer on 2010-01-20
nix_user,
You should already have your loginname, password, telephone number from
your Dialup ISP.  With that information just follow this guide to get
a PAP or CHAP file built with your information.  Start by trying PAP
and if that doesn't work you can always edit the file and try changing
to CHAP.  (pppconfig is all menu driven, so you won't have any trouble.)
Then I'd suggest using wvdial instead of pon & poff, because wvdial will
search for your modem.  (You will execute wvdial in a Terminal Window
and KEEP THAT WINDOW OPEN DURING YOUR SESSION, then use CNTL C to
terminate the session, and finally close the Terminal Window.)
 
Once you have wvdial dialing in, and pppd making the connection, then
you can install Gnome-PPP and connect from the GUI with no problems.

[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)
Posting #4

Shouldn't take more than 30 minutes total.

lk

---

### Post by Bartender on 2010-01-20
It's highly unlikely that the Acer's modem will work.  Can you type 

```
lspci
```

into a terminal and post the output?  Don't need the whole thing, just the line about a modem chipset if you can identify it.

---

### Post by nix_user on 2010-01-20
To the kindly soul who answered my earlier post. This is kind of long.  Firstly, I still can't configure pppconfig. Unable to &quot;find&quot; wvdial. I tried typing whereis wvdial at the command line. Nothing. Next tried apt-get, lspci with arguments, nothing. Please advise?  DAMN 
```
ubuntu@ubuntu:~$ sudo pon provider  
ubuntu@ubuntu:~$ wvdial  The program 'wvdial' is currently not installed.  
You can install it by typing:  sudo apt-get install wvdial  wvdial: command not found
ubuntu@ubuntu:~$ sudo apt-get install wvdial  
Reading package lists... Done  Building dependency tree        
Reading state information... Done  
The following extra packages will be installed:    
libuniconf4.6 libwvstreams4.6-base libwvstreams4.6-extras  
The following NEW packages will be installed:    
libuniconf4.6 libwvstreams4.6-base libwvstreams4.6-extras wvdial  
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.  
Need to get 1,058kB of archives.  
After this operation, 2,744kB of additional disk space will be used.  
Do you want to continue [Y/n]? y  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main libwvstreams4.6-base 4.6-2    
Could not resolve 'archive.ubuntu.com'  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main libwvstreams4.6-extras 4.6-2    
Could not resolve 'archive.ubuntu.com'  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main libuniconf4.6 4.6-2    
Could not resolve 'archive.ubuntu.com'  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main wvdial 1.60.1+nmu2ubuntu1    
Could not resolve 'archive.ubuntu.com'  Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-base_4.6-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-base_4.6-2_i386.deb)  
Could not resolve 'archive.ubuntu.com'  Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-extras_4.6-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-extras_4.6-2_i386.deb)  Could not resolve 'archive.ubuntu.com'  Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libuniconf4.6_4.6-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libuniconf4.6_4.6-2_i386.deb)  
Could not resolve 'archive.ubuntu.com'  Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.60.1+nmu2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.60.1+nmu2ubuntu1_i386.deb)  
Could not resolve 'archive.ubuntu.com'  
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?  
ubuntu@ubuntu:~$ sudo apt-get install wvdial ---missing  
E: Command line option ---missing is not understood  
ubuntu@ubuntu:~$ plog  Jan 20 07:51:59 ubuntu chat[3996]: send (ATDT9728520780^M)  Jan 20 07:51:59 ubuntu chat[3996]: expect (CONNECT)  
Jan 20 07:51:59 ubuntu chat[3996]: ^M  Jan 20 07:51:59 ubuntu chat[3996]: ATDT9728520780^M^M  Jan 20 07:52:33 ubuntu chat[3996]: NO CARRIER  Jan 20 07:52:33 ubuntu chat[3996]:  -- failed  
Jan 20 07:52:33 ubuntu chat[3996]: Failed (NO CARRIER)  
Jan 20 07:52:33 ubuntu pppd[3994]: Script /usr/sbin/chat -v -f /etc/chatscripts/provider finished (pid 3995), status = 0x5  Jan 20 07:52:33 ubuntu pppd[3994]: Connect script failed  Jan 20 07:52:37 ubuntu pppd[3994]: Exit.  
ubuntu@ubuntu:~$ lspci  
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)  00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)  
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)  
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)  00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)  00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)  00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)  
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)  
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)  
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)  
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)  
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)  
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)  
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)  
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)  
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)  
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)  
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)  0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)  
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller  
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)  ubuntu@ubuntu:~$ lspci -n  
00:00.0 0600: 8086:27a0 (rev 03)  00:02.0 0300: 8086:27a2 (rev 03)  
00:02.1 0380: 8086:27a6 (rev 03)  00:1b.0 0403: 8086:27d8 (rev 02)  
00:1c.0 0604: 8086:27d0 (rev 02)  00:1c.1 0604: 8086:27d2 (rev 02)  
00:1c.2 0604: 8086:27d4 (rev 02)  00:1c.3 0604: 8086:27d6 (rev 02)  
00:1d.0 0c03: 8086:27c8 (rev 02)  00:1d.1 0c03: 8086:27c9 (rev 02)  
00:1d.2 0c03: 8086:27ca (rev 02)  00:1d.3 0c03: 8086:27cb (rev 02)  
00:1d.7 0c03: 8086:27cc (rev 02)  00:1e.0 0604: 8086:2448 (rev e2)  
00:1f.0 0601: 8086:27b9 (rev 02)  00:1f.1 0101: 8086:27df (rev 02)  
00:1f.3 0c05: 8086:27da (rev 02)  02:00.0 0200: 11ab:4352 (rev 14)  
0a:03.0 0280: 14e4:4318 (rev 02)  0a:09.0 0607: 104c:8039  
0a:09.2 0180: 104c:803b  
ubuntu@ubuntu:~$
```   

So close, yet so far. I now have to go to work. Another day without beautiful, elegant ubuntu (online) *heavy sigh.*  Warmest,   Jin 8-|

---

### Post by Bartender on 2010-01-20
Whoah -
Kind of hard to read.  I'm attaching a screenshot.  When you have a mess of text like the output of lspci, here's what you do.

Go ahead and paste the text into your post.  Then highlight the entire chunk of text by holding down the left mouse button and dragging across it, then click on the little cross-hatch icon that I circled in the screenshot.  That'll put all the text into a "Code" box, which makes it much easier to read and it'll take up less room in the post too.  The Code box is handy when you want to post a command also.  You won't see the Code box from your end, you'll only see two little bracket thingies install at either end of the text.  But after you post the message you'll see what I mean.

So, the first part of what you pasted in makes sense.  Synaptic sees that you want certain packages, and it prepares to get them.  Then you get error messages because you're not online.  You're not online because you can't get the #$*!! modem to work.  Welcome to dial-up!

The second part - dang that's hard to read - I'm not seeing a reference to a modem.  Probably because the internal modem doesn't work in Ubuntu and isn't going to work.

According to this [thread]("http://forum.notebookreview.com/showthread.php?t=358224") it's an Agere modem.  Whether yours is an Agere or not I can't say.  I don't know much about the Ageres.  I despise all winmodems.  I use a US Robotics serial external modem, either connected to a serial port or in concert with a Sabrent SBT-USC1M serial-to-USB adapter cable.  Take a look at the Dial-Up Redux thread (below) for some more ideas.

I understand that you're impatient to get online, but I'm here to tell you it may take a few weeks to never, depending on whether you decide to get an external modem and what's available to you.  If it IS an Agere, google "agere ubuntu dial-up" or similar...

---

### Post by K-Bar on 2010-01-20
[SIZE=2]If you are using Ubuntu 9.10 the reason you can't find wvdial is that it isn't there.[/SIZE]
 
[SIZE=2]I had to download several files into my windows partition and copy them over to Ubuntu. [/SIZE]
 
[SIZE=2]Will you be able to do this? [/SIZE]

---

### Post by nix_user on 2010-01-21
Big ups to Bartender and K-Bar, thanks for your timely responses. Have been tinkering offline, each day my base of knowledge increases. Gotta love that. Purchased ($7.00) linux mint Helena CD a week ago hoping to avoid the dialup connection issue. I now see, LMH is 98%(or more)ubuntu. In addition, my virgin post went...untouched. I'm now a loyal ubuntu'er.  Bartender,thanks for the heads up. In the future for readability, I will try the highlight text and # keyboard command. You're right, I do have an Agere modem. Sucks. Do you think a US Robotics would work with my Acer? K-Bar, before I crack open the wallet, I would love to try your workaround to get wvdial. Could you provide a walk through? Sincere thanks to all, nix_user.

---

### Post by K-Bar on 2010-01-21
The first thing you will need is scanModem from [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)  copy it into your home folder then from the terminal```
gunzip -c scanModem.gz > scanModem 
chmod +x scanModem
sudo ./scanModem 
gedit Modem/ModemData.txt

```Wvdial is at the same site.  You will probably also need a modem driver.  ModemData.txt will tell you how to proceed.

It took me about two weeks to get is working but it can be done.

---

### Post by Bartender on 2010-01-21
nixuser -
I guarantee you a US Robotics external serial modem will work.  Unless it's broken!  And the Sabrent serial-to-USB adapter works too.  I've got two of those.

Do you have broadband available to you anywhere?  At the library, a coffee shop, etc.?  If you do, go into System>Administration>Synaptic Package Manager and click on the Reload icon, follow the prompts to let Synaptic update itself.  After Synaptic updates, go to the Search icon and type in 
```
gnome-ppp
```
When Synaptic reports back, click Mark all Upgrades, Apply.  Synaptic will get wvdial as part of the gnome-ppp dependencies.
I used to messa round with manually setting up wvdial, but have found it works as well and less complicated to just set up gnome-ppp and let it handle the configurations.

wvdial isn't in 9.04 either, but as described in Dial-up Redux it's not a deal-breaker.  Get online with pppconfig then Reload the packages via Synaptic then download gnome-ppp.

---

