---
title: "Disable PS/2 Mouse while typing"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by wowfunhappy on 2010-12-05
Hi.  My sister is using Ubuntu 10.10 on a Dell Inspiron Laptop.  Everything works wonderfully (much faster than Windows, which is why she likes it), except for one problem.

When she tries to type on the computer, the palms of her hand will often cause the touchpad on the computer to move around and/or inadvertently click.

So, I want to be able to disable the mouse whenever the keyboard is being used.

The problem is, Ubuntu recognizes her touchpad a PS/2 mouse.  I've read that this is a bug in Ubuntu, and that it can often be fixed by applying a bunch of non-stable kernels and stuff; things I really would like to avoid using if I can help it.

Instead... pretend this was a PS/2 mouse rather than a touchpad, since that's what Ubuntu thinks it is anyway.  If it was a normal PS/2 mouse, how could I disable input from that PS/2 mouse whenever they keyboard is being used?

Thanks in advance for any help!

---

### Post by oldmankit on 2010-12-06
This isn't a fix, but might be worth using while you're trying to find a proper solution.  On my Acer laptop there is a button combination that will disable the touchpad.  On mine, it is Function+F7.  There might be one on your sister's laptop?

---

### Post by bodhi.zazen on 2010-12-07
> **wowfunhappy said:**
> Hi.  My sister is using Ubuntu 10.10 on a Dell Inspiron Laptop.  Everything works wonderfully (much faster than Windows, which is why she likes it), except for one problem.

When she tries to type on the computer, the palms of her hand will often cause the touchpad on the computer to move around and/or inadvertently click.

So, I want to be able to disable the mouse whenever the keyboard is being used.

The problem is, Ubuntu recognizes her touchpad a PS/2 mouse.  I've read that this is a bug in Ubuntu, and that it can often be fixed by applying a bunch of non-stable kernels and stuff; things I really would like to avoid using if I can help it.

Instead... pretend this was a PS/2 mouse rather than a touchpad, since that's what Ubuntu thinks it is anyway.  If it was a normal PS/2 mouse, how could I disable input from that PS/2 mouse whenever they keyboard is being used?

Thanks in advance for any help!

This is easy to fix:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

More specifically:

[https://help.ubuntu.com/community/SynapticsTouchpad#Disabling%20Touchpad%20while%20Typing](https://help.ubuntu.com/community/SynapticsTouchpad#Disabling%20Touchpad%20while%20Typing)

---

### Post by owiknowi on 2010-12-07
Presuming you want to disable the touchpad while typing?

Go to System - Preferences - Mouse.
Then choose tab Touchpad and check 'Disable touchpad while typing'.
Should work in most cases.

---

### Post by tenbucks on 2010-12-18
You could use [mouseemu]("http://manpages.ubuntu.com/manpages/lucid/en/man8/mouseemu.8.html") to disable the mouse (improperly detected touchpad).

---

### Post by MarjaE on 2011-06-08
> **bodhi.zazen said:**
> This is easy to fix:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

More specifically:

[https://help.ubuntu.com/community/SynapticsTouchpad#Disabling%20Touchpad%20while%20Typing](https://help.ubuntu.com/community/SynapticsTouchpad#Disabling%20Touchpad%20while%20Typing)

No it isn't. That fix only works if the touchpad uses Synaptics drivers. But if the tpouchpad uses Synaptics drivers, then simpler solutions, such as "disable touchpad while typing," are possible.

---

