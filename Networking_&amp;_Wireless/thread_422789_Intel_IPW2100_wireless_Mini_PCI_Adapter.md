---
title: "Intel IPW2100 wireless Mini PCI Adapter"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by liberalist on 2007-04-25
My wireless internet does not work. My Wireless SSID does show up in the Wireless Assistant 0.5.5. I am using Kubuntu 6.06.1 LTS. Furthermore, I was asked to turn my Radio on of my wireless card and I pressed "Yes".

I looked in the KInfoCenter and I found that my wireless card is called Intel Corporation Pro Wireless/LAN 2100 3B Mini PCI adapter (rev 04). At [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/) I found a possible driver, but I don't really know how to install it. I tried unpacking the compressed file, but I got some kind of warning (I downloaded version 1.2.0.). It did open in Ark and showed the files.

I read some post on this forum that I should run dhclient in the terminal. I ran it as root user (sudo, right? I am new to Linux, forgive me if I make any mistakes.) and got the following lines:

```
Internet Systems Consortium DHCP Client v3.0.3
Copyright 2004-2005 Internet Systems Consortium
All rights reserved. 
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth/00:04:23:53:7b:61
Sending on LPF/eth1/00:04:23:53:7b:61
Listening on LPF/eth0/00:0b:db:99:12:a3
Sending on LPF/eth0/00:0b:db:99:12:a3

DHCPDISCOVER on eth1 to .... (there are a lot of lines with DHCPDISCOVER, 
please tell me if I need to provide them) 
```

*Thank you very much in advance.*

---

