---
title: "NetworkManager Applet after waking from sleep????"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by rookworm on 2009-01-26
whenever I wake my comp from sleeping, NetworkManager Applet does not pick up any new wireless access points, and moreover, it cannot connect back to the network it was connected to before sleeping....

*** Is there some sort of option that I don't know about that can fix this?

*** Barring that, how do I restart just the NetworkManager Applet without rebooting the whole system?

---

### Post by gn2 on 2009-01-26
Do you have a Fn button or a switch to turn wireless back on?

Have you tried [Wicd]("http://wicd.sourceforge.net/") instead of Network Manager?

---

### Post by rookworm on 2009-01-26
enabling and disabling wireless does nothing.

how do you restart networkmanager?

---

### Post by plucky on 2009-01-26
> how do you restart networkmanager? 


Try from a terminal ```
sudo /etc/init.d/networking restart
```


Good Luck

---

### Post by rookworm on 2009-01-26
thanks... that should suffice for now... hopefully, this will get fixed eventually

---

### Post by rookworm on 2009-01-27
it didn't quite work as planned; when i restart nm, i still get the same list of networks as i had before...... i have to reboot in order to see the new networks.

is there any way i can force it the rescan for networks?

---

### Post by gn2 on 2009-01-27
The Wicd application which I mentioned earlier has a "Refresh" button to rescan for new networks. And it works.

---

### Post by rookworm on 2009-01-27
so are you saying this is a problem with network manager??

supposing i didn't want to install a replacement program, what would i do?

---

### Post by gn2 on 2009-01-28
> **rookworm said:**
> so are you saying this is a problem with network manager??

supposing i didn't want to install a replacement program, what would i do?

I have had problems in the past with NetworkManager and have never used it with wireless.

I'm afraid that I have no idea what you would do without installing an alternative.

---

### Post by rookworm on 2009-02-06
I was able to bypass the problem by changing my default keyring password to a blank string. I suspect that there is some sort of bug involved here, but typing in less passwords is certainly more convenient for me.

---

### Post by fraser_m on 2009-02-06
There might also be a problem with your wireless driver. There might be something you need to setup to get it working after a suspend.

---

### Post by rookworm on 2009-12-16
yes, I concur, fraser_m....

The problem seems to be fixed in Karmic however (using the ath5k driver).

---

