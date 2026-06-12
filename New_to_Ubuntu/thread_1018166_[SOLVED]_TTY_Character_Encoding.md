---
title: "[SOLVED] TTY Character Encoding"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by prinny42 on 2008-12-21
My TTY sessions (ctrl-alt-F* is what I mean, in case I'm using the wrong terminology) seem to have suddenly started using a different character encoding than before.  I used to have a sort of chunky one that had @ signs that looked more like squiggly ovals; it would display Japanese characters as squares.  Now all of a sudden, I've got this very thin one that prints @ signs properly and displays Japanese characters as diamonds.

As far as I can tell, I didn't to anything to make this happen.  Perhaps it was part of an update or something, or maybe I did something unawares.  I've tried changing my TTY resolution (thinking that might have something to do with it), but as one might expect, that just changed the resolution.

I'd like to go back to the old, chunky style, does anyone know what's going on and how I might accomplish that?  Further, while I'm here, does anyone know if there is a way to display/type Japanese characters properly in a TTY session and how one might go about doing so if there is?

Thank you very much.

---

### Post by prinny42 on 2008-12-22
Okay, sorry, I found the answer is already available after doing some more digging.  I just had to run dpkg-reconfigure on console-setup and choose the font I wanted (it had defaulted to Fixed, whereas VGA looks like it's the one I was thinking of).

For clarity, the command was:
> sudo dpkg-reconfigure console-setup

---

