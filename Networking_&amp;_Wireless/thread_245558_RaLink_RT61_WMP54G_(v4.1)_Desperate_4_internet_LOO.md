---
title: "RaLink RT61 WMP54G (v4.1) Desperate 4 internet? LOOK HERE!"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by dragonlor20 on 2006-08-28
I tried every tutorial, howto, suggestion, etc. that I could find on the internet in the last week. I was ready to quit Ubuntu, in fact, I need to stop that Windows Vista download... But I will repost my post from LinuxQuestions.com on how I finally got my RT61 WMP54Gv4.1 PCI card to work:

Ok, in my excitement I am going to document how I did this, and I don't know for sure exactly which part of it fixed everything, but here it is...

For google: this is how to get your WMP54G wireless wlan card working if it has a RT61 driver which means WMP54Gv4.1

DO NOT USE ndiswrapper as its current version is not made for RT61 drivers...

***Keep in mind that my system is probably pretty muddled with a combination of fixes because after I got desperate I tried every fix I could find, so I will list everything I did in order, so if you are also depserate, then this might get you online too:

1) I started with a completely new installation next to my old installation after the suggestion from a friend to always install linux twice, once for testing, and once for implementing all of the fixes you find without clouding your system with things you don't need.

2) I installed ra0dar... you can find that here: [http://sourceforge.net/projects/ra0dar](http://sourceforge.net/projects/ra0dar) just use the README, it explains everything pretty clearly.

3) In looking for more info, I stumbled across this open-source driver, and I installed that (also thinking that a new install of Ubuntu couldn't be far ahead with so much already installed on a new installation): [http://prdownloads.sourceforge.net/r...ar.gz?download](http://prdownloads.sourceforge.net/r...ar.gz?download)
This driver requires that you have updated headers, the headers from the liveCD worked for me, there is a description of how to use the LiveCD as a repository here:
[http://www.linuxquestions.org/questi...d.php?t=471603](http://www.linuxquestions.org/questi...d.php?t=471603)


Edit: About somewhere in here I started using these codes:
```
sudo iwconfig ra0 mode managed
sudo ifconfig ra0 up
sudo ifconfig essid "ESSID here w/ or w/o quotes"
sudo ifconfig eth0 down
```

4) I used the [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) HOWTO link from Beagle following each step EXCEPT the part about the headers, I think his were actually older versions... ANyways, the CD repository gets you through that HOWTO.

5) Finally I went into the Network configurations as suggested by whereverjustice except that I left mine at ASCII **he changed his to HEX and that worked for him** (System > Administration > Networking) and activated the wireless connection that it recognized there, also adding my ESSID and leaving the the encryption alone.


I hope this helps someone, the repositories are hard to get to when you don't have internet. It isn't the best solution, but it sure feels good if nothing else has worked for you. Try the other solutions first, if they don't work, make a fresh install and try this... I really hope this helps.

Cheers,
Scott

---

### Post by gannic on 2006-08-30
Hello, thanks for the effort, but the links you made dont work and I am struggling. I am new to the command line so a little more detail would be very much appreciated. Any chance?

---

### Post by bionnaki on 2006-08-30
[http://www.ubuntuforums.org/showthread.php?t=241565](http://www.ubuntuforums.org/showthread.php?t=241565)

---

### Post by dragonlor20 on 2006-08-30
> **gannic said:**
> Hello, thanks for the effort, but the links you made dont work and I am struggling. I am new to the command line so a little more detail would be very much appreciated. Any chance?

Ok, well... before you do anything else, the first thing I would do if I could do it all over again is to back up my /etc/network/interfaces as it is when you first install Ubuntu... So to do that, open a terminal (Applications > Accessories > Terminal by install default) and enter this code:

```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```

That file is changed by what I am going to tell you to do next, so IF YOUR SYSTEM STOPS WORKING, ENTER THIS into the command line (it is possible that you may have to go into recovery mode to get to a command line, but once you are there this will save your system):

```
sudo cp /etc/network/interfaces.backup /etc/network/interfaces
```

Ok, so since that is out of the way, the first thing I would do is forget all the links I put up, I think the problem was simpler than that. First see if your system will simply run the card as is... You need to know a little info about your network, otherwise trial and error might take a really long time...

Go to System > Administration > Networking

Look and see if there is a wireless card listed there. If there is then do this:

> Click on your ETHERNET card (if there is one) and then click disable on the right side. NOTE: DONT DO THAT IF THIS IS YOUR ONLY CONNECTION TO THE INTERNET AND IT IS HOW YOU ARE GOING TO FIX YOUR WIRELESS CONNECTION, that is of course unless you are willing to reboot and replace that interfaces file I was talking about...

Click on your wireless card and click on Preferences. Under preferences you will need to know your network name and your WEP (security key of sorts) and also your EncrypType!!! That is where I was having problems, I assumed my network was on a HEX encryption, but really it was ASCII. Apparently that makes a big difference to the computer ;-)

