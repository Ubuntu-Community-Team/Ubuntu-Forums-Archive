---
title: "ndiswrapper commands explained?"
date: 2013-12-06
forum: Networking &amp; Wireless
---

### Post by mjalberts13 on 2013-12-06
Hello everyone!

So I just got my wireless dongle to [work]("http://ubuntuforums.org/showthread.php?t=1805830&page=8&p=11811107#post11811107")! But every time on startup I need to type these commands in the terminal for my wireless to "work":

Code:
> **sudo modprobe ndiswrapper**

Also I have confirmed that the wireless starts working after I execute that command but can someone please tell me if it would affect my network in any positive or negative way when executing "**sudo depmod -a**" before the above mentioned command and is there a way that I can make the above command(s) execute automatically every time I turn on the computer/log-in? What do these commands do?:confused:

Thank you in advance,
MJ

---

### Post by chili555 on 2013-12-06
Here is the quick answer:```
sudo -i
echo ndiswrapper  >>  /etc/modules
exit
```The long answer is that depmod does:> depmod creates a list of module dependencies by reading each module
       under /lib/modules/version and determining what symbols it exports and
       what symbols it needs. By default, this list is written to modules.dep,
       and a binary hashed version named modules.dep.bin, in the same
       directory.Clear as mud, isn't it?

The addition of ndiswrapper to /etc/modules will solve your problem.

---

### Post by mjalberts13 on 2013-12-06
Thank you! The code worked and I don't have to manually do it anymore :). If I had another question is it 'accepted' to ask it here or should I make an other thread? (The question is, if I upgrade to other versions of Ubuntu like 12.10/13.04/13.10 will I lose all my files? and so will the wireless dongle's drivers have to be installed again?)

---

### Post by chili555 on 2013-12-06
I think your upgrade question is better asked here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

As for your wireless drivers, I am not very sure. I think I'd keep the .inf and .sys files on a USB key just in case. Now that you have figured out the process and have the files, it's pretty easy, isn't it?

---

### Post by mjalberts13 on 2013-12-07
Yes. Thank you :)

---

