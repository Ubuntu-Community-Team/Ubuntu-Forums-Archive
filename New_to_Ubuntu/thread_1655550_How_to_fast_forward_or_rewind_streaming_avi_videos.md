---
title: "How to fast forward or rewind streaming avi videos"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by siretfel on 2010-12-29
Hi all,
I've noticed that when streaming an avi online I can't rewind or fast forward until the whole video is streamed till it finishes.
I tried with totem,mplayer plugins in firefox and also tried to stream it through vlc.
All of them manage to stream but until the video finishes i can't move forward or back in the video that's already been streamed.
In windows (beh) divx web player even vlc player can do this.
Is there a way to do it in ubuntu too?

---

### Post by Wtower on 2010-12-30
Right. I believe you will find the following helpful: 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by siretfel on 2010-12-30
Thanks for the suggestion.
So for other people who might have the same problem here's what i did and what happened:
I added medibuntu repository and installed w32codecs with 
sudo apt-get install w32codecs

The result is:
-Mplayer plugin - no change. Can stream but can't rewind or fast forward.

-Vlc player NOT as a plugin but as a sigle player can stream the video and get you to the point of the video you want even if you haven't streamed at all the way.

So this is a kind of solution for me.
Still, i don't understand why mplayer plugin can't rewind fast forward.

Thanks for your help

---

### Post by Wtower on 2010-12-30
Glad it was helpful, I have faced it too. Any chance that you convert the video to some other format before deploying to web? There are several good tools out there, both UI and command line.

---

### Post by siretfel on 2010-12-30
> **Wtower said:**
> Glad it was helpful, I have faced it too. Any chance that you convert the video to some other format before deploying to web? There are several good tools out there, both UI and command line.

If it's allright could you tell me what you did when you faced the same problem?

---

### Post by Wtower on 2010-12-30
I had used mencoder to re-encode the avi files. They were the output of an IP camera and I needed to deploy them on an intranet server with a cron job. Unfortunately I can't find the script right now, I don't use it anymore but I'm sure you can google help on mencoder it is a pretty straight-forward program.

---

### Post by siretfel on 2010-12-30
EDIT:

Unfortunately I was wrong about my assumptions.
I removed all codecs of medibuntu and have again only mplayer and vlc can still go to any time frame i want even without medibuntu.
Another peculiar problem i had was that i coulnd't install vlc-plugin for firefox.

I'm tired so I'm gonna stick to what i have.

I'm sorry i couldn't be much more helpful.

I won't give up though.

---

