---
title: "ipw3945 instead of iwl3945 on 2.6.24"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by Starks on 2008-03-12
Will Ubuntu and/or the kernel allow me to use the older driver?

---

### Post by Starks on 2008-03-12
bump

---

### Post by karan.batra on 2008-03-15
I am having slow boot up problems too with iwl3945. Hardy pauses for around 1 minute before boot-up. Thus I also wish to go back to 3945. Did you have any luck in your case on kernel 2.6.24-12.22?

---

### Post by Raghavendra Prabhu on 2008-03-16
No luck yet

rrprabhu@rrprabhu-laptop:~$ apt-cache policy linux-image-2.6.24-12-generic
linux-image-2.6.24-12-generic:
  Installed: 2.6.24-12.22
  Candidate: 2.6.24-12.22
  Version table:
 *** 2.6.24-12.22 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
        100 /var/lib/dpkg/status


lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by dei on 2008-04-25
for me wireless networking with iwl3945 isn't working at all while it worked perfectly with ipw3945...
(connecting and getting an dhcp-address is no problem, but simply hasn't any real tcp-connection)
isn't there any way to load that module on the 2.6.24?

---

### Post by bkly-dog on 2008-04-26
I just upgraded to 8.04 from 7.10. Wireless stopped working completely. It can't connect to my wireless network at all, even after I try manual configuration and entry of the passphrase. 

It seems that it may be the new iwl3945 driver. If anyone finds a way to migrate back to the ipw3945 driver on 8.04 and 2.6.24, I'd love to know how. 

This problem is really unfortunate, as it may force me back to Vista.

Thanks!

---

### Post by SGC_Sculler on 2008-04-26
I've also been having some issues since the upgrade, though I didn't know the driver had changed. I've found that when run with normal user permissions 'iwlist scan' produces no results, but when run as 'sudo iwlist scan' my AP is seen as normal. I've found a similar thing with the config panel - when opened normally it doesn't list any access points, and if the ESSID and key are entered manually it will refuse to connect. However, if opened immediately after running 'sudo iwlist scan' my access point is seen; i can select it and it will most times connect if you click OK fast enough. It will then proceed to work til shutdown.
God knows what's causing this, but this seems to make things mostly work...

---

### Post by bkly-dog on 2008-04-26
The behavior differs a bit for me. It basically never connects, whether it asks me for the passphrase or gets it from the keyring. 

The taskbar tool always lists my home SSID, but the others seem to not be listed as reliably. But, as I say, it won't connect after it tries either automatically or when I click on "Connect to other wireless network..." and then enter the settings.

Added to the other issues I've been having with lots of configuration settings going away with this upgrade to 8.04 from 7.10, I may have to go back to Vista. By the way, wireless networking worked fine in 7.04 once I got it set up, it got a little flakier with 7.10 (had to enter password manually more often), and now hasn't worked at all with 8.04.

Thanks for any help.

Here's the output of the iwlist scan. 

 Cell 01 - Address: 00:16:B6:6A:0D:0F
                    ESSID:"myhomenetname"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/100  Signal level=-86 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000001a6ec35876

---

### Post by Rafaelgarcia on 2008-04-26
This indeed is a serious problem. 

I have a VAIO vgn-TXN15P, with Gutsy installed and working well. 

Luckily I decided to try out Heron on a separate partition, because after installing the installed Hardy Heron installation has no wireless internet access. 

Before logging-in, I got some error information relating to the intel card, by pressing "ctrl-alt-F8" and seeing the following:

iwl1945 Microcode SWerror detected
restarting 0x82000008
iwl3945: error reply type )x00000005
cmd REPLY_SCAN_CMD Cox80 seq 0x4447 ser 0x0000004B
iwl3945 cant stop Rx DMA

(I apologize for any typos as I had to jot it down quickly on paper by hand)

I don't know if the problem is due to some configuration file in my home directory, because I just mounted my old home and didn't format or attempt any special migration. 

Given the similar problems reported by other users above, however, before attempting to update my main partition to Hardy Heron, I would like to know there is a solution, as I need my laptop wireless for work.

Rafael

---

