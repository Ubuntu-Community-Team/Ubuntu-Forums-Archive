---
title: "Activation of network connection failed [wired] after upgrade"
date: 2020-11-19
forum: Networking &amp; Wireless
---

### Post by dnaod on 2020-11-19
Hi All,

I'm a long time Ubuntu and Linux user running Ubuntu Gnome 20.10.  Tonight I did an update/upgrade which included an upgrade to the 5.8.0-29 kernel (but likely unrelated).  After the upgrade, my wired ethernet connection will no longer connect to the internet.

Things I've tried unsuccessfully:
- Rebooting to Windows 10.  Internet works fine on Windows 10.  (And yes, I tried disabling the fast restart to see if it had an effect on Linux)
- Using Grub recovery to go 1 or 2 kernels back
- Toggling the Gnome Network-Manager on and off for the wired profile
- Deleting and recreating the wired profile
- sudo lshw : *.network correctly shows my Intel I217-V ethernet device
- rm /var/lib/NetworkManager/NetworkManager.state

Some interesting things worth noting:
- if I 
```
sudo systemctl restart network-manager.service
```
then I get
```
Failed to restart network-manager.service: Unit network-manager.service not found
```

Is it possible that an upgrade of Network Manager failed and left me in a broken state?

Linux has been so reliable for me the last few years that I haven't had to chroot from a recovery disc for as long as I can remember but would that be a logical next step?

Appreciate the help!

---

### Post by dnaod on 2020-11-19
Bah, I should have been using
```
sudo systemctl restart networkmanager
```
regardless, no change.

---

### Post by dnaod on 2020-11-19
Alright, somehow I've fixed it. I'm going to be blunt.  I have no idea how.

It might have to do with my disabling IPv6 on the wired profile, restarting NetworkManager, enabling IPv6, restarting NetworkManager, and then rebooting.  That's the last 4-5 operations I performed after it started working again on the reboot.

I hate not understanding how something got fixed without any empirical evidence but.... if this helps someone get closer to the series of steps to fix it, I'll be happy.

---

### Post by dnaod on 2020-11-21
After multiple reboots over the past two days with successful connectivity, this morning I did an update of Ubuntu and then rebooted into Windows to claim Elite Dangerous on the Epic store.  To be clear, I've been dual booting successfully for years and years.

After rebooting back into Ubuntu Linux, I again was faced with my wired ethernet throwing an "Activation of network connection failed".  Without figuring out exactly how I fixed it last time, I'm stuck again without internet access and trying to work through the issue.  Any ideas welcome!

---

### Post by CelticWarrior on 2020-11-21
Disable Fast Startup in Windows.

---

### Post by dnaod on 2020-11-22
Yep, good call, @CelticWarrior.  It's either that or the rolling back of the Intel Network Adapter driver in Windows to the version before the latest (12.19.0.16).  Just before the original occurrence of this, I had updated my Windows boot (which I do every month or two when I rarely boot into it) and the network driver got automatically updated at that time.  Perhaps the installation of that driver turned that setting back on since I recall disabling that years ago but I'm not sure.

If you see my original posting, I had turned off the fast restart trying to diagnose the original occurrence last week and it wasn't successful.  But yesterday I rolled back the Windows driver, turned off fast restart, and  SHUT DOWN the computer (not restarted) from Windows.  My network came up as expected in Linux.  Unfortunately, it means I messed with two variables and I don't know which one it was.  When I have more time, I'll update to the new intel network adapater driver in Windows, keep fast restart disabled, and see if the new drivers are leaving the card in a bad state on the reboot into Linux.

---

