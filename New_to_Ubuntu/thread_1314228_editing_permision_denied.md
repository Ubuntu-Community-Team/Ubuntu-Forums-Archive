---
title: "editing permision denied"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by nnjond on 2009-11-04
Hi,

how do i read files at the terminal - and can i edit/delete files in X11 without going back out to grub?

thanks

---

### Post by ukripper on 2009-11-04
> **nnjond said:**
> Hi,

how do i read files at the terminal - and can i edit/delete files in X11 without going back out to grub?

thanks

Please explain bit more what you trying to achieve?

---

### Post by NoaHall on 2009-11-04
To read file -```
cat /filename
```

And I won't tell you how to delete files, until you tell me what it is you wish to delete. Do NOT delete anything outside your /home/

---

### Post by QLee on 2009-11-04
[QUOTE=nnjond]how do i read files at the terminal [/QUOTE]

One way (using CLI):
cat <filename> | more



[QUOTE=nnjond]- and can i edit/delete files in X11 without going back out to grub?[/QUOTE]

Yes, you can, because you mentioned permissions, I'm assuming you don't own the file you want to edit.
One way (using GUI)
gksu gedit <filename>

I just gave two examples, there are lots of other ways.

If you do as ukripper suggests, you will get more specific advice, as stated, it's hard to know what to suggest to you.

---

### Post by nnjond on 2009-11-04
Thanks for your help. Somehow i've misspelt 2 xorg.conf_backup files wich may possibly confuse me in the futre.

---

### Post by undecim on 2009-11-04
To view files from a terminal, try "cat filename", "more filename", or "less filename" (where filename is the file you want to view)

Each of those has a different behavior. cat just puts the entire content of the file into the terminal. This can be good for small files, but for big files, you won't be able to see all of the file, because it will go offscreen.

more lets you scroll down through a file one line at a time. This is good for extremely large files, because you can see the entire file without loading it all to RAM.

My personal favorite, less, lets you scroll back and forth through a file.

---

