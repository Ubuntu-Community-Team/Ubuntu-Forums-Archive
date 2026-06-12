---
title: "WPA no work"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by Don DeGregori on 2008-06-24
Used this procedure yesterday and got wifi to work , but not WPA
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
Computer is laptop Fujitsu P5010D, bcm4306 rev 02. So used step 2f and Hardy Fix.

Now I see procedure on this page, which may be different, and probably newer. Should I try it? Or is there a way to get WPA to work with the procedure I tried first.

donde

---

### Post by lisati on 2008-06-24
Have you had a look at [http://ubuntuforums.org/showthread.php?t=202834&highlight=setting+wpa](http://ubuntuforums.org/showthread.php?t=202834&highlight=setting+wpa) yet?

---

### Post by Don DeGregori on 2008-06-24
what is difference from WPA1 and WPA? I have NETGEAR router with WPA-PSK TKIP

---

### Post by jualin on 2008-06-24
Check if you have the package "Wpasupplicant" installed. Run > sudo apt-ger install wpasupplicant and try reinstalling it if you have it already. WPA1 and WPA are the same thing, they are the Encryption Protocol for your wireless network. Now the one that is different is WPA2 which is suppose to be even more secure that WPA (WPA1). According to what you showed us, you should use WPA(WPA1) to connect. Hope this helps!

---

### Post by Don DeGregori on 2008-06-24
I did this first

donde@donde-laptop:~$ sudo find / -name wpasupplicant
/usr/share/doc/wpasupplicant
find: /home/donde/.gvfs: Permission denied
/etc/network/if-down.d/wpasupplicant
/etc/network/if-post-down.d/wpasupplicant
/etc/network/if-up.d/wpasupplicant
/etc/network/if-pre-up.d/wpasupplicant
/etc/default/wpasupplicant
donde@donde-laptop:~$ 


So I guess WPA supplicant is there, but doesn't work, No encryption works fine. This Fujitsu P5010D has been a tough internal wireless nut to crack. No problem if I stick a USB TRENDnet access point in. WPA is fine. Just this darn BCM4306. At least I got this far.Don't want to try this and that now, unless it really shows why WPA is not being picked up.

I suppose I could start all over again (fresh 8.04) and try the procedure shown at top of this topic, but really there must be a better way. I could live without internal WPA, for in an outside envirnoment WPA is not necessary. Right now, it's just a challenge to get it to work. Any more ideas?
Thanks...donde

---

### Post by Don DeGregori on 2008-06-24
Sorry for double post

---

### Post by tl3000 on 2008-06-25
[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/207446)

---

