---
title: "Internet: Windows fast, Ubuntu painfully slow."
date: 2011-03-18
forum: New to Ubuntu
---

### Post by Torp3x on 2011-03-18
Browsing/downloading in Ubuntu is prohibitively slow. I have a Maverick and Win7 dual boot, and had to log back into Windows just to post this as Ubuntu was failing at loading web pages in under 10 minutes.
Where should I begin if I want to diagnose and fix this problem?

Cheers.

---

### Post by r-senior on 2011-03-18
Wired or wireless?

If wireless, are you able to try wired and see if the problem is the same?

---

### Post by josephmills on 2011-03-18
> **Torp3x said:**
> Browsing/downloading in Ubuntu is prohibitively slow. I have a Maverick and Win7 dual boot, and had to log back into Windows just to post this as Ubuntu was failing at loading web pages in under 10 minutes.
Where should I begin if I want to diagnose and fix this problem?

Cheers.

do you have firewalls up? In windoz and ubuntu? what kind of card(wireless) do you have? Is the driver bleeding edge? How much room is there for ubuntu?Have you tested your speed (tp test)?

---

### Post by Torp3x on 2011-03-18
Updated some backports, seems to be an improvement. Wouldn't have expected a clean installation of 10.10 to have such a problem though. Nevermind.

---

### Post by Torp3x on 2011-03-18
I tell a lie, this problem still exists.

Atheros wireless card; after some updates, browsing speed has improved but downloads hang in both Firefox and Terminal. 

Where do I start fixing this?

---

### Post by 3177 on 2011-03-18
as far as I know the atheros wireless card has issues in ubuntu.
I'll post back with some useful links.

---

### Post by Dutch70 on 2011-03-18
Until 3177 comes back, Try this.

First run this in terminal to make sure you're totally updated.
```
sudo apt-get update && sudo apt-get upgrade
```

Check your speed here...
[[COLOR="Blue"]http://speedtest.net/[/COLOR]]("http://speedtest.net/")

---

### Post by 3177 on 2011-03-18
[http://ubuntuforums.org/showthread.php?t=982105](http://ubuntuforums.org/showthread.php?t=982105)

hope this helps you since you didn't give the exact card.

---

### Post by 3177 on 2011-03-18
> **Dutch70 said:**
> Until 3177 comes back, Try this.

First run this in terminal to make sure you're totally updated.
```
sudo apt-get update && sudo apt-get upgrade
```Check your speed here...
[[COLOR=Blue]http://speedtest.net/[/COLOR]]("http://speedtest.net/")

+1
also, in a terminal 
```
lspci
```
post back the results please
that should give us exact info on your card

---

### Post by matt_symes on 2011-03-18
Hi

Try disabling IPv6. Do it from GRUB kernel command and in Firefox.

Add this

```
ipv6.disable=1
```

to your grub command line (/etc/default/grub LINE GRUB_CMDLINE_LINUX_DEFAULT) and

```
sudo update-grub
```

From firefox enter about:config into the navigation bar

search for ipv6 in the filter and set

network.dns.disableIPv6 to true.

Kind regards

---

### Post by beew on 2011-03-18
Which Atheros card? I have one machine which uses the ath5k driver, it is a dual boot between XP and Ubuntu 10.10. Wireless connection is actually faster and better in Ubuntu than in XP.

---

### Post by Torp3x on 2011-03-18
Thanks for the help. Sorry, it's an Atheros AR9285. All updates are installed. I've noticed it drops the connection and immediately reconnects too, every once in a while. Connection strength is around 90/95%.

Tried installing the Windows driver with ndiswrapper, just got a driver invalid error.

Someone mentioned bleeding edge drivers? I don't have these.

---

### Post by Torp3x on 2011-03-18
Oh and exactly where in the grub file does the ipv6 disable command go? Between the quotations in

GRUB_CMDLINE_LINUX=""

or somewhere else?


Cheers.

---

### Post by matt_symes on 2011-03-18
Hi 

try my earlier post (post 10) to disable ipv6. That helped me alot.

**EDIT** We are cross posting :)

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1"

Kind regards

---

### Post by Dutch70 on 2011-03-18
Also found these...
[[COLOR="Blue"]http://ubuntuforums.org/archive/index.php/t-1286503.html[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-1286503.html")
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=8958170[/COLOR]]("http://ubuntuforums.org/showthread.php?p=8958170")

---

### Post by 3177 on 2011-03-18
what web browser are you using?

---

### Post by oldsoundguy on 2011-03-18
just the opposite for me ... Windows using Firefox is slow as hell while Linux using  Firefox blazes.

But I do not dual boot on an old crappy laptop. SEPARATE desktop computers with identical specifications.

---

### Post by matt_symes on 2011-03-18
Hi

Another interesting question. What are your ping times like ? Are you losing packets.

```
ping -c 100 8.8.8.8
```

What DNS server are you using ? How fast are your nslookups.

```
nslookup 8.8.8.8
```

Kind regards

---

### Post by 3177 on 2011-03-18
> **oldsoundguy said:**
> But I do not dual boot on an old crappy laptop. SEPARATE desktop computers with identical specifications.

hey watch it.
no computer is old and crappy.
I know of people running lubuntu 10.10 on a 255MHZ processor with 128MBs of ram.

---

### Post by Torp3x on 2011-03-18
7% packet loss, average 55ms ping time.

Oh and the download problem is with Chrome, Firefox, Terminal and anything else I've tried that downloads data. Lots and lots of 'hang time'.

I had to plug in to the router to get the updates cos it was taking so long in Terminal...

---

### Post by Torp3x on 2011-03-18
I've noticed in iwconfig that my bitrate is 1 Mb/s. Shouldn't it be more than that?

---

### Post by beew on 2011-03-18
> **3177 said:**
> hey watch it.
no computer is old and crappy.
I know of people running lubuntu 10.10 on a 255MHZ processor with 128MBs of ram.


Yeah that would certainly  be old and crappy. :)

---

### Post by 3177 on 2011-03-18
> **beew said:**
> Yeah that would certainly  be old and crappy. :)

