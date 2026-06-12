---
title: "Broadcom 43xx Wireless Card problem"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by iamantisocial477 on 2007-10-19
Okay, so I'm having issues with my wireless card. Let me start by stating the info:


I'm running a Dell Inspiron 1501.

I ran the 'lspci' command and got this in regards to my wireless card:
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

I just re-formatted my hard drive today and made two partitions, one with Vista (that I despise) and the primary one being the brand new Ubuntu 7.10 that just came out today.

I had hopes that the Restricted Drivers Manager would be able to solve all my problems easily, but unfortunately I only received the following error message: "The software source for the package bcm43xx-fwcutter is not enabled."

I tried running [this program]("http://ubuntuforums.org/showthread.php?t=405990") (not sure if it has a name) that I found here on the forum also, but unfortunately this didn't solve the problem either. When I first ran it, out of the five options it gives, it recommended to "Install ndiswrapper and Broadcom Windows driver", so I did this. There were no error messages at all. It said it had installed ndiswrapper, the new driver, and I thought everything had gone great.

But still, no wireless. Another point of interest, wireless works fine in Windows, started up in a snap, but not in Ubuntu. My wifi radio light won't turn on at all either, even if I hit Fn&F2, still nothing.

Tried the command 'sudo pccardctl ident' on a whim, but no output at all.

