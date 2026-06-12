---
title: "Wifi troubles with WEP"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by Ultra Magnus on 2007-12-08
Hi, I've been having a few problems with my wifi and I'm not sure its related to the WEP encryption or not (unfortunately I'm in a shared house and its the land lords internet so I can't turn the WEP off to have a look).

I've been having a look at iwconfig and it appears that I am connected (in some way)
this is the output:

james@HAL-9000:~$ sudo iwconfig eth1
eth1      IEEE 802.11g  ESSID:"Derek"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 
00:1B:11:8C:D6:F0   
          Bit Rate:36 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:6E31-3637-7468-6F72-7065-7761-79   Security 
mode:open
          Power Management:off
          Link Quality=74/100  Signal level=-60 dBm  Noise level=-61 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:41   Missed beacon:0

The one thing that looks a bit troubling is the Invalid misc:41 - I'm not quite sure what it means as there is only a short entry on the man page about it.

But also when I type iwlist scanning I get this:

james@HAL-9000:~$ sudo iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:1B:11:8C:D6:F0
                    ESSID:"Derek"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 54 Mb/s
                    Quality=75/100  Signal level=-59 dBm  Noise level=-59 dBm
                    Extra: Last beacon: 48ms ago

And I noticed that the protocol is slightly different - IEEE 802.11bg for the router and I am using IEEE 802.11g

I tried changing this with iwconfig but it saied that it was unsupported on my card.

I'm kind of at a lose of what to try next so if there is any advice that would be useful!

Thanks

Jim

edit: - I tried to get rid of the smilies post submitting but was unable to - but seeing a happy face does make me feel somewhat better!

---

### Post by Potatoj316 on 2007-12-08
What kind of wireless card do you have.  

a tip:when pasting terminal output check the box that says disable smilies in text.

---

### Post by chili555 on 2007-12-08
> The one thing that looks a bit troubling is the Invalid misc:41Harmless; you can safely ignore it.> I noticed that the protocol is slightly different - IEEE 802.11bg for the router and I am using IEEE 802.11gThis simply means your router is compatible with old-timey 802.11b devices, as well as 802.11g (but not 802.11n). Also a harmless entry you can ignore.

Please try:```
sudo iwconfig eth1 key restricted
```Let us know if you connect.

---

### Post by Ultra Magnus on 2007-12-08
> What kind of wireless card do you have. 

I have an Intel PRO/Wireless 3945 card build into my laptop.
I'm using the restricted driver which ubuntu set by default

> Please try:
Code:

sudo iwconfig eth1 key restricted

Let us know if you connect.

I tried to set the key as restricted but no luck unfortunately I still had the same problem.

Incidently, I went through the Ubuntu wireless troubleshooting in the help and got up to section 3.2.5 (Check IP assignment) - I briefly tried using wcid instead of the default network manager and it always failed when it tried to aquire the IP address so I think the problem has something to do with this.

(Side Note: Also in the help in section 3.2.4 (Check for connection to the router) it said "If the ESSID for our router is shown there may be a problem with ACPI support. Boot the kernel with the pci=noacpi option." but I'm not sure how to specify boot options so I haven't tried that yet)

---

### Post by Ultra Magnus on 2007-12-09
*bump*

---

### Post by heldal on 2007-12-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-config/+bug/158045](https://bugs.launchpad.net/ubuntu/+source/network-config/+bug/158045) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				See launchpad. My experience is that the restricted (closed source) ipw3945 driver stinks. Nor is it actively developed anymore.

---

### Post by chili555 on 2007-12-09
Hmmm. One of my laptops also uses the 3945ABG card and I use the default module. It is perfectly reliable in my WEP environment. Just be sure you have the correct ESSID (we know you do from the scan result), try either "key open" or "key restricted", and you have the correct WEP key. Do you have the correct key?

I have struggled with that one myself; part of my key is BBB8B and I had a bit of trouble getting these old glasses to see if it wasn't really BB8BB!

The only thing it could be, I strongly suspect, is a glitch in the key.

---

