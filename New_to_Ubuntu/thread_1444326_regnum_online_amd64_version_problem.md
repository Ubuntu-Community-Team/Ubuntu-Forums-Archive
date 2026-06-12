---
title: "regnum online amd64 version problem"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by aloprot on 2010-04-01
I downloaded the regnum online 64 bit version for linux and when i try to install it i get "
There is no application installed for executable

How can I fix this? how can i run and install the game? I have the drivers and everything. Thanks

---

### Post by aloprot on 2010-04-01
No one knows?

---

### Post by Grenage on 2010-04-01
I used Regnum Online on my Ubuntu x64 box, it ran without a hitch.  Are you sure you haven't downloaded a Windows binary?

Assuming it's just a bin, you'll want to make it executable, then run it:

```
chmod +x *regnum-file-name*
./*regnum-file-name*
```

---

### Post by aloprot on 2010-04-01
Thank you so much, it worked. Yes it was a bin. :) Thanks very very much sir.
Ohh but i stoumbled in a problem, my sound doesn't  work on the game:| How can i fix it?

---

### Post by Grenage on 2010-04-01
A pleasure; have fun!

---

### Post by aloprot on 2010-04-01
Could you tell me how can i fix the sound on the 64 bit version? I checked and the sound isn't muted or something. Only in the game doesn't work

---

### Post by Chesamo on 2010-04-01
I don't know exactly what Regnum Online is, but check your sound settings and make sure they're going to PulseAudio. (Assuming you're using the default Ubuntu install.)

---

### Post by aloprot on 2010-04-01
Where can i modify that? I don't know.

---

### Post by Chesamo on 2010-04-01
Wherever the sound settings are in Regnum. Logically, it should be located in the menu option labeled "Settings", "Options", or "Preferences" under a menu named "Tools" or "File". I'm not in a position to test this theory at the moment.

---

### Post by Idaho Dan on 2010-04-01
aloprot,
I know you need to get Openal. I just don't remember where I got it from.
"Great tip, i had the same problem and it's nice to have sound now. libopenal1 did the job." I just got this from the Regnum forums.

---

### Post by aloprot on 2010-04-01
Sadly it's already installed, i searched on google and found that i need that, installed from the synaptic manager but still i have no sound.

---

### Post by Scibax on 2010-04-05
Make sure openAL is installed.  Then do the following:


sudo gedit /etc/openal/alsoft.conf

Uncomment line 171 and make sure it is as follows:

device = alsa

Reboot and enjoy audio in Regnum.

---

### Post by aloprot on 2010-04-24
It's working, thank you so much.

---

### Post by aloprot on 2010-04-25
I was so happy that it worked so I quit the game and wrote the post above and marked the thread as solved but it seems like I have a problem. Ok so I log in, I play, I hear music but suddently I hear some funny noise, just like when having a radio and searching for stations to listen to, that (sssssssssssssssssssssssss.....sound) It comes, it goes away, sometime it stays longer somethimes it doesn't last but 4 seconds, and sometimes it lasts long and after that I no longer hear sounds in the game. What can I do?
I'm playing this on a dell inspiron 1545.

---

