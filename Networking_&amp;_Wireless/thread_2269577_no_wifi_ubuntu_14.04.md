---
title: "no wifi ubuntu 14.04"
date: 2015-03-16
forum: Networking &amp; Wireless
---

### Post by Kari_Svahn on 2015-03-16
Totally new on this forum, Hi!
I have a Dell Inspiron 1525, using ubuntu since som years. Recently uppgraded to 14.04. Some days ago, when I reloaded the new recommended files, I lost connection to my wifi. I can not see any network to chose. I've looked att several threads on the forum and tried to do the commands in the terminal window, but nothing helps. What to do? Please, help me!
/Kari

---

### Post by Hadaka on 2015-03-16
Hi , Kari please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe b43
```
thanks

---

### Post by Kari_Svahn on 2015-03-17
Waow, this solved my problem emediatelly, I didn't even have to reboot. I can't thank you enough. So, this will continue to work now?

---

### Post by Kari_Svahn on 2015-03-17
No, I lost it again. At first I could see all networks available as usual. When the computer went black to save energy, I lost my own network, but could see others. Then I restarted the computer, and now it's the original problem again, I can see no wifi networks at all.

---

### Post by Kari_Svahn on 2015-03-17
When I do the commands you gave me, I find the wifi again. But it would be nice if it didn't disappear...

---

### Post by Hadaka on 2015-03-17
Hi Kari, please do the commands i gave you and then do..
```
sudo su
 *echo b43* >> /*etc*/[I]modules
[/I] exit
```
thanks.
igonore any offer of a popietary or additional drive

also please mark this solved if it works for you.

---

