---
title: "Ubuntu 14.10 wire connection - unmanaged"
date: 2015-04-11
forum: Networking &amp; Wireless
---

### Post by Tigarq on 2015-04-11
Hi all, I'll try to be as brief and clear as possible despite being a newbie in the Ubuntu world. Here's the chronology: 

1) I installed Ubuntu 14.10 64x on my PC replacing a Windows 7 OS, but it couldn't connect to the wire network (even though the cable was well plugged)
2) After calling the net provider they suggested that I install "pppoe confg" from the terminal and so I did but it didn't work either 
3) I deleted the inicial connection from the Network settings and then the status of the wire changed to "unmanaged" 
4) My attempts to create a new connection fail

Apparently there's been a setting I've messed up. I'll be thankful if anyone can suggest a way to create a working wire connection. 

If you have any clarifying questions go ahead, shoot them. 

Regards

---

### Post by Tigarq on 2015-04-13
Is my description poor or is there no solution to the problem?

---

### Post by michi1983 on 2015-04-14
In this suboforum you can see a sticky post on top, please download that script and post the content of the generated .txt file here in your next comment.

Meanwhile please post the output of ```
sudo ifconfig
``` and ```
sudo lshw -C network
```

---

### Post by Tigarq on 2015-04-14
Hi Michi, 

It didn´t work with the code from the sticky note. In fact, the terminal didn´t react at all upon entering the code. 

As for the other codes you suggested, here´s what came out: 

#1 [ATTACH=CONFIG]261295[/ATTACH]

#2 [ATTACH=CONFIG]261296[/ATTACH]

Regards

---

### Post by michi1983 on 2015-04-14
Can't you just copy & paste the output from your terminal in here? In my signature you can find how to format that correctly within code brackets so it is much easier to read.

Please also post the output of ```
cat /etc/network/interfaces
```

---

### Post by Tigarq on 2015-04-15
> **michi1983 said:**
> Can't you just copy & paste the output from your terminal in here? In my signature you can find how to format that correctly within code brackets so it is much easier to read.

Please also post the output of ```
cat /etc/network/interfaces
```


Of course not, don't forget that the reason I'm posting is because I'm not able to connect the pc to the net. 

Here's the output of the command you asked me to type in:

[B]# interfaces (5) file used by ifup(8) and ifdown(8)
auto lo 
inface lo inet loopback

auto dsl-provider 
iface dsl-provider inet ppp
pre-up /bin/ip link set eth0 up # line maintained by pppoecnf
provider dsl-provider 

auto eth0
iface eth0 inet manual [/B]


Do you have idea what's causing the problem?

---

### Post by michi1983 on 2015-04-15
But we need the full info from that script. 
So please download the script from the sticky post, copy it to your ubuntu machine and then execute it. it will generate a .txt file. copy its content again to a usb stick, copy it to one of your computers with internet access and post it here pls.

I have an idea yeah, but that is just guessing unless we get the information from the script.

You are connected to a ISP Modem and set up a ADSL pppoe connection and did something wrong there.

---

### Post by Vladlenin5000 on 2015-04-15
> **michi1983 said:**
> You are connected to a ISP Modem and set up a ADSL pppoe connection and did something wrong there.

My thoughts exactly. And yes, we need the result from the script.

---

### Post by Tigarq on 2015-04-16
If we're speaking about the "lspci -nn -d 14e4:" script, it doesn't work. There's no response upon entering it

---

### Post by michi1983 on 2015-04-16
We are talking about [this]("http://ubuntuforums.org/showthread.php?t=370108") script.
As I said, the sticky post on top of the forum threads in this subforum.

---

### Post by Tigarq on 2015-04-16
Thanks for the tip but it still doesn't work. Here's what I got:

#1 For the update command: 
[ATTACH=CONFIG]261359[/ATTACH]

#2 For the upgrade command: 
[B]~$ sudo apt-get dist-upgradeReading package lists... Done
Building dependency tree      
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


[/B]#3 For the wget command: 
[B]~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2015-04-17 00:44:32--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... failed: Name or service not known.
wget: unable to resolve host address ‘dl.dropbox.com’
[/B]
I know you won't be happy with the way I'm formating it but I'm not that experienced in ubuntu yet to reach the standard. Hopefully we manage to fix this issue and I get the chance to delve deeper.

---

### Post by Vladlenin5000 on 2015-04-16
About formating you can Go Advanced, select # (for CODE) and paste inside any results from commands or whatever.

You need an alternative internet connection to any of those commands.

> If you do not have ethernet connection then follow the directions at this link for running the script without internet: 
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385). 


---

### Post by michi1983 on 2015-04-17
> **Vladlenin5000 said:**
> About formating you can Go Advanced, select # (for CODE) and paste inside any results from commands or whatever.

You need an alternative internet connection to any of those commands.

Or he just could download the script manually to a usb stick, copy it over to the ubuntu machine and execute it, right?

