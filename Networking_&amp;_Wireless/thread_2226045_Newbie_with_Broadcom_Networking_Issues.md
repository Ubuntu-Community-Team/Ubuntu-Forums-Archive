---
title: "Newbie with Broadcom Networking Issues"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by Caleb012 on 2014-05-24
I certainly am excited about the new world of Linux. Thank you to all who work to help with solving issues like this one. I have a Broadcom card and it has worked previously but I reinstalled Ubuntu 14.04 and am unable to get either the ethernet or wireless working. I have searched the internet and tried many a suggestion but to no avail.  I am running a Dell Inspiron 1501. Thank you for any assistance you may offer. ( I can imagine you are tired of the networking questions as I see many, many issues with such. Is it possible for this to be addressed in future distros? .........Newbie ignorance showing here.......)

---

### Post by Hadaka on 2014-05-24
Hi, since you have no internet access we'll make this
as easy as possible. Please open a terminal ctl/alt/t
then COPY and paste in this command.
```
lspci -n | egrep '0200|0280' | awk '{print$3}'
```
post back the output
thanks.

---

### Post by Caleb012 on 2014-05-24
14e4:4311
14e4:170C

---

### Post by Hadaka on 2014-05-24
hi, first, connect your ethernet cable so it will
be ready for internet access, then please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe b44
```
then....BOOT <<=this is a must do.
you should now have ethernet internet access.
with the ethernet cable still working to the interenet
please do..
*First command may take some time
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
dissconnect the cable and boot again
you should now have wireless access

to mark solved ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Caleb012 on 2014-05-24
I get rm: cannot remove '/etc/modprobe.d/blacklist-bcm43.conf' no such file or directory

---

### Post by Hadaka on 2014-05-24
good we didnnt want it any way...thats why we are removeing it !!
No problem..continue on..you are doing great.

---

### Post by Caleb012 on 2014-05-24
I do the sudo modprobe b44 command ....enter my password and nothing happens.....If I attempt to close terminal window...I get "There is still a process running....closing terminal will kill it." I certainly wish theses things were easier........lol!

---

### Post by Hadaka on 2014-05-24
when you enter your password.,,,it is invisable
that is for security reasons.....enter your password then hit ENTER
then you can close the terminal.
not to worry...you are new...and doing just fine

---

### Post by Caleb012 on 2014-05-24
I am used to using the Terminal and seeing a list of items being installed etc........plus I was fearful.....when trying to close Terminal that I would disrupt   or kill the process. THANK YOU! THANK YOU! THANK YOU! I have a new hero.........MAY THE UBUNTU BE WITH YOU! Seriously.....Thank you for using your talent to help new Linux.....Ubuntu users! Your kindness is very much appreciated!!!

---

### Post by Hadaka on 2014-05-24
you are welcome Jay_Shelton, it is an honor to have you here
thanks for the interest, here is a link ->[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
that is a "sticky" at the top of the networking and wireless page....you probably didnt see it
but you mentioned if there were such a thing. Please feel free to post any questions you have
about linux or the operating system...there are some very very talented people here to help
you....welcome to Ubuntu !

---

