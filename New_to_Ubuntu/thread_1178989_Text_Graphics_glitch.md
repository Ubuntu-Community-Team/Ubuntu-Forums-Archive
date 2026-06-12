---
title: "Text Graphics glitch"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Casper Orillian on 2009-06-05
I keep getting a graphical glitch around my text, some times it is like lines going through other times (it is happening as i post this) is a grey or black box around the character

anyone know what is going on?

---

### Post by overdrank on 2009-06-05
> **Casper Orillian said:**
> I keep getting a graphical glitch around my text, some times it is like lines going through other times (it is happening as i post this) is a grey or black box around the character

anyone know what is going on?

Hi and welcome, what is the model of the graphics card and have you installed the drivers?
You may use the command in the terminal ```
lspci | grep VGA
``` To identify your graphics. The terminal is located under applications, accessories.
What version of Ubuntu are you using?
You can find this under system, about Ubuntu.

---

### Post by Casper Orillian on 2009-06-05
im using an acer laptop, i dont think i have installed the right graphic software, and i am using version 9.4

---

### Post by overdrank on 2009-06-05
> **Casper Orillian said:**
> im using an acer laptop, i dont think i have installed the right graphic software, and i am using version 9.4

Ok you may look under system, administration, hardware driver to see any drivers available for your system. :)

---

### Post by Casper Orillian on 2009-06-05
it says no drivers are in use

---

### Post by overdrank on 2009-06-05
> **Casper Orillian said:**
> it says no drivers are in use

Ok does it show any driver available as mine does in the screen shot attached. :)
Also have you tried the command I posted earlier to identify your graphics?

---

### Post by Casper Orillian on 2009-06-05
Yeah i tried that command line and nothing happend, do i have to use sudo to run it?

and the image you put up, no thats not what happens, all i get is the main window stays blank and the text at the top changes to say no hardware devices on this machine
here is an image of what i get, it seems to get worse the longer the pc stays on [IMG]http://i704.photobucket.com/albums/ww44/orillian/textGlitch.png[/IMG]

---

### Post by overdrank on 2009-06-05
> **Casper Orillian said:**
> Yeah i tried that command line and nothing happend, do i have to use sudo to run it?

and the image you put up, no thats not what happens, all i get is the main window stays blank and the text at the top changes to say no hardware devices on this machine
here is an image of what i get, it seems to get worse the longer the pc stays on ]

You can copy and past that command ```
lspci | grep VGA
``` no sudo needed. That is the pipe symbol on the top of the backspace key on my laptop. :)
Or just use lspci and look for vga.

---

### Post by Casper Orillian on 2009-06-05
that worked, here is what i get

00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)

---

### Post by Casper Orillian on 2009-06-05
Is there something i need to download like a patch or something, because this glitch is really beginning to annoy me

---

### Post by overdrank on 2009-06-05
> **Casper Orillian said:**
> Is there something i need to download like a patch or something, because this glitch is really beginning to annoy me

You may look at the link in my signature about [Intel Graphics Jaunty]("http://ubuntuforums.org/showthread.php?t=1130582").

---

### Post by Casper Orillian on 2009-06-05
Ok i have now discovered i think the font glitch is font related, certain fonts do it and others dont anyone know of this happening before?

---

### Post by Casper Orillian on 2009-06-05
right its not font related, its still doing it, worse then ever, i tried that thing you reccomended, but i coulnt get it to work, none of the commands would run

any advice?

---

### Post by Scunizi on 2009-06-05
You might try rebooting into the Recovery kernel from the Grub menu.  At that point you'll get a list/menu of things.. There's one referencing "fixing X".  Try that.

You might also .. Alt+F2 and enter (cut and paste this)... gedit /etc/X11/xorg.conf  ... in the file that opens (after a possible error because you haven't used sudo) look for a line starting with ... Driver .. after that it might say "automatically configured" or it might say nv or vesa or intel.  Report back.

---