Tried the command 'lshw' and got this:
  *-network
                description: Wireless interface
                product: BCM94311MCG wlan mini-PCI
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth1
                version: 01
                serial: 00:1b:fc:46:4a:f8
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.48+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Tried to follow the directions on [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") of the community documentation, but ran into trouble when I tried to install ndiswrapper through the console. After downloading all three of the files (I know not all are necessary) for ndiswrapper, I tried to install them like this...
"reid@reid-laptop:~$ sudo dpkg -i ndiswrapper-utils-1.9_1.38-lubuntu1_i386.deb"
But got this:
"dpkg: error processing ndiswrapper-utils-1.9_1.38-lubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndiswrapper-utils-1.9_1.38-lubuntu1_i386.deb"

So I figured I'd try looking for ndiswrapper in the synaptic package manager, and finally downloaded and installed the 'common' and 'utils' packages. Continued on with the NDISwrapper how to page and found my chipset. Went on the NDISwrapper site and downloaded a Windows driver that supposedly works.
Followed all instructions and network showed that I could now do wireless, but still it couldn't find any networks at all.

Next tried 'ifconfig' and 'iwconfig' and got the following:

reid@reid-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:B9:6F:00:6E  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe6f:6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:329653 (321.9 KB)  TX bytes:69896 (68.2 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

reid@reid-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


So basically now I'm stuck. I'm a noob to the world of linux as I'm sure you pros can easily tell, so somebody if you can, please try to help me out here!
If there's any addition info you need to get a better insight on my problem, please let me know! Thanks!!!!!

---

### Post by beastly on 2007-10-19
I had a similar problem on my Dell D600, and it installed quite easily on my system. The key part is this:

I had hopes that the Restricted Drivers Manager would be able to solve all my problems easily, but unfortunately I only received the following error message: "The software source for the package bcm43xx-fwcutter is not enabled."

I got that message when I tried to enable the Broadcom driver, and the reason was that I had no internet connection at that point (unsurprisingly). So I plugged into the wired ethernet port and tried again, lo and behold the Restricted Drivers Manager connected to the apt repository and installed fwcutter. You'll probably get the same result going into a terminal and typing "sudo apt-get install bcm43xx-fwcutter" but of course you still need an internet connection here too. Then go back and run Restricted Drivers Manager.

The next thing it will ask is for a suitable driver module. You can normally get this from your Windows partition but I'm not sure about Vista. I couldn't mount my WinXP drive because I had hibernated Windows so I just downloaded one. Here is one for the bcm4311 card that you appear to have: [http://ftp.us.dell.com/network/R115321.EXE](http://ftp.us.dell.com/network/R115321.EXE) - although it's an EXE, it's actually just a self-extracting zip file so you can just run "unzip R115321.EXE" from the terminal and it will reveal the contents. This is the US version of the driver which allows some different frequencies, but there is very little difference in real world use. If you're concerned do a little searching for the Euro version.

You can then choose "local file" in the Restricted Drivers Manager window, and browse to the place where you downloaded the drivers. The file you are after (from memory) is "DRIVER/bcmwl5.sys", don't worry about choosing the wrong file as the system will warn you that it's not a device file.

Once you've done that it should just work, you can connect using the Network Manager icon in the system tray, it should pop up a box asking for a WEP/WPA password if you have one set.

The only issue I have is that the connectivity is really slow with my bcm4306, it's good enough for browsing but file transfers from my Samba shares are really slow. I'm still working on solving that, but it seems the moral of this story is avoid Broadcom junk like the plague if you want stuff that actually works.

Good luck!

---

### Post by jardo on 2007-10-19
friends i experienced problems too with this card...i think restricted driver procedure doesn't work.... i installed ndiswrapper and then windows drivers...
if u type in forum bcm94311mcg u'll find my past threads but noone replied...probably it isn't easy to solve the problem

---

### Post by iamantisocial477 on 2007-10-19
Hey Beastly, thank you you've really helped me a long way but I'm still not quite getting wireless. I can tell that I'm right on the verge, but something's not working quite right.

I was trying to do something with ndiswrapper, and it came up saying I must enable the universe repositories. I had seen that a couple times now but hadn't been able to figure it out. I had also seen something not too long before this about 'software sources'. I put the two together and realized there is a 'software sources' application under System>>Administration>>Software Sources. Went there, and found that there were five things not checked, so I checked them all. Got main, universe, restricted, multiverse, and source code. Applied the changes and it downloaded and installed them all perfectly.

Next I went to the Restricted Drivers Manager and tried to enable the wireless card, but this time it didn't give me the usual error message that I had been seeing forever. It enabled it, and then asked me about the firmware. I tried at first to use the random recommended driver from the 'download from internet' option, but this one didn't work. So then I downloaded and extracted that .exe you recommended and tried it this way instead. After this I closed the box and it said 'new restricted driver enabled' or something like this, and recommended I restart my computer. Did this, but still it's a no go. I am getting some promising results, like my network settings now says "Wireless Connection - Roaming Mode Enabled", which is how I want it, but it's simply not finding any networks at all. 

I read that previous versions of ndiswrapper and fwcutter and all those can mess things up, and I'm pretty sure that I might have that problem. Is there any way I can do a clean sweep of all this and start it out fresh so I have a brand new ndiswrapper and try this all again from there? I'm considering re-formatting my hard drive again (like I did yesterday) and then going straight to the 'software sources',enabling those five options again, extracting that .exe again, and then going to the restricted drivers manager with that .sys file and see if that fixes my problem. Sound like a good idea? Any better ones?

---

### Post by jardo on 2007-10-19
do u want to use bcm43xx drivers , or using ndiswrapper with windows driver(with this one i have your same card wireless will work for sure) ?

---

### Post by iamantisocial477 on 2007-10-19
Well if you know for sure that it works and are up for giving me directions, I'll use the Windows one

---

### Post by jardo on 2007-10-21
sorry for replying u so late.... i have been a bit busy. i used this guide 
[http://ubuntuforums.org/showthread.php?t=297092&highlight=bcm43xx](http://ubuntuforums.org/showthread.php?t=297092&highlight=bcm43xx)

and it worked,if u have any problems ask :)

---

### Post by beastly on 2007-10-23
Sorry for the delay in replying. I'm not sure why your networks aren't being detected, it's possible the ndiswrapper install is causing problems.

Going down the ndiswrapper road is one possibility, but I could never get mine to work consistently with WPA-AES encryption on Feisty, and I'm not prepared to lower my encryption level so I ended  up going back to Windows on my laptop. When Gutsy was released I decided to try again as I knew there had been work on a proper reverse-engineered driver for this chipset, and by using the procedure described above it worked with very little effort. I still haven't solved the poor speed but I haven't really tried.

Nothing wrong with trying ndiswrapper as it might work for you, but certainly on my system I spent a lot of time trying to get it to play with WPA, and the best I managed was it worked now and again, but would usually fail on the next reboot.

Good luck -- the real solution is to avoid the junk that Broadcom peddle in future ;)

---

### Post by iamantisocial477 on 2007-10-24
Thank you both so much for helping me out!
Jardo, that tutorial you posted for me worked beautifully. I had been literally trying to get wireless for WEEKS, and it finally works!! =]]] You guys are both awesome!

---

### Post by jardo on 2007-10-28
that's ok, it's just the spirit of ubuntu ;) have nice time with ubuntu

---

