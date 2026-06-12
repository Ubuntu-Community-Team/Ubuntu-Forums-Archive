---
title: "Wireless config (wep key)"
date: 2005-04-14
forum: Networking &amp; Wireless
---

### Post by blackspawn on 2005-04-14
Hello, I recently installed Ubuntu on my asus laptop (M6N model) and let just say Ubuntu is the best distro I've ever tried (I've used RH 9, fedora, mandrake...). Everything was up and running after install, well almost everyting. I'm having a bit of trouble setting up a wireless connection in my Univ campus.
I've figured out how to change the username and SSID but I'm don't know what to put in the WEP key area.
In WinXP I enable WEP but I have "The key is provided to me automatically" checked. Is this the "managed" mode in linux? what configurations do I need to do in iwconfig?
My authentication in Windows is PEAP where do I configure this in Ubuntu?
Also I need to enter a password when connecting (I assume a prompt will come up when  trying to connect...)

Thanks in advance and congrats for a great distro  :wink:

---

### Post by ganatronic on 2005-04-14
I was having trouble with that also. I was adding the WEP key under the network settings (system > something > network ...I'm on a windows work box right now, not remembering all the details), under the network profile for my wireless. That wasn't working, however, and dhclient was instead connecting me to my neighbor's crappy wireless. I then read that WEP should be added in hex, and if you don't know hex you should just prefix the key with "s:" Didn't make a difference still.

So, I installed this nifty detection device [http://sourceforge.net/projects/gtkwifi/](http://sourceforge.net/projects/gtkwifi/) that someone on these forums created. It works great. It shows you the available signals, and then you can highlight one and then connect. You'll be prompted for a key if it's needed.

If you want to add a key in iwconfig, you can do it with "sudo iwconfig ra0 key xxxwhateverxxx"

But so far I've had the most success with this gtkwifi device. It also seems like it will be helpful when traveling.

gtkwifi thread - [http://www.ubuntuforums.org/showthread.php?t=18466](http://www.ubuntuforums.org/showthread.php?t=18466)


I hope this helps.

---

### Post by blackspawn on 2005-04-15
Yes I know how to enter a wep key the problem is that judging by my windows config, I think I'm not supposed to enter a key (although wep is enabled, the key is given to me by the network). In order to connect I had to register my MAC so I guess the network recognizes the MAC adress and gives me a wep key?... I know some basics of this but not enough i guess  :? 

Thx I'm gonna try that app see if I can figure this out.

---

