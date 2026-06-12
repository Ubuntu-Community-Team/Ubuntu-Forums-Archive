---
title: "virtualbox help."
date: 2010-01-18
forum: New to Ubuntu
---

### Post by ja660k on 2010-01-18
hey guys, 

how can i let the operating systems i run on virtualbox access my cdrom? when there is a cd in it?

or USB when there is one in?

thanks in advance

---

### Post by alwayshere on 2010-01-18
when in virtual box there is a menu at bottom of the window that will pop up when ya run the mounse over it . 

click the install guest additions and that should sort ya out

---

### Post by baddog144 on 2010-01-18
Down the bottom right there should be a USB icon and a CD icon. right-click these and all will become clear :)

---

### Post by ja660k on 2010-01-18
hrmm it doesnt seem to be working, 

does it matter that its not a supported os?

its under the category linux->other

---

### Post by underquark on 2010-01-18
What is the OS?
-Intrigued.

---

### Post by 3rdalbum on 2010-01-18
In the Virtual Machine Settings, you choose either an ISO disc image to use as a CD-ROM, or enable CD-ROM passthrough to let the CD show up.

---

### Post by SirBismuth on 2010-01-18
Have you enabled the USB Controller in your VM's settings?.  Note that you will have to shut the VM down to do this.

Also, are you using the OSE or PUEL editions of VirtualBox, afaik, the OSE version doesn't have USB support, possibly not CD-ROM either.

B

---

### Post by Silent Warrior on 2010-01-18
3rdalbum seems to have the solution for the OP, as far as I understand.

SirBismuth: I seem to have used this more often than you of late. :) OSE has CD/ISO, but no USB. I know Mint lets you install the Guest additions on both OSE and... the other one. Couldn't say if that's Ubuntu policy, though.

---

