---
title: "Help with Intel PRO/Wireless 2200"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by gdoyel on 2006-09-07
Having a strange problem with my wireless card - an Intel PRO/Wireless. You'll have to excuse me for making a new thread; the other threads don't seem to help with my issue, so far as I can tell.

Dapper, default 386 kernel.

When I first installed Dapper this past Sunday, wireless was peachy and I was a happy man. All of a sudden late Monday, I lost wireless capability.

Here's iwconfig:
```
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"TigerNet"
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

"radio off" leads me to believe the card isn't on, but Dapper recognizes it, and in Network it tells me the card is active.

Please, any help is appreciated.

](*,)

---

### Post by disciple on 2006-09-07
does your notebook have a wireless button/LED? is it lit? perhaps you hit it in error?

in any event, 

try ' #iwconfig eth1 power on'

---

### Post by gdoyel on 2006-09-07
Here's what I got.

```
root@gene-laptop:~# iwconfig eth1 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth1 ; Input/output error.
```

---

### Post by struther on 2006-11-19
I am having the exact same problem and receive the same error.  I was wondering if anyone made any progress on this issue or has any suggestions?

---

### Post by Braunstein on 2006-11-21
Ditto with the problem. I simply can't enable my card. In my case, the card has never worked under ubuntu.

---

### Post by Sencer on 2006-11-21
THe ipw2200 is one of the better supported cards. It works better on Linux than it does on windows (better speed, less connection problems etc.). I've set-up several notebooks with the ipw2200 and never had a problem with either dapper or edgy (it's also one of the wifi-cards that work very well with network-manager, if you want to use WPA and roaming etc). Check /var/log/messages and search for "switch" you'll likely find a line that reads something like:

> Nov 21 09:25:01 hostname kernel: [4384014.552000] ipw2200: Radio Frequency Kill Switch is On:
Nov 21 09:25:01 hostname kernel: [4384014.552000] Kill switch must be turned off for wireless networking to work.


which is as instructive as it gets. As mentioned above it's the often the "laptop's switch" to turn on/off wifi. Many people are thrown off, because the LED doesn't work, so they don't get feedback on whether their pushing has any effect. On an Acer notebook (and I presume on others as well) this can be fixed by creating a file:

/etc/modprobe.d/ipw2200

and putting into it this text:

```

options ipw2200 led=1

```

I think after that, simply once removing and reloading the module should get the LED of the WIFI button working. Of course you can simply reboot, if you're unsusre on how to do that.

The other option is to boot into windows or whatever OS came with your notebook, switching on wireless and then rebooting into Ubuntu.

---

### Post by .tommie on 2007-01-15
> **Sencer said:**
> 

Enter in terminal:
```

sudo gedit /etc/modprobe.d/ipw2200

```
And putting into it this text:
```

options ipw2200 led=1

