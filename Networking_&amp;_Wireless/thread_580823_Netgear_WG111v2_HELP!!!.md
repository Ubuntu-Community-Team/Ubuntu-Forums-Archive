---
title: "Netgear WG111v2 HELP!!!"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by DCJoeDog on 2007-10-19
OK, I have been using Ubuntu on my laptop for over a year now and I have ot say I love it to death, but my desktop can not share in the lovin' because I use a USB wifi adaptor. Netgear's WG111v2 to be exact.

Now the native linux drivers work...... for about 5 seconds, then I have to manually re-select my network and it will work once again.....for another 5 seconds.

I followed the NDISWRAPPER route only to now have my wlan0 wireless connection not show up in the network gui at all now.

HELP!!!

---

### Post by Orvar on 2007-10-19
> **DCJoeDog said:**
> OK, I have been using Ubuntu on my laptop for over a year now and I have ot say I love it to death, but my desktop can not share in the lovin' because I use a USB wifi adaptor. Netgear's WG111v2 to be exact.

Now the native linux drivers work...... for about 5 seconds, then I have to manually re-select my network and it will work once again.....for another 5 seconds.

I followed the NDISWRAPPER route only to now have my wlan0 wireless connection not show up in the network gui at all now.

HELP!!!

**This is by far the best and most simple way to do it. NOT A SINGLE LINE OF CODE TO ENTER IN TERMINAL, not even ROOT login:**
You need:
Ubuntu 7.10. (Maybe also earlier ones, I haven´t tested.)
WPA encryption (WEP doesn´t seem to work) with a passphrase no longer than 16 letters/numbers.
The .inf-file for Windows XP that is on your Netgear CD. (/Driver/WINXP/net111v2.inf)
 
1) Have the CD in the CD compartment, and your Netgear WG111v2 plugged in.
2) From the System menu, click Administration, then the last entry: Windows Wireless Drivers.
You will be asked for your password. This is your normal password used for log-in, not any special ROOT password.
3) When the window opens, click "Install new driver". 
4) Browse to the .inf-file location on your CD. click it and choose "open" and when you get back to the previous window, "install". 

Now the installation itself is complete. And you haven´t even opened Terminal. But don´t close any window yet.

Now you must (of course) configure your network to match your wireless router. This is done by clicking "Configure network". (Surprised?)
"Hardware present" should read "Yes" and the box beside Wireless connection should be marked. If not, do so.
Double-click on "Wireless connection" (or click Properties) and...
Fill in your SSID (network name), 
choose WPA Personal, 
fill in your passphrase. 
Finally choose Automatic configuration (DHCP). Click OK. That´s all. 
No need to be a geek anymore, no code hacking in Terminal. No sudo, no ROOT login...
Best regards
/Orvar

PS -- I don´t usually visit these forums, so I will not be able to give more information about this, but it really worked perfectly for me (who is a newbie, almost) so I see no reason for it not to work for anyone else.

---

### Post by DCJoeDog on 2007-10-19
Ok, I did a fresh install of 7.10 and with the on and off internet I had I downloaded ndisgtk, along with ndiswrapper1.9 common and utils

I installed my driver from the windows inf file and it shows up as driver installed and hardware present

but it refuses to use that driver, it keeps using rtl8187 and I even blacklisted it just to be sure, along with all the other recommended drivers to blacklist

I feel I am so close to fixing this problem, I just want to use Ubuntu but I need internet to make the final transition

EDIT:
I just want to clarify where I see rtl8187 driver in use, I see it in "Connection information" when I right-click the network icon by the clock on the top taskbar

---

### Post by DCJoeDog on 2007-10-20
please help :(

---

### Post by DCJoeDog on 2007-10-20
ok, where is rtl8187 on my system so I can erase it, because this is just getting ridiculous

---

### Post by DCJoeDog on 2007-10-22
please help. ndiswrapper doesn't seem to want to bother loading, and my wi-fi continues to use rtl8187 driver,and it is blacklisted.

I know someone can help me.

---

### Post by DCJoeDog on 2007-10-22
so much for the myth of Ubuntu having the best community of users helping each other out.

I will figure this out, and the rest of you can go to hell.

Sorry it had to be like this but no one wants to step up and give an answer, and I know someone out there knows the answer, but whatever.

I hope you all feel proud of yourselves, I did as much as possible on my own and ONLY then did I make this topic, which is the number one complain on all forums, laziness. I made the topic of of frustration, but seems no one can spare a few minutes to type out an reply for me, so, as said before, go to hell.

Thanks and bye.

I will most likely get modded, but at this point I don't care, you all obviously don't.

---

### Post by sennep on 2007-10-28
A bit frustrated are we?

In the terminal, type:
```
lsmod
```

is the rtl8187 driver listed?


Have you tried installing the win98 driver without using ndisgtk? Some say ndisgtk is bugged, and that you should try to do it using the terminal instead..

---

### Post by wirelessmonkey on 2007-10-28
sudo rmmod rtl8187


this will unload the module. 


Best of luck.

---

