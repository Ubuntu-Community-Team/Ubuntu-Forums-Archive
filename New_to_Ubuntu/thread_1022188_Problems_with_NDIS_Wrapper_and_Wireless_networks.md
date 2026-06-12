---
title: "Problems with NDIS Wrapper and Wireless networks"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Vendettaseve on 2008-12-26
Hey everyone.

I recently bought a Toshiba Satellite l300D-028 Pro Laptop and converted it over to the one true OS ;) lol Went very very smoothly altho I seem to be having one minor hangup, the wireless card. I have acquired the Drivers for it however they dont seem to do anything once I install them via NDISWrapper, it says the driver is functional and the hardware is detected, but still no wireless network, 

Also there is a linux version of the drivers available and I have tried that but Make and Make Install dont work :( I will post the results here.

This is the link for the Drivers. Atheros AR 9281
[http://www.atheros.cz/]("http://www.atheros.cz/")

---

### Post by rixtr66 on 2008-12-26
What version of ubuntu are you using?
im assuming you have an atheros card?
do you have build-essential installed?
I can help with this if you provide the proper information.
for madwifi drivers i recommend madwifi-hal.0.10.5.6
it works flawlessly on intrepid and hardy.
ndiswrapper does not support wpa!madwifi is better!
ive learned this from experience!
in a terminal whats the output of;
```
sudo iwconfig
```
Rick

---

### Post by Vendettaseve on 2008-12-26
IM using Hardy. I dont believe I have build Essentials installed, since I havent told it to install etc

Ah yes I had a feelng NDISWrapper wouldent work, never has for me in the past either. Here is the results from the Iwconfig you asked for. 
lo        no wireless extensions.

eth0      no wireless extensions.

I suspect that means something isnt working? Thanks.

And yes, the Atheros Card came stock on the laptop.

---

### Post by Vendettaseve on 2008-12-26
This wasnt supposed to be posted. hit refresh accidentaly pleas disregard this specific post.

---

### Post by Vendettaseve on 2008-12-26
I have installed BUild Essentials as suggested, and downloaded your recomended drivers. Everything went smooth, I browsed over to the folder they were in via terminal and hit make, everything worked etc, however I am still not able use wireless and it still says I have no wireless extensions etc. ANy help would be very appriciated.

Thanks

---

### Post by rixtr66 on 2008-12-26
ok i had the same problem.first you have to;
```
sudo modprobe ath_pci
```
then put in;
```
sudo echo ath_pci >> /etc/modules
```(if this doesnt work do it as a super user)without the sudo.
and restart.your drivers should work after restart.
the other thing is for some reason the stock network manager doesnt
support certain wpa's either.if thats the case for you then i recommend
downloading and installing wicd,as a network manager,its what i use!
make sure you download wicd first then uninstall network manager;
```
sudo apt-get remove network-manager
```
this should definately work for you,it works flawlessly for me.
wicd solved alot of problems.
good luck!
Rick:guitar:

ps i hope you did sudo make install,with the drivers?

---

