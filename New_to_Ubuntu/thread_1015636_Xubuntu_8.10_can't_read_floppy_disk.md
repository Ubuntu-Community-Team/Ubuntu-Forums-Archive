---
title: "Xubuntu 8.10 can't read floppy disk"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by 2blue on 2008-12-19
Hi 
I installed the new version of Xubuntu on my old laptop and the floppydisk station is not to be found any where. When I insert a diskette I hear the station tries to mount it, but the hardware is not recongized any where on the machine. 

This might not sound as a big problem since floppy disk are hardly ever used any more. However I was bragging to a friend of mine that I could try to print some material that he has stored on floppy disks. This is the 3 1/2 inch type. It worked in the previous version, but then I had Ubuntu. 

I have tried to install a package that are supose to read and format floppy disk but still no sign that Xubuntu can detect the hardware. Any idea of what to do?

---

### Post by plucky on 2008-12-19
Open a terminal and ```
sudo modprobe floppy
``` will load the floppy driver.

To make it load on every boot ```
sudo nano /etc/modules
``` and add the word **floppy** on a newline.


Good Luck

---

### Post by 2blue on 2008-12-19
Hi again
Floppy turned up on the desktop! I cannot make the last command work. When I restart computer no floppy can be found, I have to run "sudo modprobe floppy" every time it seems.

Another thing that is a bit strange is; I have to reboot the computer and open diskstati on to mount a new foppy. It sort of just takes one each session?

---

### Post by plucky on 2008-12-19
> I cannot make the last command work.


You have to open a terminal window to use that command.

What doesn't work?
What happens when you enter that command?
Does it ask for a password?

It doesn't echo anything when you enter your login password.You can instead use **mousepad** which is the default text editor on Xubuntu.

> Another thing that is a bit strange is; I have to reboot the computer and open diskstati on to mount a new foppy. It sort of just takes one each session?


What is diskstati? 

From a terminal,post output of the command ```
id
``` which should tell us if you are a floppy groupmember.

You should be able to double click on the icon on the desktop to mount a floppy.Also you have to right click and un-mount the floppy before you can use another.
After you un-mount the floppy give it some time to write the data to the floppy as sometimes linux doesn't write output to the device straight away.


Good Luck

---

