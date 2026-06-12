---
title: "Restore Display Resolution settings to Xubuntu while in LiveCD session"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-12-18
I bought a 22" flat screen monitor. I plugged it in. Xubuntu found it, no problem. I tried to lower the resolution, as the screen is too big for the icons & stuff. The screen lit up a message "out of range". I could not get back to the xfce desktop.

I did a alt-sys/ctrl R E I S U B K and rebooted safely, but when I tried to log back in, all I could do was enter my password. The screen showed the (like) blue supernova swirly and then it came back asking for my password. It knows my user name.

Can this be fixed in a live CD session in Ubuntu-Karmic???

---

### Post by bodhi.zazen on 2009-12-18
You can boot to recovery mode and select xfix from the menu

You could also try moving xorg.conf

```
# mount your xubuntu partition
sudo mount /dev/sdxy /mnt

cd /mnt/etc/X11
mv xorg.conf xorg.cong.bak
```

reboot to hard drive.

---

### Post by azertyh on 2009-12-18
hi,
at the login screen, open a terminal and change the resolution in the file displays.xml at                                         &#65279;/home/user/.config/xfce4/xfconf/xfce-perchannel-xml. close terminal and log in.

this bug appears if you select other resolution supported by your graphic card.

---

### Post by SDSL on 2012-10-27
in 12.10
at login screen CTRL+ALT+F3
login with current user
then 
nano /home/user/.config/monitors.xml
and change resolution to fit your monitor correct resolution

---

### Post by howefield on 2012-10-27
Thanks.

Old thread back to sleep.

---

### Post by lisati on 2012-10-27
whoa there! The desktop environment has undergone some changes in the last three years!

Thread closed.

---

