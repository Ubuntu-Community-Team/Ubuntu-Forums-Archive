---
title: "problems with wpc54g v2"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by tjtansey on 2007-02-06
I just installed ubuntu and I am trying to install my wireless card (wpc54g v2).  I ran ndiswrapper but this is what the terminal screen reads:

tim@tim-laptop:/tmp$ sudo ndiswrapper -i lsbcmnds.inf
Installing lsbcmnds
tim@tim-laptop:/tmp$ sudo modprobe ndiswrapper
Password:
tim@tim-laptop:/tmp$ echo ndiswrapper>> /etc/modules
bash: /etc/modules: Permission denied

I am new to Linux so keep in mind I'm mind i'm next to clueless as far as commands go, but am I doing something wrong?
Thanks

---

### Post by gradedcheese on 2007-02-06
That last command should be run with sudo, like so:

sudo echo ndiswrapper>> /etc/modules

Note that the error you were given is "permission denied", this is a hint that you need sudo to write to that file (as with all files in /etc).  This command will write 'ndiswrapper' to end of the the /etc/modules text file, by the way.

---

### Post by tjtansey on 2007-02-06
ok I tried that and still got the error, here's a snapshot of the screen

tim@tim-laptop:~$ cd /tmp
tim@tim-laptop:/tmp$ sudo modprobe ndiswrapper
Password:
tim@tim-laptop:/tmp$ sudo echo ndiswrapper>> /etc/modules
bash: /etc/modules: Permission denied

How on earth can permission be denied when I just installed ubuntu and have no other user accounts?
Is is possible that I unzipped in the wrong directory?

---

### Post by gradedcheese on 2007-02-06
Instead of using echo, just open the file with a text editor (here's an example with a graphical editor), scroll to the very bottom, add a new line, type in "ndiswrapper", save, and exit.

sudo gedit /etc/modules

---

### Post by tjtansey on 2007-02-06
Ok it works now here's what I did:

Download ndiswrapper 

download windows driver

open terminal

unzip ndiswrapper

mkdir linksys

unzip driver to linksys

cd linksys

sudo ndiswrapper -i (driver inf file)

cd /
sudo modprobe ndiswrapper
gedit /etc/modules (this opens text editor)
insert line "ndiswrapper" to last line in file then save and exit

reboot and I was ready to go;)
Thanks for your help graded cheese

---

