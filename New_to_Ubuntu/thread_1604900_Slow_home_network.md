---
title: "Slow home network"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by baldy4eva on 2010-10-24
Further to this thread [http://ubuntuforums.org/showthread.php?t=1604180](http://ubuntuforums.org/showthread.php?t=1604180)  
Although I can copy and paste to and from my windows shares, they're painfully slow. An 80 meg folder takes approximately 20 minutes to copy over to my Ubuntu box. The same folder copied to/from one of my win boxes takes a couple of minutes.Any clues? Thanks in advance

---

### Post by luvshines on 2010-10-24
I too am looking for some solution :(
[http://ubuntuforums.org/showthread.php?t=1592389](http://ubuntuforums.org/showthread.php?t=1592389)

---

### Post by baldy4eva on 2010-10-24
I haven't installed samba yet, just nautilus-share. Do you think samba will help?

---

### Post by SpockVulcan on 2010-10-24
Yes Samba should help

---

### Post by baldy4eva on 2010-10-24
I'm also getting connection timed out messages when copying files across... weird!

---

### Post by baldy4eva on 2010-10-24
So I'd just do a ```
sudo apt-get install samba
``` or is there anything else I'd need?

---

### Post by Morbius1 on 2010-10-24
Nautilus-share is samba. If you've used it you already have samba installed.
[B][COLOR=Blue]
EDIT:[/COLOR][/B] Samba itself calls it usershare. Nautilus-share is a package that allows the user to create samba usershares directly from Nautilus.
From: [http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)
> USERSHARES

Starting with Samba version 3.0.23 the capability for non-root users to add, modify, and delete their own share definitions has been added. This capability is called usershares and is controlled by a set of parameters in the [global] section of the smb.conf.

---

### Post by Morbius1 on 2010-10-24
I re-read your original post. Your time delays are when accessing Windows shares. Samba is used to create shares on Linux for Windows to access not the other way around. Samba itself won't help you with your problem unless for some reason it's faster for the Windows user to "push" the file to the Linux share that it is for Linux user to "pull" the file from Windows share.

---

### Post by baldy4eva on 2010-10-24
Yeah, I've noticed as I've tried both ways of getting the files, pushing and pulling. After installing samba, there seems to be no difference when pulling the files across with Linux... Ah well

---

### Post by baldy4eva on 2010-10-25
After figuring out my wireless connection problem [http://ubuntuforums.org/showthread.php?t=1604665](http://ubuntuforums.org/showthread.php?t=1604665) my network speed has increased significantly. I think that eth0 and wlan0 have been messing about with each other, and the data packets are trying to go to both mac addresses or something... But, anyway... sorted now!

---

