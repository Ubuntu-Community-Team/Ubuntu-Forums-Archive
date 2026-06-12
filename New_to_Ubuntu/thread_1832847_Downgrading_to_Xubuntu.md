---
title: "Downgrading to Xubuntu"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by sheshan123 on 2011-08-25
So, I gave Ubuntu 11.04 a try but it's just too much for my old laptop. I started experiencing crashes and lags which is why i thought if i should downgrade to Xubuntu 11.04 which from what I've heard is supposed to run faster on systems such as mine. However, I would not be able to use my laptop without the applications of Ubuntu so I was wondering if the installed software are retained when downgrading. As I have an extremely slow internet connection I would not like to download all the required software again (namely, LibreOffice). My laptop specs are listed below:
==AMD Turion 1.6X2 1.6Ghz Processor
==A little less tha 1GB ram
==160 GB Harddisk
==NVidia Graphics Card Memory 200-ish MB (shared)

Do I really need Xubuntu? Or can I do some magic onto my existing Ubuntu and make it fast(real fast)? Help? :)

---

### Post by jerrrys on 2011-08-25
the first command will remove ubuntu and install xubuntu

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by sanderd17 on 2011-08-25
XFCE is just another Desktop Manager. So it only changes how programs look, and how you switch between programs etc. XFCE is indeed lighter than Gnome (and a lot lighter than Unity).

So all applications will just keep working. 

You can install XFCE into your current Ubuntu, just go into the software center and search for XFCE. You will be able to choose between XFCE and Gnome at your login screen (when you type your password).

There is also a package xubuntu-desktop. That package contains XFCE and all default XFCE appliations (so an xfce terminal, an xfce notepad ...) I don't believe you need this since you already have similar apps in your gnome environment. Those extra apps will only fill your menus.

If XFCE is not light enough, try LXDE.

---

### Post by BlinkinCat on 2011-08-25
I did a new install today and so far I am rapt - LibreOffice works fine! - :P

---

### Post by madjr on 2011-08-25
have you tried login into ubuntu classic (no effects) or unity2d?

[http://www.omgubuntu.co.uk/2011/04/10-things-to-do-after-installing-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/04/10-things-to-do-after-installing-ubuntu-11-04/)

---

### Post by sheshan123 on 2011-08-25
O.K. So, Xubuntu is just Ubuntu with another desktop manager? So, can I just use Xfce in Ubuntu itself to reap the speed benefits of Xubuntu? Also, I did install Unity-2D but how can I bring it to use after installation? Help please. Again, Ty in advance. :)

---

### Post by pqwoerituytrueiwoq on 2011-08-25
[http://scottlinux.com/wp-content/gallery/cache/298__640x480_natty_classic_edit1.png](http://scottlinux.com/wp-content/gallery/cache/298__640x480_natty_classic_edit1.png)
it is in that menu

---

### Post by madjr on 2011-08-25
> **sheshan123 said:**
> O.K. So, Xubuntu is just Ubuntu with another desktop manager? So, can I just use Xfce in Ubuntu itself to reap the speed benefits of Xubuntu? Also, I did install Unity-2D but how can I bring it to use after installation? Help please. Again, Ty in advance. :)

just log out and choose it.

there's also ubuntu classic no effects

---

### Post by bodhi.zazen on 2011-08-25
> **sheshan123 said:**
> O.K. So, Xubuntu is just Ubuntu with another desktop manager? So, can I just use Xfce in Ubuntu itself to reap the speed benefits of Xubuntu? Also, I did install Unity-2D but how can I bring it to use after installation? Help please. Again, Ty in advance. :)

service for service, application for application, I do not see much of a performance difference with the various DE (window managers).

To increase performance, disable unnecessary services, disable unnecessary auto-start applications, and use light weight applications when possible (gedit rather then LibreOffice).

---

### Post by XubuRoxMySox on 2011-08-25
Unity is too much for my old 'puter too, but Classic runs fine on it. 

I like Xfce because of it's simplicity and menus and easy configurability. 

On my old hand-me-down, I see no noticeable difference at all in speed or performance between Xfce, Gnome 2 ("Classic"), and even the ultralight LXDE! So for me it just boiled down to personal preference. I use elements from all of them! I like LXDE's superb file manager better than the others, KDE's K3B burner is my favorite, and I use a few Gnome tools in my Xfce desktop. Mix'n'match! Even on my old hardware it's fine.

I like the *look* of Unity though, and even set up my Xfce desktop to "look" and act alot like Unity, just for giggles and grins. Enjoy the diversity!

---

### Post by whatthefunk on 2011-08-25
> **dixiedancer said:**
> Unity is too much for my old 'puter too, but Classic runs fine on it. 

I like Xfce because of it's simplicity and menus and easy configurability. 

On my old hand-me-down, I see no noticeable difference at all in speed or performance between Xfce, Gnome 2 ("Classic"), and even the ultralight LXDE! So for me it just boiled down to personal preference. I use elements from all of them! I like LXDE's superb file manager better than the others, KDE's K3B burner is my favorite, and I use a few Gnome tools in my Xfce desktop. Mix'n'match! Even on my old hardware it's fine.

I like the *look* of Unity though, and even set up my Xfce desktop to "look" and act alot like Unity, just for giggles and grins. Enjoy the diversity!

I didnt experience much difference between Xfce and Gnome, but there is definitely a difference between the two and LXDE.  On my old laptop, Xfce and Gnome barely moved but LXDE works fine.

---

### Post by XubuRoxMySox on 2011-08-25
> **whatthefunk said:**
> I didnt experience much difference between Xfce and Gnome, but there is definitely a difference between the two and LXDE.  On my old laptop, Xfce and Gnome barely moved but LXDE works fine.

Cool! I guess it depends on the hardware, and what distro you're using too. In SalixOS, LXDE was faster than Xfce, but I think it might be that I messed something up when I added Xfce.

As they say, "Your mileage may vary." Some folks experience a noticeable increase in speed and responsiveness with LXDE, and some don't. The only way to know is to "throw it on the wall and see if it sticks."

---