### Post by Ultra Magnus on 2007-12-09
> This post could be related to an Ubuntu bug filed at: [https://bugs.launchpad.net/ubuntu/+s...ig/+bug/158045](https://bugs.launchpad.net/ubuntu/+s...ig/+bug/158045)
----------------------------


See launchpad. My experience is that the restricted (closed source) ipw3945 driver stinks. Nor is it actively developed anymore.

I had a look and tried out the iwl3945 driver.

I enabled it as described in comment 4 and rebooted, my wireless card is now under "wlan0_rename" instead of eth1.

Unfortunately I wasn't able to connect with this either, and It kept freezing so I tried enabling the hardware encryption but still no luck.

The WEP key is currently a 128 bit ascii passphrase ( when I type it into the terminal using iwconfig i have been using "s:passphrase" but just passphrase in the network manager) and when I type the passphrase in the network manager and then check it using iwconfig it is different.

So in answer to ...

> Hmmm. One of my laptops also uses the 3945ABG card and I use the default module. It is perfectly reliable in my WEP environment. Just be sure you have the correct ESSID (we know you do from the scan result), try either "key open" or "key restricted", and you have the correct WEP key. Do you have the correct key?

I have struggled with that one myself; part of my key is BBB8B and I had a bit of trouble getting these old glasses to see if it wasn't really BB8BB!

The only thing it could be, I strongly suspect, is a glitch in the key. 

I know exactly what the passphrase is but I suspect that I may not be entering it quite correctly.

edit: dammit I wish there was a way to disable smilies by editing - I need to be mor careful!

---

### Post by Ultra Magnus on 2007-12-09
I've tried typing my password as "128 bit passphrase" and 128 bit ascii key and with the prefix s: in the following ways

"s:password"
s:"password"
s:password

for both the proprietory driver and the opensource one and still no luck and whats more for all combinations they hex key displayed when i do an iwconfig is different.

This is the output when I do an iwconfig:

```

wlan0_rename  IEEE 802.11g  ESSID:"Derek"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:8C:D6:F0   
          Bit Rate=36 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:6E31-3637-7468-6F72-7065-7761-79
          Link Quality=65/100  Signal level=-55 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by chili555 on 2007-12-09
Hex is not ASCII. If you are trying to connect to a wireless router made in the last few years, and I think you are, because it tells us it's 802.11b *and* g capable, I would be shocked to find it uses ASCII. Not impossible, but improbable. According to *man iwconfig*, s: password is for ASCII.

Some router's configuration process allow you to generate a random WEP key. The trouble is, different router manufacturers use different algorithms to generate keys! For example, the phrase "ilovecoldbeer" will make a different key in a Linksys router than a Netopia router!

What we are looking for is the 26-character Hex key that got generated; 6E31 etc. You will probably need to see the administration pages of the router to get the right sequence.

---

### Post by Ultra Magnus on 2007-12-09
Hmmm... I know the make and model of the router - would there be any way to tell from knowing the password what the hex key that was generated is?

---

### Post by chili555 on 2007-12-09
I would suggest Googling it. You may be able to find it.

---

### Post by Ultra Magnus on 2007-12-12
Hi. I had a look and I think setting an ascii wep key means the hex wep key is a direct hex translation of the ascii key.  Also, this is what ubuntu was trying to do so I think that the key I am typing is correct but I am just unable to connect.

I managed to persuade my land lord to let m try out my wireless without the wep key and it worked perfectly! But unfortunately he insisted on turning it back on. So I know where the problem lies, but I don't really know what to do about it. 

Any suggestions? 

Thanks,

Jim

---

### Post by chili555 on 2007-12-12
> the make and model of the routerWhat is it? I'd like to take a look at the documentation on line.

---

### Post by Ultra Magnus on 2007-12-13
Hi,

The router is a: DLink DL624+A
and to reiterate my wifi card is an: Intel PRO/Wireless 3945
and I'm using the ipw3945 driver but I have tried the iwl3945 driver.

Thanks for all your help.

Jim

Edit: Also the router itself seems to be chinese (the land lord is from china)

---

### Post by pndragon on 2007-12-13
I have a similar problem. I wanted to run KDE on my laptop but kwifimanager does not support WEP 128 hexacimal passkeys. Is there a workaround for this?

---

### Post by Ultra Magnus on 2007-12-13
> **pndragon said:**
> I have a similar problem. I wanted to run KDE on my laptop but kwifimanager does not support WEP 128 hexacimal passkeys. Is there a workaround for this?

What have you tried so far?

If you have the same wireless card as me then I have read in various places that iwl3945 is a better driver but I couldn't get it to work unfortunately..

Here a how to though anyway:
[http://ubuntuforums.org/showthread.php?t=636177](http://ubuntuforums.org/showthread.php?t=636177)

Or if the problem is that you can't actually enter the password (I've never used KDE) then just go to the command line and enter:

sudo iwconfig eth1 (or whatever your wireless interface is)
sudo iwconfig eth1 essid
sudo iwconfig eth1 key "s:password"

sorry thats supposed to be "s:  password" - no spaces

---

### Post by pndragon on 2007-12-13
> If you have the same wireless card as me No... I have a Broadcom card (BCM94311MCG wlan mini-PCI). Gutsy supposedly supports this card but I ended up having to use ndiswrapper to get it to work.
> What have you tried so far?
I went with the Gnome desktop even though I am not completely happy with it because I am happy with Ubuntu.

--- Another Jim

---

### Post by pndragon on 2007-12-14
Thanks for the assist!
```
sudo aptitude install netgo
```
adds a graphical tool for working with iwconfig

---

### Post by chili555 on 2007-12-14
Here is a posting that may help us: [http://newsgroups.derkeiler.com/Archive/Alt/alt.internet.wireless/2006-06/msg01095.html](http://newsgroups.derkeiler.com/Archive/Alt/alt.internet.wireless/2006-06/msg01095.html)

I am continuing the search for the Dlink algorithm.

---

### Post by chili555 on 2007-12-14
And here is another; it's the manual for the DI-624.  [http://www.uk-bug.net/UpDownload-req-getit-lid-76.html](http://www.uk-bug.net/UpDownload-req-getit-lid-76.html) On page 15, you see that is supports HEX or ASCII but does *not* generate the HEX key with a passphrase. Finally we are getting somewhere!!!

If you have a phrase like ilovecoldbeer, it is certainly ASCII. ASCII will use any number or letter. HEX uses the characters 0123456789ABCDEF only.

Next, let's be sure we have the correct number of characters: 

# 40-or 64-bit ASCII WEP code has five characters
# 40- or 64-bit HEX WEP code has 10 characters
# 128-bit ASCII WEP code has 13 characters
# 128-bit HEX WEP code has 26 characters 

Next, try keys one through four, thus:```
sudo iwconfig eth1 key s:ilovecoldbeer [2]
```If you refer to *man iwconfig*, you will see quotes around the passphrase are not needed.

---

### Post by Ultra Magnus on 2007-12-16
Hi,

Thanks allot...

I've just tried to do what you suggested typing s:mypassword [1] -> [4] and I seem to get the same hex key for each one - I'm afraid i'v just driven the best part of 300 miles and I have work tomorrow but I'll have a look at the documentation for the router - is there anything I should note in particular?

Incidently - when trying the different keys I've been doing

sudo iwconfig eth1 essid
sudo iwcondif eth1 key s:my password [1]
sudo dhclient eth1

Is this the right kind of procedure?

I get an output which is pretty much the same each time:


```
james@HAL-9000:~$ sudo iwconfig eth1 key s:editedpassword [1]
james@HAL-9000:~$ sudo iwconfig eth1
eth1      IEEE 802.11g  ESSID:"Derek"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:8C:D6:F0   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:6E31-3637-7468-6F72-7065-7761-79   Security mode:open
          Power Management:off
          Link Quality=77/100  Signal level=-57 dBm  Noise level=-58 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:83   Missed beacon:0

james@HAL-9000:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:1b:77:37:a0:ed
Sending on   LPF/eth1/00:1b:77:37:a0:ed
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Thanks for all your help...
I'll have a look and bit of a play around tomorrow and report how it goes.

---

### Post by chili555 on 2007-12-17
> sudo iwconfig eth1 essid
sudo iwcon**fig** eth1 key s:my password [1]
sudo dhclient eth1Exactly correct.

May I assume your password has 13 characters?> documentation for the router - is there anything I should note in particular?Not really. I just pointed it out because it shows that HEX or ASCII may be used, but that a passphrase is *not* used to generate a HEX key. Since your landlord gave you a password, we must assume we are dealing with ASCII.

---

### Post by kevdog on 2007-12-17
chili -- What happened to the gorilla??

---

### Post by Ultra Magnus on 2007-12-18
> May I assume your password has 13 characters?

Yep - my password is 13 characters (alpha numeric - nothing wierd)

> Not really. I just pointed it out because it shows that HEX or ASCII may be used, but that a passphrase is *not* used to generate a HEX key. Since your landlord gave you a password, we must assume we are dealing with ASCII.

He let me have a look at the router setting page when we tried turning the WEP off, although it was mostly in chinese I think I could discern that it was an 128 bit ascii key.

In my output from iwconfig it lists the key as being a hex string - is the problem that Ubuntu is converting my password into hex before sending it off when the router is expecting a plain ascii password - (even though it seems that ubuntu is sending a pure hex translation of my password)?

Thanks,

Jim

---

### Post by gilf on 2007-12-18
> **pndragon said:**
> I have a similar problem. I wanted to run KDE on my laptop but kwifimanager does not support WEP 128 hexacimal passkeys. Is there a workaround for this?

I believe it does support 128 bit WEP (I'm assuming you are at feisty or gutsy level)

A lot of people don't understand where to enter the password and try to do in a profile manually (applies to WPA also)

In a fresh install (and you can check this with a LiveCD session) WEP and WPA passwords are entered AFTER you try to connect to a network, and then saved in the keyring (Ubuntu) or Kwallet (Kubuntu).

To initially connect to a network in a LiveCD or fresh install, don't turn off roaming or enter anything manually. Simply click on the little network  icon on the top right of the screen (Ubuntu) or bottom right of the screen (Kubuntu).

This will open out a menu of available detected networks with little bargraphs on them. Click on one of these bargraph network lines to connect. If the network requires any kind of password you will then be asked for it. Choose the right type (WPA, WEP-128, WEP-64) and then enter the password.

Keyring or Kwallet will ask you if you want to store that password for future reference. I do.

You will then be connected.

You may want to look at my post at:

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

### Post by Ultra Magnus on 2007-12-22
*bump*

---

### Post by Ultra Magnus on 2007-12-22
Ok... I'm not quite sure how but my problem seems to be fixed..

I tried doing 

```

sudo iwconfig eth1 key s:mypassword [4]

```

and it didn't work but After leaving it for a while i noticed that data was being sent over the network and I tired firefox and it worked!

Very wierd but can't complain - I still can't enter the password in network manager but anyway If anyone has a problem in the future try this.

Thanks for all the help.

Jim

---

