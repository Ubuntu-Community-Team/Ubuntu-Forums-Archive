---
title: "Weird Belkin Card issue!"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by geomysterio on 2007-03-12
Alright, here's the deal.
I've gone through all the channels I can after beating my brains out on this thing for the past few days.  I've used diswrapper correctly, I think, and the driver claims to be installed and correct, as follows.

~$ ndiswrapper -l
Installed drivers:
blkwgnv7                driver installed, hardware present 

Yet, my network manager gives me no option to configure the wlan0 connection or anything remotely similar.

Any help would be much appreciated
Thanks

---

### Post by n00b@linux on 2007-03-13
Never trust a GUI tool when an unambiguous set of command line tools will do the job!

Have you run 'lsmod' to check ndiswrapper has been loaded into the kernel?

If yes, have you run 'ifconfig' to see is wlan0 is up?

If yes, ave you run 'iwconfig' to make sure wlan0 has been recognised as a wireless interface?

If yes, have you run 'iwconfig wlan0 scan' to see if your access point is within range?

If yes to all of the above, then it's just a configuration/association problem.

P.S.  You may need to run some of the above commands with root privileges, ie prefix them with 'sudo'.

---

### Post by geomysterio on 2007-03-15
lsmod shows a list of programs, but ndiswrapper isn't on it.  I'll look into that.  Thanks.

---

### Post by geomysterio on 2007-03-15
well, lsmod doesn't show any ndiswrappers at all.  I tried to completely re-install by using the "sudo aptitude install" command, which appeared to be successfull, but when I run lsmod, it still shows no ndiswrapper.  Help here would be much appreciated.

---

### Post by n00b@linux on 2007-03-16
You haven't stated which release of Ubuntu you are using.  If you're using Edgy (and I presume you are) then you should be aware that there is a problem with its ndiswrapper.  You will need to uninstall it and then download and compile the source code from the ndiswrapper project web site directly.  It's not so hard and there is a link in my signature that can be followed.  The main thing is to ensure you install the build-essential package from the repos before you attempt to compile the ndiswrapper source code.  It's all in link in my signature.

Once you've compiled it and loaded your windoze drivers with it, you then need to load the ndiswrapper kernel module into the kernel.  To do this just type:```
modprobe ndiswrapper
```Then use 'lsmod' to check it's been loaded.  Then you can pick up where we left off in my original post to this thread.

---

### Post by geomysterio on 2007-03-17
Well.  Now lsmod lists ndiswrapper, but ifconfig still shows no wlan0.  Thanks, by the way, you've gotten me much farther then I could have gotten on my own.

---

### Post by n00b@linux on 2007-03-19
So now you have:
1. Loaded the windoze drivers into ndiswrapper; and
2.  Loaded ndiswrapper into the kernel.
Make sure you've done these in the correct order.  If you need to start again, unload ndiswrapper from the kernel with:```
modprobe -r ndiswrapper
```Next, you need to amend your /etc/network/interfaces file to include:```
auto wlan0
Iface wlan0 inet dhcp
```Then restart the networking initialisation script with:```
sudo /etc/init.d/networking restart
```Then try ifconfig to see if wlan0 appears.  If it does, continue on with my initial post.

---

