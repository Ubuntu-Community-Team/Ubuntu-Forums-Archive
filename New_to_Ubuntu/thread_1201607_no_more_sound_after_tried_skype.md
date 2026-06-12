---
title: "no more sound after tried skype"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by balta on 2009-07-01
hello there!
i've been using ubuntu for about 2 years and i've never done such a stupid thig like this :???:

i was trying to get skype to work on my computer so i downloaded the .deb from the site and installed, no sound tough :(

i stupidly followed a guide somewhere on the internet that told me do to this:
```

$ killall pulseaudio
$ sudo apt-get remove pulseaudio
$ sudo apt-get update
$ sudo apt-get install pulseaudio ubuntu-desktop

```

after that skype still didn't work and moreover i was unable to her any sound so i did

```

$ killall pulseaudio
$ sudo apt-get remove pulseaudio
$ sudo apt-get update
$ sudo apt-get install pulseaudio

```

which i believed would restore the situation but nothing changed

can someone please tell me what to do to restore the audio configs?

i already checked the 
System>preferences>sound but everything seems fine and changing the default options don't solve anything

sound has never been a problem for me (never had to change settings or other) so i just can't get what i messed up

i'm running 9.04 please help me

thx

---

### Post by ~sHyLoCk~ on 2009-07-01
Did you try running ```
sudo alsaconf
```  and ```
sudo alsactl store
```

---

### Post by balta on 2009-07-01
thanks for the attention!
i just tried the comands you suggested and this is the output

```

balta@balta-linux:~$ sudo alsaconf
[sudo] password for balta: 
sudo: alsaconf: command not found

```

---

### Post by balta on 2009-07-01
ffiu solved it
```

sudo alsamixer 

```

clearly showed me the master was to 0% :???: 

thanks for your time sry for bothering you.

one last question if you don't mind: why this happened?

edit: nevermind, i shall never leave my account open to my brother :???:

---

### Post by ~sHyLoCk~ on 2009-07-01
Not sure maybe reinstalling pulseaudio messed up your alsa settings.

---