---

### Post by Tigarq on 2015-04-17
I got the txt file on the desktop, made the file executable and then the issue is how to run it. It doesn't run by clicking on it, it opens in the text editor. 
I tried to find the files/preferrences/behaviour tab but I'm not succeeding. The post is from 2012 and it seems as if the settings have changed quite a lot. 
So, now the big issue is how to run the file. The OS is ubuntu 14.10 64x and the laptop is dell inspiron.

---

### Post by michi1983 on 2015-04-17
If you would have read the post carefully you would know that the file itself is no .txt file but a script. A script is just a file (doesn't need to have a file extension) which can be executed.

So please open up a terminal and type:
```
cd /home/$username/Desktop
```
```
sudo nano wireless
```
then you copy paste the content of [this]("https://dl.dropboxusercontent.com/u/57264241/wireless_script") script in your file.
With CTRL+x and "y" and Enter you save the file.
Then do a ```
sudo chmod +x wireless && sudo ./wireless
``` and THEN it will create a .txt file on your Desktop.

---

### Post by Tigarq on 2015-04-17
Alrighty, I got it. Here's all the info from the txt file: 

```


########## wireless info START ##########



Report from: 18 Apr 2015 00:42 EEST +0300


Booted last: 18 Apr 2015 00:38 EEST +0300


Script from: 06 Apr 2015 17:23 UTC +0000



##### release ###########################



Distributor ID:    Ubuntu

Description:    Ubuntu 14.10

Release:    14.10

Codename:    utopic



##### kernel ############################



Linux 3.16.0-23-generic #31-Ubuntu SMP Tue Oct 21 17:56:17 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7



##### desktop ###########################



sed: can't read /home/bissoneli/.dmrc: No such file or directory

Could not be determined.



##### lspci #############################



01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

    Subsystem: ASRock Incorporation Device [1849:8136]

    Kernel driver in use: r8169



##### lsusb #############################



Bus 001 Device 002: ID 0781:5567 SanDisk Corp. Cruzer Blade

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



##### PCMCIA card info #################

#

#####rfkill ###########################

#

##### lsmod ###########################



mxm_wmi                13021  1 nouveau

wmi                    19193  2 mxm_wmi,nouveau



##### interfaces ########################



auto lo

iface lo inetloopback



auto dsl-provider

iface dsl-provider inet ppp

pre-up /bin/ip link set eth0 up # line maintained by pppoeconf

provider dsl-provider


auto eth0

iface eth0 inet manual



##### ifconfig ##########################



Home-url  Link encap:Ethernet  HWaddr <MAC 'Home-url' [IF]> 
 
          inet6 addr: fe80::549e:53ff:fe7b:bc2a/64 Scope:Link

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0
 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth0 
     Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>
  
   UP BROADCAST MULTICAST  MTU:1500  Metric:1

     RX packets:0 errors:0 dropped:0 overruns:0 frame:0

     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

     collisions:0 txqueuelen:1000
 
    RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



##### iwconfig ##########################



eth0      no wireless extensions.


Home-url  no wireless extensions.


lo        no wireless extensions.



##### route #############################



Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface



##### resolv.conf #################

######

##### NetworkManager info############### 



NetworkManager Tool


State: connecting


- Device: Home-url  [Bridge connection 1] --------------------------------------

  Driver:            bridge
  State:             connecting (getting IP configuration)

  Default:           no


  
Capabilities:
    
Carrier Detect:  yes



- Device: eth0 -----------------------------------------------------------------

  Type:              Wired

  Driver:            r8169

  State:             unmanaged

  Default:           no

  HW Address:        <MAC 'eth0' [IF]>



  Capabilities:
    
  Carrier Detect:  yes



  Wired Properties
    
  Carrier:         off



##### NetworkManager.state ##############



[main]

NetworkingEnabled=true

WirelessEnabled=true

WWANEnabled=true

WimaxEnabled=true



##### NetworkManager.conf ###############



[main]

plugins=ifupdown,keyfile,ofono

dns=dnsmasq



[ifupdown]
managed=false



##### NetworkManager profiles ########

##

##### iw reg get ########################



Region: Europe/Bucharest (based on set time zone)


country 00: DFS-UNSET

    (2402 - 2472 @ 40), (6, 20)

    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN

    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN

    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN

    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN

    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN



##### iwlist channels ###################



eth0      no frequency information.


Home-url  no frequency information.


lo        no frequency information.



##### iwlist scan #######################



eth0      Interface doesn't support scanning.


Home-url  Interface doesn't support scanning.


lo        Interface doesn't support scanning.



##### module infos #################

#####

##### module parameters ###########

######

##### /etc/modules ################

######

##### modprobe options ##########

[/etc/modprobe.d/blacklist-ath_pci.conf]

blacklist ath_pci



[/etc/modprobe.d/blacklist.conf]

blacklist evbug

blacklist usbmouse

blacklist usbkbd

blacklist eepro100

blacklist de4x5

blacklist eth1394

blacklist snd_intel8x0m

blacklist snd_aw2

blacklist i2c_i801

blacklist prism54

blacklist bcm43xx

blacklist garmin_gps

blacklist asus_acpi

blacklist snd_pcsp

blacklist pcspkr

blacklist amd76x_edac
blacklist b43

blacklist ssb



[/etc/modprobe.d/blacklist-rare-network.conf]

alias net-pf-3 off

alias net-pf-6 off

alias net-pf-9 off

alias net-pf-11 off

alias net-pf-12 off

alias net-pf-19 off

alias net-pf-21 off

alias net-pf-36 off



[/etc/modprobe.d/iwlwifi.conf]

remove iwlwifi \

(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \

&& /sbin/modprobe -r mac80211



[/etc/modprobe.d/mlx4.conf]

softdep mlx4_core post: mlx4_en



[/etc/modprobe.d/modesetting.conf]

options cirrus modeset=1

options mgag200 modeset=1



##### rc.local ##########################



exit 0



##### pm-utils ###################
#######

# udev rules ########################



[/etc/udev/rules.d/70-persistent-net.rules]

# PCI device 0x10ec:0x8136 (r8169)

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"



##### dmesg ####################

#########

########## wireless info END ############


```



Hopefully this gives you some pointers to solving the issue

---

### Post by Tigarq on 2015-04-18
Is it what you guys needed?

---

### Post by Tigarq on 2015-04-19
I tried to format the data from the file as I´ve seen data formated in the forum. Let me know if I haven´t done it correctly

---

### Post by Tigarq on 2015-04-21
It makes perfect sense, finally when I got the txt file data and posted it as some wanted I didn't get a reply. I would have know what it is if it was 1st of April but right now I'm puzzled

---

### Post by michi1983 on 2015-04-24
So, as expected you set up a pppoE connection. Does your ISP needs that? 
How did you connect your Windows to the internet before you replaced it with Ubuntu?

---

### Post by Tigarq on 2015-04-24
Previously, when using the windows, the connection was pppoe. It has always been like that. It a problem for ubuntu?

---

### Post by michi1983 on 2015-04-25
Nope not at all, if you set it up correctly.
You could give this a try:
[http://ubuntuguide.net/setting-up-pppoe-ubuntu-command](http://ubuntuguide.net/setting-up-pppoe-ubuntu-command)
But I don't know how far your GUI experiments interfer with that.

---

### Post by Tigarq on 2015-04-27
Just did it but it displayed the following message:

```
 Sorry, I scanned 2 interfaces, but the Access Concentrator of your provider did not respond. 
 Please check your network and modem cables. Another reason for the scan failure may also be
 another running pppoe process which controls the modem.
```

---

### Post by michi1983 on 2015-04-27
Okay, so I gotta be sure about that Windows part. 
You are definitely using a dial-in connection on your Windows OS? 
This means you don´t just start up your Windows and are automatically connected to the Internet? 

If you are really using a dial-in connection then please post the output of```
sudo ps -aux | grep pppoe
```

---

### Post by Tigarq on 2015-04-28
When the windows loads the connection is always initiated authomatically. 

But here´s the output:```
 2362 0.0 0.0 13664 2216 pts/8 S+ 01:50 0:00 grep --color=au to [COLOR=#ff0000]pppoe[/COLOR] 
```

---

### Post by michi1983 on 2015-04-29
> **Tigarq said:**
> When the windows loads the connection is always initiated authomatically. 

But here´s the output:```
 2362 0.0 0.0 13664 2216 pts/8 S+ 01:50 0:00 grep --color=au to [COLOR=#ff0000]pppoe[/COLOR] 
```

Okay, I hope I don't sound rude but I am not sure if you really know what a pppoe connection is.
But anway, let's try this.

**1.**
edit your /etc/network/interfaces file to the following

```

auto lo
iface lo inetloopback

auto eth0
iface eth0 inet dhcp

```

**2.**
delete this file
```
sudo rm /etc/ppp/peers/dsl-provider
```

**3.**
restart your network service with
```
sudo /etc/init.d/networking restart
```

**4.**
post the output of 
```
sudo ifconfig
```

---

### Post by Tigarq on 2015-05-01
I was trying with those commands but the terminal doesn't recognize any of them.

---

### Post by praseodym on 2015-05-01
You should be able to run:
```

sudo pppoeconf eth0
```
Add the Login/PW of the ISP and answer all other questions with YES or OK

---

### Post by Tigarq on 2015-05-12
It turned out to be a hardware problem. The PC was bought in 2008 and I couldn't establish a wired connection on Ubuntu 14.10 and 15.04; yet when I tried the 13.04 version it connected automathically to the net.  

Thanks for the advices :)

---

