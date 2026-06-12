---
title: "vim registers question"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by rumca.js on 2010-01-18
I'm using Vim as text editor for now.

To yank the text into register (for example register 'a') I have to input "ay in normal mode since " is input key for choosing register. However in my work I need one register other than the default register. (for example my task is to yank current line, clean mess in text in place and paste reg a contents somewhere else).

" is a veery dificult key to press. Therefore I found :y a (it's a command line thing). However it works only on a line of text. Not on the word. :yw a is not working.

Does anyone know if I can create a command myself :yw a which will yank only a word of text?

Or is there a method to change current working registry. For example I'm using a register for now, but in a moment I will switch onto register b.

Or is there any other way do cope with similar task (yank, do some other things, and paste yanked text later).

---

### Post by Barriehie on 2010-03-28
Try yw in normal mode, i.e. not :yw

---

