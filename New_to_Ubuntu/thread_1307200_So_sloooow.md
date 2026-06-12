---
title: "So sloooow?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by Loki57701 on 2009-10-30
My system is slow after the 9.10 upgrade. Sometimes it takes up to 30 seconds for a program like firefox, f-spot or banshee to open (just a few examples), and even the boot up time is pretty slow. I have decent specs:

intel core 2 duo 2.53Ghz
4Gb memory
320Gb HD X 2
nVidia 9800GT 512mb

So that shouldn't be a problem. I also noticed while watching my system monitor that core 1 is almost always maxed out and the 2nd core is not far behind.. not for doing processor intensive things either. Things like copying a file or opening a program.. as far as I know that shouldn't tax a processor at all. My system feels like its running a bunch of virtual machines or something. Can anyone help me out here?

---

### Post by claymater on 2009-10-30
> **Loki57701 said:**
> My system is slow after the 9.10 upgrade. Sometimes it takes up to 30 seconds for a program like firefox, f-spot or banshee to open (just a few examples), and even the boot up time is pretty slow. I have decent specs:

intel core 2 duo 2.53Ghz
4Gb memory
320Gb HD X 2
nVidia 9800GT 512mb

So that shouldn't be a problem. I also noticed while watching my system monitor that core 1 is almost always maxed out and the 2nd core is not far behind.. not for doing processor intensive things either. Things like copying a file or opening a program.. as far as I know that shouldn't tax a processor at all. My system feels like its running a bunch of virtual machines or something. Can anyone help me out here?

I have noticed some slow things starting (mainly firefox)

---

### Post by hacker128 on 2009-10-30
When it is slow, can you post the output of "ps axl"? That will show all running processes.
Also try running "top" when slow, give the first few items.
Here, take this script:
```

rm ~/Desktop/SystemLoadLog.txt
echo "Attach this file to your post: it's the paperclip icon." > ~/Desktop/SystemLoadLog.txt
ps axl >> ~/Desktop/SystemLoadLog.txt
top -b -n 1 >> ~/Desktop/SystemLoadLog.txt
lshw >> ~/Desktop/SystemLoadLog.txt
notify-send "System Info Collection finished. Now post me!"
firefox "http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8202142" &
gedit ~/Desktop/SystemLoadLog.txt

```

---

### Post by Loki57701 on 2009-10-31
Unfortunately the .txt file exceeds the forums upload size limit.. I can post ps axl on here if you want? It's alot of output though..

---

### Post by humphreybc on 2009-10-31
Try enabling the "proposed" updates and check for new updates. There were some Firefox ones released today that seemed to have sped up Firefox loading times.

---

