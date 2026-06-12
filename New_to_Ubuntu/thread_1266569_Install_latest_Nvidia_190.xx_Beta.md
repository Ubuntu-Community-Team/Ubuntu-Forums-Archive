---
title: "Install latest Nvidia 190.xx Beta?"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by MrWeenus on 2009-09-14
Hello there.
I'd like to install the latest nvidia 190xx beta from nvidia.com on Ubuntu 9.04 x86 (32bit).

I've tried the others in the past and all I did was screwing up everything.
So I need exactly step by step instructions.

Also if you guys need to know I have 9600GT 512MB PCI-E.

---

### Post by DasEi on 2009-09-14
You run hardy or newer

- you downlaoded the NvidiaBlah.run file

- you did - sudo apt-get update && sudo apt-get upgrade
          - sudo apt-get install build-essential
          - sudo cp /etc/X11/xorg.conf  /etc/X11/xorg_backup
            (case things go worse, copy it bacl)


Ctrl-alt-backspace or F1 to command line

- cd ~/Desktop        (assuming your download is there)

sudo sh NvidiaBlah.run

sudo /etc/init.d/gdm restart  (assuming running gnome) 

k ?

---

### Post by pedro3005 on 2009-09-14
Check out this great guide: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)
It was made for 185.18 but works with the latest beta, just be sure to read it all.

---