After you set that stuff up then click OK and go back and make sure to click on the wireless card again and click ACTIVATE. This may take a while (I am pretty sure it runs dhclient in the background). Then click OK, that takes a while too...

Last try your internet and hope for the best...

If your card doesn't show up, or if your internet isn't working after you set up the card, then it is time to do a few things:

> A) You are probably going to need to install the driver, which can be quick and painless or a bit complicated depending on you and your system... If you have the same card as I do, then your driver will be the **RT61** driver on the RaLink chip. Otherwise it will be the **rt2500** driver, which is great because you can use **ndiswrapper** to make it work and that is supposed to work very well and the setup is fairly simple.

B)Post on this forum. Include the output from these things (just enter them into the command line) so that all the gurus (which I am not...) know what is going on with your system:
```
iwconfig
ifconfig
iwlist scan
gedit /etc/network/interfaces
```

I hope this gets you started, I'm sorry the links I made didn't work, I should edit that post probably...

---

### Post by gannic on 2006-08-30
Thanks again. Its an RT61 - bought with the hope it would work out of the box with WPA...oh dear.

How do I install the drivers?

---

### Post by dragonlor20 on 2006-08-30
Did the other stuff with the gnome networking setup not work? Haha, I think it's better not to expect anything to work out of the box with Linux, and then if it does you are just pleasantly suprised ;-)

What are you using to connect to the internet now?

Post what the terminal gives you when you type each of these commands:

```
ifconfig
iwconfig
iwlist scan
dhclient
```

THEN, open a terminal and type
```
gedit /etc/network/interfaces
```

and paste the output of that here too, from there we can figure out what to do about your drivers...

Scott

---

### Post by gannic on 2006-08-31
Thanks for any help you can give. A bit of history, I has a wireless ACX111 card running fine, on 64 bit but it wouldnt work with WPA so I switched to 32 bit hoping that may fix it - it didnt. I saw people had had success with this card and WPA so I thought I would try....didnt notice there are four versions. Anyway - Ralink seem to provide drivers for Linux, but my "make all" command fails with no such directory. It seems such a simple thing. With my last card I read pages and pages of complex howtos and then found all I needed to do was add one line to a file.

Anyway, if you can help I would be grateful here is the output you requested. When I activate the card in networking the computer freezes and requires forced shutdown. This is why I think the drivers are up the spout.
I have not disabled ethernet.

