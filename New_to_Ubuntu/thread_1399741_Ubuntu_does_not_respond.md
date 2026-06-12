---
title: "Ubuntu does not respond ?"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by GauravVK on 2010-02-06
hey , i successfully installed Ubuntu 8.10 on my PC , i already had widows XP installed , so i wanted to dual boot . now that Ubuntu is installed , when i enter mu username and password , i just get a brown screen and nothing else . i tried waiting for an hour . pls help .

---

### Post by mushwars on 2010-02-06
in linux wait usually doenst really help. you need to find out what is wrong.

try going ctl + alt + f2
you should get to a login screen.. do so

then type this
```
cat /var/log/Xorg.0.log | grep EE
```you could also cat /var/log/Xorg.0.log | tail and search look for anything out of the ordinary. If possible I would like to see the entire log.


edit: a dmesg | tail might be in order too, see if you see anything that looks odd. A paste of that would be nice...
do this 
```
cd ~ && dmesg > ubuntuerror.txt
```than pastebin that by putting it on a flash drive.

do this.
put in your flashdrive.
```

sudo mkdir /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
cd /mnt/usb
sudo cp /var/log/Xorg.0.log /mnt/usb
sudo cp ~/ubuntuerror.txt /mnt/usb
cd ..
sudo umount usb/

```

then put your flashdrive in a working computer and post the conetnets of the files

---

### Post by GauravVK on 2010-02-06
i tried that but it does not respond to
Ctrl + alt + F2

---

### Post by mbzn on 2010-02-06
Does the live cd work fine?

Try burning at lower speed, it could be something on the install disc

---

### Post by mushwars on 2010-02-06
> **GauravVK said:**
> i tried that but it does not respond to
Ctrl + alt + F2
I have seen that problem where it kills the whole graphics card when you startx. do you mind telling me what kind of graphics card you have?


ps. dont worry if it was the cd's fault you wouldnt have gotten this far.

---

### Post by GauravVK on 2010-02-06
i got the login screen .
i entered the username and password successfully .
then i entered the code
cat/var/log/Xorg.0.log|grp EE 

then it says no such file found .

---

### Post by GauravVK on 2010-02-06
i am using intel82845G graphics controller .

---

### Post by mushwars on 2010-02-06
> **GauravVK said:**
> i got the login screen .
i entered the username and password successfully .
then i entered the code
cat/var/log/Xorg.0.log|grp EE 

then it says no such file found .

are you positive you typed it EXACTLY as I did? with spaces capital X more spaces and there is an e in grep.

That log file has everything I need in it to tell you what you have to do to get it working :)

---

### Post by GauravVK on 2010-02-06
as I entered 
sudo mount /dev/sdb 1 /mnt/usb
it says 
mount: only root can do that .

---

### Post by mushwars on 2010-02-06
> **GauravVK said:**
> as I entered 
sudo mount /dev/sdb 1 /mnt/usb
it says 
mount: only root can do that .
then you have more problems than just your graphics going on.
sudo allows you to run as root, if for some reason you are out of the wheel group or your sudo config file got changed you have bigger problems.

---

### Post by GauravVK on 2010-02-06
shall i delete this installation and install it again ?
if yes , then how do i do that ?

---

### Post by mushwars on 2010-02-06
now that you mention it, you say a "brown" screen. brown as in ubuntu desktop background brown? if so hit alt + f2 and type nautilus I think for some odd reason nautilus didnt start.

do you have a mouse? can you right click and get a menu?

---

### Post by GauravVK on 2010-02-06
yes , i have a mouse , but the right click does not give me a menu , infact it gives me nothing .

---

### Post by GauravVK on 2010-02-06
thats ubuntu brown .

---

### Post by mushwars on 2010-02-06
did you try alt + f2?

if you have a middle button try clicking that, if not click both the left and right button 

( this reminds me of when I first started using sawfish it is the same as what you have now only a black background then you cant just left click or right click you have to middle click, took me a LONG time to figure it out, at first I thought it didnt work ) <-- ignore that

---

### Post by GauravVK on 2010-02-06
tried alt + F2 , does not help .

---

### Post by mushwars on 2010-02-06
I am out of Ideas, maybe someone else will read this thread.

---

### Post by GauravVK on 2010-02-06
i hope so . neways , thanks a lot mate . cheers .

---

### Post by galdren on 2010-02-06
some general questions:

what are your computer specs?

which version of ubuntu did you install? (amd64/etc..)

did your installation work before? Or was it like this at first log-in?

if it worked before, did you try installing drivers for your graphics card or any other significant software?

---

### Post by GauravVK on 2010-02-06
i have 768 MB of RAM , intel pentium processor ,  intel 82845G graphics controller , intel 82845 motherboard , 160 GB of HDD . I am dual booting my system with windows XP , This was my first time with Ubuntu . it got installed properly , as I logged in successfully , i got the UBUNTU brown screen and nothing else . It does not respond to keyboard or mouse clicks , nothing . pls help .

---

### Post by galdren on 2010-02-06
---

---

### Post by galdren on 2010-02-06
well the live cd should install an almost identical copy to your hard drive...yeah I'd say try reinstalling it from the live cd

use a 32-bit version in case your current live cd is 64-bit

if that also doesn't work, try kubuntu (which is ubuntu without gnome :D)

---

