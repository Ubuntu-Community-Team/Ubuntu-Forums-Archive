---
title: "no sound"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by rhythmiccycle on 2009-04-23
:confused:

my sound stopped working
it was working,

then i installed vlc player.
it was working with sound.

 I went to shut down later on,
it started to shut down.
then the screen when black (not off, just black)
the computer never stopped running,
so i pulled the plug

when i started up again
some words flew past the screen (not normal ones)
and then it loaded ubuntu seeming fine.
but when i went to play the same file, that was working after i installed, didn't have sound.

i shutdown again and had the same problem.

there is no sound at all, even the start up sound.

what should i do?

---

### Post by RichardLinx on 2009-04-23
Did you check if the sound is even turned on? It might just be muted. I've seen a lot of users (Trust me, it's more then you'd believe) that have had similar issues only to realise that for some reason or other the sound decided to go mute. (Just check your vloume control, you can open it by clicking the icon of a speaker in your top bar Ubuntu menu - If you're using GNOME that is).

If it's not muted then it's easily fixed. Run the following:

```
killall pulseaudio
```
```
sudo apt-get remove pulseaudio
```
```
sudo apt-get install esound
```
```
sudo rm /etc/X11/Xsession.d/70pulseaudio
```

Reboot your system and sound should work fine. (Again, check that it isn't muted)

And yes, that last command does involve "rm" but I assure you it won't corrupt your data.;)

---

### Post by rhythmiccycle on 2009-04-23
i did the  code like you said,

and the master volume, in the top right corner, is set to 100%.

but i still don't have sound.

when i start in windows the sound works, so the hard ware is all connected.

is there anything else i can do?

---

### Post by rhythmiccycle on 2009-04-24
It works!!


i updated every thing and restarted again, and now it works


(i also did a check disk)

thanks for the help

---

