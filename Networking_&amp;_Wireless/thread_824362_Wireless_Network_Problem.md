---
title: "Wireless Network Problem"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by tsk84eva on 2008-06-10
I've recently set up a Vista/Ubuntu Hardy Heron dual boot on my laptop.  Wireless works fine with Vista but not on Ubuntu.  I can see my home's wireless network in Ubuntu but can't connect to it.  I'm able to enter my ISP password and IP address info in the Network section, but it still won't let me online.  Any ideas on how to connect? Thanks

---

### Post by cdtech on 2008-06-10
what do you get with iwconfig? What hardware are you using; lshw -C network?

---

### Post by tsk84eva on 2008-06-10
> **cdtech said:**
> what do you get with iwconfig? What hardware are you using; lshw -C network?

iwconfig: 

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





lshw -C network

WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:65:da:92
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:5f:a9:2b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

---

### Post by tsk84eva on 2008-06-10
sorry for the double post:
i've just tried the ndiswrapper/ndisgtk method and have the vista drivers for my network card, but even this didnt seem to help

---

### Post by pytheas22 on 2008-06-11
You shouldn't need ndiswrapper for your card; it has good native Linux drivers.  So blacklist ndiswrapper for the time being:
```

sudo -s
echo 'blacklist ndiswrapper' >> /etc/modprobe.d/blacklist
exit
```

Then reboot.  Next, if feasible, can you try turning off WPA temporarily on your router and see if you can connect to the network unsecured?  At least then we'll narrow the problem down.

If you still can't connect even without encryption, post the output of:
```

iwlist wlan0 scan
```

and I'll give you some commands to run in the terminal to see if you can get connected that way.

Also some quick googling revealed this [thread]("http://ubuntuforums.org/showthread.php?t=305662"); it's old so I'm not sure if the stuff they mention there is still necessary, but you could try (it deals with the same kind of wireless card that you have).

---

### Post by tsk84eva on 2008-06-11
ok thanks pytheas.
i've already uninstalled ubuntu, but give me a little while to set it back up and i'll try what you said.
thanks for that thread link btw. i'll try some of the methods in that one too

---

### Post by tsk84eva on 2008-06-12
ok i've tried what you said pytheas, and even temporarily disabling wpa didn't work.  Also i failed to mention before that the light for my wireless indicator is off on my laptop, and flipping the switch does nothing.  I saw something similar in the thread you linked me to, and this may be part of the problem.  So do you know how i can get it on?  Anyway, here is the iwlist you asked me to post:

wlan0     Scan completed :
          Cell 01 - Address: 00:12:0E:75: DF:9C
                    ESSID:"WEST6013"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/100  Signal level=-70 dBm  Noise level=-127 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000022a284cd879

---

