---
title: "noob with wifi questions"
date: 2005-11-21
forum: Networking &amp; Wireless
---

### Post by thenoobest1 on 2005-11-21
ok, keep in mind im a COMPLETE noob when it comes to linux. I have a USB DLink DWL-122 for the wireless connection on my laptop. i cant get it to see the adapter at all. 

I used ndiswrapper as described in a tutorial i seen doing countless searches. it said it installed at first, but when i tried to "sudo modprobe ndiswrapper" it just didnt do anything. i did "sudo ndiswrapper -l" to list the drivers and it showd 4 there... not sure if thats right or not, but it said: 

Installed ndis drivers:
netprism        driver present
prism   invalid driver!
prismusb        invalid driver!
prismusb.sys    invalid driver!

and to top it off it wont let me uninstall those with "sudo ndiswrapper -e" so that i can try to install a different version of the driver.

i tried installing the other version but it says that it was already installed. i would appreciate any help i can get. ive seen tutorial after tutorial and did them word for word but have had no luck and eventually ended up with this problem.

lol, sorry for my extreme noobness in advance

---

### Post by thenoobest1 on 2005-11-21
i found this post just a few minutes ago... after a few typos and restarts as soon as i plug my usb adapter in i connect to the net.

[http://www.ubuntuforums.org/showthread.php?t=25676&highlight=dwl-122](http://www.ubuntuforums.org/showthread.php?t=25676&highlight=dwl-122)

---

