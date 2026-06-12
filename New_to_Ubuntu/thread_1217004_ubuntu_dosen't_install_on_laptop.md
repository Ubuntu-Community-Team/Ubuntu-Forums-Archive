---
title: "ubuntu dosen't install on laptop"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by Art3mis on 2009-07-18
Hi,

I just tried installing Ubuntu on my new Laptop.

When trying to set partitions etc. nothing happens and after 15 min or so , 

I get a message that tells me something about an error. I don't remember

what the error was, and I certainly can't redo this whole operation, cause 

it takes too much time. Straight to the point Ubuntu (x64) dosen't want to 

install for some reason concerning my partitions. I have one windows 

and one HP-Recovery partition. Also when running Ubuntu as a live-cd I do not have any sound.

My laptops specs are: 

Amd Turion X2 Dual Core

320 Gb Hard drive

4 gb ram

Ati Radeon HD 3200



Can anyone help?

---

### Post by philcamlin on 2009-07-18
format the partition then try again :popcorn:

---

### Post by Art3mis on 2009-07-19
can't I want to install ubuntu side by side to windows so I can dual boot

---

### Post by philcamlin on 2009-07-19
try wubi ?

itll simplify what you wanna do :)

---

### Post by Art3mis on 2009-07-19
what's Wubi?

---

### Post by Art3mis on 2009-07-19
Oh ok got It thanks I will give it a try

---

### Post by Art3mis on 2009-07-19
sorry but i can't find the thread solved button any more... were is it?

---

### Post by philcamlin on 2009-07-19
no problem 

you install it inside of windows :)

---

### Post by ben105 on 2009-07-19
I have done the same last weekend.

Make enough free space on your machine. 

Download the Ubuntu iso file and burn it.

Insert the disk, restart the machine with changed boot

Ubuntu launch manager will come up and choose "Install inside Windows"

If you have 2 partitions, then choose the one where you have or don't have Windows on it. (C:\Windows, D:Data)

Differences of this procedure: 

1. If you install Ubuntu inside C:\, then Ubuntu will not recognise your Windows partition and your data on it. 
 
2. If you have all your data on D:\Data and you install Ubuntu on C:\, then it will recognise the D:\data files.

Give Ubuntu as much free space as possible (I chose 30 GB)

Finish the installation and re-start the machine.

Now, you will launch with Windows booter and Windows is on the first position, Ubuntu on the second.

If you go in Windows to Control Panel -Add/Remove Programs, you will find Ubuntu there. If you want to remove Ubuntu later, then it's 1 click and it disappears.

---

### Post by cooper77z on 2009-07-19
Just why is it that you want to run windows and linux side by side?

---

### Post by Art3mis on 2009-07-20
I want to install windows and linux side by side, cause I want to use both OS's

---

### Post by cooper77z on 2009-07-21
Totally understandable. I just don't want to run both os's myself. I am seriously contemplating constructing a complete off-line system for privacy reasons.

But, I'll still talk to you on the internet, I promise.

---