### Post by Rafaelgarcia on 2008-04-27
Apparently some people report a solution using backports, see 
[http://ubuntuforums.org/showthread.php?t=765647&page=3&highlight=iwl3945](http://ubuntuforums.org/showthread.php?t=765647&page=3&highlight=iwl3945)
I will have to wait until I get a cable connection before I can try it out. Rafael

---

### Post by tanis.mezzelfo on 2008-04-27
I confirm. I had the some problem on my DELL LATITUDE D520. I use the old 2.6.22-14 linux kernel and now my wireless connection works fine!

I hope that the problem on the new 2.6.24-16 kernel'll resolved early :-(

Bye, bye 

Tanis

---

### Post by clevergeek on 2008-04-29
I can confirm this issue on my Dell Inspiron e1705.  Wireless worked great with the ipw3945 on gutsy and feisty, and didn't work after the hardy upgrade.

Installing the backports package as suggested on this forum fixed things up for me.  Wireless is working great, and my LED works (although it's either on or off, there is no longer flickering with activity).

```
sudo apt-get install linux-backports-modules-hardy-generic
```

If this doesn't work for you, you might also make sure you don't  have your killswitch on, and that the driver modules are actually loading on your system.

I'd also like to say it's a little silly to post "vista threats" on a forum where you're asking for help.  If you have trouble using the search function on this forum (which got me back up and running within a few minutes), you'll probably enjoy a commercial MS product more anyway?  At the very least if you can't get things working for youself, wait a little while before upgrading.  ;)

---

### Post by Yako on 2008-05-11
I got ipw3945 to work on 2.6.24.

1. Download ipw3945 microcode ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net)) and copy it into /lib/firmware/(`uname -r`)/
2. Download ipw3945 regulatory daemon ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net)) and copy it into /sbin/
3. Download ipw3945 source ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net))
4. Apply patch from [http://james.colannino.org/downloads.html](http://james.colannino.org/downloads.html)
5. Make & make install
6. Add these lines to /etc/modprobe.d/ipw3945 (Creating the file if it doesn’t exist)

install ipw3945 /sbin/modprobe –ignore-install ipw3945 ; sleep 0.5 ; /sbin/ipw3945d –quiet
remove ipw3945 /sbin/ipw3945d –kill ; /sbin/modprobe -r –ignore-remove ipw3945

7. modprobe ipw3945
8. blacklist iwl3945 (put ipw3945 into /etc/modprobe.d/blacklist)

And voila! ipw3945 on linux 2.6.24!

---

### Post by bkly-dog on 2008-05-11
Thanks for the additional possibilities for fixing this problem. Earlier, I tried the backports installation line given above, and it completely solved the problem for me.

---

### Post by deltaprime on 2008-05-17
so here is my problem... :(

the iwconfig shows up differnet stuff then it used to. I need my 3945 working for work (wifi 

cracking features and surveillance ....) ubuntu 7 worked fine but this is getting me mad! 

The internet works perfectly fine, is even a bit faster on the new kernel. so i can google 

but i cant use m card for what i really need it. Any ideas?? 


Please help me out THX\\


delta prime


btw here is what i get

[COLOR=Red]lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"belkin54g"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: mac   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality=79/100  Signal level=-59 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.[/COLOR]



Ideas?

---

### Post by bjtuna on 2008-05-20
Yako's directions did work for me to get ipw3945 running on 2.6.24 but I've yet to determine if this is more reliable than the other driver.  Also, Yako's directions need some cleanup and clarification; here's what I had to do in order to get them to work.

1. Download ipw3945 microcode ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net)) and copy it into /lib/firmware/(`uname -r`)/
2. Download ipw3945 regulatory daemon ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net)) and copy it into /sbin/
3. Download ipw3945 source ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net))
4. Apply patch from [http://james.colannino.org/downloads.html](http://james.colannino.org/downloads.html)  (unpack ipw3945 source, copy the patch file into that directory, cd to that directory, and run ```
patch -p0 < {patchfile}
```. Note that James Colannino's directions call for you to run patch -p1, this will NOT work.

5. Run 'make SHELL=/bin/bash' and then 'sudo make SHELL=/bin/bash install'
6. Add these lines to /etc/modprobe.d/ipw3945 (Creating the file if it doesn’t exist)

install ipw3945 /sbin/modprobe –ignore-install ipw3945 ; sleep 0.5 ; /sbin/ipw3945d –quiet
remove ipw3945 /sbin/ipw3945d –kill ; /sbin/modprobe -r –ignore-remove ipw3945

7. modprobe ipw3945
8. blacklist iwl3945 (put ipw3945 into /etc/modprobe.d/blacklist)

> **Yako said:**
> I got ipw3945 to work on 2.6.24.

1. Download ipw3945 microcode ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net)) and copy it into /lib/firmware/(`uname -r`)/
2. Download ipw3945 regulatory daemon ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net)) and copy it into /sbin/
3. Download ipw3945 source ([http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net))
4. Apply patch from [http://james.colannino.org/downloads.html](http://james.colannino.org/downloads.html)
5. Make & make install
6. Add these lines to /etc/modprobe.d/ipw3945 (Creating the file if it doesn’t exist)

install ipw3945 /sbin/modprobe –ignore-install ipw3945 ; sleep 0.5 ; /sbin/ipw3945d –quiet
remove ipw3945 /sbin/ipw3945d –kill ; /sbin/modprobe -r –ignore-remove ipw3945

7. modprobe ipw3945
8. blacklist iwl3945 (put ipw3945 into /etc/modprobe.d/blacklist)

And voila! ipw3945 on linux 2.6.24!

---

### Post by bjtuna on 2008-05-20
Update: even with this backported driver, my wireless is still VERY unreliable.

---

### Post by deltaprime on 2008-05-22
this is really annoying the crap out of me! i tried for about 4 hours today and i could not figure out how to set my kernel back to the previous settings so i can see what i saw before in the previous release.
some one help me out i am [COLOR=Red]_**s**_[/COLOR]t[COLOR=DarkRed]*_**uckkkkk**_*[/COLOR]

---

### Post by bkly-dog on 2008-05-22
Deltaprime, I feel your pain. I ran the command shown in post #12 above, and it fixed the thing completely. Try it! And, good luck.

I am looking forward to the time when GNU/Linux/Ubuntu requires MUCH less system administration! It's an obstacle even for fairly savvy users.

---

### Post by bjtuna on 2008-05-23
Guys, the reason we're all having problems, it appears, is the default GNOME Network Manager.  You need to install WICD.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by deltaprime on 2008-05-23
> **bjtuna said:**
> Guys, the reason we're all having problems, it appears, is the default GNOME Network Manager. You need to install WICD.
 
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
 
> **bkly-dog said:**
> Deltaprime, I feel your pain. I ran the command shown in post #12 above, and it fixed the thing completely. Try it! And, good luck.
 
I am looking forward to the time when GNU/Linux/Ubuntu requires MUCH less system administration! It's an obstacle even for fairly savvy users.
 
 
hmm thats interesting, ill check it out when i get home. 
ive been using iwlwifi for a long itme but the new ubuntu just screwed it all up 
hope i canfix it in the next few days.
 
update me on any new stuff you guys can find thanks a lot
 
delta

---

