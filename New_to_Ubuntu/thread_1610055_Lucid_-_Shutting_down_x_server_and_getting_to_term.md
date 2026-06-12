---
title: "Lucid - Shutting down x server and getting to terminal"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by shanep-server on 2010-10-31
Ok i'm trying to get 260.19.12 installed on my Lucid 64 bit. I need to shut down x server and run NVIDIA-Linux-x86_64-260.19.12.run Problem is... when I type sudo /etc/init.d/gdm shutdown it kills gdm but doesn't bring me to a terminal. The other way I tried also killed gdm but didn't give me a terminal. I tried to use terminal at splash screen but it wouldn't open with sh ./NVIDIA..xxx I tried to use nautilus to execute 260.19.12.run but it said I have to kill gdm first. Any ideas how I can go about getting this done? 

I've also tried using ppa to install 260.19.12 but having Lucid installed 173.xxx.xxx if I was using 10.10 it would have installed 260.19.12 an since Maverick isn't the greatest I would like to keep 10.04.1

---

### Post by bioterror on 2010-10-31
Press ctrl+alt+f1
Login to the TTY1
say "sudo service gdm stop"
do your spells with the nvidia driver
"sudo service gdm start"
ctrl+alt+f7 will get you back to the X. Or F8 if F7 doesnt work.

---

### Post by shanep-server on 2010-10-31
ctrl + alt + f1 doesn't do anything but lock up my computer... nothing appeared an my cursor disappeared.

ctrl + alt + f7 brings the cursor back though.

Would this have anything to do with using 

gconf-editor>apps>metacity>default>compositing ?

---

### Post by shanep-server on 2010-10-31
Ok I figured it out... to install the 260.18.12 in Lucid

Requires 2 pc's on same network.

Desktop - needs NVIDIA-Linux-x86_64-260.19.12.run installed

Laptop - needed to install drivers on Desktop

From Desktop... Go to synaptic package manager > edit > mark by task > openssh server... apply and install

terminal > sudo gedit /etc/modprobe.d/blacklist.conf

add these to the file to blacklist modules

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv 

save n exit

From Laptop - terminal - type - ssh "ip of Desktop" hit enter

verify key type "yes" hit enter

from terminal prompt > sudo service gdm stop

> sudo sh ./NVIDIA-Linux-x86_64-260.19.12.run ( follow instructions )

> sudo service gdm start

login at your desktop and drivers should be up and running.

now my nvidia settings manager was not present after install so i went too system>preferences>monitors and it presented me with an option to use the nvidia managers which doesn't have a menu listing so I clicked yes and the nvidia settings manager appeared... I then pinned the manager to my docky for quick access in the future.

If you have any questions just ask

---

