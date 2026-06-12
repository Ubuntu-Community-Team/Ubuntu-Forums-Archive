---
title: "ubuntu won't load"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by Def_101 on 2009-06-14
tried to change some network connection settings. and now os won't load. it gets part way through load screen then goes to text. it checks a few things but stops at 
reconfiguring network interface
ignoring unknown interface eth2=eth2
ignoring unknown interface ath0=ath0

any help would be appreciated can't really do much with it right now

---

### Post by Def_101 on 2009-06-14
this is what i did is there a way to change it back from command line





# The loopback network interface
auto lo
iface lo inet loopback
 auto eth2
#iface eth2 inet dhcp
 auto ath0
#iface ath0 inet dhcp
 # WLAN
allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
 wireless-essid [replace this with your network name!]
 wireless-key [replace this with your wep key (hex!)]

---

### Post by 123456789123456789123456 on 2009-06-14
What network settings did you change, and what did you change them to?
that could help identify what file was altered, could explain the error message, on the network reconfiguration.  It should never come up with reconfiguring network, not every time it loads, this usually only takes place, when the system was told that there was changes made, detection of new hardware, such as ethernet NIC, or wireless NIC.  Secondly, does it load into busybox?  basically text interface, not graphical?
If so we can perform the changes using vi text editor, if not, we may have to load up into live cd, to perform the correct changes.
First step after identifying this, would be to set the network settings back to what they were before you made changes, then attempt to make the changes, in a way that Ubuntu can handle, at least figure out what part in the new settings you applied caused the error.

---

### Post by Def_101 on 2009-06-14
post #2 is what i changed thanks for the quick reply
minus the wireless key
and yes it starts graphical then goes to text

---

### Post by 123456789123456789123456 on 2009-06-14
> **Def_101 said:**
> this is what i did is there a way to change it back from command line





# The loopback network interface
auto lo
iface lo inet loopback
 auto eth2
#iface eth2 inet dhcp
 auto ath0
#iface ath0 inet dhcp
 # WLAN
allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
 wireless-essid [replace this with your network name!]
 wireless-key [replace this with your wep key (hex!)]

yes, what file was edited?
Do you know the original settings?
the original settings need to be put back into file
you can use any text editor, I tend to use vi editor, problem is that there are keyboard commands that are used for vi, I can walk you through the process, and the commands.  I would need first off, the name of the file, and exact file location from /.
for instance /etc/ so on.
to access the file, you will need possibly sudo before the program vi name, only if the file requires root adiminstrator access to be changed.  if not vi alone would be enough, after vi type the location of the file, directly from the / as root structure on the hard disk.  simular to how you would open or run a command in windows, that is located in several sub directories.

---

### Post by 123456789123456789123456 on 2009-06-14
> **Def_101 said:**
> post #2 is what i changed thanks for the quick reply
minus the wireless key
and yes it starts graphical then goes to text

welcome, at least you have text mode, in text/console mode, are you shown as logged in, or does it log you off after GUI ends?
how much linux commands do you know?
I have this thread to e-mail me as soon as there is a reply to it.
so I will check back periodically.

---

### Post by Def_101 on 2009-06-14
this is the file 
gksu gedit /etc/network/interfaces


and i believe this is the original text
auto lo
iface lo inet loopback

---

### Post by Def_101 on 2009-06-14
when it loads and goes to text i can type but it doesn't do anything. i have to reboot and press escape to enter boot options and i am a newb

---

### Post by Def_101 on 2009-06-14
have to go to work will check back with you later

---

### Post by 123456789123456789123456 on 2009-06-14
> **Def_101 said:**
> this is the file 
gksu gedit /etc/network/interfaces


and i believe this is the original text
auto lo
iface lo inet loopback

to restart the computer from text, type shutdown -r
if that does not work
type poweroff
poweroff command will turn the machine off entirely.
using gedit program, should still work
when you get to text mode
type "logoff"
then "logon" ""your user name""
it will ask for password
type that in, you should be on.
do me a favor, and use the following command when you get loged on.
ls -l /etc/network/interfaces
and give me the output.
is the program gedit graphical or text based?

---

### Post by Def_101 on 2009-06-15
ok. the first place it goes to do system checks in text i can type but commands don't work.

---

### Post by Def_101 on 2009-06-15
at start up i can hit esc and then c to get to the command line but it shows up as Grub>

---

### Post by 123456789123456789123456 on 2009-06-15
> **Def_101 said:**
> at start up i can hit esc and then c to get to the command line but it shows up as Grub>

Just like it should.  By entering that command you excape out of load.  that should be like a built in busy box, see if command work, see if you can log in.

If you are able to logon, then the prompt should change to your user name

Of course if that does not work, you can restart the computer, go to the grub menu, by hitting excape, and edit grub.conf temporarilly to initiate runlevel 1 command

changing the runlevel will force the computer to start into text mode only.
would never load x, so it should not do a system check.

to change the runlevel, add the command init 1, to the grub configuration temp file, that will for the first time startup change the normal runlevel to 1, forcing system maintance text mode.

---

### Post by Def_101 on 2009-06-15
normal commands don't work here


i'm not sure exactly what your asking me to do and i was wondering if it may be easier to boot live cd and run this

sudo mkdir /media/Install
sudo mount -t ext4 /dev/sda1 /media/Install

i only have two partitions so it will be 1 and i use ext 4 file sys

---

### Post by Def_101 on 2009-06-15
then run
gksu gedit /etc/network/interfaces


  and put original text back
auto lo
iface lo inet loopback


save and reboot also remove live cd

---

### Post by Def_101 on 2009-06-15
run fdisk -l first in terminal of live cd to ensure proper partion number???

---

### Post by 123456789123456789123456 on 2009-06-15
> **Def_101 said:**
> run fdisk -l first in terminal of live cd to ensure proper partion number???

First off I would backup all personal data before trying this.
then identify the partition number, if Ubuntu is the only system on the disk, it should be sda1.

Run the commands you listed in two earlier posts.
Live cd would deffinatly allow you to do this, first however make sure you mount the file system, sometimes the live cd does not like mounting the disks.

What I was refering to, is when you boot the computer, at grub section where it says grub 1.5, there is the escape command that allows you to go into the grub menu.  you can there temporirly edit grub, select what type to load into, recovery mode, regular so on.
If you were to edit grub, and incerted the command init 1, that would tell grub not to load the GUI, Desktop of Ubuntu, and go strait to text mode.

---

### Post by Def_101 on 2009-06-15
back up is all on the pc i'm using right know so that is done.

for know i will go into live cd and see if i can get that partion to mount

---

### Post by Def_101 on 2009-06-15
it mounted know how would i go about getting into the terminal as myself?

---

### Post by Def_101 on 2009-06-15
ok i found the file in the file browser but it tells me that i don't have sufficient privileges to change it

---

### Post by Def_101 on 2009-06-15
got to go again will try other method later thanks

---

### Post by 123456789123456789123456 on 2009-06-15
Try this, in terminal type sudo and then the command
at password, press enter
the live cd user does not have a password
but using the sudo command allows you to run the command as root.

---

### Post by Def_101 on 2009-06-16
ok will try that. tonight or tomorrow when i get done work

---

### Post by Def_101 on 2009-06-17
ok sudo from the live cd doesn't work to access the mounted partition will need to edit using text

when i hit esc at start up

i hit e on
ubuntu kernel generic

then i am givin four options 

uuid
kernel
initrd
quiet

---

### Post by Def_101 on 2009-06-17
solved

load live cd

in terminal 

sudo gedit media/disk/etc/network/interfaces

changed my mess up back and all is now good

thanks for your tips

---

