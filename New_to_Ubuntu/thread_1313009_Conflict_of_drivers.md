---
title: "Conflict of drivers?"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by nnjond on 2009-11-03
Hi

I did a clean install of 9.10 and Hardware Drivers recommended i install NVIDIA "173'. After installing nothing much happened so i warm-booted.

I couldn't get beyond the spash screen except to a flickering command prompt so i,ve gone into recovery mode.

I guess there is a conflict of drivers and i'm hopping it's a simple matter to remove the latest one. Can anyone advise me please?

No doubt i could load the live cd.

---

### Post by CaptainMark on 2009-11-03
can you get to a terminal prompt or use a live cd to access your main drive. post back the contents of /etc/X11/xorg.conf 
the section display should tell you what drivers its trying to use, (i think, i regard myself as still a noob anyway but had to deal with this file when i made the mistake of buying a ati card)

---

### Post by nnjond on 2009-11-03
Thanks for yr interest. i'm at a prompt in the live cd.

ubuntu@ubuntu:/home$ cd /home/nnjond
bash: cd: /home/nnjond: No such file or directory
ubuntu@ubuntu:/home$ 
ubuntu@ubuntu:/home$ cd /etc/X11/xorg.conf
bash: cd: /etc/X11/xorg.conf: No such file or directory
ubuntu@ubuntu:/home$ cd /etc/X11
ubuntu@ubuntu:/etc/X11$ xorg.conf -l
xorg.conf: command not found
ubuntu@ubuntu:/etc/X11$ ls xorg.conf
ls: cannot access xorg.conf: No such file or directory
ubuntu@ubuntu:/etc/X11$ ls
app-defaults             fonts    xinit       Xsession          XvMCConfig
cursors                  rgb.txt  xkb         Xsession.d        Xwrapper.config
default-display-manager  X        Xresources  Xsession.options
ubuntu@ubuntu:/etc/X11$ 

Not confident i'm in the right place. Sorry

---

### Post by CaptainMark on 2009-11-04
looks like your looking in the live cds /etc directory, you will need to mount your hdd somewhere probaly /mnt is the best place and then look in the /etc directory on that so you will probaly find these codes should get you the driver info
```
sudo mkdir /mnt/hdd
sudo mount /dev/sda1 /mnt/hdd
cd /mnt/hdd/etc/X11
cat xorg.conf
``` this presumes your hdd is sda1 it may be different to find out run```
sudo fdisk -l
```and identify your hdd based on the size of it and edit the above commands to fit

EDIT: the command cat will let you veiw the text content of a file you type after it, by typing in just a file name eg, [email]mark@mark-desktop:~$/etc/X11/xorg.conf[/email] your trying to execute a text file which wont do anything unless its a bash script (thats something else all together,)

---

