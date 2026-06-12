---
title: "Matroska / .mkv question"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by earthpigg on 2010-11-17
Got a video I'd like to watch, in the Matroska video container format.

As explained to me by wikipedia, it's a container format that contains other video/audio/subtitle stuff inside it.

I'd like to access it.

Here's why:

In totem (aka system -> sound and video -> movie player) the audio is perfect and the video horribly choppy.

In VLC, the video is perfect and the audio horribly choppy.

So, both audio and video are perfectly intact.

Both VLC and totem also do this wonderfully annoying thing of caching the video only 5 seconds in advance, with fast forward and rewind completely impossible. I can pause and play, but watching it is essentially identical to a VHS player without a rewind or fast forward button.

Blek. I'm on an i7 with a well supported nVideo card, so I don't think hardware or processing power is the problem. 

So, what tools should I use to find out what files are in this container and, maybe, attempt to remove a layer of abstraction?

OggConvert's output is the same as if I were playing it in totem or VLC.

---

### Post by stefangr1 on 2010-11-17
You can give mplayer a try. It used to perform quite a lot better when compared to VLC and the other players, though the latter have improved a lot during recent years.

---

### Post by bioterror on 2010-11-17
'sudo apt-get install mkvtoolnix' might help you.
mkvinfo and mkvextract are the commands you might be after.

is your file 1080p or what? do you have VDPAU in use? not that your CPU couldnt handle ;)

---

### Post by earthpigg on 2010-11-17
i knew there was a big media player i was forgetting. mplayer seems to work fine, thanks.

---

### Post by stefangr1 on 2010-11-17
> **bioterror said:**
> 'sudo apt-get install mkvtoolnix' might help you.
mkvinfo and mkvextract are the commands you might be after.

is your file 1080p or what? do you have VDPAU in use? not that your CPU couldnt handle ;)

If you use mplayer from the command line (if needed with the -v (verbose) option), you can get even more info on why the file isn't playing well.

---

