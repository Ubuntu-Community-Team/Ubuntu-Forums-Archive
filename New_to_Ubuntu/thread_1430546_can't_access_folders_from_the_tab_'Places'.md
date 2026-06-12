---
title: "can't access folders from the tab 'Places'"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by myrnamynkoff on 2010-03-15
Hi,  please help me! 
I'm new with linux/ubuntu and today I was downloading pictures from my camera to the 'Images' folder and trying to switch users from the chat program Empathy at the same time. but when I tried to do that, I clicked on switch users of the whole computer instead. So it took me back to he first screen where you are supposed to choose your user. So i clicked back on my opened session and the computer just froze. after a long time i shut it off and back on again, and now i can't access any folder under the tab that says 'Places'. But if for example I try to open a video with the Movie Player program, it does allow me to go into the folder 'videos', it's just that if I want to go straight to that folder I can't. 
I don't know how to fix it and also I don't know how to open folders from the terminal either :(

please help me ge back to my folders!


thank you my friends :)

---

### Post by lidex on 2010-03-15
Run this command in a terminal and post any error output:
```
nautilus --no-desktop
```

---

### Post by myrnamynkoff on 2010-03-15
[FONT=monospace]ok thank you, this is what it showed up. by the way i tried creating a new user with administrator rights and it does let me go to the folders from that user. the problem is i don't know how to share the folders between users now. also the problem is getting a little bit worse now, because it already froze 2 times since my firs post :S

anyways, this is the result from the terminal: 

myrna@noelia-laptop:~$ nautilus --no-desktop

(nautilus:3001): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:3001): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3001): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3001): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Fallo de segmentación


sounds bad :(
[/FONT]

---

### Post by lidex on 2010-03-15
Really bad -- kidding ;)

Run this command and reboot:
```
mv ~/.local/share/gvfs-metadata gvfs.old
```

---

### Post by myrnamynkoff on 2010-03-15
yey!

I'm so happy I can see my folders again!!!

thank you so much Lidex you're the best! :D

have a great day, thanks!! ^^

---

### Post by lidex on 2010-03-15
You're welcome! You can delete that renamed folder now (gvfs.old).
And don't forget to mark the thread as "solved" using "thread tools" near the top.

---

### Post by Henery on 2010-04-16
Wow thank  you I had the same problem and this fixed it I was worried it was the hd thank you!!!

---

