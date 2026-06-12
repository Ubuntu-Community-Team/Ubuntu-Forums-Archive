---
title: "Can´t remove the 10.04 login sound"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by Jaraqui on 2010-07-06
Hi people,


   I can't remove that sound in the 10.04 login screen.

   What I already did:
   1) System - Preferences - session applications -> remove gnome/login;
   2) System - Preferences - Sound Preferences -> mute in Sound effects

   These two actions didn't remove that sound.

   Any ideas/recommendations to solve this problem?
   If this problem is already solved here in the forum, sorry and, please,
indicate me the link.

Regards
Jaraqui

---

### Post by jtarin on 2010-07-06
[Try this solution]("http://ptspts.blogspot.com/2010/06/how-to-disable-login-sound-and-other.html")

---

### Post by stmiller on 2010-07-06
Yeah it's System > Preferences > Startup Applications > uncheck GNOME Login Sound

---

### Post by warfacegod on 2010-07-06
```
sudo apt-get remove ubuntu-sounds
```

This will remove the sound theme from Ubuntu, including the damned drum roll login sound.

---

### Post by lidex on 2010-07-07
Uncheck 'Play login sound' in 'System>Administration>Login Screen'
...or do you have that?
You could also remove gnome-session-canberra - note:also removes ubuntu-desktop metapackage.

---

### Post by philinux on 2010-07-07
Navigate here with gksu nautilus

/usr/share/sounds/ubuntu/stereo

Rename dialogue-question.ogg to dialogue-question.ogg.back

You can always have it back if needed.

Or change any other .ogg or .wav file to replace it.

---

### Post by KdotJ on 2010-07-07
Glad I stumbled across this thread, I hate the login sounds, Thanks guys!

---

### Post by warfacegod on 2010-07-07
> **KdotJ said:**
> Glad I stumbled across this thread, I hate the login sounds, Thanks guys!

Why not post which solution worked for you? That way everyone benefits.

---

### Post by Jaraqui on 2010-07-07
> **warfacegod said:**
> ```
sudo apt-get remove ubuntu-sounds
```This will remove the sound theme from Ubuntu, including the damned drum roll login sound.


Cirurgically correct! Thank you! 

Problem Solved.

Regards
Jaraqui

---

### Post by warfacegod on 2010-07-07
> **Jaraqui said:**
> Cirurgically correct! Thank you! 

Problem Solved.

Regards
Jaraqui

You'll need to throw me a definition here. I have no idea what "Cirurgically" means.:p

Don't forget to mark this as Solved under Thread Tools.

---

### Post by Jaraqui on 2010-07-07
Cirurgically = Exactly correct!

---

