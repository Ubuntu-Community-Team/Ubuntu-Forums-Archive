---
title: "WEP key will not save"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by gamelord12 on 2008-09-23
When connecting to my wireless router, I have to type in the WEP key every time.  It will then come up with a prompt for the super user password, and I'll type it in and hit okay, allowing it to unlock my wireless settings or something.  Then the same prompt comes up again as if I never typed in my password before.  This happens infinitely.  Why does it happen?

---

### Post by willca on 2008-09-24
Try it this way if it works for you.

edit /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
wireless-essid whateverthatis
wireless-key whateveryourkeyis

Then restart network
sudo /etc/init.d/networking restart

---

### Post by gamelord12 on 2008-09-30
Is there any way to get this feature to just work the way it's supposed to?  I'm connecting to this wireless network through my applet on my GNOME panel.  I can connect to unprotected networks just fine, but I want this thing to save WEP keys through the GUI (or at least allow me access like it's supposed to).

---

### Post by kolibri on 2008-10-01
So, I'm having this same problem, network manager allows me to connect wired, and after going through the hardy guide on this forum, I can see all the wireless networks now, and i can connect to unsecured networks, but not to anything that requires a WEP key, it just keeps 'waiting for network key' I tried the edit two posts above, but 

I just get this error:
wlan0: ERROR while getting interface flags: No such device

I can't believe this is so hard to get wireless working, I did it once 6 months ago, why can't I get it now?

---

### Post by shredder12 on 2008-10-01
hey why don't u try "wifiradar" may be it will help...

---

### Post by gamelord12 on 2008-10-08
Even with WiFi Radar, it's not automatically connecting.  Is it something wrong with the notification applet?

---

### Post by gamelord12 on 2008-10-09
Anyone?  I've installed Ubuntu plenty of times on this laptop, and it always worked until I got the 8.04 release on a fresh install.  When I used the Dell disc, this thing always worked, but I've got the Dell repositories in my list and it still doesn't work.

---

### Post by Nathan Friend on 2008-10-28
Hi all, I'm running 8.10 on a Philips Freevents laptop.  I put in the wireless key and all works OK.  But then after a restart the key is lost and I have to re-enter it.

Any ideas? :confused:

---

### Post by Nathan Friend on 2008-10-29
Bump!  Little help pleaase :KS

---

### Post by mostwanted on 2008-11-06
I have the same problem. NetworkManager queries me for my password every time I log in. I have enabled auto-login, perhaps that has something to do with it...?

---

### Post by rx7haze on 2009-02-27
I know this is an old post but was the issue ever resolved? I have the same problem with network manager not saving the wep key and i have to enter it after every reboot. Is it possible it has something to do with the keyring? After every reboot i am asked for my keyring password when evolution launches.

---

### Post by sythe on 2009-04-20
I had the same problem for a little while in 8.10 with network manager. All that I had to do was uncheck the system setting box for my wireless network and reboot. After that it works just fine everytime.

---

### Post by azotyp on 2009-04-23
[sythe]("http://ubuntuforums.org/member.php?u=194402") could you post a screen of what did you do, I have the same problem only that ubuntu is setting its own wep instead of mine im depresed need help

---

### Post by sythe on 2009-04-26
> **azotyp said:**
> [sythe]("http://ubuntuforums.org/member.php?u=194402") could you post a screen of what did you do, I have the same problem only that ubuntu is setting its own wep instead of mine im depresed need help

I can't do a screen shot since I'm not at home, but what I did is this:

Right click on the network manager applet and click edit connections. 

Then select the wireless tab and highlight your wireless network and click edit. 

At the top of the resulting window are two checkboxes which are "connect automatically" and "system setting". I had initially checked system setting when I was setting up the network and had to input my key every time. After I unchecked it I was prompted once to allow access to the keyring and since then the network has connected perfectly.

---