```


Doing this under Ubuntu 6.10 Edgy Eft works perfectly to turn on the IPW2200 LED!

---

### Post by Harin on 2007-01-17
I'm sorry but I followed your instructions and my crappy intel card is still doa, I'ven upgraded all the drivers and the firmware, the card used to work under ubuntu but all of a sudden it stopped, the hardware switch has no effect and neither does the echo command. The rf_kill file shows the number 2 which means that the hardware switch is responsible for the radio being off. I've read everything out there about this problem and it seems a lot of people have had the same issue, I've tried every suggested fix but haven't found a working one yet. I've tried enabling the radio via a terminal, tried a fresh install of ubuntu, tried turning it on in windows, and upgraded all drivers, and restarted countless times in between. Any help would be appreciated. Thanks.

Edit:
Some more info:
IPW2200BG 1.2.0
Firmware v3.0
Latest ieee from repository
Ubuntu 6.10 (Not dual boot)
Acer travelmate 290

Thanks again

---

### Post by andnobodyslept on 2007-01-25
I have a similar problem on my Dell inspiron 600m, I can get the radio to turn back on by hitting Fn-F2 but this only works some of the times, and often times for only a short while. Any advice on how to make sure that the radio stays on for permanently would be great.

---

### Post by Black_Gamer on 2007-05-04
I have an acer 1691WLMI with Feisty. I tried the method above to turn on the ipw2200 led, but i can't find the ipw2200 module in /etc/modprobe.d/ . Does anyone know how to turn the led on in Feisty?

---

### Post by davidgypsy on 2007-05-05
My ipw 2200 works great under Mepis, but not under Ubuntu 6.10. And it definitely is switched on.

---

### Post by davidgypsy on 2007-05-26
> **davidgypsy said:**
> My ipw 2200 works great under Mepis, but not under Ubuntu 6.10. And it definitely is switched on.

Just installed 7.04, and the wireless works now, but the led doesn't come on. Will try to fix that, but I am just happy to be able to go online with Ubuntu!! Well done dev's team! :D

---

### Post by Big Bear on 2007-06-09
I'm running ubuntu studio, mine is still off.... I have tried my wireless switch both ways, same result, the command "iwconfig eth1 power on" does nothing...  I have an Asus Z83V laptop if that helps.  I'm a bit new to Linux but trying to learn, luckily I have another computer so far.... :p

---

### Post by ghonz on 2007-06-10
I'm having similar issues, I'm running Feisty on a HP Pavilion ze2262.  I've tried everything thats been suggested on this forum and managed to get my wireless button to go from being permanently off to constantly flashing.

I've been using Ubuntu since February and still can't get wireless to connect.  Using Wireless assistant I have been able to detect networks but I can't connect.

This is starting to get slightly frustrating.

---

### Post by Tilex on 2007-06-14
> **Black_Gamer said:**
> I have an acer 1691WLMI with Feisty. I tried the method above to turn on the ipw2200 led, but i can't find the ipw2200 module in /etc/modprobe.d/ . Does anyone know how to turn the led on in Feisty?

You just create a file an put in the information mentioned above.

```
sudo pico /etc/modprobe.d/ipw2200

```

write:

```
options ipw2200 led=1
```

then ctrl+o to save, and ctrl+x to exit. Reboot, and you're LED should work.

---

### Post by Tilex on 2007-06-14
> **ghonz said:**
> I'm having similar issues, I'm running Feisty on a HP Pavilion ze2262.  I've tried everything thats been suggested on this forum and managed to get my wireless button to go from being permanently off to constantly flashing.

I know how frustrating that can be.  Instead of using any assistant, I use a simple script.  Here it is:

Open a terminal, and type:
```
pico wireless_connect
```

then, copy/paste this code
```

#!/bin/bash
#Scripts to connect automatically to wireless network [your_access_point_name]

ACCESS_POINT="[your_access_point_name]"
KEY="[your_key]"
ETH="eth1"
echo "The computer is connecting to $ACCESS_POINT"

sudo iwconfig $ETH mode managed essid $ACCESS_POINT key $KEY
sudo dhclient $ETH

```

-  Change your access point name, your key, and your wireless adapter (eth1 here),
-  Ctrl+o to save, ctrl+x to exit.
-  Change the file to executable by typing:
```
chmod +x wireless_connect
```

-  Then, every time you want to connect to your wireless, go where you saved that script via a terminal and type:
```

./wireless_connect.

```

Hope it works!

---

### Post by torstenaf on 2007-06-16
I have a Sony VAIO with the Intel Pro/Wireless 2200BG internal wireless card. My wireless connection worked perfectly for about a year.

In the last few days or couple of weeks, some upgrade or other has made my wireless connection barely work. Most of the time, it doesn't connect. Every now and then I get a few minutes of functionality, and it dies again.

I'm typing this under Windows XP (Agh!), because the connection is so flaky now, it's nearly unusable.  :(

**Diagnosis**
I've tried to unload and reload the *ipw2200* module, and bring the interface up and down with *ifconfig.* I've also tried to turn the radio on and off, but still can't seem to get anywhere.

---

