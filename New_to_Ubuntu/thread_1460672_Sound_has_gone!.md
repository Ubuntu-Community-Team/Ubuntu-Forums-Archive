---
title: "Sound has gone!"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by da burger on 2010-04-23
I'm sure there is a simple solution to this but my sound has stopped working. Until recently I could listen to music both from my headphones or the inbuilt speakers on my laptop but now neither work. I have tried listening to music on we7, watched a video on youtube and played a sound file on my hard drive.

I have not used my laptop for a couple of weeks (I was on holiday) but I just got back and would really like to listen to some music and watch some TV on the iplayer.

Thanks in advance
Angus

---

### Post by xumuk37 on 2010-04-23
it seems that your sound daemon isn't running try ```
pulseaudio --start
```

---

### Post by da burger on 2010-04-23
I'm afraid that didn't help. The command ran without any errors but when I tried to listen to some music I still didn't hear anything. Something I just noticed is that in the output pane for sound preferences it says the the output device is Dummy Output and no other options are available and in the input panel no options are available at all (although I have a microphone built in)

EDIT: I now feel like an idiot. I always forget remember to try log in and log out after I post a support request. Everything is back to normal now. Thanks for your help. I would still like to know what the problem was but that's just curiosity. Again thanks

---

