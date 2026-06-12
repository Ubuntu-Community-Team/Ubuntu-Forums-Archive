---
title: "using/finding built in webcam."
date: 2009-04-25
forum: New to Ubuntu
---

### Post by maggiemonic on 2009-04-25
hello,

i just installed eeebuntu on my eee pc 1000 and cant seem to find the built in webcam. its not listed in the hardware section of the control center and i dont see any particular app that screams "camera!". is there an application that will afford me access to it or is it just hiding someplace?

thanxxx!

---

### Post by blackened on 2009-04-25
First, you'll likely need eee-control to power it up. So,

```
sudo apt-get install eee-control
```

and then you'll need a program to interact with it

```
sudo apt-get install cheese
```

Once you start eee-control, use the notification-area icon to enable/disable hardware as needed.

Note that cheese my be installed by default, I can't remember.

---

### Post by maggiemonic on 2009-04-25
perfect! thanks!

---

### Post by blackened on 2009-04-25
You're very welcome. There are newer debs available for Jaunty should you decide to upgrade. You can find them here: [http://greg.geekmind.org/eee-control/deb/]("http://greg.geekmind.org/eee-control/deb/").

---

### Post by blueridgedog on 2009-04-26
In 9.04 it is now called eee-applet - but my eee pc 1000 still can't see with it's camera...perhaps I should try the deb you pointed to.

---

### Post by blackened on 2009-04-26
> **blueridgedog said:**
> ...perhaps I should try the deb you pointed to.

It's certainly worth a shot. I still haven't tried the version for Jaunty, but am using a version meant for Intrepid (0.8.3) that I've modified to work with Jaunty.

---

### Post by rajamouli2000 on 2009-04-26
What is a good program to shoot using built in webcam?
I am using a toshiba M300 satellite laptop and installed 9.04 recently.

---

### Post by blackened on 2009-04-27
> **blueridgedog said:**
> In 9.04 it is now called eee-applet - but my eee pc 1000 still can't see with it's camera...perhaps I should try the deb you pointed to.

All eee-applet does on my 900 is prompt for superuser privileges, but doesn't actually change anything. I've tried every option and none work, which is why I didn't even bother suggesting it in the first place.

> **rajamouli2000 said:**
> What is a good program to shoot using built in webcam?
I am using a toshiba M300 satellite laptop and installed 9.04 recently.

As stated in my first post under this thread: cheese is my favorite. It's in the repos.

---

### Post by blueridgedog on 2009-04-27
eee-applet indeed does nothing on my system as well.

---

### Post by blueridgedog on 2009-04-27
Well, I removed eee-applet (which was in the repos) and installed eee-control (from the site listed above) and it works great.

---

### Post by rajamouli2000 on 2009-04-27
> **blackened said:**
> 
As stated in my first post under this thread: cheese is my favorite. It's in the repos.
Works perfectly. Thank you.

---

### Post by blackened on 2009-04-27
> **blueridgedog said:**
> In 9.04 it is now called eee-applet - but my eee pc 1000 still can't see with it's camera...perhaps I should try the deb you pointed to.

eee-applet asks for authorization every time I try to change a setting, but then nothing actually changes. Yeah, junky, I uninstalled it.

The newest version of eee-control, 0.9.2, works flawlessly in Jaunty on my 900.

---

### Post by coffeecat on 2009-05-03
> **blackened said:**
> eee-applet asks for authorization every time I try to change a setting, but then nothing actually changes. Yeah, junky, I uninstalled it.

The newest version of eee-control, 0.9.2, works flawlessly in Jaunty on my 900.

Ditto with my Eee 701.

What, I would like to know, is the point of an application that merely asks for one's password, but does nothing? And even before I discovered it was a non-event I wasn't exactly filled with confidence by the 'Enable Card Reeader' line. Or was that meant to be a joke? :|

---

