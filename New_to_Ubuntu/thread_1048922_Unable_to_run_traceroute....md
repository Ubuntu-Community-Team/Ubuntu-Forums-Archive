---
title: "Unable to run traceroute..."
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Ironica on 2009-01-24
...No matter how many times I install it!

Running (I think) Intrepid Ibex on an AMD 64 chip, but running the 32-bit version.  I ran Dapper Drake for a couple of years, and did many traceroutes in that time, but ever since I upgraded to Ibex (unless it's Heron, but I don't think so) this is what happens:

@@ [ironica@ironica-desktop - ~]$ traceroute google.com
The program 'traceroute' can be found in the following packages:
 * traceroute-nanog
 * traceroute
Try: sudo apt-get install <selected package>
bash: traceroute: command not found
@@ [Ironica@Ironica-desktop - ~]$ sudo apt-get install traceroute
Reading package lists... Done
Building dependency tree       
Reading state information... Done
traceroute is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libavutil1d libpostproc1d kgeography-data
  ttf-sjfonts libgsm1 libavcodec1d libisc32 linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 180 not upgraded.
@@ [Ironica@Ironica-desktop - ~]$ traceroute google.com
The program 'traceroute' can be found in the following packages:
 * traceroute-nanog
 * traceroute
Try: sudo apt-get install <selected package>
bash: traceroute: command not found

I have apt-get removed traceroute.  I have whereised traceroute (it claims /usr/bin) and tried running /usr/bin/traceroute.  Turns out that's a pointer to /etc/alternatives/traceroute, which in turn is a pointer to /usr/bin/traceroute.lbl, which doesn't exist.

I don't seem to be able to convince Ubuntu to install traceroute.  I'm usually very persuasive, but I'm stymied here.  Any ideas?

---

### Post by Crafty Kisses on 2009-01-24
Try the following:
```
sudo apt-get remove --purge traceroute
```
Once you have ran that command, run these commands:
```
sudo apt-get update
sudo apt-get clean
```
Once you have updated, try installing it again:
```
sudo apt-get install traceroute
```
See if that does anything for you.

---

### Post by Ironica on 2009-01-24
Thanks for the suggestion, Codename.  All the commands did go through without error, but when I attempted to run traceroute afterward, I got the same result.  :-/  The whereis command gives me the same info, and looking up the files it discusses show me the same path (/usr/bin/traceroute is a pointer to /etc/alternatives/traceroute, which in turn is a pointer to the nonexistent /usr/bin/traceroute.lbl).

---

### Post by zvacet on 2009-01-24
```
sudo dpkg --remove --force-remove-reinstreq traceroute
```

You have 180 unupgraded packages so 

```
sudo apt-get update && sudo apt-get upgrade
```


To find out what are you runing 

```
lsb_release -a
```

After all of these commands try to install traceroute again.

---

### Post by Ironica on 2009-01-25
Tried it.  Took *forever* which probably isn't surprising.  I felt like I was cleaning house, top to bottom... I was SURE this would work!

Same exact results after installing traceroute.  I got told to install traceroute.

*sigh*  I think maybe my ISP got smart on me; without traceroute, I can't troubleshoot my way to Tier 2 quite so quickly...

---

### Post by kavon89 on 2009-01-25
You're using the wrong command.

```
sudo tracert google.com
```

---

### Post by Ironica on 2009-01-25
Ok... so the Windows spelling works.  But... I don't understand why, between Drake and Heron (which is what it turns out I'm running) they changed it?  And who is "they" anyway?  And why do I need to be an admin to run a tracert (although traceroute works from my regular account)?

---

