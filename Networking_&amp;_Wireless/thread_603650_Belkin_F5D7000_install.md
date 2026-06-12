---
title: "Belkin F5D7000 install???"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by mmccaule on 2007-11-05
I've just installed 7.10 and I'm new to Linux. I setup a dual boot system with XP pro sp2. All went well and all works so far except the belkin fd57000. I looked around this forum and found directions to install it. I acquired the driver, then  tried to install it, the system couldn't find "ndiswrapper".  So I looked around some more and found directions to install ndiswrapper and did that. I'm not sure ndiswrapper installed correctly because now when I try to install the f5d7000 driver I get a message about not being able to locate the  ndiswrapper utils.  At this point I'm kind of lost and need help. The f5d7000 is an early version and works fine in XP. The more I read about installing stuff in Linux, it sure reminds me of the DOS days, to bad I've forgotten most of that.

---

### Post by mmccaule on 2007-11-09
Ok, after more reading here and other forums I got the F5D7000 installed and working in 7.10 using NDISWRAPPER. I used the Dell bcmwl5a.inf and bcmwl5.sys from the R74092us.EXE. It will be interesting if this still works after a shutdown and boot.

---

### Post by mmccaule on 2007-11-25
Ok, I've learned a lot since my last post. After trying various "bcwml5" drivers I've discovered that I need to enter my WPA key manually at each login. Doing this gets me online most of the time. The next issue that I had was connecting to Windows shares on my home network. This seems to be hit and miss at times. After installing and configuring samba, Windows can see my Ubuntu shares. Also, browsing the network doesn't always locate the shares but entering the IP address usually works. Another thing that I have found with my dual boot system that after booting in one OS then booting in the other I need to reboot my router to be able to see shares again consistently. It took a while to figure this out because it's not always necessary which caused me much pain. One other point, there's a lot of good info on this forum but a lot of it assumes that you have a unix/linux background so I've found that googling for issues will sometimes return more understandable solutions from other forums.

---

### Post by smellycorpse on 2007-11-25
do you think you could guide me through installing my Belkin F5D8001?

nvm i should do more research...

---

### Post by mmccaule on 2007-11-26
The F5D8001 is based on a different chip set than the F5D7000 but here's what I did. First I installed ndiswrapper with the Synaptic Package manager. Next I created a folder in my home directory and placed the ***driver***.inf and the ***driver***.sys files into it. I found the files by searching the Internet and had to try several verisons before got ones that worked. Next I started a terminal session then went to the folder that I created for the drivers and entered the following:

sudo ndiswrapper -i ***driver***.inf
sudo ndiswrapper -m
sudo ndiswrapper -mi
sudo ndiswrapper -ma
sudo modprobe ndiswrapper

Then I closed the terminal session and rebooted. Now each time after I boot I click on the network icon on the top right and choose manual configuration then go to the properties of the wireless connection and enter my WPA key phrase and ok. I'm not sure that this is the correct way to go but it's how I got my card working and it took about a week to come up with this. the following link may be of more help for your card. Good luck.

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by smellycorpse on 2007-11-26
i'm not sure how to install ndiswrapper using synaptic, can you explain how to do that?

---

### Post by mmccaule on 2007-11-27
To install ndiswrapper using the synaptic package manager you will need to have the Ubuntu CD handy. First click on **system**, then click on **administration**, then click on **synaptic package manager**. At some point it will ask for your password. Once you have the synaptic package manager open go down the list and check **ndiswrapper-common** and **ndiswrapper-utils-1.9** and **mark them for installation**. You may also want to install **ndisgtk**. With the packages marked go to the top and click **apply** and it will ask for the CD then install them. FYI, yesterday I deleted the ubuntu  partitions and did a fresh install since I had tried many things and didn't know how to undo some of the needless stuff I did. I did this while the PC was on a wired network and did all the updates and setup the home network before I setup the wireless. One interesting thing that I found was that the wireless configuration was set to roaming after I finished and now it will connect automatically at boot. Since my PC is a desktop I never thought to set the wireless to roaming. I guess that's what I get for thinking. Anyhow, with the fresh install I think I've finally got this right and that was after 6 complete installs.

---

### Post by smellycorpse on 2007-11-27
well i think i'm gonna switch back to xp for a while cause i don't think my wireless card is gonna work... i'll check back and see if people make any progress.

---

### Post by sudo_t43p on 2007-12-01
I have also BIG problems getting this card (ver. 1) installed on my computer:

The problems are many. For instance my system freeze when I modprobe ndiswrapper* so I cannot use it. Nor can I get it working with the restricted drivers.

[* I have 2gb ram installed, If I remove 1gb ndiswrapper works fine]

uname -a:
Linux desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux



```

eth2      Link encap:Ethernet  HWaddr 00:30:XX:XX:XX:XX  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fe9d:8eaf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:415 (415.0 b)  TX bytes:5242800 (4.9 MB)
          Interrupt:11 Base address:0xc000 


chrisse@desktop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11b/g  ESSID:"pingu"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.457 GHz  Access Point: 00:13:XX:XX:XX:XX   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=51/100  Signal level=-70 dBm  Noise level=-58 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chrisse@desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.100 icmp_seq=10 Destination Host Unreachable
From 192.168.1.100 icmp_seq=11 Destination Host Unreachable
From 192.168.1.100 icmp_seq=12 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
13 packets transmitted, 0 received, +3 errors, 100% packet loss, time 12001ms, pipe 3


```

Does anyone else have problems with getting it to work with WEP encryption? I think I'll try to install 32bit ver of Ubuntu and see if I can get ndiswrapper working.

---

