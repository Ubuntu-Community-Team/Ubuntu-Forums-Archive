---
title: "Intel 2200BG on Gusty - still can't do wifi"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by JoJerome on 2007-10-20
I hope I'm not treading any protocol here. Started my quest for help in 
[http://ubuntuforums.org/showthread.php?t=580009](http://ubuntuforums.org/showthread.php?t=580009)
But much has changed, including my upgrade to 7.10 so I thought I'd start over with a more descriptive title. 

Following kevdog's instructions in
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
Very easy to follow by the way. :)

ndiswrapper appeared to install smoothly. 
ndiswrapper -l tells me the driver is installed and device present.
lspci lists the correct hardware.

Where I got stuck (same place I got stuck when doing this in Feisty) is re-associating the name from eth1 to wlan0.

In kevdog's directions, my snag appears to be in running;
gksu gedit /etc/iftab
A pop-up window asks for a password, I enter it, and nothing appears to happen.

~$ less /etc/iftab
/etc/iftab: No such file or directory 

I'm guessing this is why when I follow the instructions to edit /etc/iftab, there is no change. The wireless device is still named eth1 and still not up and running.

On the downside, this install I told my friend would take an hour is now into week 2. On the upside, I'm getting a refresher course in my tiny bit of shell command knowledge from once upon a time...

Suggestions? Help? Advice? Rescue?

- Jo

---

### Post by JoJerome on 2007-10-20
P.S.; In System Settings -> Network Settings it shows eth1 as an enabled wireless device. Although the last time I was in a wifi hotspot it also showed this but I still couldn't connect.

Is it possible I just need to configure something from there?

Hopefully these questions aren't too eye-rollingly newbie. I'm horribly wifi illiterate, mostly because I'm too poor to have such niftyness of my own.

- Jo

---

