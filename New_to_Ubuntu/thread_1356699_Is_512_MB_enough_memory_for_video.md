---
title: "Is 512 MB enough memory for video?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Synoc on 2009-12-16
ok I've been looking for answers to this question. and I am still new to Ubuntu, but I'm on 9.10. I got MoviePlayer to work, I can play my DVDs on it, but the video and audio, don't match, the audio track runs fine but the video has to catch up and it's fuzzy. After searching for two days I found nothing to help me. so I made a few calls, my brother who was using linux tells me "Linux's Ram uses isn't as polished as Windows, if you are using Ubuntu, it's better designed for newer systems, you might be better off using Debian." now if this is true it's all well and good, not like I spent any money on this... but before I spend time downloading another linux, is there anything I can do to clean up my DVD playback?

---

### Post by SlickRick on 2009-12-16
Try downloading a media player that uses xine as a backend. Just type in xine-ui in the synaptic package manager. Sometimes my compuetr struggles with higher quality video, so I play it in another player.

---

### Post by snowpine on 2009-12-16
Hi Synoc, RAM is only part of the equation... tell us about your CPU and video card too.

(SlickRick has a good suggestion too.)

ps Ubuntu gets the majority of its code from Debian--it is unlikely (though not impossible of course) that switching to Debian will solve the problem.

---

### Post by rajeev1204 on 2009-12-16
> **Synoc said:**
> ok I've been looking for answers to this question. and I am still new to Ubuntu, but I'm on 9.10. I got MoviePlayer to work, I can play my DVDs on it, but the video and audio, don't match, the audio track runs fine but the video has to catch up and it's fuzzy. After searching for two days I found nothing to help me. so I made a few calls, my brother who was using linux tells me "Linux's Ram uses isn't as polished as Windows, if you are using Ubuntu, it's better designed for newer systems, you might be better off using Debian." now if this is true it's all well and good, not like I spent any money on this... but before I spend time downloading another linux, is there anything I can do to clean up my DVD playback?

Use vlc player.

---

### Post by Synoc on 2009-12-16
> **snowpine said:**
> Hi Synoc, RAM is only part of the equation... tell us about your CPU and video card too.

(SlickRick has a good suggestion too.)

just integrated video, 2.4 ghz processor. again though with Windows I could play movies fine and multitask with internet and MS word on a second monitor before i had to start working about quality reduction.

---

### Post by snowpine on 2009-12-16
> **Synoc said:**
> just integrated video, 2.4 ghz processor. again though with Windows I could play movies fine and multitask with internet and MS word on a second monitor before i had to start working about quality reduction.

My point is, some video needs special drivers... use the terminal command 'lspci' to figure out exactly which card you have, then use the Search function on these forums to read if others are having the same experience (and if so, how did they solve it).

This is of course assuming that installing xine or vlc doesn't fix the problem.

---

### Post by sandy8925 on 2009-12-16
Try using mplayer. If the video card you have is an Intel card (which I suspect it is since most integrated ones are Intel) then you can try using the xv video output to play video. Using that makes video playback smoother for me and I can even play 720p video smoothly to some extent. To use xv for video output, use the command : 

mplayer -vo xv filename

To make sure that audio and video are synched you could use the -framedrop option. If the system is too slow to play the video this will result in jerky video.

You can also install gnome-mplayer and select the above in the options, if you want an easier way.

---

### Post by Synoc on 2009-12-16
I'll have ot get back to you when I figure out why my wireless internet only cuts out when I try ot use it
LOL keep the light on for me : )

---

