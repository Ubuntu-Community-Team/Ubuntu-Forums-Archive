---
title: "segmentation fault with visual boy advance"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by thomz92 on 2009-10-03
i tried to open visualboy advance from the menu and it said loading on the bottom panel, but then it disappeared and it didn't open. So, i tried opening it in the terminal, but then it said segmentation fault. what does that mean? it worked before...

---

### Post by thomz92 on 2009-10-05
bump...

---

### Post by mikechant on 2009-10-06
I suggest you post all the messages it outputs when you run it from the terminal.


Also, have you looked at this post?
[http://ubuntuforums.org/showthread.php?t=646952](http://ubuntuforums.org/showthread.php?t=646952)

---

### Post by Eisenwinter on 2009-10-06
General information about segmantation faults (segfault):

[quote="Wikipedia"]A segmentation fault (often shortened to segfault) is a particular error condition that can occur during the operation of computer software. A segmentation fault occurs when a program attempts to access a memory location that it is not allowed to access, or attempts to access a memory location in a way that is not allowed (for example, attempting to write to a read-only location, or to overwrite part of the operating system).[/quote]

[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

I hope this will help you "debug" the programs you're using in the future.

---

### Post by thomz92 on 2009-10-06
here's the output:

```

thomas@thomas-desktop:~$ gvba

(gvba:8164): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
Segmentation fault
thomas@thomas-desktop:~$ 

```

by the way, i'm not using wine to run visual boy advance

---

### Post by lavinog on 2009-10-07
are you using ubuntu 32 bit or 64? what version? (hardy, intrepid, jaunty...etc)
what video card do you have?

does the command vba filename work?

---

### Post by thomz92 on 2009-10-07
> are you using ubuntu 32 bit or 64? what version? (hardy, intrepid, jaunty...etc)
what video card do you have?

does the command vba filename work?

im using ubuntu jaunty 32 bit. my video card is a 256mb nvidia geforce fx5500. 

what filename do i use?

heres another thing. i just restarted my computer and i typed gvba in the terminal and it opened fine. then i tried it from the menu. it didn't work. i tried it again from the terminal...and it didn't work. i have no clue whats going on here.

---

### Post by lavinog on 2009-10-08
> **thomz92 said:**
> im using ubuntu jaunty 32 bit. my video card is a 256mb nvidia geforce fx5500. 

what filename do i use?

the filename of a vba rom.

The problem is most likely the front end and not the emulator itself.
> 
heres another thing. i just restarted my computer and i typed gvba in the terminal and it opened fine. then i tried it from the menu. it didn't work. i tried it again from the terminal...and it didn't work. i have no clue whats going on here.
segfaults can appear to be random sometimes.
It could be the video driver...did you enable the restricted driver for your card?

---

### Post by thomz92 on 2009-10-08
> The problem is most likely the front end and not the emulator itself.

Should i reinstall it then? or is there anything i can do to fix it?

> It could be the video driver...did you enable the restricted driver for your card?

yeah i did...

---

### Post by thomz92 on 2009-10-10
i tried vba filename and it worked, but thats way too much work to do every time... any more ideas?

---

### Post by lavinog on 2009-10-10
> **thomz92 said:**
> i tried vba filename and it worked, but thats way too much work to do every time... any more ideas?

I would wait and see if it works with karmic...chances are, it is a bug in the nvidia driver, that may have already been fixed in a more recent version.   If you are up to it, you can update the driver.

---

### Post by thomz92 on 2009-10-10
im postive it worked before though... i never did anything to the nvidia drivers.

---

