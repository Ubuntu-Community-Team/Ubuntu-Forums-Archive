---
title: "[SOLVED] Guide to connect 2 Linux machines via crossover cable required!"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-09-23
Hi,
I have a crossover cable and want to connect my Ubuntu desktop to my Kubuntu laptop to quickly copy over files.

What is the easiest and most straight forward way of doing this? Also, could I have a setup whereby the Kubuntu laptop can be pluged and unpluged from the Ubuntu desktop and still have the settings remembered if I need to connect the two computers again?

Thanks.

---

### Post by nixscripter on 2008-09-23
The easiest way to do that:

1. Connect the cable.
2. Wait for the network manager to spin around and time out.
3. Assign both ethernet cards addresses manual IP addresses on an imaginary subnet (like 169.254.0.0).

Step 3 can be done in the command line as something like:
```
sudo ifconfig eth0 169.254.**xxx**.**yyy** up
```

On both computers, where xxx is the same and yyy is different for each. You can then enter the IP of the other one for whatever services you need.

Hope this helps.

---

### Post by Iowan on 2008-09-23
Getting them connected will be only the first half of the battle.  Then, you'll need to decide on a sharing filesystem.  You can choose between Samba, NFS, or SSHFS - to name a few. One (or both) machines will need to be set up as servers.

---

