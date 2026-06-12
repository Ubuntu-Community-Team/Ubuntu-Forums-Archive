---
title: "Run 'Samba' from Usb? But cant login again after install... please help!"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by Suitsuke on 2011-05-26
I'm about to cut my laptop in half..

I don't want to install ubuntu yet, I just want to run it from a usb so I can share files over an ethernet connection to a windows 7 computer using the 'Samba' on ubuntu.

Ubuntu doesn't ship with Samba so I needed to install it from the internet, it told me to restart my session and I have no idea what the login credentials are now... I've tried everything. So I'm stuck there.. I just keep getting authentication failure.

Is there an easy way to do what I am doing? I have about 500GB I need to transfer to another computer, all of it is sensitive data and I've had to hard reset my computer at least 30 times... I'm starting to get scared that the sudden stops to my hard drive are going to cause faults..

Please help..

---

### Post by prshah on 2011-05-26
> **Suitsuke said:**
> I just want to run it from a usb so I can share files over an ethernet connection to a windows 7 computer using the 'Samba' on ubuntu.

Installing samba requires your user to be added to the "samba" (pre 10.10) or "sambashare" group. While this is done (usually) automatically by installing samba, a logout/login or reboot is required for the new permissions to take effect.

If you reboot, all changes are lost unless you have specifically created a live USB with "persistence" (casper). Please advise if you have done this, or, if you have no idea, please tell how you have created the live USB.

If you choose to logoff, then you cannot login again, since the credentials are not known (prior to 9.10, the user/password was ubuntu/demo).

Currently, the username is probably ubuntu (note case) and password is blank.

---