thats funny because they run into less problems than anyone else Ive seen on the forums.

---

### Post by matt_symes on 2011-03-18
Hi

Post the whole output of iwconfig. That is low speed and quite high packet loss.

Also what is the output of 

```
nm-tool
```

Kind regards

---

### Post by Torp3x on 2011-03-18
Ok, I've just swapped back and forth between Windows and Ubuntu. I downloaded an identical 10Mb file with each OS. Windows took a few seconds at 300kbps plus. Ubuntu started off at 30kbps, then I watched as the speed slowly dwinded away and levelled off around 12kbps. This aint right.

iwconfig now shows a higher bitrate though for some reason:

```
IEEE 802.11bgn  ESSID:"xxxxxx"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: xx:xx:xx:xx:xx   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```The output of nm tool is

```
- Device: wlan0  [Auto xxxxxx] -----------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        xxxxxxxx

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
   Freq 2442 MHz, Rate 54 Mb/s, Strength 54 WPA

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
```

---

### Post by matt_symes on 2011-03-18
Hi

Hmmm. I have an Atheros Communications Inc. AR928X and i don't have these issues.

Maybe try the newest drivers ?

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

It's very late here though.

Kind regards

---

### Post by beew on 2011-03-18
> **3177 said:**
> thats funny because they run into less problems than anyone else Ive seen on the forums.

I completely expect that. You won't run into many problems with old crappy PC since you don't do (and can't do) much of anything with it. So if the old crappy PC cannot even play videos then of course you won't have any problem with media players. :)

---

### Post by Torp3x on 2011-03-18
Ok so I downloaded this driver pack-

[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

And installed the lot. Now working 100% :D

Thanks all for the help!

---

### Post by 3177 on 2011-03-18
> **beew said:**
> I completely expect that. You won't run into many problems with old crappy PC since you don't do (and can't do) much of anything with it. So if the old crappy PC cannot even play videos then of course you won't have any problem with media players. :)

lol

---

