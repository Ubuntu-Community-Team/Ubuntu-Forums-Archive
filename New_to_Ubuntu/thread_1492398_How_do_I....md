---
title: "How do I..."
date: 2010-05-24
forum: New to Ubuntu
---

### Post by BrainWart on 2010-05-24
How do I edit the grub so I don't have to select Windows or Ubuntu each time?
I think its grub2... :confused:

---

### Post by racie on 2010-05-24
Is this link helpful at all?  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

What do you want it to do instead of giving you options anyway?

---

### Post by 311005901 on 2010-05-24
The easiest way is to open the Software Center and install a program called "Startup Manager".

This might be what you're looking for.

---

### Post by bodhi.zazen on 2010-05-24
> **BrainWart said:**
> How do I edit the grub so I don't have to select Windows or Ubuntu each time?
I think its grub2... :confused:

Remove windows :lolflag:

The grub link will show you how to set / change the default.

---

### Post by BrainWart on 2010-05-24
I hate being new but I can't edit the grub file...  311005901 it doesn't have what I was looking for.

---

### Post by bodhi.zazen on 2010-05-24
What is "grub file...  311005901" ??

See also :

[Grub 2 - Ubuntu Wiki]("https://wiki.ubuntu.com/Grub2")

You want to edit /etc/default/grub and change the line "GRUB_DEFAULT=0" to the OS you wish to boot.

To edit system files, use gksu

```
gksu gedit /etc/default/grub
```

Then save your edit and run

```
sudo update-grub
```

---

### Post by pizza-is-good on 2010-05-24
> **bodhi.zazen said:**
> What is "grub file...  311005901" ??


I think that's the name of the user that replied.... I was a little confused too.

---

### Post by bodhi.zazen on 2010-05-24
> **pizza-is-good said:**
> I think that's the name of the user that replied.... I was a little confused too.

OIC, :lolflag:

That went way over my head, too used to seeing the quotes.

---

### Post by 311005901 on 2010-05-26
Sorry about that. :-|
My name is a little weird...

---

### Post by bodhi.zazen on 2010-05-26
> **BrainWart said:**
> I hate being new but I can't edit the grub file...  311005901 it doesn't have what I was looking for.

So long as you understand the grub terminology, you can try the command "grub-reboot"

See:

[http://ubuntuforums.org/showpost.php?p=9334347&postcount=19](http://ubuntuforums.org/showpost.php?p=9334347&postcount=19)

---

