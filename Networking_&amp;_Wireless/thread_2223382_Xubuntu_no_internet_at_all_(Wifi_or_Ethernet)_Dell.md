---
title: "Xubuntu no internet at all (Wifi or Ethernet) Dell Inspiron 1520"
date: 2014-05-10
forum: Networking &amp; Wireless
---

### Post by dylan20 on 2014-05-10
Hey all, I've searched and searched but I can't find a solution to the issues i'm having. I can't get any internet connection on my fresh installation of Xubuntu. Nothing happens once I plug in the ethernet and it doesn't recognize any wifi at all. I'd appreciate some help! thank you guys.

---

### Post by Hadaka on 2014-05-10
hi, please post the output of..
```
lspci -n | egrep '0200|0280' | awk '{print $3}'
```
thanks.

---

### Post by dylan20 on 2014-05-10
```
whalefish@whalefish-Inspiron-1520:~$ lspci -n | egrep '0200|0280' | awk '{print $3}'
14e4:170c
14e4:4311
```




sry not sure how to put the text in the 'code' thing, also I did this with no ethernet plugged in (not sure if that matters)

---

### Post by Hadaka on 2014-05-10
[URL="https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"]https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads


hi, while connect to the ethernet cable please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
[/URL]

---

### Post by dylan20 on 2014-05-10
```
sudo apt-get remove --purge bcmwl-kernel-source
```

worked just fine

but then I got this output 

```
whalefish@whalefish-Inspiron-1520:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove &#8216;/etc/modprobe.d/blacklist-bcm43.conf&#8217;: No such file or directory
```

---

### Post by Hadaka on 2014-05-10
Hi, that is not a problem, its just saying that
it isnt there,,,so GREAT glad its working..
please mark this thread SOLVED
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by dylan20 on 2014-05-10
No.... it's not working I still have no internet connection even with an ethernet plugged in.
 
none of the other commands past the```
 --purge bcmwl-kernel-source
``` work.

---

### Post by Hadaka on 2014-05-10
ok, i missread your response.sorry.
please do..
 ```
sudo modprobe b44
```
BOOT

now is the wired connection working??

---

