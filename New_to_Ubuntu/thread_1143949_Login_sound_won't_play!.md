---
title: "Login sound won't play!"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by abbott_j on 2009-04-30
I have tried to change my login sound, the one that plays when you type in your password incorrectly or login.

---

### Post by LowSky on 2009-04-30
did you install MP3 support?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by abbott_j on 2009-04-30
then what, do i just rename them all?

---

### Post by NightwishFan on 2009-04-30
Go to:

Administrator -> Login Window?? (Something like that, I am not on Ubuntu now so I forgot...)

The sound that plays when you fail your password should be configurable from there. I would think you should make it a PCM .wav file.

If you want to convert a file into wav, simply install soundconverter.

```

sudo apt-get install soundconverter

```

Drag and drop a file into sound converter, and under preferences, tell it to convert it to wav. Make sure you do not tell it to delete the original.

---

### Post by abbott_j on 2009-04-30
they are already in wav but they still don't work

---

### Post by NightwishFan on 2009-04-30
Hrmm...... Well sometimes the login thing resets some configuration on its own like a bug, though I doubt that is the problem. Sorry I could not be of more help.

Does it play the default sound, or no sound when you change it?

---

### Post by abbott_j on 2009-04-30
it's the default beep when it has nothing to play, ya know, the one that comes from the computer itself

---

### Post by NightwishFan on 2009-04-30
Ah, I see. I am not currently on Ubuntu right now, however when I go home I will see if I can get it to work. I will report back.

---

### Post by unutbu on 2009-04-30
```
gksu gedit /etc/gdm/gdm.conf
```

Edit```

SoundOnLoginFile=/usr/share/sounds/question.wav
```
so that the path points to your sound file.

You will have to restart gdm to make the change effective:
Either reboot the machine, or try this:

Log out. Press Ctrl-Alt-F2. Log in at the text prompt. Type
```

sudo /etc/init.d/gdm restart
```
Logout. Press Ctrl-Alt-F7 to get back to the gdm login window.
Try logging in.

---

### Post by abbott_j on 2009-04-30
i can log in fine, it just doesn't make the sounds that i want it to, the ones in the sounds menu in preferences work but not the login window ones

---

### Post by NightwishFan on 2009-05-01
T_T I forgot to check.. I will make a note this time.

Edit: I have F11 KDE installed right now anyway....

---

