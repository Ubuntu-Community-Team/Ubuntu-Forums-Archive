---
title: "Lenovo Yoga 2 Pro has Wifi Hardware Hard Bloked ; Intel 7620 Card"
date: 2014-08-04
forum: Networking &amp; Wireless
---

### Post by Mario_Del_Boccio on 2014-08-04
Hello,

This is my first time using ubuntu and I using this forum; so I apologize if I'm a bit naive about some things. I'm running windows 8.1 and ubuntu on a dual boot setup on my Lenovo Yoga 2 Pro. The wifi setting is grayed out in the menu and the wifi says its hard blocked in terminal. I don't know if I need to install drivers for this wifi card but I'd appreciate some help. Attatched is the network file that terminal made after I ran the code mentioned in the sticky topic. Thanks for your help   

[ATTACH]255242[/ATTACH]

Also, the wifi card is an Intel 7620 I believe....

---

### Post by chili555 on 2014-08-04
First, let's see if we can get the device unblocked:```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
```Now is it working? If so, let's blacklist the module:```
sudo -i
echo "blacklist ideapad-laptop"  >>  /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by Mario_Del_Boccio on 2014-08-04
chili555 I owe you one :) Ran the code and it worked like a charm. Would you mind giving me a quick explanation as to what was wrong and what I permanently corrected with the code? Thanks!

---

### Post by chili555 on 2014-08-04
> Would you mind giving me a quick explanation I don't mind in the least.

The module ideapad-laptop is supposed to translate key presses, Fn+F2 for example, into action, in this case, turn on the wireless radio. On the Yoga 2 Pro, it is a known issue that it doesn't do wireless so well and the fix is to remove it. We did so and your wireless came to life as expected.

Next, we blacklisted it so it doesn't reappear and interfere on boot. Read more here: [http://forums.lenovo.com/t5/Linux-Discussion/Yoga-2-Pro-LINUX-thread/td-p/1326323/page/6](http://forums.lenovo.com/t5/Linux-Discussion/Yoga-2-Pro-LINUX-thread/td-p/1326323/page/6) and here: [http://ossnotebook.blogspot.com/2014/05/ubuntugnome-running-on-yoga-pro-2.html](http://ossnotebook.blogspot.com/2014/05/ubuntugnome-running-on-yoga-pro-2.html)

Glad it's working! Have fun.

---

