---
title: "Quickest &amp; easiest way to connect to my Ubuntu system?"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by jmc1 on 2008-10-24
Ok, here's what I would like to do: I would like to set up the system so I can easily connect to a folder on it with either Windows or Mac, with the minimum of setting up the Windows or Mac systems. In other words, I don't care how hard it is to set up but I want to connect to it quickly and easily.

What is the best approach to take?

---

### Post by Iowan on 2008-10-24
Sounds like a [Samba]("https://help.ubuntu.com/community/SettingUpSamba") server. [Here]("http://ubuntuforums.org/showthread.php?t=202605") is another good link.

---

### Post by AudioDef on 2008-10-24
What I'd like to do is mount a folder on my Ubuntu box on another linux box. But when I do

mount -t cifs //(ip)/(homedir) (mountdir)

or

mount //(ip)/(homedir) (mountdir)

I get a permission denied error.

---

### Post by Iowan on 2008-10-24
AudioDef:
You should start your own thread, but check [this ]("http://ubuntuforums.org/showthread.php?t=288534")How-To for CIFS mounting info.

---

### Post by AudioDef on 2008-10-25
Thanks Iowan. I found that page earlier but passed it over because I wanted info on connecting TO an Ubuntu machine, not from. 

However, I re-learned yet again not to take things for granted, as I found the info I needed on that page - info I already knew but needed to re-learn. 

Just do

sudo mount -t cifs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,iocharset=utf8,file_mode=0777,dir_mode=0777

And that hooks you up. I simply used an IP address instead of netbiosname.

---

