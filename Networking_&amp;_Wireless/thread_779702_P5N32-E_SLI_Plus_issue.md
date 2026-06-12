---
title: "P5N32-E SLI Plus issue"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by dokjones on 2008-05-02
Hello, I would first like to say this is my first try at Ubuntu and  I am no the most knowledgeable. Here is my issue, I have installed Ubuntu on my computer (put together myself) and I am not getting network connectivity. I am assuming that it is a driver issue with Ubuntu. When I try to configure eth0 or 1 it says "interface does not exist". I have looked at the forums and see people with this issue but no resolve. What steps do I need to do to get this working or what info do you guys need? Thanks.

---

### Post by Paris Heng on 2008-05-03
> **dokjones said:**
> Hello, I would first like to say this is my first try at Ubuntu and  I am no the most knowledgeable. Here is my issue, I have installed Ubuntu on my computer (put together myself) and I am not getting network connectivity. I am assuming that it is a driver issue with Ubuntu. When I try to configure eth0 or 1 it says "interface does not exist". I have looked at the forums and see people with this issue but no resolve. What steps do I need to do to get this working or what info do you guys need? Thanks.

What is P5N32-E SLI Plus ?

---

### Post by chili555 on 2008-05-03
> What is P5N32-E SLI Plus?It's a very cool motherboard I wish I could afford! How about opening a terminal (Applications->Accessories->Terminal) and letting us see:```
sudo lshw -C network
```Once we know the chipset involved, we can help you get going.

Is your primary concerned wired or wireless?

---

### Post by Psyphre on 2008-05-26
Ive got a p5n32-sli premium.

Im guessing ours are pretty similar? Is the wifi a while round thing with an antena?
If so, forget hardy for now, ive struggled with it to no avail. The previous ubuntu's work with it PERFECTLY. Im sticking with gutsy until someone comes up with a solution to the wifi/ethernet issues on our board.

---

### Post by aleblanc on 2011-05-27
See here: [http://www.overclock.net/linux-unix/508176-how-asus-p5n32-e-sli-plus.html#post6236427]("http://www.overclock.net/linux-unix/508176-how-asus-p5n32-e-sli-plus.html#post6236427")
and here: [http://ubuntuforums.org/showthread.php?p=10871352#post10871352]("http://ubuntuforums.org/showthread.php?p=10871352#post10871352")

---

