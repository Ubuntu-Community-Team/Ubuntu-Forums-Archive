---
title: "after update this morning will not connect to wifi"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by SVWander on 2007-09-01
after clicked on update this morning and restarted my Dell 1200 laptop I can no longer connect to my wifi system. It is an open router so there are no security settings. It has been working well for over a month now without a single problem. I am running Feisty Fawn . . . I am on the road and don't have all my resource and information here. I am posting this through a friend's computer. Anyone have any ideas what might have happened? Or how I can undo the latest updates until I get back home where I can look at the problem closer.
 
Okay, after panicking for a few couple of hours I remembered the POWER of command lines and with iwconfig eth1 mode Manage . . . followed by dhclient eth1  I was able to obtain a DHCP lease. So the latest update screwed up networkmanager. I used the howto: [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)  . To configure this machines wireless card. Something went wrong with the update this morning. How do I troubleshoot what happened and fix the problem?


Thank you Tim

---

### Post by fishyf on 2007-09-01
I compiled a new kernel by following the instructions in the tutorial section and my wireless stopped working so I went back to the original kernel. This was probably a month ago. Then, today's update caused it to revert to the 2.6.22.1 kernel and my wireless again stopped working (see [http://ubuntuforums.org/showthread.php?t=540251](http://ubuntuforums.org/showthread.php?t=540251)).

I'm not sure if the update changed to the latest kernel version, or if it modified the menu to use the kernel that I had compiled, ausing the problem to resurface. I did investigate the problem at the time, but without success.

---

### Post by SVWander on 2007-09-01
> **fishyf said:**
> I compiled a new kernel by following the instructions in the tutorial section and my wireless stopped working so I went back to the original kernel. This was probably a month ago. Then, today's update caused it to revert to the 2.6.22.1 kernel and my wireless again stopped working (see [http://ubuntuforums.org/showthread.php?t=540251](http://ubuntuforums.org/showthread.php?t=540251)).

I'm not sure if the update changed to the latest kernel version, or if it modified the menu to use the kernel that I had compiled, ausing the problem to resurface. I did investigate the problem at the time, but without success.

LOL you lost me at compiled a new kernel . . . you might point me in the right direction there.  As long as I can connect using command lines I am okay but when I get to a secured AP I might be in for some trouble. I guess I should investigate this while I have access to other computers. I am really very new to this and been learning as I go. At least on the wireless/laptop end Ubuntu is not ready for prime time. I wouldn't feel comfortable recommending it to someone that didn't like to mess around with computers, so at least in that dream Ubuntu fall short of the mark, but I really enjoy messing with it.

Tim

---

### Post by fishyf on 2007-09-01
I only mentioned that I compiled the kernel because I thought that might have been my problem. The simple fix is to boot the old kernel. When it's booting, choose the 2.6.16 or whatever rather than 2.6.22.1 and that should work.

Someone more knowledgeable might have a better fix.

---

