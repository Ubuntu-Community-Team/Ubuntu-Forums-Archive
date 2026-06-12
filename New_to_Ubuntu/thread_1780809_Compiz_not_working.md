---
title: "Compiz not working"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by mr.akik on 2011-06-12
I am using ubuntu 9.04.My graphics card is intel845 (built in).My problem is, I can not make compiz work.Resolation is ok.It is 1024x768 but when I try to change visual effect from none to normal or extra, every time it says "Desktop effects could not be enabled".Please tell me how to solve it.I am so much curious about compiz effects.

---

### Post by sikander3786 on 2011-06-12
First of all, 9.04 isn't supported any longer so you might not receive any updates or security patches for that. Even. you cannot reach the repositories for installing drivers or some other applications unless you tweak your sources.list a bit. And that too, wouldn't be much helpful because of the security issues.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

If you still want to use the repositories, this might help.

[http://ubuntu4beginners.blogspot.com/2011/01/access-repositories-on-eol-end-of-life.html](http://ubuntu4beginners.blogspot.com/2011/01/access-repositories-on-eol-end-of-life.html)

So, the most important thing is to upgrade or do a fresh install of one of the current releases i.e, 10.04 (Supported for 3 years on the desktop) or 11.10 (most recent one supported for 18 months).

If you want to stay with your current install for any reason, enable the repositories as mentioned above. Go to Applications > Accessories > Terminal and run:

```
sudo apt-get update
```

Now, go to System > Administration > Hardware Drivers and see if any drivers are available. If they are, install them and try enabling Compiz again.

If not, we might need to see the output of this command from Terminal:

```
lshw -c video
```

---

### Post by mr.akik on 2011-06-12
Here is the output:
herok@herok-desktop:~$ lshw -c video
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
herok@herok-desktop:~$

---

### Post by manzdagratiano on 2011-06-13
The intel video driver is installed along with X when Ubuntu is installed. Have you updated the system completely by running update manager?

---

### Post by mr.akik on 2011-06-13
> **manzdagratiano said:**
> The intel video driver is installed along with X when Ubuntu is installed. Have you updated the system completely by running update manager? I never updated but I tried lucid and natty.Even in these versions, I faced the same problem.

---

