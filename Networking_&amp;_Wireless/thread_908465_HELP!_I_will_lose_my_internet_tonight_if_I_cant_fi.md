---
title: "HELP! I will lose my internet tonight if I cant figure this out!"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by matdombrock on 2008-09-02
I am using Ndiswrapper with the bcmwl5 driver from dell on my iMac. I cannot get it to connect to my wireless network unless it's open. When it has WPA or WEP on it I cannot connect. NM-applet just keeps asking my for the network key over and over. 

I really need some help. If I don't get this working before my dad gets home I loose my internet because "If we leave the network open people will hack into to [his] bank account". I really don't want to be using Mac or Windows tonight.

Sorry if this is the wrong forum. I will move it if i have to but I really need help.

Thanks!:)

---

### Post by caljohnsmith on 2008-09-02
Just as a basic check, have you blacklisted all the other broadcom drivers in /etc/modprobe.d/blacklist so you are sure you are using ndiswrapper? Also, if you do:
```
lsmod | grep 43
```
Does it return anything? 

With WPA/WEP, have you tried a really simple pass phrase first, like "test" or similar? If that still doesn't work, you might have more success using the ["WICD"]("http://wicd.soureforge.net") network manager rather than Gnome's network manager. Let me know how it goes.

---

### Post by LittleKoy on 2008-09-02
Same here if I try to set a static IP... Did you try wicd?

---

### Post by james_vanb on 2008-09-02
Not sure this works with WPA, but if the router is set to WEP, Try this to get connected - When you boot and the network manager is looking for a connection in roaming mode - Open a terminal and run the following:

```
sudo iwconfig wlan0 key "hex key"
```

Where "hex key" is the key for your router. See if that at least gets a connection.

---

### Post by matdombrock on 2008-09-02
Ok, first off, thanks for the help.
And soncondly here is what i get when i run "lsmod | grep 43"
```

mat@mat-desktop:~$ lsmod | grep 43
scsi_mod              151436  5 sbp2,sg,sd_mod,sr_mod,libata
```

I will also try wicd in a while.

---

### Post by matdombrock on 2008-09-02
Wicd works but I am yet to try connecting to wpa, i have to wait til my dad goes to bed so i can mess with the router.

---