### Post by chili555 on 2007-04-25
It sounds, so far, like your adapter is working! Let's take a look at:```
iwconfig
sudo iwlist eth1 scan
```That assumes eth1 is your relevant wireless interface from *iwconfig*. If not, substitute wlan0 or whatever *iwconfig* tells you your interface is. Sounds like we can get it going.

---

### Post by liberalist on 2007-04-25
OK, thanks for your reply :) However, I have business to attend to and will try out everything from the above post sometime later. Thanks again, though. 

A question of another nature: is it worth it to upgrade to (K)Ubuntu 7.04 (I am a business user). Is it easy to upgrade to this version (just insert the CD and start-up from it and then opt for a "clean" install?)? Or are there any other (possibly easier) methods? Thank you in advance for your answer.

---

### Post by chili555 on 2007-04-25
The following, not to start a flame war, is my opinion only. I am not a moderator or a developer.

I have an oh-so-smooth running Edgy laptop. I ran the Feisty live CD and had many problems. For my daily-driver needs, I said no thanks to the upgrade. A glance at this forum yields many complaints about wireless not working as perfectly in Feisty as it did in Edgy, so I'll wait.

On the other hand, I have an ancient IBM laptop that I use to try new, and potentially hazardous, software. Feisty runs perfectly on it! But I do not trust on-line banking and investments to my test mule.

If you do decide to upgrade, run the live CD for a few days and see if it works well for you. Here is the recommended procedure: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Back up everything. Blank DVD's are cheap insurance.

---

### Post by liberalist on 2007-04-26
Thanks for your advice. As stated earlier, I have version 6.06.1 LTS. Do you recommend me to upgrade to the newer version Edgy Eft (6.10)? Is upgrading similar from 6.0.6.1 LTS to Edgy Eft as to Feisty Fawn (7.04)? 

Where can I download Edgy Eft and till when is it supported? Thank you very much in advance.

---

### Post by liberalist on 2007-04-26
I have tried iwconfig in the Konsole (Terminal) to get my wireless card working. The results are attached in .odt format and available for download below. However, I **cannot** connect to my wireless network (yet).

---

### Post by chili555 on 2007-04-26
Your iwconfig file tells me your card is working fine. No need for new drivers, unpacking questionable files from outside of Ubuntu.

I notice in the scan, that encryption is on in the access point. Is this WEP, WPA or otherwise? If you know the encryption is WEP and the key you have is hex, connecting should be as easy as:```
sudo iwconfig eth1 essid "Inalambrico de Casa"
sudo iwconfig eth1 key 0123xyzwhatever
sudo dhclient eth1
```Sometimes cards will come to life if the word 'open' or 'restricted' follows the key, like this:```
sudo iwconfig eth1 key 0123xyzwhatever open
```

More on upgrades later.

---

### Post by liberalist on 2007-04-27
Thanks for your reply, you are really kind to help me so good :) 

Yes, I have WEP 128 bits encryption (the access point is from a Dutch company named Orange, but I don't think you have Orange anywhere outside Europe). I don't know whether it is an open/shared key or HEX or ASCII, where can I find that information (i.e. what do I need to search for in Google?)? I am working now, so I will try your suggestions in the above post sometime later today. Again, thank you very much.

---

### Post by liberalist on 2007-04-27
I had a moment to test out if your method worked, and unfortunately it didn't. Maybe I have typed something wrong (although I have checked). Attached is the things I typed in my Konsole (Terminal) window. Thank you very much in advance for your help.

---

### Post by chili555 on 2007-04-27
#40 or 64 bit ASCII WEP code has 5 characters
#40 or 64 bit HEX WEP code has 10 characters
#128 bit ASCII WEP code has 13 characters
#128 bit HEX WEP code has 26 characters 

Since your key has 10  characters, I'm fairly certain it's hex. Please try these commands, each on its own line and press enter after each line. Unless there is an error, you won't get any output until the last one:```
sudo iwconfig eth1 essid "Inalambrico de Casa"
sudo iwconfig eth1 key 0xyzxyz9 open
sudo dhclient eth1
```If you do not connect, try this:```
sudo iwconfig eth1 key 0xyzxyz9 restricted
sudo dhclient eth1
```Let us know.

---

### Post by liberalist on 2007-04-30
> **chili555 said:**
> sudo iwconfig eth1 essid "Inalambrico de Casa"
sudo iwconfig eth1 key 10XX11XX10 open
sudo dhclient eth1[/CODE]

Could you please remove/subsitute the wireless access point password in the post on page 1 as soon as possible? Thank you very much in advance.

---

### Post by liberalist on 2007-04-30
Your previous suggestions did not work as well. See below for details (a copy of the details from a terminal window/Konsole)

```
john@john-latitudeD800:~$ sudo iwconfig eth1 essid 'Inalambrico de Casa' 
sudo iwconfig eth1 key 10XXXX1121 open 
sudo dhclient eth1
Password:
Error : unrecognised wireless request "sudo"
john@john-latitudeD800:~$ sudo iwconfig eth1 key 10XXXX1121 restricted 
sudo dhclient eth1
Error : unrecognised wireless request "sudo"
john@john-latitudeD800:~$
```

I checked for typos, but all seemed well. Attached is a screenshot of my network status (for security reasons is my SSID hidden). 

Thank you very much in advance.

---

### Post by chili555 on 2007-04-30
> Could you please remove/subsitute the wireless access point passwordDone.

I am afraid I have not explained myself well enough. Please do:```
sudo iwconfig eth1 essid "Inalambrico de Casa"
```Put the ESSID in quotes, not apostrophe. Press enter. Let the cursor come back to the prompt. Next, do:```
sudo iwconfig eth1 key 10XXXX1121 open
```Press enter. Let the cursor come back to the prompt. Then do:```
sudo dhclient eth1
```Press enter. Let us know the result.

---

### Post by liberalist on 2007-05-01
Hi everyone,

My internet is working now :) Thank you very much for all your kind help. Below is an attachment with the output given by the terminal window.

---

### Post by liberalist on 2007-06-07
> **chili555 said:**
> Done.

I am afraid I have not explained myself well enough. Please do:```
sudo iwconfig eth1 essid "Inalambrico de Casa"
```Put the ESSID in quotes, not apostrophe. Press enter. Let the cursor come back to the prompt. Next, do:```
sudo iwconfig eth1 key 10XXXX1121 open
```Press enter. Let the cursor come back to the prompt. Then do:```
sudo dhclient eth1
```Press enter. Let us know the result.

Hi, I am back in Kubuntu again. Internet does work if I enter the above code in the terminal. However, if I boot into Kubuntu again, it apparantly has forgotten that I have set up the wireless card. I cannot connect with Wireless Assistant (I have set it up with my WEP key and it is an open key), but need to type in the above again in the Konsole to connect to the internet.
Thanks in advance for your reply.

---

### Post by chili555 on 2007-06-07
I suggest you *sudo kate /etc/network/interfaces* to put the relevant settings there permanently:```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid "Inalambrico de Casa"
wireless-key 10XXXX1121 open
```Save and close kate. On boot, it should start and connect automatically.

---

### Post by liberalist on 2007-06-07
Your suggestion above did **not** work. 

This is what I have in the interfaces file:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid "Inalambrico de Casa"
wireless-key 10XXXX1121 open

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by chili555 on 2007-06-08
First, since you do not have eth2, ath0 or wlan0, I suggest removing those entries in *interfaces.* Next time you boot up and the wireless is not enabled, please try:```
sudo ifup eth1
```If that works, *sudo gedit /etc/rc.local* to add:```
ifup eth1
```Add it on its own line *above* the line 'exit 0'  Save and close gedit. Let me know if a reboot fixes the problem.

If this does *not* work, try:```
sudo ifdown eth1 && sudo ifup eth1
```If that works, change the addition to rc.local to:```
ifdown eth1 && ifup eth1
```Please let us know.

---

### Post by liberalist on 2007-06-10
Thank you very much for your help. I think my internet now works :)

How did you get a registered Linux user?

---

### Post by liberalist on 2007-10-20
Hi everyone and chili555,

Yesterday, I upgraded to Kubuntu version 7.10 Gutsy Gibbon. The new file manager Dolphin is amazing, as well as some other features. 

However, my wireless network does not work again. I tried the above solutions (except for the ones on page 2)? 

I thought that it'd easier in 7.10 to install **restricted drivers**? But I don't seem to figure the right thing out. 

Thank you very much in advance for your reply. 

PS: There is no rush, *festina lente* (rush slowly).

---

### Post by peterbrewer on 2007-10-20
You shouldn't need restricted drivers as intel wireless card drivers are usually open source.  When you go to the network manager in the system tray does it show nearby wireless networks.  If so what happens when you try to connect, when it asks for your password make sure above the entry box it is set to WEP-HEX rather than WEP-PASSPHRASE or something like that.

---

### Post by liberalist on 2007-10-20
> **peterbrewer said:**
> You shouldn't need restricted drivers as intel wireless card drivers are usually open source.  When you go to the network manager in the system tray does it show nearby wireless networks.
No, there are no wireless networks shown in KnetworkManager. 

> **peterbrewer said:**
> If so what happens when you try to connect, when it asks for your password make sure above the entry box it is set to WEP-HEX rather than WEP-PASSPHRASE or something like that.
I know about that, but I can't seem to figure out why my wireless network does not show up.

All help is very much appreciated and greetings from Holland.

PS: Would you like to have the output from the Konsole (Terminal)? I ran dhcp or something as described in previous posts in this thread. My USB data stick does not work at the moment (it did work for a short while). In the previous version, Feisty Fawn, more things seemed to run well.

---

### Post by peterbrewer on 2007-10-20
What does iwconfig show?

---

### Post by liberalist on 2007-10-20
I can barely read what it says (still high resolution):

```
john@john-laptop:-$ sudo iwconfig
lo         no wireless extensions.