clueless@computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr **:**:**:**:**:**
          inet addr:***.***.***.***  Bcast:***.***.***.***  Mask:255.255.255.0
          inet6 addr: ****::***:****:f****:****/** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1274891 (1.2 MiB)  TX bytes:187120 (182.7 KiB)
          Interrupt:233 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:969 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:222441 (217.2 KiB)  TX bytes:222441 (217.2 KiB)

clueless@computer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:0
          RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

clueless@computer:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results
sit0      Interface doesn't support scanning.


INTERFACES

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

---

### Post by amrock on 2006-10-15
I'm the noobiest nooby for linux so please have patience. I have a desktop with a linksys 54g wireless card. I don't know the version, but it must be pretty new because I bought it today. I installed the latest ubuntu on the computer the other day as a dual boot with Windows XP Professional.

I disabled the ethernet card, enabled the wireless card set the SSID to eightstreetcoffee (the network I'm trying to hook up to), selected Plain (ASCII) under the key type and left WEP key blank, because it has been diabled according to [http://192.168.1.1](http://192.168.1.1) which I was able to peek into because they left the default password there from linksys. I also selected DHCP under configuration because that is what it was listed under [http://192.168.1.1](http://192.168.1.1). Clicked ok, then clicked ok again and the internet connection did not work.

I opened up the network settings again and discovered that the Key type went to hexidecimal for some reason.

I found the terminal mentioned above and entered iwconfig and got this information:

lo      no wireless extensions
ra0     RT61 Wireless  ESSID:"eightstreetcoffee"
        Mode:Auto Frequency:2 MHz   Bit Rate=1 Mb/s
        RTS thr:off    Fragment  thr:off
        Link Quality=34/70 Signal level: -121 dBm Noise level: -111 dBm
        Rx invalid nwid:0 Invalid misc:0 Missed beacon:0

eth0    no wireless extensions.
sit0    no wireless extensions.


Then I entered ifconfig and got this:

Lo   Link encap:Local Loopback
     inet addr:127.0.0.1 Mask:255.0.0.0
     inet6 addr: ::1/128 Scope:Host
     UP LOOPBACK RUNNING  MTU:16436  Metric:1
     RX packets:1443 errors:0 dropped:0 overruns:0 frame:0
     TX packets:1443 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes: 108848 (106.2 KiB)  TX bytes:108848 (106.2 KiB)

ra0  Link encap:Ethernet HWaddr 00:18:39:1A:B0:74
     inet6 addr: fe80::218:39ff:fela:b074/64 Scope:Link
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
     RX packets:61807 errors:0 dropped:0 overruns:0 frame:0
     TX packets:3470 errors:1 dropped:1 overruns:0 carrier:0
     collisions:3 txqueuelen:1000
     RX bytes:6104099 (5.8 MiB)  TX bytes:1868 (1.8 KiB)
     Interrupt:185

Then I typed in iwlist scan and got this:

lo   Interface doesn't suppor scanning.

ra0  Scan completed:
     Cell 01 - Address: 00:14:BF:40:99:D7
               Mode:Managed
               ESSID:"eightstreetcoffee"
               Encryption key:off
               Channel:2

eth0  Interface doesn't support scanning.

sut0  Interface doesn't support scanning.

Then I typed in this gedit /etc/network/interfaces and got this:

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Any ideas?

---

### Post by amrock on 2006-11-10
Okay, I determined that I need to download and install ndiswrapper with the linksys RT61 determined by typing lspci -n into the terminal I came up with 1814:0301 and looked up the driver in the wiki list.

The instructions to install ndiswrapper say I need a recent kernal, at least 2.6.6 or 2.4.26, with header files.

I have no idea what they are talking about here, but I have downloaded and installed ubuntu 6.06 LTS The Dapper Drake according to what it says when I go to System->About Ubuntu

The next instructions state: Make sure there is a link to the kernel source from the modules directory. The command ls /lib/modules/'uname -r'/build should at least 'include' directory and '.config' file.

Not sure what they meant here either so I posted it into the terminal and received the message that there is no such file or directory.

After the file for ndiswrapper got extracted the instructions say go to that directory and run

make uninstall
make

login as root and run
make install

I don't see any files named, 'make uninstall' or 'make install'. Do I have to run this through the terminal? If so, how do I make it 'point' to the directory? I can do it is dos, but I don't know how to do it from the terminal. I saved everything into a folder called 'linksys' that was placed in the Places->Home Folder. So the path of the extracted ndiswrapper file is Places->Home Folder->linksys->ndiswrapper-1.28.tar->ndiswrapper-1.28

Okay I figured out how to change to that directory using CD and typing in the folder names. Typing in 'make uninstall', or 'make uninstall make', or 'make install' just came up with the error:
bash: make: command not found

The only file I see in that directory that resembles the commands is one just called 'install'.

I tried just typing install and got the error message 'missing file operand'  (Where can I learn to do this right?)

Okay, I found out through searching the internet that the make function does not work on my computer and I found a suggestion to type this into the terminal to make the 'make' bash function:

sudo apt-get install build-essential

I ended up getting error codes because it couldn't download it. I can't download it because I'm trying to hookup the linksys card and I can't hook up the linksys card without downloading this it appears. I'm frustrated! ](*,) 

I should have compiled enough information for someone to help me. Can anyone out there reply?

---