### Post by pytheas22 on 2008-06-12
I've never had a card like you myself so I don't know exactly how to make sure it's on.  But check the BIOS to make sure it's enabled (even if this wasn't necessary in Windows, it might be for Linux), and of course make sure any physical switches for the card are on.  There are also instructions [here]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/") for installing a better version of the driver that might solve the problem with the LED not coming in.  I'd recommend giving them a try; they probably can't make it any worse.

You could also try these commands to connect from the command line (with encryption on your router still disabled):
```

sudo -s
ifconfig wlan0 down
iwconfig wlan0 channel 6
iwconfig wlan0 mode managed
iwconfig wlan0 essid "WEST6013"
ifconfig wlan0 up
dhclient wlan0
```

If things go the way you want, that last command will result in you being assigned an IP address (assuming your network uses dhcp; if it doesn't, let me know) and you'll be on the Internet.

Let us know if this gets you anywhere.

---

### Post by diamorph on 2008-06-12
had the same problem, installing b43-fwcutter and b43-firmware packages got my broadcom working - indicator on, networks listed...but i still couldn't connect.

---

### Post by pytheas22 on 2008-06-12
> had the same problem, installing b43-fwcutter and b43-firmware packages got my broadcom working - indicator on, networks listed...but i still couldn't connect.

You should try blacklisting the b43 driver and reverting to bcm43xx, an older version of the Broadcom driver that works better for a lot of people.  You would do this (copied and pasted from another thread):

1. open a terminal and type:
```

sudo gedit /etc/modprobe.d/blacklist
```

look for a line that says "blacklist bcm43xx." Delete this line and add the lines "blacklist b43", "blacklist b43legacy", "blacklist ssb" and "blacklist ndiswrapper"

2. run:

```
sudo bcm43xx-fwcutter
```

You should be asked to download firmware; tell it yes.

Then reboot and see if the card works again.

----

The original poster of this thread has an Intel wireless card, however, so Broadcom isn't the issue.

---

### Post by tsk84eva on 2008-06-12
> **pytheas22 said:**
> I've never had a card like you myself so I don't know exactly how to make sure it's on.  But check the BIOS to make sure it's enabled (even if this wasn't necessary in Windows, it might be for Linux), and of course make sure any physical switches for the card are on.  There are also instructions [here]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/") for installing a better version of the driver that might solve the problem with the LED not coming in.  I'd recommend giving them a try; they probably can't make it any worse.

You could also try these commands to connect from the command line (with encryption on your router still disabled):
```

sudo -s
ifconfig wlan0 down
iwconfig wlan0 channel 6
iwconfig wlan0 mode managed
iwconfig wlan0 essid "WEST6013"
ifconfig wlan0 up
dhclient wlan0
```

If things go the way you want, that last command will result in you being assigned an IP address (assuming your network uses dhcp; if it doesn't, let me know) and you'll be on the Internet.

Let us know if this gets you anywhere.

when i try to put in that 2nd line of code, i get this:
root@tsk84eva-laptop:~# ifconfig wlan0down
wlan0down: error fetching interface information: Device not found

FYI, i've just plugged in an ethernet cable and was able to get online without an issue

---

### Post by nickdbliss on 2008-06-13
Seems like drivers interference. I have created a thread try it if it works for you.thanks

[http://ubuntuforums.org/showthread.php?t=827799](http://ubuntuforums.org/showthread.php?t=827799)

---

### Post by pytheas22 on 2008-06-13
> when i try to put in that 2nd line of code, i get this:
root@tsk84eva-laptop:~# ifconfig wlan0down
wlan0down: error fetching interface information: Device not found

You made a typo :)  There should be a space between "wlan0" and "down."

---

### Post by ajwak95 on 2008-06-13
I am having the same problem as the guy who posted the original problem. I also have another problem, When I attempt to connect to the internet, it shuts down my 1000SW Home Portal too.

---

### Post by tsk84eva on 2008-06-13
> **pytheas22 said:**
> You made a typo :)  There should be a space between "wlan0" and "down."

o wow i cant believe i did that haha.
thanks for showing me that.
i'll fix it right away and see what happens:)

---

### Post by tsk84eva on 2008-06-13
alright i ran that command again and this was the result:

root@tsk84eva-laptop:~# ifconfig wlan0 down
root@tsk84eva-laptop:~# iwconfig wlan0 channel 6
root@tsk84eva-laptop:~# iwconfig wlan0 mode managed
root@tsk84eva-laptop:~# iwconfig wlan0 essid "WEST6013"
root@tsk84eva-laptop:~# ifconfig wlan0 up
root@tsk84eva-laptop:~# dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:77:65:da:92
Sending on   LPF/wlan0/00:1b:77:65:da:92
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


i'm not sure if this worked the way it was supposed to, or if i'm supposed to use the ip listed

---

### Post by pytheas22 on 2008-06-13
> i'm not sure if this worked the way it was supposed to, or if i'm supposed to use the ip listed

It didn't work the way you wanted because dhclient wasn't able to fetch an IP address.  You could try setting one statically by going to System>Administration>Network, if you know enough your network to know how to configure it.

Otherwise I'm not sure what else to try--it looks like your card works fine at all stages until it gets to the part where it needs to fetch an IP address, and I don't know why.  It doesn't seem to me to be as issue with the card being turned off, because it doesn't make sense for it to be able to see networks and request IP leases if the wireless is off.

I would recommend giving ndiswrapper a shot but you said you already tried that and it didn't help.  Are you sure you configured it correctly?

---

### Post by tsk84eva on 2008-06-13
i'll try ndiswrapper again.
it couldn't hurt.
thanks for all the replies though

---

### Post by pytheas22 on 2008-06-13
Alright, try with ndiswrapper again and if you need help, post.  Make sure you blacklist the native Linux drivers or ndiswrapper won't work.  I'm not sure which drivers to blacklist for your card, but if Google doesn't tell you let me know.

---

### Post by nickdbliss on 2008-06-14
Ndiswrapper didnt work as you said earlier because there is a conflict between ndiswrapper and ssb in Hardy. I have posted the solution in this other thread, it should work for your card as well (use your windows driver). Try it and post the results here. Thanks

[http://ubuntuforums.org/showthread.php?t=827799](http://ubuntuforums.org/showthread.php?t=827799)

---

### Post by tsk84eva on 2008-06-14
> **nickdbliss said:**
> Ndiswrapper didnt work as you said earlier because there is a conflict between ndiswrapper and ssb in Hardy. I have posted the solution in this other thread, it should work for your card as well (use your windows driver). Try it and post the results here. Thanks

[http://ubuntuforums.org/showthread.php?t=827799](http://ubuntuforums.org/showthread.php?t=827799)

thanks nickdbliss.
i forgot you had posted earlier.
i'll try what you said asap

---

### Post by pytheas22 on 2008-06-14
Ndiswrapper should work, but keep in mind that the tutorial from nickdbliss is for a Broadcom card, while tsk84eva has an Intel card.  You can follow the general steps for configuring ndiswrapper, but the Windows driver that you install will be different (not bcmwl5) and you don't need to do any of the fwcutter stuff (that's specific to Broadcom).  Also the modules to blacklist mentioned in nickdbliss' thread (b44, b43, ssb and so on) will be different for you...you need to blacklist the Intel wireless modules.

---

