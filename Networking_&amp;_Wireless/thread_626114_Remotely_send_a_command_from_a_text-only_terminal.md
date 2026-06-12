---
title: "Remotely send a command from a text-only terminal"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by willmcgree on 2007-11-28
Hi guys.

I have Gutsy running on an Intel Mac (and it purrs, by the way :D) and I use Rhythmbox as my jukebox.

Since leaving Quicksilver behind from the Mac, I'm starting my self-taught training as a command-line ninja. (I bound Shift-RightSuper to pop a terminal for me.)

Preferring not to take my hands off the keyboard if at all possible, I found that Rhythmbox can be controlled through --parameters. (Thank you, man().)

So, while I'm at my desktop, a simple punch of a few keys will change track etc, etc, etc. I've bound aliases to make the whole thing quicker too.

Now, where's the problem with that, you might ask? There isn't one.

The problem comes in when I say that I want to use my Nokia N800 tablet as a remote control.

I've put the terminal emulator on the tablet, so I can ssh into my Mac easily, but if I send the same commands from my tablet, there's an error because it tries to run Rhythmbox on my tablet through X (which it doesn't have).

Right, what I would love is some way to send a text command such as:

```
$ rhythmbox-client --play
```

but to my desktop's TTY. Any way to get this working?

All help appreciated! :D

Thanks,
Will

---

### Post by tgalati4 on 2007-11-28
If you have an N800, why don't you try rhythmweb and control your player through a web page?

[http://web.vee.net/projects/rhythmweb/](http://web.vee.net/projects/rhythmweb/)

---

### Post by willmcgree on 2008-02-24
*bump*

I have tried using the web interface for Rhythmbox, Exaile and Amarok, but I'm looking for a more general-purpose tool.

Thanks for the input though! All help appreciated.

---

