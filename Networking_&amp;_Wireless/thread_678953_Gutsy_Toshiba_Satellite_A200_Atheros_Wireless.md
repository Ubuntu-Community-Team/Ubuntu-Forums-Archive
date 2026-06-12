---
title: "Gutsy Toshiba Satellite A200 Atheros Wireless"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by einstein on 2008-01-26
Greetings;

This is, primarily, how I got wireless working on a Toshiba Satellite A200-25V.
 
I purchased a Toshiba Satellite A200-25V last week (one of only about two new laptops in town, excluding Staples, and I needed one a hurry).  Immediately discovered that Gutsy could not partition the 180 Gb disk with VISTA on it.  No problem, really, I prefer running my Ubuntu from an external USB HDD (Firelite) anyhow.

Pretty well everything, including sound, worked out of the box.  Built in webcam worked after installing Cheese.

The big, big, BIG problem was the wireless.  lspci reported an Atheros AR5006EG but it is really an AR5007EG which, for me it seems, was irrelevant.  Searched and searched the forums and could not get the thing to work.  So, given that I finally got things working after reading what seem to be a lot of very convoluted posts, decided to post what worked for me.

[LIST=1]
[*]First, get rid of a couple of modules.  Blacklist ath_pci in /etc/modprobe.d/blacklist and disable ath_hal in /etc/default/linux-restricted-modules-common. Then remove the modules.
```
echo "Blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
sudo gedit /etc/default/linux-restricted-modules-common
sudo modprobe -r ath_pci
sudo modprobe -r ath_hal
```
[*]If wifi-radar is installed, get rid of it (I used Synaptic).  wifi-radar was a massive problem in my case.  Don't know about madwifi.
[*]Get Win XP driver xp32-6.0.3.85.zip for Atheros AR5007EG at [http://www.atheros.cz/download.php?atheros=AR5007EG&system=1]("http://www.atheros.cz/download.php?atheros=AR5007EG&system=1")
[*]Install ndiswrapper and ndisgtk from Gutsy repository (I used Synaptic).  ndisgtk is not required but gives you a nice GUI interface saving opening a terminal, cding around and so on.
[*]Run ndisgtk and install XP driver.
```
sudo ndisgtk
```
Alternatively, using ndiswrapper in terminal after cding to the directory containing the driver:
```
sudo ndiswrapper -i net5416.inf
sudo ndiswrapper -m
ndiswrapper -l
```
The third line should give output showing that the driver was installed and the hardware is present.  Don't worry about ath_pci being listed as alternative - this is, apparently, irrelevant.
[*]Install wicd from wicd repository.  I have my own mirror using apt-mirror so I point /etc/apt/sources.list to my local drive but this is for those who do not do this.  See [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) for some info.
```
sudo gedit /etc/apt/sources.list
```
Add the line (substitute feisty, edgy for gutsy if you are using one of them):
> deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras 
Do
```
sudo apt-get update
```
Install wicd (I used Synaptic).
[*]Run wicd (should be in menu under Internet) and fill in the blanks in the config dialog.
[*]Reboot several times.
[/LIST]

Life should be good now.  If it is not, I have no idea what to suggest.  The Atheros wireless on the Satellite seems to act very differently from computer to computer as evidenced by all the previous posts.

wicd is what finally got things working for me.

Hope this helps someone.

Best regards,
             Dennis

---

