---
title: "Laptop Plug"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by BanksKy on 2010-11-29
Hey, I am fairly new to Ubuntu, as well as the forum, but my problem is that if the plug on my laptop is removed, and I attempt to plug it back in, the computer freezes. I have tried waiting it out, but after about an hour I gave up. 

The computer is an Alienware M17x, running Ubuntu 10.10 natively, no other OS on the computer.

If I remove the power and plug it back in before Ubuntu boots (during the grub loader or the computers BIOS) everything is fine, when i used to use Windows 7, it was fine, but in Ubuntu the whole system freezes up.

Any ideas?

P.S. same thing when i try to shut down, or when trying to bring the computer back from hibernation, the screen freezes, and nothing happens no matter how long i wait.

---

### Post by BanksKy on 2010-11-29
Shameless bump, this is driving my crazy :P

---

### Post by sandyd on 2010-11-29
you tried noacpi?

---

### Post by BanksKy on 2010-11-29
not even sure what that is

---

### Post by Jerry N on 2010-11-29
This might not apply in your situation but with my new HP netbook I need to plug the external power supply in to the computer and then plug the power supply into the AC outlet.  If I connect the PS to the AC first and then plug it in to the computer, the computer doesn't hang but it will often indicate that the batter is not charging.  

Jerry

---

### Post by BanksKy on 2010-11-29
I wish it were that simple, but ive tried already :)

I should also note that the batter charges just fine.


Any help is immensely appreciated

---

### Post by sandyd on 2010-11-29
> **BanksKy said:**
> not even sure what that is

when booting, press esc/shift to get to the grub menu.
press 'e' when you see the grub menu.

add 'noacpi' (without quotes) to the end of the line that has "kernel in it"

press control +x

---

### Post by BanksKy on 2010-11-29
Thanks Sandyd, I tried what you said, followed the directions very carefully, but to no avail.

However, I tried it twice, and when I went back into the GRUB editor, the 'noacpi' was no longer there? Is that normal?

(without quotes of course)

---

### Post by BanksKy on 2010-11-30
FIXED :)

Turns out the ATI card had "Power Play" enabled, so when I plugged in the power it went to maximum performance.

Disabling this has stopped the problem

---

