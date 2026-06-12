---
title: "Wubi free disk space"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by Sumsi on 2011-05-24
Hi, I know nothing whatsoever about programming, so I used Wubi to install Ubuntu and be able to dual boot, because I'm not quite ready to leave windows completely (mainly for the sake of iTunes, but hey)

I have 2 hard drives on my PC, C and D, when I first installed ubuntu via Wubi I only had 500MB of free space, which was fairly useless when I wanted to install MS office through Wine, so I de-installed ubuntu, and re-installed it (again through Wubi) deliberately selecting the D drive that has 54Gb free... however when I booted up it Ubuntu it told me I still only had 1.1gb free... 

I don't really understand why or what I have to do to sort it out, any help would be appreciated and I should probably clarify that my technical skills are virtually non-existant when it comes to PCs, so I can't do a "real" dual-boot, and I haven't the first clue about creating partitions and things! 
Thanks in advance!

---

### Post by Rubi1200 on 2011-05-24
Hi and welcome to the forums :-)

There are some limitations to using Wubi, including the fact that the default install is 17GB with a maximum of 30GB.

You can, however, add more space to the Wubi root.disk:
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

Please post the output of the following command from the terminal in Ubuntu so we can see a more precise accounting of the disk usage:

```
df -H
```

---

### Post by beew on 2011-05-24
> **Sumsi said:**
> Hi, I know nothing whatsoever about programming, so I used Wubi to install Ubuntu and be able to dual boot, because I'm not quite ready to leave windows completely (mainly for the sake of iTunes, but hey)


If you just need Win for one program then instead of installing a crippled version of Ubuntu in Windows why not do it the other way around? Make a real install of Ubuntu and run windows in virtual box.

---

### Post by Paqman on 2011-05-24
If you open up System Monitor it'll show how much free disk space you have. Some things you can do to quickly free up disk space:

Open a terminal window and feed it the following commands:
```
sudo apt-get autoremove
```
```
sudo apt-get clean
```

You should also empty your trash, and you may want to uninstall any old kernels if you still need more space. Let us know if you want to do that and we'll show you how.

---

