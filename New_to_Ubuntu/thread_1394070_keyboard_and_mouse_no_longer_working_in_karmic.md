---
title: "keyboard and mouse no longer working in karmic"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by techno-mole on 2010-01-30
hello.

I have a problem, my wife turned on her pc this morning (she is running ubuntu karmic) and her keyboard and mouse don't work, the mouse is a wireless mouse (nothing fancy just a tesco one) and the keyboard is a usb keyboard (again just a tesco one) neither work for some reason, my first thought with the mouse was the batteries, so I changed them, but no joy.

I tried running the recovery option from the grub menu, but nothing has changed, I have also tried hooking up an old ps2 mouse and keyboard, but they didn't work either.

I have no idea why they don't work, I have tried running the karmic cd I have and the keyboard and mouse both work fine on the live cd (both the usb ones and the ps2 ones) I have done some searches but the only sure fire way of solving the issue is to re-install, which seems a bit drastic (and if I'm honest a little like a windows solution)

I would be grateful for any help, I am now running the live cd, just so I can copy my wife's files onto the file server so they don't get lost.

cheers

---

### Post by techno-mole on 2010-02-19
solved by reinstalling.

---

### Post by SaintDanBert on 2010-02-20
> **techno-mole said:**
> hello.

I have a problem, my wife turned on her pc this morning (she is running ubuntu karmic) and her keyboard and mouse don't work, the mouse is a wireless mouse (nothing fancy just a tesco one) and the keyboard is a usb keyboard (again just a tesco one) neither work for some reason, my first thought with the mouse was the batteries, so I changed them, but no joy.

I tried running the recovery option from the grub menu, but nothing has changed, I have also tried hooking up an old ps2 mouse and keyboard, but they didn't work either.

I have no idea why they don't work, I have tried running the karmic cd I have and the keyboard and mouse both work fine on the live cd (both the usb ones and the ps2 ones) I have done some searches but the only sure fire way of solving the issue is to re-install, which seems a bit drastic (and if I'm honest a little like a windows solution)

I would be grateful for any help, I am now running the live cd, just so I can copy my wife's files onto the file server so they don't get lost.

cheers

[highlight]The same thing happened to me.[/highlight]

It is an X11 thing and not a hardware issue but something has gone wrong with xinput.

** GDM does not see key input so login does not happen
** console boot and I can **startx** but nothing accepts key input.
** **ALT+SysRq** does not work either -- this is a strange symptom cuz those are supposed to be caught by the kernel.
** I tried to use the on-screen tap-keyboard with same results
** I cannot access an alternate console
** GDM does not let me login to a console

It seems that [highlight]re-install[/highlight] is a bit drastic.

---

### Post by McMahonSport on 2010-02-21
This has happened to me too: Mouse works although keyboard does not; apart for some keys: h,f,g,j,k

---

### Post by techno-mole on 2010-02-21
sorry to hear you are having problems, however i cant offer any other advice, apart from re-installing, its not ideal, but i found nothing else that worked to solve it.

cheers

---

