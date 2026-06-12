---
title: "NDISWrapper problem"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Creadak on 2009-02-17
Hey all, new to the forums :D.

Uh, I recently dual-booted my Toshiba Equium L10 with Ubuntu and the wireless drivers don't work and Linux variants don't exist so I have to use the NDISWrapper. I have the WINXP drivers for the card (an InnProComm IPN2220 model)

I've looked it up again and again but I can't seem to get the DISWrapper installed :/ Any suggestions?

It'd be brilliant if I could get the wireless up and running as I really like ubuntu :/

Craig

---

### Post by adult swim on 2009-02-17
hey ive searched the internet for your problem and i found this website
[http://sicksand.net/post/32208741/inprocomm-ipn-2220-wireless-lan-adapter-problem-in](http://sicksand.net/post/32208741/inprocomm-ipn-2220-wireless-lan-adapter-problem-in) which has a solution.  below ill make those instructions easier.

first go to this webpage [http://driverscollection.com/?file_id=32880](http://driverscollection.com/?file_id=32880) and scroll down to the bottom.  enter in the captcha thing and click to download the file.  once it is done downloading, put the file into your home folder (which you can access by clicking on Places>Home Folder.)  Once that file is in your home folder, right click on it and select 'Extract Here'  when it finishes extracting, open up a terminal (Applications>Accessories>Terminal) and you will want to enter in these commands one at a time.
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
``` after you type that in, hit enter, type in your password, and hit enter again.  it will ask if you want to install, youll need to hit y and enter.  when that finishes up, youll need to enter in, (it may be easier to copy this and paste it into your terminal) ```
sudo ndiswrapper -i wlesslan-sl10-xp-303112004135/Winxp/neti2220.inf
```  now to test if it worked enter in ```
ndiswrapper -l
``` that is a lower case L, not a one.  if it returns something along the lines of ```
neti2220 : driver installed

device 17FE:2220 present
``` then it worked!  to get it up and running youll need to run these commands one at a time ```
sudo depmod -a

sudo modprobe ndiswrapper

gksudo gedit /etc/modules
``` that last command you entered in will open up a file.  you need to scroll to the bottom of that file and add a new line that says ```
ndiswrapper
```  once you have done that save the file and close it.  now go up to your internet icon in the taskbar and try to connect.  good luck!

---

