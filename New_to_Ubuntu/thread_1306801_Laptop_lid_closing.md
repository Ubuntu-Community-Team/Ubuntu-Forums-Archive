---
title: "Laptop lid closing"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by lotharmat on 2009-10-30
I have just installed Karmic on my laptop and previously, when docked; and the power management set to 'do nothing' when the lid is closed, the external monitor would remain on. It no longer does this. Basically there is no 'do nothing' option under 'when lid is closed' 

Does anyone know how I could solve this?

Cheers Y'all

Mat

---

### Post by phillw on 2009-10-30
> **lotharmat said:**
> I have just installed Karmic on my laptop and previously, when docked; and the power management set to 'do nothing' when the lid is closed, the external monitor would remain on. It no longer does this. Basically there is no 'do nothing' option under 'when lid is closed' 

Does anyone know how I could solve this?

Cheers Y'all

Mat


i'm not fobbing you off, is there anything mentioned here ....  

[http://newyork.ubuntuforums.org/forumdisplay.php?f=332](http://newyork.ubuntuforums.org/forumdisplay.php?f=332)

It's the laptop area 

I'll gladly go have a dig for you, but would need your laptop make / model etc.  I think it'd be quicker for you !!

I'm guessing it is one of dreaded acpi items ...

Phill.

---

### Post by lotharmat on 2009-10-30
The frustrating thing is that it worked in Jaunty and Intrepid.

---

### Post by phillw on 2009-10-30
> **lotharmat said:**
> The frustrating thing is that it worked in Jaunty and Intrepid.


in that case, it's probably quite fixable ... it will be a switch in the acpi config files ......

I'm sorry not to be of more help, it's a while since I dealt with acpi stuff....

Those people in the laptop forum could well already have gotten it sorted :)

Phill.

---

### Post by lotharmat on 2009-10-30
How easy is it to move this post to the Laptop Forum?

---

### Post by happyhamster on 2009-10-30
In a terminal (Applications-->Accessories-->Terminal), type: gconf-editor

Navigate to apps-->gnome-power-manager-->buttons and set lid_ac and/or lid_battery to "nothing" (without the quotes).

Good luck.

---

### Post by lotharmat on 2009-10-31
> **happyhamster said:**
> In a terminal (Applications-->Accessories-->Terminal), type: gconf-editor

Navigate to apps-->gnome-power-manager-->buttons and set lid_ac and/or lid_battery to "nothing" (without the quotes).

Good luck.

Many thanks.

I'll give it a try on Monday (back at work) and let you know how I got on!

I love this place! It has to be one of the most helpful places on t'internet

---

### Post by humphreybc on 2009-10-31
Cheers, i've been looking for the answer to this. I thought it would be a simple gconf edit, but have been too lazy to look :P

Why is the "do nothing" option removed from the list in power preferences though?

---

### Post by Oranges10e on 2009-10-31
I am confronted with the same problem. Why would anyone remove that? Especially on a Laptop. Almost all Laptops have a vga or digital-out >,>" What to do? 

Oranges

---

### Post by lotharmat on 2009-11-02
Yup! The setting in gconf-editor worked a treat!

Many thanks!

---

