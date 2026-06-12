---
title: "Upgrade to maverick not working"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by telovin on 2011-01-21
Hi,
I was upgrading my ubuntu from lynx to maverick. Its stuck on installing upgrades. The terminal says 

```
 unpacking ttf-kacst 
```

The time shows 
```
about 12 minutes remaining.. 
```

Its stuck on this dialogue for past 6-7 hours. Dunno what to do..

---

### Post by NightwishFan on 2011-01-21
If it continues to stall I would just cancel it, if there is no such option (I do not think there is). I would press alt+f2, type xkill and click the window that is the upgrade manager. Then open a terminal and type:
sudo apt-get -f install. It should finish the upgrade.

Please note this is a last resort. I would wait for another few second opinions first before you try this.

---

### Post by lotus@terminal on 2011-01-21
There was a previous problem like this one on the forums. It might solve your problem. [http://www.uluga.ubuntuforums.org/showthread.php?t=1643008](http://www.uluga.ubuntuforums.org/showthread.php?t=1643008)

---

### Post by garvinrick4 on 2011-01-21
It has already downloaded and is unpacking I would use post #2's thought:
```
sudo apt-get -f install
```
or:
```
sudo dpkg --configure -a

```

---

### Post by telovin on 2011-01-21
Before I saw any of these replies, my system was stuck.
So I restarted the system n now it shows
     
      ```
install problem. Was not able to configure gnome smthing smthing. 
```It shows ubuntu 10.10 now

So I am currently logged in using live cd (of karmic koala)
Can I do the edits that garvin n nightwishfan suggested from this live cd? Kindly help. I think i cant but still I'll try
Guess my impatience has cost me so much :(

---

### Post by telovin on 2011-01-21
```
ubuntu@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo dpkg --configure -a
ubuntu@ubuntu:~$ 

```
This is from Live cd terminal. Guess I have to go back to ubuntu desktop terminal. But when booted from harddisk, it loads ubuntu n i get a somewhat pink screen which says 

```
ubuntu 10.10. install problem! Configuration of gnome dint complete or smthing like that. contact computer administrator.
```

---

### Post by NightwishFan on 2011-01-21
You should not have rebooted, however this is fixable. Hold shift while booting and choose "recovery mode" when prompted. When you get to a menu choose "root" or "root shell" (something with root). Then run:
```
sudo apt-get -f install
```

---

### Post by telovin on 2011-01-21
Damn happy to hear its fixable :) Let me try that out right now. Thanks nightwish for keeping my hopes up!

---

### Post by telovin on 2011-01-21
[SIZE="3"]Hey Nightwish,
Thanks a ton! That just did the trick, I went to recovery mode - net root n when i typed the above command, it had asked me to type 

```
dpkg --configure -a 
```

(something like that.. forgot the exact command)

I managed to upgrade to the latest version available without spending much time!(I meant I could resume n complete installation successfully.) [During this process, I became greedy n went for THE LATEST VERSION!:)]

I had a problem of grub previously and now Grub is loading beautifully n showing all the entries! I am able to log on to Ubuntu n windows smoothly.

You are awesome dear Nightwishfan!:KS

Thanks a lot for helping me out  Nightwish!
My thanks to garvinrock n lotus@terminal[/SIZE]

---

### Post by lotus@terminal on 2011-01-21
No problem. :)

---

