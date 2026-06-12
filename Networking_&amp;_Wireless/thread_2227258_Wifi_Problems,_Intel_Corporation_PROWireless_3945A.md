---
title: "Wifi Problems, Intel Corporation PRO/Wireless 3945ABG [Golan]"
date: 2014-05-31
forum: Networking &amp; Wireless
---

### Post by liam12 on 2014-05-31
Hey Guys, 
I'm relatively new to ubuntu. My parents had an old computer which was extrememly slow, so I decided to put lubuntu on it. Of course, everything works fine except the wifi. I have spent 6 or 7 hours so far reading various forums and trying various things to get it working. Any help would be much appreciated. 
For info on my setup and what's going on, please see the attatchment.
Thank you,
Liam

---

### Post by chili555 on 2014-05-31
You have a conflicting driver installed; let's remove it and see if things improve:```
sudo apt-get purge bcmwl-kernel-source 
```After it finishes, detach the ethernet, reboot and let us hear your report.

---

### Post by liam12 on 2014-05-31
Okay, I did that and no dice. Just to double check that I'm not making a really stupid mistake, to determine if the wifi is working, I click on the "start" menu -> preferences -> network connections and then check if there is a "wireless" option there. Currently, there is only a "wired" connection option. See attached the output of the given command and an updated wireless info log.

---

### Post by chili555 on 2014-05-31
[https://dl.dropboxusercontent.com/u/58267392/NM-applet.png](https://dl.dropboxusercontent.com/u/58267392/NM-applet.png)

Do you  see the Network Manager icon at the top? It should list available networks to choose from. Are you running Lubuntu? Please check here:  [http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing](http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing)

---

### Post by liam12 on 2014-05-31
So I had seen that ( and now did it) and I think it's fixed, the thing is I think my screen resolution is also messed up somehow. All I can see is the little volume icon in the very bottom right of the screen. I figured I would try to solve one problem at a time, and the wifi was the most pressing. Should I take the time to try to figure all that out before I continue with the wifi?

---

### Post by chili555 on 2014-05-31
I recommend you do try to solve your video or resolution problem first.

---

### Post by liam12 on 2014-05-31
okay I will post back here after I figure it out.

---

### Post by liam12 on 2014-05-31
And of course it turns out one of those many solutions I had already tried had worked. Thanks. I guess I misunderstood what that network manager was for.

---

### Post by chili555 on 2014-06-01
> **liam12 said:**
> And of course it turns out one of those many solutions I had already tried had worked. Thanks. I guess I misunderstood what that network manager was for.So, solved?

---

