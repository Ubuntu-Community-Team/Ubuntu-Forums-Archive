---
title: "how to increase internet speed in karmic koala"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by vishnuscorpion on 2010-11-30
[B]hi all...
i need to increase my internet download speed in karmic koala .....anyone help me in providing the steps taken for that...will be highly appreciated

i also need to know which is the best tottent client available for ubuntu...!!
[/B]

---

### Post by mikechant on 2010-11-30
Generally speaking, the operating system does not affect your download speed - e.g. if you are running Windows, Mac OS or Linux/Ubuntu a file should take the same time to download on average.
Usually, your download speed is influenced by three main factors:

- The maximum speed allowed by your Internet Service Provider (typically fixed)
- The amount of contention with other users of your ISP (varying by time of day, day of week etc.)
- The speed of the server you are downloading from.

If you are connecting via wi-fi this can also limit your speed.

Do you have any reason to think that Ubuntu is limiting your speed instead of one these factors? For example, do you also use Windows, and get consistently faster downloads in Windows than Ubuntu?

As for bit torrent, most people will find the one that comes installed with Ubuntu - called transmisssion - acceptable, but it's very much a personal preference.

---

### Post by 00arthuryu on 2010-11-30
If you are using the default bittorrent, Ubuntu has it blocked via firewall by default. 
To change this install gufw
```
sudo apt-get install gufw
```
then go into System -> Administration -> firewall configuration -> edit 
Make sure to check the following boxes
[Allow] [In] [Program]
and change the next one to bittorrent from the dropdown box
click add and afterwards, you should see an increase in download speed
:popcorn:

---

### Post by bkratz on 2010-11-30
> **00arthuryu said:**
> If you are using the default bittorrent, Ubuntu has it blocked via firewall by default. 
To change this install gufw
```
sudo apt-get install gufw
```
then go into System -> Administration -> firewall configuration -> edit 
Make sure to check the following boxes
[Allow] [In] [Program]
and change the next one to bittorrent from the dropdown box
click add and afterwards, you should see an increase in download speed
:popcorn:

I'm just interested because I have used the default bittorrent to download all the Ubuntu versions in the past, and I have never messed with a firewall at all. Are you sure it is blocked by default?

---

### Post by 00arthuryu on 2010-11-30
Double post sorry

---

### Post by 00arthuryu on 2010-11-30
not 100% sure but I've definitely noticed a speed increase after doing so. Also by downloading a torrent with so many seeds (such as ubuntu distros) it doesn't really matter. But with other files with less seeds, the difference feels more significant.
Also I couldn't port forward without doing so.

It is also possible that enabling ufw changes some of the default settings. But to be honest, even if it doesn't block it by default its always good practice to enable it through the firewall. Whatever works for you in the end.

---

### Post by vishnuscorpion on 2010-11-30
@every one...:thanks all!!:)

---

### Post by lolpenguin on 2011-11-17
Also, I would recommend upgrading to at least Ubuntu 10.04 LTS "Lucid Lynx" as Karmic is no longer supported and that it is and Long Term Support release. (I'm pretty sure Ubuntu has told you before though.)

---

### Post by oldos2er on 2011-11-17
And with that we will say good night.

---