eth0    no wireless extensions.

eth1    unassociated ESSID:off/any Nickname:"ipw2100"
           Mode:Managed channel=0 Access-point: Not-Associated
           Bit Rate: 0 kb/s Tx-power: 16 dBm
           Retry short limit:7 RTSTHR:off Fragment thr:off
           Encryption: key off 
           Powermanagement:off
           Linkquality: 0 Signal level:0 Noise level:0
           Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
           Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```

*I am just scanning for viruses/problems and ~50 of them are found so far*

---

### Post by peterbrewer on 2007-10-20
Run the following commands replacing ESSID with the name of your network and the_key with your wep key.  Everything beginning with sudo is a new command.

sudo iwconfig wlan1 essid "ESSID"
sudo iwconfig wlan1 mode managed
sudo iwconfig wlan1 key the_key
sudo dhclient wlan1

---

### Post by liberalist on 2007-10-21
I ran the commands, comments are inline. 

> **peterbrewer said:**
> Run the following commands replacing ESSID with the name of your network and the_key with your wep key.  Everything beginning with sudo is a new command.
Understood. Thanks. 

> **peterbrewer said:**
> sudo iwconfig wlan1 essid "ESSID"
SET failed on device wlan1 ; No such device. 

> **peterbrewer said:**
> sudo iwconfig wlan1 mode managed
Error for wireless request "Set Mode" (8B06) :
SET failed on device wlan1 ; No such device. 

> **peterbrewer said:**
> sudo iwconfig wlan1 key the_key
iwconfig: unknown command "key the_key" (Of course I replaced key the_key with my passcode) 

> **peterbrewer said:**
> sudo dhclient wlan1
There is already a PID file /var/run/dhclient.pid with pid 123qrstabcd (hidden)

*Question:* Since I need to type everything by hand, do you need the output of the DHCP client?

---

### Post by peterbrewer on 2007-10-21
Sorry, you need to replace wlan1 with the name of your wireless device, in your case eth1.

---

### Post by liberalist on 2007-10-21
No worriess... Polle, polle (or something like that, an African term which roughly means: take it easy)

---

### Post by liberalist on 2007-10-21
My wireless connection still does **not** work. It has something to do with 

1. ```
"iwconfig:unknown command "Key the_key"
```
2. ```
sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid 1234xyzab.
``` 

Would you like to have the full dhclient output? (This might take a while, as my USB data stick does not work with Gutsy all of a sudden)

---

### Post by peterbrewer on 2007-10-21
Instead of typing the_key type your actual wep key.

---

### Post by liberalist on 2007-10-21
> **peterbrewer said:**
> Instead of typing the_key type your actual wep key.


Of course I typed my actual WEP key. I don't display this key on the forums out of security reasons.

My encryption is WEP 64 bits, I checked. I have a wireless access point named Livebox from Orange (T-Mobile).

Again, my wireless network worked fine in Feisty Fawn.

**Update:** I tried the same code three times again, but to no avail. My sister was with me to check for typing errors, but we could not spot one. We separated every command with the enter key. 

In any case, all help is appreciated. Thank you for the excellent support here.

---

### Post by liberalist on 2007-10-22
Thanks everyone for their assistance.

I have good and bad news. The bad news is that my Dell Latitude D800 laptop still does not connect to the wireless network (or has a notion of it). The good news is that KNetworkManager works more or less.

This means that I can try an ethernet connection someplace else.

Again, all of your kind help is so much appreciated. Kubuntu and Ubuntu still remain high on the list of Linux distributions.

---

