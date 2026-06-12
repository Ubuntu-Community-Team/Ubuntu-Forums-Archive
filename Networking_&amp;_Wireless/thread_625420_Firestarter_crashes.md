---
title: "Firestarter crashes"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by BakaGaske on 2007-11-28
Hey guys,

I downloaded firestarter and after awhile, it just..disappears\crashes. I'm using gutsy. 

and on a side note, i can't seem to add policies as well..i don't know why though and i'm having a hard time trying to figure it out. :confused:

---

### Post by santiagoward2000 on 2007-11-28
> **BakaGaske said:**
> Hey guys,

I downloaded firestarter and after awhile, it just..disappears\crashes. I'm using gutsy. 

and on a side note, i can't seem to add policies as well..i don't know why though and i'm having a hard time trying to figure it out. :confused:

Normally, there's no problem in running Ubuntu without opening Firestarter. Firestarter is just a way to configure iptables (Ubuntu's preinstalled firewall). I don't know why it may be crashing, but I don't think you'll need to worry too much about it. Still, it would be nice finding out why this is happening...

---

### Post by starsheeep on 2008-01-10
Same here, I'm using gutsy and firestarter 1.03, after a while it will close by itself :/ no error message pops out when it does.

---

### Post by davescafe on 2008-01-11
Firstarter crashes on me as well. I know that the firewall is still active (IP Tables) but when Firestarter is running, it collects information about incoming, outcoming and blocked connections. When Firestarter closes or crashes, it loses that information. I would like to see Firestarter more stable, so that I could aggregate this connection information over time. I suppose there's another tool out there that is specifically designed for this kind of logging. Still, it would be nice if Firestarter were more stable on Gutsy.

Dave

---

### Post by davescafe on 2008-01-11
Firestarter still crashing, although my concern about losing aggregated data is not valid.
I learned  (by reading the documentation at: [http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)) that all I need to do is hit the "Reload" button to add data from Firestarter's logs. 

For those who are interested, the Firestarter FAQ has some good info as well: [http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

Dave

---

### Post by bks on 2008-01-12
I have the same problem, but it's a but worse now. I tried to set Firestarter up to load on boot up as per the FAQ and now it won't load at all! I click on the menu icon and it says "Starting Firestarter" and then nothing.

This is what I get:
```
bradford@gateway400sd-bschroe:~$ sudo /usr/sbin/firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:9323): Gtk-WARNING **: cannot open display:  
bradford@gateway400sd-bschroe:~$ 

```

---

### Post by Jburgess on 2008-01-20
Same here. Firestarter 1.0.3 and gutsy, but it only seems to crash when (or after) viewing active connections on the status tab. otherwise very stable.

---

### Post by Khelge on 2008-01-21
Same here. Firestarter 1.0.3 and gutsy. Crashes randomly some minutes (sometimes just sec's after) I have started it. 
but it seems to work fine as long as I have the "Active Connections" hidden.

and btw, if you have the problem with the Add Rule button being faded out so you can click it, just go to the "Policy" tab and right click inside of the window below "Allow connections from host" and add a rule, and then suddenly the buttons on the menu works fine :o

---

### Post by GooglieS on 2008-01-22
Yes! I also have this problem!

---

### Post by frogotronic on 2008-01-30
Hello,

According to LAUNCHPAD ([https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/120445](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/120445)), there is a patch (see attatched file).

Q  How does one apply the patch?  Would the order below be correct?

1) Download source code
2) change the code via the patch (how? manually?)
3) recompile?
4) install patched deb?


Thanks,
CH

---

### Post by frogotronic on 2008-01-31
> **cement_head said:**
> Hello,

According to LAUNCHPAD ([https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/120445](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/120445)), there is a patch (see attatched file).

Q  How does one apply the patch?  Would the order below be correct?

1) Download source code
2) change the code via the patch (how? manually?)
3) recompile?
4) install patched deb?


Thanks,
CH

From RobNield [[Launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/120445")]

```
RobNeild wrote 15 hours ago: (permalink)

You can apply the patch, build and install firestarter doing something like

sudo apt-get build-dep firestarter
sudo apt-get install fakeroot
apt-get source firestarter
cd firestarter-1.0.3/src/
wget http://launchpadlibrarian.net/11480727/foo2.patch
patch < foo2.patch
cd ..
dpkg-buildpackage -rfakeroot
cd ..
sudo dpkg -i firestarter_1.0.3-6ubuntu1_i386.deb
```


This patch is working for me, but bcs the new deb has the same # as the current deb, UPDATE MANAGER wants to "upgrade" it to the broken version (which has the same number).  Anyone know a way to change the deb numbering during the build so that this annoying problem of PM goes away?

- Thanks

---

### Post by starsheeep on 2008-02-06
an alternative is guarddog
can be installed from synaptics, and then called from a terminal >sudo guarddog
i'm using it wth no problems so far and seems much more configurable

here is also a guide (4 debian)
[http://newbiedoc.berlios.de/wiki/Setting_up_a_personal_firewall_on_Debian_using_Guarddog](http://newbiedoc.berlios.de/wiki/Setting_up_a_personal_firewall_on_Debian_using_Guarddog)

---

### Post by mexpolk on 2008-02-08
Also crashes for me... so I ran it from command line expecting some output an this is what it tells me:

```

$ sudo firestarter
Firewall started

***MEMORY-ERROR***: firestarter[10252]: GSlice: assertion failed: sinfo->n_allocated > 0
Aborted (core dumped)

```

I like guardog but you need to install Qt libs (that as far as I know are not completely free), and I prefer not to mix Gnome/KDE.

---

### Post by blacksm1th on 2008-02-15
Start firestarter with this option:
```
G_SLICE=always-malloc firestarter
```

---

### Post by oxyk on 2008-02-27
I have the same problem with Firestarter on Ubuntu 7.10 (gnome/kde)
it runs and dissapeared in 3-5 minutes
Before I have old version of Firestarter on 7.04 and 7.10 - and it works well.
now I try guarddog

---

### Post by Ux64 on 2008-04-08
Yep, same here. Especially if I'm viewing event log. It crashes in a few minutes.

Ubuntu 64 bit 7.10

---

### Post by blacksm1th on 2008-04-08
If you want firestarter to work properly run it with this string from terminal:
```
G_SLICE=always-malloc firestarter
```
or make script with this body if you want to start firewall on boot:
```
#!/bin/bash
G_SLICE=always-malloc firestarter --start-hidden 

```
This method work for me perfectly.

---

### Post by Ux64 on 2008-04-11
> **blacksm1th said:**
> ```
G_SLICE=always-malloc firestarter
```

Thanks. I'm sorry but I'm don't know linux well enough. Could you shortly explain what that does and why it matters.

- Thank you!

---

### Post by blacksm1th on 2008-04-11
> **Ux64 said:**
> Thanks. I'm sorry but I'm don't know linux well enough. Could you shortly explain what that does and why it matters.

- Thank you!

I don't know what this string mean. But this is very unusual situation with applications and this fix is not important :). I found it from Google.

---

