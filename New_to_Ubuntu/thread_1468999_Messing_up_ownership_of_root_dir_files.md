---
title: "Messing up ownership of root dir files"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by karatedog on 2010-05-01
I use: Ubuntu 9.10(32 bit), GNOME

I was mounting an USB ext2 hdd, then I realized it is not writable until I own the drive's root directory. But somehow my mind slipped, and I issued:
```
sudo chown -R myuser:myuser /
```

Uhh-ohh. Although I quickly pressed Ctrl+C a few of my root folders were already overwritten from root:root to myuser:myuser :(
Then I tried to write back everything - that has been overwritten - to root:root then I restarted my system. Of course not everything is working.

The worst symptom is that nm-applet now won't load by normal user, it throws an error:
Error: (9) Connection: ":1.1551" is not allowed to own the service "org.freedesktop.NetworkManagerUserSetting" due to security policies in the configuration file.

A less worse symptom is that Shutdown, Restart options disappeared, only Log-Out appears when I click on the main Gnome menu.
I would prefer not to reinstall the whole systems, anybody has this kind of "experience"?
I have a virtual Ubuntu 64bit on my Windows, I tried to check line-by-line the directories and files, but the ownerships seem similar.

Others:
- Bluetooth now cannot be disabled from taskbar icon, the "Turn off" function is missing
- Battery icon changed (huhh?)

Can it be something to do with suid bits? (Changing ownership surely destroyed those)

Thanks.

---

### Post by karatedog on 2010-05-02
Looks like problem is solved :guitar:

As Suspend, and Hibernate went missing, I tried to force it manually by sending DBUS messages, and they always failed.
So I reinstalled 'dbus' with Synaptic, then lo and behold, everything popped back into production (Bluetooth icon, restart now works, even suspend&hibernate as well), the most important achievement that I got back Wi-Fi.

Perhaps in time with enough collected knowledge I can decipher what just happened.

---

