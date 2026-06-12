---
title: "Laptop keyboard not working"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2010-10-28
Recently I had to replace the keyboard on my Dell 630m laptop.

Now, for some strange reason it wont work properly when I log into Ubunto. 

It works in grub and the initial login window, but when it reaches my desktop it stops. the only keys that work are the arrow and page keys.

I have a USB keyboard plugged in, and it works fine

When I boot up into XP the keyboard work fine, its only when I am in my desktop in Ubuntu 10.04 that it stops working...

Any ideas

---

### Post by papibe on 2010-10-28
Does it work if you boot to safe mode (no graphics, just text mode)?
Regards.

---

### Post by Ducatiboy Stu on 2010-10-30
I  have upgraded to 10.10, and now the USB keyboard wont work as well as the internall keyboard

In safe graphics mode it works, and when I sign in as a guest it work fine, but just not in my own desktop environment

---

### Post by papibe on 2010-10-30
My guess then, is that your X Windows configuration file is somehow configured to use the old keyboard. Although I'm not an expert, if you post it, maybe we can get something out of it. The file is /etc/X11/xorg.conf

Regards.

---

### Post by Ducatiboy Stu on 2010-10-30
I found the problem, it was the keyboard layout.

I went to generic 101 key-PC and it came good

:)

---

### Post by papibe on 2010-10-30
I'm glad you solve it.

Did you change it on xorg.conf directly? or
Did you do it using System -> Preferences -> Keyboard?

Regards.

---

### Post by Ducatiboy Stu on 2010-10-30
System -> Pref -> Keyboard

---

