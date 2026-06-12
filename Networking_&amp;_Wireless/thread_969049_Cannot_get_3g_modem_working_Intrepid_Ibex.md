---
title: "Cannot get 3g modem working Intrepid Ibex"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by pauwl on 2008-11-03
Hi,

I'm using a (3G HSDPA)ZTE MF628 modem from KPN (Dutch provider).
If I boot with the modem connected, the network manager adds it as an option (have configured it by selected from the supplied default lists).

If I however try to connect by selecting that network, the network monitor immediately says "The network connection was disconnected".

It doesn't matter if I fill in the PIN in the configuraion or not.

Am I missing something? Do I need to configure or start some process before I can select the network?

(device itself works fine from Windows - so no errors there).

Any ideas would be really appreciated.

thanks,

Pauwl

---

### Post by STrRedWolf on 2008-11-03
I'm with you here in the USA.  I have an AT&T USBConnect 810 (aka Sierra Wireless 810 USB HSDPA modem tied to AT&T's 3G network).  Works fine in windows.  Works fine in all Ubuntu variants for 8.04 and Gentoo if you use the PPP dialer as instructed on Sierra's website (I'm using it now to post on a commuter train up to Baltimore, MD).  Fails with Network Manager and 8.10.

The syslog has some clues, but I won't be able to post them until tonight when I have a WiFi connection to the netbook (Asus EeePC 900A) that I slapped Xubuntu 8.10 on.

---

### Post by pauwl on 2008-11-03
I'm a little further now based on this bugreport:
[http://bugzilla.gnome.org/show_bug.cgi?id=558948](http://bugzilla.gnome.org/show_bug.cgi?id=558948)

It's not the same device, but is the same provide.

So now if I do:

echo "ATZ^M" > /dev/ttyUSB0
echo "AT+CPIN=0000^M" > /dev/ttyUSB0

The when I now connect via the network manager, it proceeds to ask me for a password. I type in the PIN (as already entered above), and it pauses a while - then nothing. If I type in the wrong PIN it immediately comes back to re-request.

The LED on the device also changes colour to show it has connectivity with the (public) 3G network...

<<EDIT.....>>>

Dit the ECHO commands as ROOT, and now it does show it's connected, but the LED shows GPRS only (no UMTS or HSDPA) - and cannot actualy seem to connect to internet.

---

### Post by rephreak on 2008-11-03
I have same problem with you. I'm from Indonesia, using Option Icon2 USB.
I hope someone could help me.

---

### Post by STrRedWolf on 2008-11-03
Looks like they're going to fix it at the Gnome level.

I'm more apt if they put in a universial PPP driver so we can edit the configuration of the pppd utility for each connection.

---

### Post by blackcoatman on 2008-11-07
i have the same problem with my huawei e172 modem...

Anyone resolved this? Any updated packages maybe?

---

### Post by pauwl on 2008-11-13
Right, it works for me now, but I THINK I need to drop the last ^M

so either I do:

echo "ATZ^M" > /dev/ttyUSB0
echo "AT+CPIN=0000^M" > /dev/ttyUSB0

or I do:
echo "ATZ^M" > /dev/ttyUSB0
echo "AT+CPIN=0000" > /dev/ttyUSB0

and then it works.

**NOTE: sometimes it's USB0, sometimes USB1, USB2 etc.**

**EXTRA NOTE: IT ONLY WORKS IF I BOOT WITH THE DEVICE PLUGGED IN.** Plug & Play doesn't work with the device.

---

### Post by damienduff on 2008-12-08
Hi pauwl, I just posted how i setup this modem. However, I am not using the same ISP.
Hence, just for your reference.
[http://ubuntuforums.org/showthread.php?p=6331792#post6331792](http://ubuntuforums.org/showthread.php?p=6331792#post6331792)

---

### Post by ToineM on 2008-12-12
The solution for Dummies: Disable the PIN on youre SIMcard:

I had the same problem with the Huawei E870 (KPN internetkaart 820) A
simple solution can be: remove the pin code from the SIM card. I did
this by placing the SIM card in a cellphone and in the settings menu,
disabled the pin code.
 
After removing the pin code from the sim card the modem is hot plugable! in ubuntu 8.10

---

### Post by simonbanyard on 2008-12-14
I've got a ZTE MF622 that was working fine on Intrepid without any configuration until the last kernel upgrade, which seems to have broken ***lots*** of other things too... Any ideas?

---

