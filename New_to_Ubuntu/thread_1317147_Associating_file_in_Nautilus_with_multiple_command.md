---
title: "Associating file in Nautilus with multiple commands"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by kopatops on 2009-11-06
Hi!

I just started trying to write shell scripts. I have the infamous stuttering-vlc-sound-with-pulseaudio problem. Although there may be a more logical approach to solving it in my specific case, I found that if i just execute

```
killall pulseaudio 
```

just before opening the video file the problem disappears for that file. So I wrote a script
```

#! /bin/bash
#
# FIRST kill pulse
killall pulseaudio;
# THEN start vlc with file
/usr/bin/vlc %U
clear
exit
```

, where the intention was  for vlc to interpret %U as the path to the file opened in Nautilus, copying the panel launcher command. The script has been made executable and added to the Open-with list in nautilus.

Bottom-line; It doesn't work, and I have absolutely no idea how to do this properly. 
Anyone want to help me? How do I pass arguments properly? (killall pulse is executed but VLC complains about not finding %U, literally.) 

Tnx!

---

### Post by amingv on 2009-11-07
Try this:

```
#!/bin/bash
#
# FIRST kill pulse
killall pulseaudio;
# THEN start vlc with file
/usr/bin/vlc **$1**
clear
exit
```

---

### Post by kopatops on 2009-11-20
Thanks for the reply! :) 

Yeah, it works a lot better! However the path which is represented by the argument '$1' generally has space characters (several) in it. This means somehow the input argument is interpreted as several input files, so instead of the correct

'/path/to/some /nice file'

the argument(s) become

'path/to/some'
'/nice' 
and
'file'

Is there a simple way to deal with this, i.e. allowing the $1 argument to be interpreted as one path '$1'?

Thanks!!

EDIT: Oh, and I tried to replace $1 with '$1', which didn't work.  :P

---

### Post by sisco311 on 2009-11-20
```
vlc "$1"
```

---

### Post by kopatops on 2009-11-20
Works like a charm. ;)

Hehe, feeling like such a first-cup. It seems so obvious now. Well, I guess one always has to start somewhere.

Now I can enjoy smooth audio with a click from within Nautilus. Thank you!

Marking the thread as [SOLVED]

---

