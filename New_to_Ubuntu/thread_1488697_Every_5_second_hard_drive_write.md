---
title: "Every 5 second hard drive write"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by kid1000002000 on 2010-05-20
Every 5 seconds, the hard drive light on my laptop blinks at me.  Not a huge deal, but I'm wondering if this will decrease my drive's life in the future.  Suggestions?  Is there a way to tell what processes are writing to the disk?

---

### Post by ubunterooster on 2010-05-20
just a little, short blink is usual and will not affect life much.

Constant flickering (several blinks per second), however, would likely indicate an overactive program

---

### Post by befana on 2010-05-20
To monitor the state of the hard drive install smartmontools:
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
Pay attention to load/unload cycle count value.

---

### Post by philinux on 2010-05-20
> **befana said:**
> To monitor the state of the hard drive install smartmontools:
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
Pay attention to load/unload cycle count value.

There are already in use on 10.04.

**System>admin>Disk Utility**

---

### Post by befana on 2010-05-20
> **philinux said:**
> There are already in use on 10.04.

**System>admin>Disk Utility**

Thanks! I didn't know that.

---

### Post by bodhi.zazen on 2010-05-20
Linux is fairly disk intensive. You can reduce this by mounting tmp and var with tmpfs

Add these lines to fstab :

```
tmpfs  /dev/shm  tmpfs  defaults           0  0
tmpfs  /var/log    tmpfs  noexec,nosuid  0  0
tmpfs  /tmp         tmpfs  noexec,nosuid  0  0
tmpfs  /var/tmp   tmpfs  noexec,nosuid  0  0
```

Occasionally the noexec is a problem , upgrading 8.04 -> 10.04 for example, but this is rare.

---

### Post by cryptotheslow on 2010-05-20
You can also try the iotop command in a Terminal.

Using karmic I get a disk write every 5 or so seconds by the kjournald2 process - which I believe is the ext4 journalling process.

---

### Post by HarrisonNapper on 2010-05-20
> **bodhi.zazen said:**
> Linux is fairly disk intensive. You can reduce this by mounting tmp and var with tmpfs

Add these lines to fstab :

```
tmpfs  /dev/shm  tmpfs  defaults           0  0
tmpfs  /var/log    tmpfs  noexec,nosuid  0  0
tmpfs  /tmp         tmpfs  noexec,nosuid  0  0
tmpfs  /var/tmp   tmpfs  noexec,nosuid  0  0
```Occasionally the noexec is a problem , upgrading 8.04 -> 10.04 for example, but this is rare.

Side question: will this still write logs to disk at shutdown?

Also, OP, if you have a SSD, as is common in many netbooks, consider not only reducing writes manually, but using the UNR distro, as my understanding is that its focus is doing just that.

---

### Post by bodhi.zazen on 2010-05-20
> **HarrisonNapper said:**
> Side question: will this still write logs to disk at shutdown?

No, you would loose your logs at shutdown. Either write a scrip as start / stop or do not mount /var/log in tmpfs .

On a desktop honestly I do not find the logs all that useful, and if I need them across boots, make an adjustment.

Server side, I watch the logs much closer , but almost never reboot servers so "works for me , YMMV .

My uptime would be a year and a half on my SBHO server, except my two year old pulled the plug  a few months ago, not to mention the cat. Oh, and my son likes to "rewire" things from time to time - dammed gremlins :lolflag:

---

### Post by CSInDevelopment on 2010-05-20
To decrease this you can adjust the "vm.swappiness" attribute
the lower the number it equals, the less it writes to the hard drive, beware though not to go lower than 10 and to make sure you have plenty RAM first.
The variable lies in the file "/etc/sysctl.conf"
for this to take effect, after modifying run
```

sudo sysctl -p

``` 
or restart

---

### Post by bodhi.zazen on 2010-05-20
> **CSInDevelopment said:**
> To decrease this you can adjust the "vm.swappiness" attribute
the lower the number it equals, the less it writes to the hard drive, beware though not to go lower than 10 and to make sure you have plenty RAM first.
The variable lies in the file "/etc/sysctl.conf"
for this to take effect, after modifying run
```

sudo sysctl -p

```or restart

That works if you are using swap, otherwise it does no do anything.

---

### Post by kid1000002000 on 2010-05-20
iotop was exactly what I was looking for.  Thanks.  Future readers might want to take a look at how much swap they are using, but for me, that wasn't the problem.  Also, didn't know that was already installed via disk util- thanks for that.  Haven't tried changing those tmp directories, as the following were what I saw:
 gconfd-2
 gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
 and my journaling command for the disk.

Not really worth shutting all these things down, just wanted to make sure there's nothing extraneous.

Thanks for the posts and for the help, everyone.

I wonder if setting ubuntu to spin down my hd will cause it to spin up and down every 5 seconds or not?

---

