---
title: "Keyboard input garbled"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by scucow on 2009-02-22
Hi there.

I am having a problem with my desktop computer, where one of my flatmates has accidentally done something to change the keyboard's settings. 

For example, pressing:
"backspace" = "3"
"k" = "kl"
"2" = "24"
"n" = "hn"
"d" = doesn't work

Can anyone help me? I can't use terminal or any commands because I can't enter the letters.

Cheers

---

### Post by hyperyoda on 2009-02-22
> **scucow said:**
> Hi there.

I am having a problem with my desktop computer, where one of my flatmates has accidentally done something to change the keyboard's settings. 

For example, pressing:
"backspace" = "3"
"k" = "kl"
"2" = "24"
"n" = "hn"
"d" = doesn't work

Can anyone help me? I can't use terminal or any commands because I can't enter the letters.

Cheers

Load the keymap you want with loadkeys, such as:

$ sudo loadkeys /usr/share/keymaps/i386/qwerty/us.kmap

If you still have problems try this:

$ sudo dpkg-reconfigure console-data

Zach

---

### Post by scucow on 2009-02-22
Thanks for the feedback.

However, the problem I face is that I can't enter any comands - for example, I try to write "sudo' but the "d" and "u" don't work.

I am typing this from a laptop.

Is there a toggle or something I can use?

Cheers

---

