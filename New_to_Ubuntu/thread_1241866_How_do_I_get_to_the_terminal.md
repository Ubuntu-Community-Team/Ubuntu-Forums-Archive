---
title: "How do I get to the terminal?"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by audit on 2009-08-16
I only know how to use the terminal through a window. I would like to get to the terminal directly. 

How do I get to the terminal?

I was told by someone that I could get to the terminal using [alt] + [F2]; but this does not work (it gives me a run window). I know this sounds unclear; I hope someone understands.

---

### Post by wil08son on 2009-08-16
At the top left of your screen, go to Applications > Accessories > Terminal.

---

### Post by Barrucadu on 2009-08-16
Ctrl+Alt+F1. To get back to X: Ctrl+Alt+F7

---

### Post by rifak on 2009-08-16
im not sure what you mean by you can only use the terminal trough a window...but if you want a full, working, terminal, the first poster has it. or, if you are looking to not even have a graphical interface, and just want to be looking at the command line interface, press alt+f2 at the login screen

---

### Post by audit on 2009-08-16
Thanks for the response--does anyone know why this happens to me. when I press cntrl+alt+F1; I get an unreadable blinking screen. If I enter cntrl+alt+F2 I find myself at a usable prompt? 

Thanks for the quick responses--because I can now get to the prompt.

---

### Post by grizzler on 2009-08-16
Now this is strange. I also get an unusable terminal with Ctrl+Alt+F1. It's a completely black screen with just a vague hint of the mouse pointer in the center. No text at all. Unfortunately, the other five Ctrl+Alt+F combinations give the same result... :(

It did work a couple of weeks ago. I think that was with kernel 2.6.28-13.

---

### Post by HermanAB on 2009-08-16
The boot-up status messages go to the first terminal (ctrl-alt-f1), so if something sent a weird command that upset the settings of the terminal then it could be blinking.  This is hard to reset, because you cannot see what you are typing.

---

### Post by Iowan on 2009-08-16
I had that happen with older version [(Edgy?)]("http://ubuntuforums.org/showthread.php?t=289272") Changing Grub boot line to "nosplash" fixed it.

---

### Post by ashwinhgtx on 2009-08-16
Ctrl+Alt+F1 works for me. I see the last part of the boot up messages and then I get the login prompt. I'm on Linux Mint 7(Jaunty).

---

### Post by grizzler on 2009-08-16
> **Iowan said:**
> I had that happen with older version [(Edgy?)]("http://ubuntuforums.org/showthread.php?t=289272") Changing Grub boot line to "nosplash" fixed it.

That's done it for me as well. Thanks!

Someone suggested you could switch off the splash screen by omitting 'splash'. So I did. Obviously, that wasn't enough... :)

---

### Post by colau on 2009-08-17
> **audit said:**
> i only know how to use the terminal through a window. I would like to get to the terminal directly. 

How do i get to the terminal?

I was told by someone that i could get to the terminal using [alt] + [f2]; but this does not work (it gives me a run window). I know this sounds unclear; i hope someone understands.
ctrl+alt+f2 --> ctrl+alt+f7

---

### Post by grizzler on 2009-08-19
> **Iowan said:**
> I had that happen with older version [(Edgy?)]("http://ubuntuforums.org/showthread.php?t=289272") Changing Grub boot line to "nosplash" fixed it.
Well, that did work. Until today, after I upgraded the kernel to 2.6.28-15. Changed splash to **nosplash** in the new entry in menu.lst, rebooted...

Same problem as before with Ctrl+Alt+F1 - F6: blank screen, no text, vague image of a frozen mouse pointer in the center.

Sometimes I really, really hate Linux... :(

---

### Post by audit on 2009-08-19
I can get to tty1 if I first open the gnome-terminal and press cntl+alt+f1.
If I do not first open up gnome-terminal--tty1 is blinking and unusable. After I open tty1 once it can then be opened any time I press cntl+alt+f1. I have no idea why.

---

### Post by Windows Nerd on 2009-08-20
> **Barrucadu said:**
> Ctrl+Alt+F1. To get back to X: Ctrl+Alt+F7
You can just type in "exit" (without the quotes of course) and you will go back into X-Windowing system (Aka the normal GUI)

---

