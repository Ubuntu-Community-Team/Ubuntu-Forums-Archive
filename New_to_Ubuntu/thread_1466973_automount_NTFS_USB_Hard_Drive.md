---
title: "automount NTFS USB Hard Drive"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by hellomoto on 2010-04-30
Just upgraded to lucid 10.04 on my desktop and laptop. 

can anyone explain why my NTFS eternal hard disk will auto mount on my laptop running lucid but not on my desktop (it shows up on my desktop computer under places menu but I have to click the hard disk icon to mount it)

both clean installs. 

thankyou in advance

---

### Post by psusi on 2010-04-30
Let me guess.  You are connecting it to the laptop with usb, but using esata on the desktop?

---

### Post by hellomoto on 2010-04-30
no, USB cable to connect to  laptop and desktop

---

### Post by wookiefoot on 2010-04-30
Do you have an entry for the drive in /etc/fstab on your desktop?

If you had the drive plugged into your laptop while installing it mad have added an fstab entry for you.

---

### Post by hellomoto on 2010-05-01
i tired manually adding an entry in fstab but it didn't work, i got an error message, both fstab files appear to be the same

---

