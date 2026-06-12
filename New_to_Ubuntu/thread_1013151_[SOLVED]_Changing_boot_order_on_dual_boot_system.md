---
title: "[SOLVED] Changing boot order on dual boot system"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by Norm24 on 2008-12-16
Vista is at the top of the list in Grub.I searched through tons of threads and can't find an answer.

How do I change the order of the boot.lst file?

---

### Post by ieee488 on 2008-12-16
I'm not sure what you mean by changing boot order.

If you want to change the default, look for the line that says **default**. It will be followed by a number. Change that number.

---

### Post by doobiest on 2008-12-16
sudo gedit /boot/grub/menu.lst

you will see sections for vista and ubuntu, you will also see the default listed in there, just change it.

---

### Post by Norm24 on 2008-12-16
> **doobiest said:**
> sudo gedit /boot/grub/menu.lst

you will see sections for vista and ubuntu, you will also see the default listed in there, just change it.

Thanks dude.Solved easily.

---

### Post by doobiest on 2008-12-16
Word

---

### Post by historical on 2009-02-06
Quote: originally posted by Doobeist

"you will see sections for Vista and Ubuntu, you will also see the default listed in there, just change it"

I have recently installed linux Ubuntu as a dual boot system, but with XP, not Vista. By default Grub loads Linux but my family do not want to have to select Windows every time and do not want Linux.

I have typed in "sudo gedit /boot/grub.menu.1st" but when I hit return, all I get is a new blank text editor box with nothing in it but a tab labeled "menu.1st" and a blinking cursor. There is nothing to edit. 

Any ideas where I am going wrong?

"Historical"

---

### Post by newbee70 on 2009-02-06
> **historical said:**
> Quote: originally posted by Doobeist

"you will see sections for Vista and Ubuntu, you will also see the default listed in there, just change it"

I have recently installed linux Ubuntu as a dual boot system, but with XP, not Vista. By default Grub loads Linux but my family do not want to have to select Windows every time and do not want Linux.

I have typed in "sudo gedit /boot/grub.menu.1st" but when I hit return, all I get is a new blank text editor box with nothing in it but a tab labeled "menu.1st" and a blinking cursor. There is nothing to edit. 

Any ideas where I am going wrong?

"Historical"




sudo gedit /boot/grub.menu.1st" 1st should be lst that is a small "L"st not a one st.

see if that helps you out. typo's are hell-o on commands.

---

### Post by longtom on 2009-02-06
Had the same problem 3 days ago.  Couldn't get it going in the terminal so one of the chrissharp123 suggested:

"You can go to the Synaptic Package Manager and search for startupmanager, which is a graphical interface for setting up your GRUB menu. It will allow you to pick which OS you would like to be your default."

That did it for me.

Good  luck

lt

---

### Post by rbhigday on 2009-04-16
> **longtom said:**
> Had the same problem 3 days ago.  Couldn't get it going in the terminal so one of the chrissharp123 suggested:

"You can go to the Synaptic Package Manager and search for startupmanager, which is a graphical interface for setting up your GRUB menu. It will allow you to pick which OS you would like to be your default."

That did it for me.

Good  luck

lt

Just what I was looking for, Thanks.

---

