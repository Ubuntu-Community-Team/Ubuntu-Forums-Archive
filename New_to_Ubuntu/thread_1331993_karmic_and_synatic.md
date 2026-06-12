---
title: "karmic and synatic"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by manners2345 on 2009-11-19
How space do I need on hard drive to update to karmic?? My hard drive is 10GB, I have 4+ GB on it.

In synaptic it shows in NOT INSTALLED(residual Config), maybe 100 items, is there anyway to mark them for complete removal all at one time, I have been looking cannot find;);)

---

### Post by cariboo on 2009-11-19
Just mark the list of files the same way you would any other list of files. Click on the first file, then scroll down, hold the shift key and click the last file. Next right click the list of miles and select mark for complete removal.

The alternative way to do it is to open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get autoremove
```

and then

```
sudo apt-get clean
```

You can just highlight the command and copy and paste them into a terminal instead of having to type the command.

The first command removes all the unneeded dpendencies, and the second command removes all the archived packages from /var/cache/apt/archives. The two commands can free up quite a bit of space on your hard drive.

I just upgraded one of my vm's to karmic and it had to download about 1300 files.

---

### Post by lgiordano on 2009-11-19
I found this post very helpful in clearing space by getting rid of unnecessary files:

[http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")

---

### Post by manners2345 on 2009-11-20
Sir:
  Thank you for your help!!

  Tried to use the apt-get clean command
    Got back reply,  unable to resolve host name,
     This also maybe why on the network icon there is a RED X and when I go to the network there is nothing to configure, no DNS, or Host name, the internet does work, I can ping, and traceroute, and download.

Thank you for any help

---

### Post by oldos2er on 2009-11-21
> **manners2345 said:**
> In synaptic it shows in NOT INSTALLED(residual Config), maybe 100 items, is there anyway to mark them for complete removal all at one time, I have been looking cannot find;);)

 Not installed=not installed.

---

