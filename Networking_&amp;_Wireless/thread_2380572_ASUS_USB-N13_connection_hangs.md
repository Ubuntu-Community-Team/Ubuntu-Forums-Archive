---
title: "ASUS USB-N13 connection hangs"
date: 2017-12-19
forum: Networking &amp; Wireless
---

### Post by hochacha667 on 2017-12-19
I'm increasingly at a loss with Ubuntu. I bought a TP-Link TL-WN823N  USB wi-fi dongle a couple months back, and had to unplug and plug it  back in on every reboot to get it to work. So the other day, I gave up  and bought an ASUS USB-N13, and it seemed like it worked fine for a day  or two. But now it's simply dropping connection. The wi-fi signal seems  to stay strong, but the connection dies. It's not the fiber-optic  connection because other devices have no problem. Here's the output of  the wireless-info thing I ran when the connection died a few minutes  ago.


  [URL="http://pastebin.ubuntu.com/26213997/"]http://pastebin.ubuntu.com/26213997/

[/URL]

  When the connection dies, it simply hangs there for a minute or two,  refusing to do anything. I've tried the USB-N13 on two different USB  ports with no difference. Also: following a tip in a different forum or  thread, I ran the command to change the power setting (?) from 3 to 2.  Think this was in NetworkManager or a .conf file. No change.

---

### Post by jeremy31 on 2017-12-19
It is loading two different modules for the wifi, try
```
echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/realtek.conf
```
Reboot and see if it works better, if not we can switch to blacklist the other module and try again
```
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/realtek.conf
```
Reboot

---

### Post by hochacha667 on 2017-12-19
Thanks for the reply. I'm a bit confused. I ran the first line of code. The connection doesn't seem to be hanging up anymore. But it seems to have recreated the problem I had with the TP-Link TL-WN823N. The ASUS adapter now doesn't startup with the reboot. I have to manually unplug and re-plug it into USB. Also the blue LED has stopped working on the adapter. It comes on for a second after a reboot, then cuts out at the Ubuntu splash window and doesn't come back on.

This is basically the exact same thing that was going on with the TP-Link TL-WN823N. The LED wouldn't come on with that one either, and I had to manually unplug and replug. I dual-boot Windows 10. On Windows 10, the blue LED on that adapter would stay on and it generally didn't require manual unplg/plug on reboot.

---

### Post by jeremy31 on 2017-12-19
Try the second line of code and reboot.  I am not familiar with what features each of the modules have
What source did you use for the TL-WN823N driver?

---

### Post by hochacha667 on 2017-12-19
So far, so good. You're a boss! I'll keep an eye on it. You've restored some of my faith in Ubuntu.

Re: the TL-WN823N, I used this: ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu 

Now I wonder if your fix would have solved the problem with the TL-WN823N as well. Maybe I'll try it at some point if I'm feeling bold.

---

### Post by jeremy31 on 2017-12-19
If you want to work some more with the TP Link uninstall the driver from the PPA and use [https://github.com/Mange/rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver)
I think that TP Link shows in lsusb results as 2357:0109

---

### Post by hochacha667 on 2017-12-19
How do you go about doing that? I'm not finding a straightforward answer via Google search.

Well, Still experiencing a hanging connection though it's less frequent than before. I did shift the USB dongle to a USB port on the monitor not long after running the code when it looked like it was going to work.

---

### Post by jeremy31 on 2017-12-19
To install the new one from Mange see [https://ubuntuforums.org/showthread.php?t=2351228&p=13601820#post13601820](https://ubuntuforums.org/showthread.php?t=2351228&p=13601820#post13601820)
You will likely have to uninstall Pilots version with
```
sudo apt-get remove rtl8192eu-dkms
```

---

### Post by hochacha667 on 2017-12-19
After another slowdown for 30-60 seconds, I've decided I'd like to try the TP-LINK again. Following the first terminal command you linked to, I get this:

> Package dkms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'dkms' has no installation candidate

Thanks in advance for your help.

Well, after a couple of hours, I managed (I think) to install dkms. There was no way to do it even after adding repository locations, trying different variations of commands, etc. I had to somehow or other do a package download from the website and then use software installer.

Then I followed your instructions per the other thread, and am now back on the TP-LINK. Will monitor it and see how it turns out.

---

