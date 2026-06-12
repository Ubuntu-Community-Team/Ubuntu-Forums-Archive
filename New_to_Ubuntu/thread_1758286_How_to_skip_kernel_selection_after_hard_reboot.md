---
title: "How to skip kernel selection after hard reboot"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by tim_adhi on 2011-05-14
Hi!

My Atom box run 10.10 server 64 bit, fresh install with LAMP & SSH. After complete update, I add debian.org to my repository to install the latest Zoneminder package. It supposed to run headless.

My problem arise when the box got a power loss, it will start and stop for a kernel selection. How can I skip this prompt? The default 2 seconds timer won't work either. It just stop there waiting an Enter key pressed to select the default kernel.

---

### Post by spikoley on 2011-05-18
You can edit the Grub2 boot options in /etc/default/grub.

```
sudo nano /etc/default/grub
```

Try turning the default time to 0.  When you make changes to that file you need to run *update-grub*.

```
sudo update-grub
```

---

### Post by froderick on 2011-06-03
I had what sounds like the same problem. I found a solution for it here:

[http://ubuntuforums.org/showthread.php?t=1347360]("http://ubuntuforums.org/showthread.php?t=1347360")

---

