---
title: "Printer Problems"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by dre3 on 2010-12-17
I have two ubuntu cpu, desktop and laptop with the printer via usb on desktop.  Everything was fine until i change the printer name and forgot to set-up the laptop with the same name, and i try to print a page and now the program is just hanging the printing app is gone from the admin tab and when i open the print i get:  Connecting to printer..;Print (printer name) may not be connected   Please any help would be appreciative, I just got finish (great big headache) with samba and file sharing and solve that issue by going with sshfs, so if i can get this back everything will be so gravy.  Thanks

---

### Post by cariboo on 2010-12-17
What happens if you change the printer name back to what it was

---

### Post by dre3 on 2010-12-17
Same results,  it's still hanging.

---

### Post by Morbius1 on 2010-12-17
What's not clear in your post is if you just did this or if it does this after a reboot. It's also not clear if you're using samba as a pass-though to cups or if you are connecting to cups directly. If you're using samba then restart the samba service so it can acquire the new printer name:
```
sudo service smbd restart
```

---

### Post by dre3 on 2010-12-17
I believe (not to sure the LPD PORT 660) way.

---

