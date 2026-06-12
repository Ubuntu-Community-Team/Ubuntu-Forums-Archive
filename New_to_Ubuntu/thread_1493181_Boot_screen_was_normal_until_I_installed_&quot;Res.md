---
title: "Boot screen was normal until I installed &quot;Restricted Driver&quot; from task bar"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by iMattcotv on 2010-05-25
I was prompted to install "restricted drivers" so I went ahead and installed them.

The little icon was on the very right of the task bar and was green.
When i clicked it it told me to activate an ATI/AMD driver (I cant remember the exact name, but it had something like FTGTK or similar)

Anyway, the boot screen resolution used to be high res but now the logo is all big and blury..

Is there any way to fix this?

Thanks :)

---

### Post by iMattcotv on 2010-05-25
I forgot to mention, after the bootscreen, everything is back to the correct resolution.

I am running Ubuntu 10.04 on AMD Athlon64 IIx4 4GBram dual booting W7 64bit

---

### Post by Jose Catre-Vandis on 2010-05-25
Edit this file:
```
sudo nano (or gedit) /etc/default/grub
```
Add this to the bottom of the file:
```
GRUB_GFXPAYLOAD_LINUX=1920x1080
```
replacing your preferred resolution e.g. 1024x768 or 1280x1024 where I have 1920x1080

Run
```
sudo update-grub
```
and reboot

---

### Post by isaacj87 on 2010-05-25
Hey there,

I had this issue as well after installing my nVidia drivers. Hopefully, these instructions will get your boot screen back to normal. 

**One thing to consider**: make sure you use the right resolution size during the course of these instructions!

Here's the link, if you have any questions, feel free to ask: [Fix that ugly boot screen!]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

---

