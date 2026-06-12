---
title: "fstab, IPTABLES, and startup applications."
date: 2009-06-08
forum: New to Ubuntu
---

### Post by furialis on 2009-06-08
1. I learned how to set up a tmpfs and add them to the fstab file to have them mounted at startup. Then I went through the file browser and found some cache folders and added them to fstab. Is there any harm in doing this?
```
none /home/myuser/.mozilla/firefox/profile.default/Cache tmpfs size=2G,nr_inodes=200k,mode=01777 0 0

none /home/myuser/.mozilla/firefox/profile.default/OfflineCache tmpfs size=2G,nr_inodes=200k,mode=01777 0 0

none /home/myuser/Desktop/MemoryHole tmpfs size=2G,nr_inodes=200k,mode=01777 0 0

none /home/myuser/.mozilla./firefox/profile.default/Cache.Trash tmpfs size=2G,nr_inodes=200k,mode=01777 0 0

none /home/myuser/.mozilla./extensions tmpfs size=2G,nr_inodes=200k,mode=01777 0 0

none /root/.cache tmpfs size=2G,nr_inodes=200k,mode=01777 0 0

none /root/.local/share/Trash tmpfs size=2G,nr_inodes=200k,mode=01777 0 0

none /home/myuser/.local/share/Trash tmpfs size=2G,nr_inodes=200k,mode=01777 0 0

none /home/myuser/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys tmpfs size=2G,nr_inodes=200k,mode=01777 0 0

none /home/myuser/.googleearth tmpfs size=2G,nr_inodes=200k,mode=01777 0 0

none /home/myuser/.cache tmpfs size=2G,nr_inodes=200k,mode=01777 0 0
```

2. Could someone show me how to add a rule to IPTABLES to drop all unsolicited requests?

3. I have truecrypt installed and I added a line to the startup applications so it would start on login. That works OK. However, it doesn't place the icon in the notification bar, it places it in the upper left hand corner of my desktop, and occasionally I get a "Truecrypt is already running" error. This doesn't happen if I start Truecrypt manually after login. Is there a way to put a delay on Truecrypt's startup?

Thanks.

---

### Post by Francewhoa on 2009-12-04
Here is a solution for the "TrueCrypt is already running" error.

STEPS 
1. Using Ubuntu Desktop LTS 8.04.x Navigate to PLACES > HOME FOLDER
2. Search for the file '.TrueCrypt-lock-yourusernamehere'
'yourusernamehere' is your Ubuntu username.
3. Delete the file '.TrueCrypt-lock-yourusernamehere'.
4. Open TrueCrypt. It can be found under APPLICATIONS > OTHERS > TRUECRYPT 

Source: [http://wiki.archlinux.org/index.php/Truecrypt#TrueCrypt_is_already_running](http://wiki.archlinux.org/index.php/Truecrypt#TrueCrypt_is_already_running)

---

