---
title: "Shut down does not power off the PC"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by User X on 2009-01-25
When I shut down Ubuntu I get the Ubuntu splash screen but it won't fully power the computer down.  If I hit the power button it turns off but I don't know why it won't turn itself off when I choose shut down...?

---

### Post by callan79 on 2009-01-25
> **User X said:**
> When I shut down Ubuntu I get the Ubuntu splash screen but it won't fully power the computer down.  If I hit the power button it turns off but I don't know why it won't turn itself off when I choose shut down...?



Hello User X,

I've seen this twice in past, and both times it's been related to ACPI which is the way that the operating system talks to the hardware.

The first instance, was due to a really old computer (pre-2000), and Ubuntu disabled all ACPI services.

The second was due to a motherboard with a BIOS bug, and again Ubuntuy disabled ACPI. Once I upgraded the BIOS on the board, everything worked fine.

What you can do to test ...

(1) Start Computer
(2) Get into the GRUB menu (press ESC if it does not show by itself)
(3) Go to the normal Ubuntu option and press 'e' to edit
(4) Find the line that talks about /boot/vmlinuz. Press 'e' to edit.
(5) Get rid of the words 'quiet' and 'splash. then press enter.
(6) Press 'b' to boot

What you'll see is a heap of diagnosic information on your screen. Look out for anything obvious about ACPI.

Also you can see same information if you start Ubuntu, go to a terminal and type :

```
dmesg | less
```

Then you use the up and down arrow keys to scroll through the logs from the last boot.

Hope this helps!

Callan

---

