---
title: "No sound on 8.04, no idea!"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by marieclairewilson on 2009-09-24
Apologies for bringing up a topic that has been answered, but I have tried many of the things listed here and elsewhere and nothing is working!:confused:
Firstly - I have no idea about programming. I run Ubuntu because it came with our new laptop and I like the philosophy.

I upgraded from 7.10 to 8.04 today, so that I could download Wine and get iTunes (also downloaded Banshee). Have got both the programmes I wanted but sound does not work. At start up, there was a message saying that either sound card isn't configured, or that I don't have the right GStreamer plugins installed.

[LIST]
[*]On sound preferences, when I try to test ALSA, I get an error message "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback". when I try to test autodetect, I get "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: No such entity"
[*]Have tried downloading and installing ALSA again, that wouldn't complete, could only find instructions for installing via the terminal, but I can't do anything cia sudo as I don't know my sudo password, or how to get one!
[*]Have tried installing pulseaudio, it is now installed and the icon is displayed in the taskbar but did not get a list of sinks and sources and couldn't add them, don't know where to look for them
[*]When I "asked" the terminal for available sound cards it didn't return anything
[/LIST]
If anyone can help me get my sound back it would be much appreciated!!
Thanks
Marie-Claire

---

### Post by rreese6 on 2009-09-24
First of all, your sudo password is the same as when you log in or install programs.
Sound can be easily messed up, especially if you keep installing programs. 

We need more information to help you.
in your terminal, type ```
lspci |grep audio
```
that should tell you what sound card you have. post the info here.
then we will go down the road some more...

---

### Post by unmole on 2009-09-24
Did you install the restricted extras ?

---

### Post by ~sHyLoCk~ on 2009-09-24
> **rreese6 said:**
> 
We need more information to help you.
in your terminal, type ```
lspci |grep audio
```
that should tell you what sound card you have. post the info here.
then we will go down the road some more...

I doubt audio will work though. It should be:

```
lspci | grep Aud
```

---

### Post by marieclairewilson on 2009-09-25
Hi all
Thanks for your replies.

I couldn't get sudo to work, but found a command somewhere to bypass it - then I followed some directions regarding a kernel - didn't really understand what I was doing, but it worked!:P

Thanks again

Marie-Claire

---

