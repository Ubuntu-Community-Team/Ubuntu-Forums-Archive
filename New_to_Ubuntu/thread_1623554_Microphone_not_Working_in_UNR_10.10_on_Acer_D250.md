---
title: "Microphone not Working in UNR 10.10 on Acer D250"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by bbright20 on 2010-11-16
The microphone is working for the sound recording application; however, it doesn't work in skype or gtalk (through google chrome). Will try with firefox to verify the same problem.

I've looked in the community and had no luck. [https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

Any help would be much a appreciated!

---

### Post by cariboo on 2010-11-18
I found I had to use alsamixer to turn up the microphone volume in order to use it with skype.

Open a terminal and type:

```
alsamixer
```

use the arrow keys to navigate and turn the volume up and down. You may have to press F5 in order to see all the controls. Once you have set the volume to your liking, press Esc, and then at the prompt type:

```
sudo alsactl store
```

to save  the settings.

---

### Post by bbright20 on 2010-11-18
> **cariboo907 said:**
> I found I had to use alsamixer to turn up the microphone volume in order to use it with skype.

Open a terminal and type:

```
alsamixer
```

use the arrow keys to navigate and turn the volume up and down. You may have to press F5 in order to see all the controls. Once you have set the volume to your liking, press Esc, and then at the prompt type:

```
sudo alsactl store
```

to save  the settings.

Thanks for the reply! 

My mic volume was all the way down and I turned it up and saved the settings but I still wasn't able to get anything working.

Any other suggestions?

---

### Post by a quarter past seven on 2010-11-18
ive been having trouble with my mic aswell i came across these when i was trying to find out how to fix mine

[http://ubuntuforums.org/showthread.php?t=1601922](http://ubuntuforums.org/showthread.php?t=1601922)
[http://ubuntuforums.org/showthread.php?t=1592115](http://ubuntuforums.org/showthread.php?t=1592115)

[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)

there might be a solution for you in there somewhere

---

### Post by bbright20 on 2010-11-19
> **a quarter past seven said:**
> ive been having trouble with my mic aswell i came across these when i was trying to find out how to fix mine

[http://ubuntuforums.org/showthread.php?t=1601922](http://ubuntuforums.org/showthread.php?t=1601922)
[http://ubuntuforums.org/showthread.php?t=1592115](http://ubuntuforums.org/showthread.php?t=1592115)

[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)

there might be a solution for you in there somewhere

Thanks alot!! Post #4 on the first link got skype working :D! Thanks for your help!!!

---

