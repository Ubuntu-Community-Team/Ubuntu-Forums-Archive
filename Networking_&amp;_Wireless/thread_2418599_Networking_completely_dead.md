---
title: "Networking completely dead"
date: 2019-05-08
forum: Networking &amp; Wireless
---

### Post by phe-h-o1 on 2019-05-08
Hello,

Apologies if this was already solved somewhere else, but I tried all solutions and none worked.

Today, after a reboot, all networking in my laptop stopped working, both wired and wireless. I checked all the obvious stuff (function button to disable wireless, cable, router) and the connection isn't the problem (I'm writing this from another computer in the same network).

What puzzles me most is that if I run 'ifconfig' the only network device that shows is 'lo'.

I couldn't find any solution for that, so I'm asking here.

I used the Wireless Script from here [https://ubuntuforums.org/showthread.php?p=12350385#post12350385](https://ubuntuforums.org/showthread.php?p=12350385#post12350385) and the result is here: [https://pastebin.ubuntu.com/p/NYFmtk7ScZ/](https://pastebin.ubuntu.com/p/NYFmtk7ScZ/)

Thanks in advance!

---

### Post by crip720 on 2019-05-08
I can't help much but what I would suggest is to delete one of your wired or wireless connections and reload them.  Then reboot your system.  Lately on my system I find that I need to reboot three or four times to make network changes take effect.

---

### Post by chili555 on 2019-05-08
What is the exact response to the terminal command:```
sudo modprobe ath9k
```

---

### Post by phe-h-o1 on 2019-05-08
Thanks for the replies.

crip720: I deleted all the unused connections and restarted the laptop, but there was no difference at all. The network manager only shows (apparently I can't take a screenshot of it) a grayed out “No network devices available”, a menu for “VPN connections”, an activated “Enable Networking”, a grayed out “Connection information” and an item “Edit connections...”.

chili555: the command fails with:
```
modprobe: FATAL: Module ath9k not found.
```

---

### Post by chili555 on 2019-05-08
> 
modprobe: FATAL: Module ath9k not found.
YIKES!!!

Let's see:```
sudo updatedb
locate ath9k
```

---

### Post by phe-h-o1 on 2019-05-08
The first command (sudo updatedb) didn't print anything, the second (locate ath9k) printed this list: [https://pastebin.ubuntu.com/p/h3f6KX4Fd9/](https://pastebin.ubuntu.com/p/h3f6KX4Fd9/)

---

### Post by chili555 on 2019-05-08
You have a lot of kernels on your system! You are running, according to your first paste, 4.4.0-143-generic. However, please notice that under /lib/modules/ you have ath9k.ko in kernel versions 4.4.0-98-generic, -91, -81, etc., but not -143. Something in the installation of -143 went very wrong.

Can you interrupt the boot process at the GRUB menu and boot into -98? If so, I am confident that your wireless will work. We will then try to reinstall -143.

---

### Post by phe-h-o1 on 2019-05-08
Wow. Just wow!

I would've never seen that. Thank you very much, it's working perfectly with -98.

I searched for ‘how to reinstall the Linux kernel’ and found [https://askubuntu.com/a/298855/517513](https://askubuntu.com/a/298855/517513)

```
sudo apt-get install --reinstall linux-image-4.4.0-143-generic

```

Is this it?

---

### Post by chili555 on 2019-05-09
I would suggest that you add a few things:```
sudo apt-get install --reinstall linux-image-4.4.0-143-generic
sudo apt-get install --reinstall linux-modules-4.4.0-143-generic
sudo apt-get install --reinstall linux-headers-4.4.0-143-generic
```After those commands finish successfully, then run:```
sudo updatedb
locate ath9k.ko
```Be certain that you see[I] /lib/modules/4.4.0[COLOR="#FF0000"]-143[/COLOR]-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
[/I]
If so, I suspect you are all set. Reboot and post back the good news.

---

### Post by phe-h-o1 on 2019-05-09
Not *that* good news, I'm afraid...

I run the three commands you suggested and the installation went apparently okay. Then I did ‘sudo updatedb’ and ‘locate ath9k | grep 143’, but the list didn't show the line you mentioned (terminal output: [https://pastebin.ubuntu.com/p/QCDr6bydP7/](https://pastebin.ubuntu.com/p/QCDr6bydP7/) see line 95).

Then I noticed that the re-installation of linux-headers-4.4.0-143-generic ended with (line 93):

```

Unpacking linux-headers-4.4.0-143-generic (4.4.0-143.169~14.04.2) over (4.4.0-143.169~14.04.2) ...
Setting up linux-headers-4.4.0-143-generic (4.4.0-143.169~14.04.2) ...

```

which looked odd (unfinished), so I tried completely removing ‘linux-headers-4.4.0-143-generic’ (lines 119 to 155) and then reinstalling everything again (lines 156 to 260). But I ran ‘sudo updatedb’ and ‘locate ath9k | grep 143’ again and still nothing :/

Have I done something wrong in the re-installation?

---

### Post by chili555 on 2019-05-09
Oops! Please also try:

```
sudo apt-get install --reinstall linux-modules-extra-4.4.0-143-generic
```And then:```
sudo updatedb
locate ath9k.ko
```Any -143??

---

### Post by phe-h-o1 on 2019-05-09
Ooh, that was it!

I installed that and then ‘locate ath9k.ko | grep 143’ reported:

```
/lib/modules/4.4.0-143-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
```

I rebooted the laptop and everything's working fine now!

Thank you very much!

---

### Post by chili555 on 2019-05-09
Awesome! Glad it's working.

Ubuntu 14.04 is now end-of-life, meaning that crucial security updates will no longer be offered. Please consider upgrading to 18.04 LTS at least.

[https://www.omgubuntu.co.uk/2019/04/ubuntu-14-04-end-of-life](https://www.omgubuntu.co.uk/2019/04/ubuntu-14-04-end-of-life)

---

### Post by phe-h-o1 on 2019-05-09
Hm... I will. Thanks for the reminder!

---

