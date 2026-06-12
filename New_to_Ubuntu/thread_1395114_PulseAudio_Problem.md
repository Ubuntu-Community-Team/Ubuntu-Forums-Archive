---
title: "PulseAudio Problem?"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by Hman242 on 2010-01-31
For some reason, all of my internet applications stop playing sound about three times a day. To fix it, I enter

sudo alsa force-reload

in the terminal. It always fixes the problem, but it's an annoyance to enter it in three times a day. What is the problem, and what can I do to make the problem stop?

---

### Post by dolphinaura on 2010-01-31
Try
```

sudo apt-get remove pulseaudio*

```

---

### Post by Hman242 on 2010-01-31
That's going to remove it, I hope it works or I'm ******. The sound seems to still be working, so that's good. I'll tell you if the problems arrives again.

---

### Post by Psumi on 2010-01-31
> **Hman242 said:**
> That's going to remove it, I hope it works or I'm ******. The sound seems to still be working, so that's good. I'll tell you if the problems arrives again.

Once you remove pulseaudio, you'll need to install some packages (I think) to get back the mixer functionality to your panel. If not, you'll have to use alsamixer in terminal.

---

### Post by Hman242 on 2010-01-31
What packages would I need?

---

### Post by Psumi on 2010-01-31
> **Hman242 said:**
> What packages would I need?

One of them should be libasound of some kind, make sure gstreamer0.10-alsa are installed.

KDE doesn't use gstreamer unless you use parole or totem.

This is based on use of xfce though, so I don't know if it works with gnome volume mixer. Most gnome-media tools are based solely on pulse.

---

### Post by Hman242 on 2010-01-31
I've ended up installing Alsamixer, and I'm wondering how to get the sound icon in my panel. I read that that is possible, but I can't find out how. I'm using Gnome if that helps.

---

### Post by Psumi on 2010-01-31
You might want to read this thread:

[http://ubuntuforums.org/showthread.php?t=1284219](http://ubuntuforums.org/showthread.php?t=1284219)

---

### Post by cariboo on 2010-01-31
Instead of removing pulseaudio, why not just restart it, by typeing in a terminal:

```
killall pulseaudio
```

Then checking your logs to see what happens when sound stops, the log files are located in /var/log. Instead of removing it, try to sort out why it is stopping.

---

### Post by Psumi on 2010-01-31
> **cariboo907 said:**
> Instead of removing pulseaudio, why not just restart it, by typeing in a terminal:

```
killall pulseaudio
```

Then checking your logs to see what happens when sound stops, the log files are located in /var/log. Instead of removing it, try to sort out why it is stopping.

Why do we need a process tree that we can see, when we can just use ALSA, which runs without a process tree we can see.

---

### Post by Hman242 on 2010-01-31
> **cariboo907 said:**
> Instead of removing pulseaudio, why not just restart it, by typeing in a terminal:

```
killall pulseaudio
```Then checking your logs to see what happens when sound stops, the log files are located in /var/log. Instead of removing it, try to sort out why it is stopping.
Someone didn't read my post :P

---

