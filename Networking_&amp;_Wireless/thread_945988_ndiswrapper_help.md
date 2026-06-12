---
title: "ndiswrapper help"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by Narel on 2008-10-12
[I]If there are drivers for several versions of Windows on the CD, use the most recent version. Drag and drop the contents of the folder - let's call it 'DriverXP' into your home directory in Ubuntu. Returning to the terminal, you should already be in your home directory, so navigate to the folder you just copied over by typing

cd DriverXP

or whatever the name of the folder was. Now load the driver into ndiswrapper:

sudo ndiswrapper -i <your_ralink_driver>.inf

where <your_ralink_driver> is the name of the .inf file in the folder you just copied over.[/I]

I try to drag the files into a a different folder, but it says i dont have permisson. I have the files on my desktop, but in terminal it always says bash.

---

### Post by Ayuthia on 2008-10-12
The quick way to do this in the Terminal would be to do the following:
```
sudo cp <file> <destination>
```This will copy the file (not move them) to where you want it to be.  The other way is to move the file:```
sudo mv <file> <destination>
```.  In case you did not know, replace the <file> with the location of the file (without the <>) and replace <destination> with the path of the directory where you want to put the file (again without the <>).  For example:
```
sudo mv /home/Fred/Desktop/rt71.inf /home/Fred/DriverXP
```The sudo will give you administrator privileges.

Hope that helps.  If you need more information, just let us know.

---

### Post by Narel on 2008-10-12
Thx.
I didn't know that. I'm going to try this now.

---

### Post by Narel on 2008-10-12
```
narel@Sonny:~$ sudo mv /home/Narel/Desktop/rt2500usb.inf /home/Narel/Public 
mv: cannot stat `/home/Narel/Desktop/rt2500usb.inf': No such file or directory 
narel@Sonny:~$ 
```

What did I do wrong?

---

### Post by Narel on 2008-10-12
I've moved it to a couple different places and terminal says there is no such file or directory. I know it exist because I'm looking at. A little help lol

---

### Post by Narel on 2008-10-12
Please, anyone. I've been working on this since Friday.

---

### Post by Ayuthia on 2008-10-13
> **Narel said:**
> ```
narel@Sonny:~$ sudo mv /home/Narel/Desktop/rt2500usb.inf /home/Narel/Public 
mv: cannot stat `/home/Narel/Desktop/rt2500usb.inf': No such file or directory 
narel@Sonny:~$ 
```

What did I do wrong?

Can you do the following:
```
ls -l /home/Narel/Desktop
ls -lF /home/Narel
```
I just want to verify that the file exists (and see the permissions) for rt2500usb.inf and /home/Narel/Public.

---

### Post by Narel on 2008-10-15
I just installed the beta version and I was able to access the internet "out of the box". Thx for your help

---

