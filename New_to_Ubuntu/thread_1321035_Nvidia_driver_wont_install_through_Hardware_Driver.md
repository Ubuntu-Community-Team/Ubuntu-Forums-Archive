---
title: "Nvidia driver wont install through Hardware Drivers"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by g3k0 on 2009-11-09
Nvidia accelerated graphics driver(version 96) will download when I click activate, but it endlessly waits once it gets to a certain point (I assume the install point).  I don't know what card I have (I think its integrated) or I would try to download drivers from nvidias site.  Anyone know what I should do to get it to work?  BTW I am on 9.10

Thanks

---

### Post by Bunnybugs on 2009-11-09
As far as I know, there are 2 versions of the driver available in the driver section...

Have you tried the other version? I have the choise between version 173, and version 180...

180 is recommended, but if needed, you can use the other version as well

---

### Post by sdpiowa on 2009-11-09
I had a similar problem.  Eventually, though, it started working (after several computer restarts).

---

### Post by jimbean on 2009-11-09
in version 9.04 i had problem when trying to activate card and did a couple of reboots
but i did not have a problem with 9.10
{except}
the servers for 9.10 are being overloaded because 9.10 is a hot potato right now

---

### Post by mikewhatever on 2009-11-09
You can find out your card model with **sudo lshw -C display**  ,
and install the driver with **sudo apt-get install nvidia-glx-96**  .
Perhaps if you post the outputs we can see what's wrong.

---

### Post by wheatpenny on 2009-11-09
Integrated video drivers can be downloaded from NVidia's site (i downloaded mine from there). When I had trouble installing mine, I had to unlock the root account (sudo passwd root to set  the password) and access root priveleges in the terminal (su then enter the root password) then shut off the X-server (CTRL Alt F1, then when the black screen comes up, enter su and the root password again, then sudo/etc/init.d/gdm stop) to shut off the Xserver, then enter the path of the driver you're trying to install.

---

### Post by g3k0 on 2009-11-09
Thanks Mike.  It worked with the apt-get. :D

---

### Post by fundakaraoglu on 2009-11-10
> **Bunnybugs said:**
> As far as I know, there are 2 versions of the driver available in the driver section...
 
Have you tried the other version? I have the choise between version 173, and version 180...
 
180 is recommended, but if needed, you can use the other version as well
 hi guys,
I had problems with ubuntu 9.04 because  of Xserver configs and I did fresh install with ubuntu 9.10,but 9.04 resides in other partiton.I searched available  hardware drivers in system but there is not any driver.How could &#305; fix this prblem or I'm missing sth?
thanks so much

---

