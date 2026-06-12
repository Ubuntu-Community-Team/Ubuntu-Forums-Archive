---
title: "Installing the control center"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Mariane on 2009-11-09
Hi, 

I would like to install the control center on 9.10, could someone please tell me the package name? (apt-cache search returns too many hits). 

Mariane

---

### Post by lavinog on 2009-11-10
```

apt-cache search control|grep -i center
gnome-control-center - utilities to configure the GNOME desktop

```

---

### Post by Mariane on 2009-11-10
Thank you, I've had trouble before with apt-cache search returning miles of results and I never could figure out the syntax of the vertical line. 

It finds the gnome control center but not the kde one (and the gnome-control-center is already installed). 

I tried:
sudo apt-cache search kde |grep -i center
and
sudo apt-cache search kde |grep -i control

sudo apt-cache search control |grep -i kde
showed one package called kde-core

Which I didn't have, but installing it didn't give me the control center. So it didn't solve my problem but it taught me something very useful, thanks! 

Mariane

---

### Post by lavinog on 2009-11-10
you don't need to use sudo with apt-cache

I thought kde has the control center by default.

---

### Post by camaron1 on 2009-11-10
> **Mariane said:**
> Thank you, I've had trouble before with apt-cache search returning miles of results and I never could figure out the syntax of the vertical line. 

It finds the gnome control center but not the kde one (and the gnome-control-center is already installed). 

I tried:
sudo apt-cache search kde |grep -i center
and
sudo apt-cache search kde |grep -i control

sudo apt-cache search control |grep -i kde
showed one package called kde-core

Which I didn't have, but installing it didn't give me the control center. So it didn't solve my problem but it taught me something very useful, thanks! 

Mariane

What you are looking for is called SYSTEMSETTINGS but I woud've thoght you had that installed by default

---

### Post by Mariane on 2009-11-10
[quote="camaron1"]
I woud've thought you had that installed by default
[/quote]

I thought so too... I did a fresh install of kde and all, this time via Debian because I was getting fed up with all the problems. As far as I'm concerned Ubuntu was fine until 9.10, but with 9.10 the problems started pilling up. I've spent the last 2 days troubleshooting and my old laptop, which is still under Ubuntu, is still not working properly at all. 

But I won't mark this thread as solved because it wouldn't be very friendly for all the people who like Ubuntu to say "SOLVED: the answer is to use Debian". 

Mariane

---

