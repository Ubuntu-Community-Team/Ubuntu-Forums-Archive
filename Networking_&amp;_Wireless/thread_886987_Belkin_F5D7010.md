---
title: "Belkin F5D7010"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by 2j4ez on 2008-08-11
Hello i wonder if someone can help me please

Ive just got a BELKIN F5D7010 pcmcia network card,Ive plugged it in to my thinkpad r40E and it can see wireless networks but i cannot connect to them.

If i click my home wireless network and type my network key it says its connected.

Firefox just says cannot find page if i plug in my ethernet cable i get internet 

Clicking the wireless bar icon says i am connected but i'm not!
Ive been searching google,these forums but noting seems to be coming up

Do i need to install a driver for this card to make it connect??

Please help thanks

---

### Post by Crafty Kisses on 2008-08-11
For this card I believe you're going to have to use a ndiswrapper.

First go to the Realtek website and look for the drivers [http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/) and search for 8185, make sure the card is inserted before following my instructions.

After you have the driver downloaded, unzip it then do the following:
```
sudo ndiswrapper -m
```
That will add the alias to ndiswrapper under wlan0.

Then run:
```
sudo ndiswrapper -i net8185.inf
```
This copies the driver files to the **/etc/ndiswrapper** directory and makes them usable for the ndiswrapper.

After you do that, do the following:
```
sudo ndiswrapper -a 1799:701f net8185
```
This tells ndiswrapper to use the net8185 driver you just installed with your wireless card.

After you have told the ndiswrapper where to look, do the following:
```
sudo modprobe ndiswrapper
```
This will load the ndiswrapper module to get the Belkin card up and running.

```
sudo -i
echo ndiswrapper >> /etc/modules
```

Once these commands have been run, you should be able to use NetworkManager to configure the card and what not.

---

### Post by 2j4ez on 2008-08-12
I type SUDO NDISWRAPPER -M and i get no ndiswrapper found so i installed ndiswrapper retyped it and got

WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'e'
WARNING: /etc/modprobe.d/blacklist line 43: ignoring bad line starting with 'ndiswrapper'
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

any ideas?

---

### Post by muckngrind on 2008-08-13
Try this:
sudo apt-get install b43-fwcutter

Choose to download firmware when prompted.

More instructions are here:
[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware]("http://linuxwireless.org/en/users/Drivers/b43#devicefirmware")

---

### Post by giancast on 2008-10-06
I am in the same situation. I have a Belkin F5Dn010 v3001, I had it working with Xubuntu for a while and then it stopped working. I think that it has something to do with Ubuntu v8.4. Well my hard drive died so I had to reinstall and here I am again with a dead wireless. Wired works fine. The driver for this card is RT2500 (I have the CD) so after the install the card lights worked, it saw my network, then I entered the password and nothing, no connection. Then I installed ndiswrapper and now the card lights do not come on at all. The network interface now does not see my network at all. When I do lspci I get the following:01.00.0 Network Controller:RaLink RT2500 802.11g CardBus/mini-PCI (REV01). Any help will be appreciated. I am at a loss here. Thanks.

---

### Post by burneverything on 2008-11-11
After trawling the forum and reading many tutorials I followed the informations for "ubuntu (all flavours) on that page:
[http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation](http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation)
and it worked fine for my belkin 7010 rev:1100
on xubuntu 8.04

---

### Post by krownty on 2012-10-03
[COLOR="Navy"]Hello people!

I checked this forum because I have a **Belkin F5D7010** wireless card **ver.3000tt** (at least that's what the label say) I need that card for a Dell latitude C840 with Xubuntu 12.04 Pangolin, I tried the @muckngrind command with a modification that I found in [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access").
"***_sudo apt-get install b43-fwcutter firmware-b43-installer_***" and now my card is running.
Thanks you for your post.
On purpose, I found previous page on [http://linuxwireless.org/en/users/Drivers/b43#Caveats]("http://linuxwireless.org/en/users/Drivers/b43#Caveats") where driver's info is very specific for me.
Greetings from Mexico.[/COLOR]:guitar:

---

