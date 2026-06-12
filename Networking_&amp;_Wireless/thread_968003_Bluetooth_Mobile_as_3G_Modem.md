---
title: "Bluetooth Mobile as 3G Modem"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by Boffy on 2008-11-02
I have my phone connected to my 8.10 box and I've set up the mobile broadband connection. How do I get it to actually connect to the internet using the phone as a modem?

Cheers

---

### Post by and.duncan on 2008-11-04
> **Boffy said:**
> I have my phone connected to my 8.10 box and I've set up the mobile broadband connection. How do I get it to actually connect to the internet using the phone as a modem?

Cheers

Does this mean you have paired it using the bluetooth applet and found the 3G entry relevant to your provider in the network manager?

(I'm actually stuck after this point too!) Awaiting some kind soul with a useful reply :)

Also, is it just me or does that 'connect' button in the bluetooth preferences not do anything?

---

### Post by Xepra on 2008-11-04
I too have gotten this far, but haven't been able to connect.  I actually had the same problem with trying through USB.

Since it is a Windows Mobile phone there are a couple USB profiles - the Active_RNDIS automatically creates an ethernet device which shows up in the network applet, but it just shows a self-assigned ip and does not get internet.  I tried enabling internet connection sharing on the phone but couldn't do it.

In the past I've used wvdial and ttyACM0 (usb DUN profile) and rfcomm0 (bt DUN profile) to connect which works just fine, but I was looking forward to it being automatically configured and having a gui.

It looks like once you configure the Mobile Broadband Connection that it is supposed to show up on the left-click network applet menu, but mine, at least, is not doing this.

---

### Post by jdos2 on 2008-11-05
I had to install the reverted bluez package to get the pand utility back- there are no instructions anywhere that I can find to get my Thinkpad to connect to my AT&T Tilt that pertain to the default package installation with Ubuntu 8.10.

If you can get the phone to share Internet via PAN, you might well have better luck as I did. Otherwise, someone is going to have to Really Document the procedure for PPP connections over Bluetooth in a way that actually (or "just", as Ubuntu is supposed to be known for) works.

I was lucky- my phone isn't my only Internet connection. Imagine those poor souls that had to go find a wire when they found out that their Bluetooth functionality had been ripped out of the OS with no explanation.

---

### Post by Hobgoblin on 2008-11-05
[This of any use?](https://help.ubuntu.com/community/BluetoothDialup)

I found you only need to do the Pairing and Configuring the rfcomm device sections then install Gnome PPP, type /dev/rfcomm0 in as the modem, *99# as the number and your provider's user and password for the internet apn.

Since it's not using network manager, Firefox doesn't know you have an internet connection so needs to be put in online mode manually (you can add a toolbar button for it).

---

### Post by geyids on 2008-11-06
What about sharing the connection to other PC's

---

### Post by SeanBlader on 2008-11-06
> **Hobgoblin said:**
> [This of any use?](https://help.ubuntu.com/community/BluetoothDialup)

I found you only need to do the Pairing and Configuring the rfcomm device sections then install Gnome PPP, type /dev/rfcomm0 in as the modem, *99# as the number and your provider's user and password for the internet apn.

Since it's not using network manager, Firefox doesn't know you have an internet connection so needs to be put in online mode manually (you can add a toolbar button for it).

Unfortunately the whole point of the Network Manager Applet 0.7 was to allow you to use it to connect via mobile 3G and avoid the series of configs necessary used in dial up networking. On the other side though, I did have bluetooth dun working before I upgraded to ibex, which killed it and now without an unencrypted wifi connection, or a wire, I have no network. So far network manager 0.65 performed better in that I could connect to an encrypted wifi access point.

---

### Post by Hobgoblin on 2008-11-06
> **SeanBlader said:**
> Unfortunately the whole point of the Network Manager Applet 0.7 was to allow you to use it to connect via mobile 3G and avoid the series of configs necessary used in dial up networking.

Well it does work for me using a USB cable, it's the bluetooth side of things which isn't.

But it's come a long way since I first tried bluetooth with Ubuntu so hopefully it's only a release or two away.

---

### Post by ubiwan on 2008-11-08
I too am having the same problem I can connect without any problems when the phone is connected via USB cable but not via Bluetooth. I hope this problem will be sorted out soon.

---

### Post by aba_ec on 2008-11-09
The same for me.  Nokia 6120 3G not working as a bluetooth modem.  I'm using gnome-ppp to use GPRS/3G.  Anyone knows a workaround?

---

### Post by socceroos on 2008-11-10
Unfortunately, Network Manager does not yet support connecting to 3G networks through bluetooth devices (like mobile phones). This feature is expected to be added in the near future.

In the meantime, we all have to put up with using the USB cable for our phones. If you *need* bluetooth 3G, then follow the guide linked in the previous post - it requires manual set-up.

Here is the discussion on Launchpad regarding this issue: [https://bugs.launchpad.net/network-manager/+bug/269329](https://bugs.launchpad.net/network-manager/+bug/269329)

---

### Post by shinoj on 2008-11-11
i too found that ubuntu 8.10 does not provide a gui. you have to manually configure it. follow this link to set up a rfcomm modem.
[http://www.thinkdigit.com/forum/showthread.php?t=73530](http://www.thinkdigit.com/forum/showthread.php?t=73530)
change your the settings according your service provider.

and to connect net, issue the command with root privileges. 
issue the command sudo pon airtel
or
sudo pppd call airtel
 
this works

---

### Post by tanere on 2008-11-20
Hi,

I have posted a guide on my blog for connecting my Nokia N95 and Asus EEE PC 901 to the Internet using Blueman Bluetooth Manager on Ubuntu 8.10 Intrepid.

This should work for any BT enabled phone & computer. I have previously used Gnome PPP, which is somewhat problematic but this solution for Intrepid is working very good.

[http://tanere.blogspot.com/2008/11/mobile-broadband-over-bluetooth-on.html](http://tanere.blogspot.com/2008/11/mobile-broadband-over-bluetooth-on.html)

I hope it helps.

Regards,
Emir

---

### Post by Zeedok on 2008-11-20
I have followed your guide and successfully bonded my phone to my laptop.  I have set-up the 3G network, but when I try to connect to it, I get a password prompt.  The only problem is, I don't have a password.  I have a PIN code for my phone service (which doesn't work), but under the Access Point definitions on my phone the username and password fields are empty.

Any idea how to resolve this?

---

### Post by tanere on 2008-11-20
> **Zeedok said:**
> I have followed your guide and successfully bonded my phone to my laptop.  I have set-up the 3G network, but when I try to connect to it, I get a password prompt.  The only problem is, I don't have a password.  I have a PIN code for my phone service (which doesn't work), but under the Access Point definitions on my phone the username and password fields are empty.

Any idea how to resolve this?
The user / password combination should be dependant on your mobile operator.

try that web page, choose your country;
[http://www.unlocks.co.uk/gprs_settings.php](http://www.unlocks.co.uk/gprs_settings.php)

If these dont work, try blank user / password, it worked for me.

---

### Post by gabor111 on 2008-11-21
> **tanere said:**
> Hi,

I have posted a guide on my blog for connecting my Nokia N95 and Asus EEE PC 901 to the Internet using Blueman Bluetooth Manager on Ubuntu 8.10 Intrepid.

This should work for any BT enabled phone & computer. I have previously used Gnome PPP, which is somewhat problematic but this solution for Intrepid is working very good.

[http://tanere.blogspot.com/2008/11/mobile-broadband-over-bluetooth-on.html](http://tanere.blogspot.com/2008/11/mobile-broadband-over-bluetooth-on.html)

I hope it helps.

Regards,
Emir

It's working fine for me, on my eeePC 901 with intrepid, and Nokia E51. :guitar:

But I can't disconect from the menu in the network manageer icon in the system tray. I have to disconect from the phone by long-pressing the red button... :confused:
But it's very well comparing to connect with USB cable... :KS

And an other question: ho can I do to start blueman on boot???

---

### Post by tanere on 2008-11-21
Hi,

For autostart of any program:
Click Menu -> System -> Preferences -> Session
Select Startup Programs tab
Click Add

Name: Blueman Bluetooth Manager (or anything you like)
Command: blueman
Comment: (anything you like)

For disconnecting:
N95 is known for its weak battery, to save power I do not keep BT on if I am not using it. I have a shortcut for turning the BT on and off. So I do turn bluetooth off in the phone, which effectively disconnects me. :)

---

### Post by gabor111 on 2008-11-22
Thank you, it'sworking fine on boot now.:guitar:

Concerning the E51, I have bloetooth always on, because of using BT headset.:-$
Disconnecting with the red button on the phone is not a big problem, but it may more elegand to disconect from the NM aplet...:confused:
Anyone have ideas?

---

### Post by chilskater on 2011-05-15
anyupdate from this?i try to follow available steps butfailed to connect to internet via bluetooth to my hset..i can connect from laptop to hset but i didnt see any Mobile Internet at network manager..i have already add Mobile internet in the settings..

---

