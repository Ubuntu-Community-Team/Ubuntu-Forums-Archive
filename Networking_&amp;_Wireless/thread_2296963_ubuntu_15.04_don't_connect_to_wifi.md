---
title: "ubuntu 15.04 don't connect to wifi"
date: 2015-09-30
forum: Networking &amp; Wireless
---

### Post by mike369 on 2015-09-30
Hi, I've now installed on my lenovo g50-30 ubuntu 15.04, but it doesn't connect to Wi-Fi.
I tried to ```
rfkill unblock all
``` but it no changes.
Can someone help me please?
I know that my english is not very well.
Thank you very much.

---

### Post by jeremy31 on 2015-09-30
What kernel ```
uname -a
```  I believe this issue is fixed in kernel 3.19.0-26, so you may just have to install updates

---

### Post by mike369 on 2015-09-30
3.19.0-15-generic

Can you tell me step by step what I have to do?
Thank you very much

---

### Post by jeremy31 on 2015-09-30
You should just have to ```
sudo apt-get update && sudo apt-get upgrade
``` with a wired connection and reboot

---

### Post by mike369 on 2015-09-30
I can't use a wired connection, the laptop hasn't ethernet ports.
Now I'm using 2 differents computer.

---

### Post by jeremy31 on 2015-09-30
Should be able to get wifi working with ```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
```

Then see if you can connect and update

---

### Post by mike369 on 2015-09-30
YEAHHHH
I LOVE YOU  jeremy31.

It shows me nothing, but now I can switch on Wi-Fi

---

### Post by mike369 on 2015-09-30
I shut down the laptop, the changes I've done are useless.
Can I make this changes fixed, without repeting the same commands all the time?

---

### Post by jeremy31 on 2015-09-30
The newer 3.19.0-26 kernel should contain the correct fix, you could ```
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/ideapad-laptop.conf
sudo modprobe -r ideapad-laptop
```
And it should function after a reboot without using other commands

Then when you see that ```
uname -a
``` shows the 3.19.0-26 kernel or newer see if wifi still works after ```
sudo rm /etc/modprobe.d/ideapad-laptop.conf
```

The issue with removing/blacklist ideapad-laptop is that some FN key combos might not work anymore

---

### Post by mike369 on 2015-09-30
Now I've downloaded and installed upgrades, it works perfectly.
Thank you very very very much, I was searching for this problem since 3 days.

---

