---
title: "Newbie needs Wireless Help"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by Nikopie on 2008-10-10
I'd like to preface this with I've tried all the things in the Help and Support section with no avail.

Here is my issue:  I cannot connect to my wireless network.  In fact, my wireless card is not even being turned on, however it is in the hardware drivers.

I use a Atheros Network Card.... any help would be much appreciated.

Thanks,

-Nik

---

### Post by jheaton5 on 2008-10-10
Have you looked at the help page at [WifiDocs/WirelessCardsSupport]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")?  There is a link on that page to [WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

The more research you do in trying to resolve your issue the more you learn.  I had to find that out the hard way.  Folks around here like you to be self supporting. :)

---

### Post by Nikopie on 2008-10-11
I've tried that and it didn't work.  I've seriously tried about a dozen things and I can't get it to recognize my Atheros card.  
When I did the Windows Wireless Drivers program and put the netathr.inf file in the program it said it wasn't a valid driver.

I also tried the site you linked in your post, and I couldn't get it to work.  Like I said, I'm a newbie and have only been using Linux/Ubuntu for about 48 hrs so my skill level may be a factor...

-Nik

---

### Post by jheaton5 on 2008-10-11
I do understand where you are.  I've only been using for a little over a month now.  It took me several weeks to find the solution to my card.  I had virtually no help from the forum community.  I did read a lot of threads and tried to understand the logic behind the actions so I could convert the commands to my own situation.  Oh, yes, a search for "SOLVED" helped a lot because these were issues that actually got solved.

I wish I could help you, but I know only enough to be dangerous.  Hopefully a guru will stop by and give you some help.  You need to post the results of several commands in terminal:

```
lshw -C network

```
```
iconfig
```

```
iwconfig
```

```
dmesg | grep -i iwl
```

the results from these commands will help in diagnosing your issue.

Good Luck.

---

### Post by Nikopie on 2008-10-11
Here's what I get when I type in the commands:

lshw -C network:

 *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:15:f2:8e:46:ec
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.103 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes



iconfig
bash: iconfig: command not found
nik@nik-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

nik@nik-desktop:~$ dmesg | grep -i iwl
nik@nik-desktop:~$ 



So basically what I'm gathering is that this is only recognizing my Ethernet and loopbacks.  But it knows I have an Atheros wireless adaptor.
I gotta take a break from this...my heads starting to hurt from reading forums!

---

### Post by gulatiakshay on 2008-10-11
description: Ethernet interface
product: 82566MM Gigabit Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
version: 03
serial: 00:1f:e2:14:a3:83
size: 100MB/s
capacity: 1GB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.3-0 ip=136.159.91.20 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
*-network UNCLAIMED
description: Network controller
product: AR5418 802.11abgn Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list
configuration: latency=0

Help Help..I am fed up...i am trying to get wireless network work from last one week on windows its working fine..

---

### Post by gulatiakshay on 2008-10-11
akshay@akshay:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

akshay@akshay:~$ dmesg | grep -i iwl
akshay@akshay:~$ 

Help neeeded :confused:

And if any one suggest to install some driver please also give us the step by step command

Thanks

Aki

---

### Post by lemmy999 on 2008-10-11
Try this howto ([http://ubuntuforums.org/showthread.php?t=792158&highlight=ar5212](http://ubuntuforums.org/showthread.php?t=792158&highlight=ar5212)) to get the madwifi drivers installed for your card. Copy and paste them into the terminal.

Just used it myself and it works fine!

---

### Post by gulatiakshay on 2008-10-21
akshay@akshay:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

so its not working i am fraking out of this wireless thing

---

### Post by Raymond Petit on 2008-10-21
gulatiakshay,

I can see that you are getting frustrated.  I had a similar problem with an Aerolan card.  Spent many hours reading forums looking for a solution.  Finally I just went to craig'slist and bought a lynksys 54G card.  Once I checked every repository box in Software Sources and updated the list of repositories, the firmware for the driver was automatically downloaded.  Then, I had to download the driver itself which is on the Live CD.  Sometimes when you are new trying to figure out the fix is just not worth the headache.  Ubuntu is wonderful! I hope you can get past this bump in the road to experience how truly great and OS this is.  This is a non-technical solution from anther newbie.  Good luck!

                            Raymond

---

### Post by geezerone on 2008-10-21
Take a look at the troubleshooting guide [here]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"). In particular you will probably have to paste here (as code) the output from commands: lshw, lsmod, lspci, lsusb, iwconfig, ifconfig and iwlist.

Try looking there first and see how you get on. Don't give up (just yet). I know how difficult it can be but bear with it. :)

---

### Post by gulatiakshay on 2008-10-23
Long live ubuntu my wireless is working fine now, thanks evrey one

---

### Post by gulatiakshay on 2008-10-23
I have some doubt, although my wireless working fine now, so when i type iwconfig i get

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"dd-wrt"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:D4:B9:8C   
          Bit Rate:54 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-45 dBm  Noise level=-96 dBm
          Rx invalid nwid:12417  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


my wireless coonection is dd-wrt, what is wifi0 above and whats ath0

---

### Post by gulatiakshay on 2008-10-24
some thing weird is happening, now when i started ubuntu no wireless connection is there i mean didnt get it whats happening, last time i used it it was there in network manager but nnow i cant see it where is it.........ghosh so doubtfull fr me

---

### Post by geezerone on 2008-10-24
Type in a terminal: 

```
sudo /etc/init.d/networking restart
```If this doesn't work please output the dmesg, iwconfig and lshw -C network commands at least.

The ath0 is for the atheros driver. I presume you used the link in previous page to get semi-working?

---

### Post by gulatiakshay on 2008-10-24
MY computer has a dual boot , when i login it shows follwoing

ubuntu generic 2.1
ubuntu generic recovery
ubuntu genetic 1.9
ubuntu generic recovery
visa
vista recovery

now why there r two ubuntus and when i login on 2.1 there is no wireless when i login in 1.9 i can see the wireless

---

