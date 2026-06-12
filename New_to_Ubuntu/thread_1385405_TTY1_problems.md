---
title: "TTY1 problems"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by SymphonicNerd on 2010-01-19
okay, so i was hoping to avoid learning on a fix it basis but what better way. for a while i was able to use ctrl+alt+f1 to switch to tty1 but now when i try to switch it makes the screen like a nice multi colored rainbow. the only thing thats changed today is i installed flash for linux so i would be able to watch online tv... didn't think this would affect my terminal but it may have. has anyone else experienced an issue like this? or have a solution or query as to how i may fix it?

---

### Post by warfacegod on 2010-01-19
Try changing your key board short cuts under Preferences.

---

### Post by jward3010 on 2010-01-19
> Try changing your key board short cuts under Preferences.

I don't think this will help, I've seen this myself and it's possibly a graphical bug. When you switch to a tty console, X changes the resolution and colour depth and doesn't handle it properly. When you return to Gnome (F7) everything is fine.

Try another console like Ctrl + Alt + F3 or F4, same? Probably.

---

### Post by warfacegod on 2010-01-19
> **jward3010 said:**
> I don't think this will help, I've seen this myself and it's possibly a graphical bug. When you switch to a tty console, X changes the resolution and colour depth and doesn't handle it properly. When you return to Gnome (F7) everything is fine.

Try another console like Ctrl + Alt + F3 or F4, same? Probably.

I thought his short cut had been rewritten and was opening something else than the default. My fault.

---

### Post by SymphonicNerd on 2010-01-19
first of all my shortcuts option didn't even allow for the changing of tty shortcuts because there not listed there, as for the other screens none of the TTY's will work. is flash player the cause of this? i had no problems switching around before installing flash

Symphonic

---

### Post by mbzn on 2010-01-19
Mine did it the first time on 9.10. After a reboot it seemed fine.

---

### Post by Hospadar on 2010-01-19
A couple points of education before I make a suggestion:

Normally the tty is something (to my understanding) which is offered by the hardware on the machine, you (your operating system that is) can feed characters, colors, etc to the hardware and it will print them out.  This would be opposed to a graphical system where you (the X window system on your machine) tell the hardware what color each pixel is supposed to be.

Certain old machines did not provide a real tty (old powerpc macs for example), so OS's like linux implemented the kernel framebuffer to fake a tty on systems like that.  Aside from faking a tty, the framebuffer can be used on systems that do have a real tty (all modern machines for example) to change the resolution/number of characters on the tty (the faked tty replaces the hardware one).

The way this is done is by setting a vga mode in a kernel option, this happens through grub.  Next time you get into your grub menu, you can hit 'e' on your first boot option to edit that boot entry.  Take a look at the kernel arguments and see if you see something like 'vga=766' or something like that.  The number is a code for a certain framebuffer vga mode (tty resolution).  Try deleting the vga option alltogether, then boot that entry and see what happens.

The reason the framebuffer is used is (to my understanding), when it works it makes for a nicer tty (and the existence of a tty is guaranteed on all machines), and I think it's used for the newer bootsplash (the ubuntu loading bar when you boot up, and the logo before it). 

I've had weird graphics issues in the past and reverting to the non-framebuffer video mode has solved my problems.  This might not be the case at all for you, but if I had strange problems in my tty, that's the first place I'd check.

If you discover this to be the problem, youll need to edit some files in your /etc/grub (I think?) which are scripts used to generate the grub2 equivalent of menu.lst and get rid of the vga option they add.  If you do this you'll need to run 'sudo update-grub' to update the boot menu entries.

If you're using something older than 9.10, you'll just edit your /boot/grub/menu.lst

if you change grub files, be sure to make backups first and have a live-cd handy.
don't worry about editing entries in the grub menu at boot time, those changes aren't persistent.

If you aren't even using a vga mode, this post will be of no use to you! but hey, at least you learned more than you ever wanted to know about the framebuffer.

---

### Post by SymphonicNerd on 2010-01-19
can someone better help me understand where i can find the entry in grub? i thought i had found it but upon the next reboot the same problem still occured and im not entirely sure where to look in the grub folder, rather not mess with system settings i need not, that and what does he mean by e upon grub? it boots straight to the login, never see it load up grub

---

### Post by SymphonicNerd on 2010-01-19
still need a little help, im not super eager to touch the grub menu without a little clarification but i guess there may not be better way to learn then by doing so i'll keep looking

---

### Post by SymphonicNerd on 2010-01-19
nevermind, learning to open as read only... definately not what i wanted. ill keep searching, i miss my tty's

Symphonic

---

