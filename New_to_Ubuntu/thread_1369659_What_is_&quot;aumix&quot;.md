---
title: "What is &quot;aumix&quot;"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Chris Edgell on 2010-01-01
I have asked this question obliquely before, but today I will ask directly.  

What is aumix?  I have it downloaded, but did I do that with some particular package?  Which one?  Why is it that in all the posts I've read about sound, I don't believe I have EVER seen "aumix"?  

Well, I ran search and there are many cases of it being mentioned, but not much by way of defining.

---

### Post by thatguruguy on 2010-01-01
Taken straight from the listing in Synaptic:

aumix is a small, easy-to-use program to control the mixer of your sound
card. It runs in text mode using the ncurses library, or from the command
line (non-interactively). It can read default settings from a file, and it
can also automatically save and restore the mixer settings at shutdown and
boot.

A wrapper script xaumix is provided that finds and invokes xterm or a
replacement. This is primarily for creating the best sized terminal window.
If you want a true graphical interface, install aumix-gtk instead. That has
the same functionality as this one in addition to offering a nice X GUI.

The old companion package aumix-alsa, which did take advantage of the
extra facilities in the ALSA sound driver, is no longer available.
This package should work fine with the OSS compatibility layer of the
modern ALSA drivers.

---

### Post by Chris Edgell on 2010-01-01
I did go and search "aumix" and found that "aumix-gtk" that you refer to.  If I add one is it mandatory to delete the other, or how DOES that work?

(Thanks)

---

### Post by thatguruguy on 2010-01-01
They conflict. synaptic will handle the conflict for you.

---

