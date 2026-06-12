---
title: "smb mounts work when done manually, but not when done at boot up"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by phile on 2007-07-10
I'm having trouble getting ubuntu to automatically mount a NAS share at boot up. It works beautifully if I issue the following manually:
```
sudo mount -t cifs //ip-address/share /media/NAS -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
```
The drive pops up on the desktop and it's all super.

Unfortunately, when I try to get it to mount automatically at boot, it just doesn't work. I've added the following line to /etc/fstab:
```

//ip-address/share /media/NAS cifs credentials=/etc/.smbcredentials,file_mode=0777,dir_mode=0777 0 0
```
and created the .smbcredentials file, which contains:
```
username=*****
password=*****
```
(obviously, the un & pw are correct - not stars)

But on boot, I get no drive on the desktop, and issuing
```
sudo mount -a
```
in terminal results in a flashing cursor and nothing else (not even any network activity, if the lights on the front of my router are to be believed). I have to ctrl-c to get the prompt back.

I have put the .smbcredentials file in several different places (/home, /root, /etc) all with the same results.

Clearly, the share does work - I can do it manually - so the problem would seem to be with the credentials file? Can anyone suggest how I can sort this out? (if it's complicated, then step-by-step instructions would be great - I'm a bit new at this).

Cheers,

Phil

---

### Post by strangeion on 2007-07-18
You may want to put your credentials file in your home folder. By putting it in etc, you're making it readable by any user. Place it in your home folder and give it permissions of 600.

```
chmod 600 .smbcredentials
```

One other thing to check is if you have smbfs installed.

```
sudo apt-get install smbfs
```

Furthermore, check your syslog and see if there are any errors related to SMB.

---

