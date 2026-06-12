---
title: "Feisty RT2500 ra0:avahi ??? and more.."
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Handssolow on 2007-04-23
Like others I've lost wireless with Feisty, made some progress and lost it again.

My Belkin RT2500 pci card was reported as ra0 under Edgy not wlan0 as I guess is typical with other wireless cards.

ifconfig shows
lo
ra0
ra0:avahi

Why? What is ra0:avahi and where has it come from?

iwconfig shows
lo
ra0

Network Manager still had all my settings but iwconfig showed my essid as "" and no entry for my WEP key however, my network settings from Edgy are still there in /etc/network/interfaces

sudo iwconfig ra0 essid XXXXX didn't input my essid, nothing changed.

After playing around with 

sudo /etc/init.d/networking/ interfaces stop
sudo /etc/init.d/networking/interfaces start

ra0:avahi disappeared from ifconfig
I was also able to input my essid and key with the terminal and connect to my wlan.

After a reboot I've lost wireless again, ifconfig shows ra0:avahi back and iwconfig shows no essid.

Suggestions?

---

### Post by Handssolow on 2007-04-23
Having a problem with yours RT2500 card under Feisty?  Apparently some of this was reported in Bug #78037 and prompted the suggestion that this should be fixed before Feisty was on general release. It also appears that Feisty's Network Manager doesn't work with a RT2500 chipset card?

So here's the workround I'm using but I'm having input this after every reboot.

sudo ifconfig ra0 down

sudo iwconfig ra0 essid "XXXXXXX" key XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX

sudo ifconfig ra0 up

sudo dhclient ra0 

How can my essid and key be saved?

---

### Post by Handssolow on 2007-04-28
Currently when I boot up, I can only make a wireless connection if I first open the terminal and enter
sudo ifconfig ra0 down
sudo iwconfig ra0 essid  "xxxxx" key xxxxxxxxxxxxxxxxxxxxxx 
sudo ifconfig ra0 up
sudo dhclient ra0 
as described in Launchpad Bug  #37120
I'd chosen to buy a Belkin F5D7000uk v3  (RT2500 chipset) because of the claims of its compatibility with Linux.

Following suggestions in the Forum, as an experiment I removed Network Manager and the applet and installed earlier versions. I did get a message saying that not everything could be removed. Rebooting, Update Manager now tells me that Network Manager and Network Manager Gnome needs to be updated which I am ignoring. So I was expecting that I'd be connected as with Edgy but no, ifconfig shows
lo
ra0
ra0:avahi

iwconfig shows essid "" and no WEP key. However, if I input my essid and key (as above) I can connect and now ifconfig only shows
lo
ra0

ra0:avahi has now disappeared

Any suggestions where ra0:avahi came from, why it disappeared when I connected and what it means?

---

### Post by cracker on 2007-04-28
I'm having the same problem, as posted here:
[http://ubuntuforums.org/showthread.php?t=424503](http://ubuntuforums.org/showthread.php?t=424503)

However, it's not only with my ra0 card.

---

### Post by Handssolow on 2007-04-28
I've reverted back to the latest Network Manager after I discovered that Evolution Mail's Send/Receive had become greyed out whilst I was trying an earlier version of Network Manager. oh bother.

---

### Post by haldi on 2007-05-07
I had the same problems with a linksys wlan card (RT2500).

I had to remove the networkmanager and i had to edit the file */etc/network/interfaces*

I removed the networkmanager via:
```

sudo apt-get remove --purge netwok-manager network-manager-gnome

```

and edited the file interfaces that it looks like:
```

[...]
iface ra0 inet dhcp
pre-up iwpriv ra0 set NetworkType=Infra
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid Networkname
pre-up iwpriv ra0 set WPAPSK="passphrase"
auto ra0

```

Important are the entries *pre-up ...*

With that changes I succeeded! It connects automatically at the booting to my wlan.

Good luck
Ruben M.

---

### Post by cheetaux on 2007-05-07
Ruben,
I followed you instructions and got my RT2500 card working with Fiesty.  Thanks.

Question - why was/is it necessary to remove the network-manager and network-manager-gnome?

Thanks

---

### Post by haldi on 2007-05-11
I'm not sure, but I think the network-manager doesn't support WPA yet (in combination with the RT2500).

Ruben M.

---

### Post by RavanH on 2007-07-19
> **haldi said:**
> I had the same problems with a linksys wlan card (RT2500).

I had to remove the networkmanager and i had to edit the file */etc/network/interfaces*

I removed the networkmanager via:
```

sudo apt-get remove --purge netwok-manager network-manager-gnome

```

and edited the file interfaces that it looks like:
```

[...]
iface ra0 inet dhcp
pre-up iwpriv ra0 set NetworkType=Infra
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwconfig ra0 essid Networkname
pre-up iwpriv ra0 set WPAPSK="passphrase"
auto ra0

```

Important are the entries *pre-up ...*

With that changes I succeeded! It connects automatically at the booting to my wlan.

Good luck
Ruben M.

Wow! With this methode, my Ralink RT2500 wireless connects and with Networkmonitor (not NetworkManager!) in the taskbar, I can even see signal strengh! Skype and Kopete (MSN and Jabber/GTalk) work smoothly... but strangely, I cannot browse the internet with Firefox. Amaya nor Epiphany. Not even my local network by means of IP (so it's not DNS related?)... With LAN cable connected, all is well again. Still, I'm very thrilled to get 'so close' ;) AND using WPA with RT2500.

With NetworkManager I never even got it to connect to an *un-encrypted* Wireless network. Only **Wicd** could do that for me (see [http://wicd.sourceforge.net](http://wicd.sourceforge.net)) but for some reason (never found out why) that stopped working too :(

Anyone have any idea how to get internet browsing to work? What could be causing this? Could it be that my browsers still try to connect through eth0 or even wlan0 instead of ra0 while messengers like Skype and Kopete work fine? Why can I not browse :confused:

Any hints appreciated :)

--ravan

---

### Post by imdano on 2007-07-19
> **cheetaux said:**
> Ruben,
I followed you instructions and got my RT2500 card working with Fiesty.  Thanks.

Question - why was/is it necessary to remove the network-manager and network-manager-gnome?

ThanksBecause RT* cards don't use the standard Linux methods of connecting via WPA (namely, wpa_supplicant), and instead uses the driver specific iwpriv method.  Right now no general gui network managers support that, although wicd is adding it for its next release, and have had a few people test it successfully.

---

### Post by Gruelius on 2007-07-23
Hrmm,
Im using wep and still get the same problem, im forced to use IWpriv. Rutilt doesnt work either for me, it can set the network but it cant monitor it. Im using the RT2500 drivers atm, havent tried the 2x00 drivers.


So whats the solution? wait for new drivers or use an alt app to network-manager


and if i want it to automatically connect instead of me running the script and typing in the password how would i put it into the interfaces file?

---

### Post by imdano on 2007-07-23
> **Gruelius said:**
> So whats the solution? wait for new drivers or use an alt app to network-manager
?Yep.  Or switch to the rt2x00 drivers now.

---

### Post by Gruelius on 2007-07-23
Are the drivers a bit buggy? ill grab em tonight

---

### Post by imdano on 2007-07-23
I really couldn't tell you for sure.  Their [website](http://rt2x00.serialmonkey.com) would have you believe that the default rt* drivers are the buggiest, their enhanced versions of rt* drivers are better, but the rt2x00 are best (since they support wpa_supplicant).

---

