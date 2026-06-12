---
title: "ubuntu uses more battery power"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-02-17
I am using ubuntu 10.10 and windows 7 side by side. my battery would last for about 2 hours when i am using windows but it wouldn't last more than a hour when i am using Ubuntu!!!
is there anything i can do about it???

---

### Post by Linyx on 2011-02-17
> **amitpokhrel said:**
> I am using ubuntu 10.10 and windows 7 side by side. my battery would last for about 2 hours when i am using windows but it wouldn't last more than a hour when i am using Ubuntu!!!
is there anything i can do about it???

I Don't think so that an OS will consume your Battery, 
Moreover, The Processes running on an OS can consume it depends on their usage of CPU,

The Following links will help you to last you battery more in Ubuntu > [http://ezinearticles.com/?How-to-Manage-Your-Laptop-Battery-in-Ubuntu-to-Make-it-Last-Longer&id=4319612]("http://ezinearticles.com/?How-to-Manage-Your-Laptop-Battery-in-Ubuntu-to-Make-it-Last-Longer&id=4319612")

> [http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=1]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=1")

---

### Post by jaricanese7 on 2011-02-17
> **Linyx said:**
> I Don't think so that an OS will consume your Battery, 
Moreover, The Processes running on an OS can consume it depends on their usage of CPU,

The Following links will help you to last you battery more in Ubuntu > [http://ezinearticles.com/?How-to-Manage-Your-Laptop-Battery-in-Ubuntu-to-Make-it-Last-Longer&id=4319612]("http://ezinearticles.com/?How-to-Manage-Your-Laptop-Battery-in-Ubuntu-to-Make-it-Last-Longer&id=4319612")

> [http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=1]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_battery_life&num=1")

OSs definitely consume battery. If it is running (the computer is on), then it will consume battery. How much, like you said, depends on what its running a such.


Personally I think Ubuntu is decent with battery life. If anything, I know on one of my laptops, Ubuntu didn't support changing the brightness on my screen and keyboard. Something like that then caused my battery life to run out much quicker than it would on Windows.

---

### Post by maqtanim on 2011-02-17
In my laptop, the brightness of the screen is always in full-form. So it takes much power. May be it happens to you too. Try to minimize the brightness...

---

### Post by NightwishFan on 2011-02-17
Yes at the moment Linux varies a lot more in power usage. On a supported device it may use less power than Windows. On a device where built in or unique power management features aren't supported it will certainly use more. Also note by default I believe Ubuntu does not install certain disk power management features as they shorten disk life. That is one of the biggest hits on power is the disk being on.

There is a command line utility to measure power usage called powertop. Install it with:
```
sudo apt-get install powertop
```

Run it with:
```
sudo powertop
```

---

### Post by philinux on 2011-02-17
Yes I think it depends on the hardware as nightwishfan says.

My Acer 1410 gives me 6 hours in win7 and in ubuntu. As long as brightness is turned down.

---

### Post by amitpokhrel on 2011-02-18
I can't control brightness in ubuntu. it's always full.. Then i think this may be the reason!!

---

