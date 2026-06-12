---
title: "Transfering Files Painstakingly Slow from Windows box"
date: 2005-04-02
forum: Networking &amp; Wireless
---

### Post by IceDigger on 2005-04-02
I am trying to transfer files from my windows computer to my ubuntu computer and it is taking a looong time to do so.

I am running a gigabit network and am transfering over only 500MB of files.  Ubuntu says it has 3hrs left on the transfer!?

Any idea whats up with that?

Both computers have gigabit nics installed connected to a gigabit switch.

---

### Post by ubuntu_demon on 2005-04-02
1)what transfering method are you using ?

2)A lot of small files take considerable more time than 1 big file.

3) Are you sure that a 1 gb connection was negotiated ?

---

### Post by IceDigger on 2005-04-02
Its alot of pictures.  When I boot into windows on the same pc it doesnt take long at all.  Less then 5min.

I am transfering via the "Network Servers" under "Places" in ubuntu.  Only way I know.

---

### Post by ubuntu_demon on 2005-04-02
this guy appears to have the same problem :

[http://www.ubuntuforums.org/showthread.php?t=22445](http://www.ubuntuforums.org/showthread.php?t=22445)

---

### Post by alastair on 2005-04-02
I don't have to do this with Ubuntu, but am unsettled that there might be such poor performance if I ever have to. I assume this uses Ubuntu's Samba server setup? It might be worth checking the Samba config file "smb.conf" (I don't have Samba installed). Then look at Samba tuning e.g.

[http://us2.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html](http://us2.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html)

or searcg google groups : [http://groups-beta.google.com/group/linux.samba](http://groups-beta.google.com/group/linux.samba)

---

### Post by king20878 on 2005-05-02
I don't know if you ever found a solution to your problem, but I ran into this same thing tonight.  I don't have a definitive explanation, but it's not samba itself.  It's apparently something about the way nautilus manages samba shares.  When copying an iso file from a samba share I had reached through the nautilus network browser, the approximate time was one hour. :shock: When mounting the same network share conventionally using the mount -t smbfs command, the same file takes six minutes to copy.  :-P 

The lesson, put all of the shares you normally use in fstab until Gnome gets this sorted out.

---

### Post by deimios on 2007-09-30
I had a similar problem (slow samba transfer) but I managed to solve it.

I have a gigabit connection too but on a 100Mbit switch. For some weird reason Kubuntu negotiated the speed to 10Mbit.

You can check this with:
```

sudo ethtool eth0 | grep -i speed

```

if the speed is anything other than 1Gbit  then you should run 
```

sudo ethtool -s eth0 speed 1000 

```

Your numbers might differ (if your NIC is not eth0 then change that/ if your network is 100Mbit then change  to speed 100)

Weird bug anyhow.

---

