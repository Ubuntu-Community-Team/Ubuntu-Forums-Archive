---
title: "ubuntu 10.10 loading to terminal not to desktop"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by indyeah on 2010-11-08
well i cleaned my cpu and i dont know what i did but now whenver i try to boot ubuntu,it shows me GRUB menu and then when i choose "ubuntu generic pie" it takes me straight to ubuntu tty1 terminal log in asking for my login name and password...please help me to get "normal" ubuntu login back so i can go to my desktop
thanks

---

### Post by indyeah on 2010-11-08
umm anyone???
i mean i cant login to ubuntu desktop instead it always shows me terminal full screen window.....

---

### Post by sikander3786 on 2010-11-08
What happens if you type

```
sudo service gdm start
```

If it says it is already running, try

```
sudo service gdm restart
```

If it doesn't bring up the login screen, press Alt + Ctrl + F7. Does it show anything?

Please post any errors encountered there.

---

### Post by toekneewood on 2010-11-08
Run the following command
```

sudo nano /etc/default/grub

```
The above is the grub boot menu.  You should find what you are looking for.  Make sure you run the following after
```

sudo update-grub

```

---

### Post by indyeah on 2010-11-08
> **sikander3786 said:**
> What happens if you type

```
sudo service gdm start
```

If it says it is already running, try

```
sudo service gdm restart
```

If it doesn't bring up the login screen, press Alt + Ctrl + F7. Does it show anything?

Please post any errors encountered there.


when i pressed Alt + Ctrl + F7.it gave me a long list but one thing particularly caught my eye.."mountall failed"

also firestarter firewall showed fail

---

### Post by indyeah on 2010-11-09
i really cant use my ubuntu....wat else can i do to make my ubuntu workable???

---

### Post by bioterror on 2010-11-09
> **indyeah said:**
> i really cant use my ubuntu....wat else can i do to make my ubuntu workable???

Login to TTY
run next commands:

```
sudo Xorg -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo reboot
```

And we'll see if gets you to graphical screen, or even close to it.
If you get some problems you can always say:

```
sudo rm /etc/X11/xorg.conf
```

Have you updatet your Ubuntu before this happened?

---

### Post by indyeah on 2010-11-09
@bioterror
actually yes i did update my ubuntu using update manager few days ago,those were some software updates plus some critical security updates dont remember exactly.

plus i took my graphic card out of my cpu yestreday and when i tried logging in it gave me this problem.

let me try your method and then see what happens

will post back soon

---

### Post by indyeah on 2010-11-09
sudo Xorg -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo reboot


well i ran this script.the login screen was back but the main screen was all upside down and text was mirror image of original...quite weird

---

### Post by sikander3786 on 2010-11-10
> **indyeah said:**
> sudo Xorg -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo reboot


well i ran this script.the login screen was back but the main screen was all upside down and text was mirror image of original...quite weird
If it is yet unsolved, please post the output of

```
cat /etc/X11/xorg.conf
```

Here is a similar problem.

[http://ubuntuforums.org/showthread.php?t=1106761](http://ubuntuforums.org/showthread.php?t=1106761)

This link might help you understand xorg.conf.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by indyeah on 2010-11-11
well i reinstalled ubuntu this time not as wubi but as seperate OS in another partition.anyways thanks for the links..i will check them out

edit:i think i figured out why my ubuntu installation behaved that way..i took out my graphic card out of my cpu and it affected my monitor and config/resolution somehow.

---

### Post by ceejay724 on 2010-11-11
Hello

I had the same problem with ubuntu 10.04

The ```
sudo service gdm start
``` command worked. 

I had to install gdm first though.
[CODE]sudo apt-get install gdm[CODE]

Thank you
:)

---

