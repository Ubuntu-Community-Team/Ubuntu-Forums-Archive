---
title: "Ubuntu 8.10 newbie mess up"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by escozul on 2009-01-16
Hello,

I own a Sony Vaio VGN-B1XP laptop and decided to move on from windows and try a linux distro on it.

So I installed the 8.10 version on it and it seemed to work GREAT! On almost every aspect too! graphics, CD etc worked excelent. However the sound card was not working.

It seemed to acknowledge the existence of a sound card as It did have a mixer working, but no sound would come out.
I also tried the lspci command as so:

```
escozul@escozul-VAIO:~$ lspci | grep Audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
```

And it seemed to find the right audio card... strange...

anyway I tried fixing the problem using the guidelines noted on this thread: [http://ubuntuforums.org/showthread.php?t=415363&highlight=vgn-b1xp+sound](http://ubuntuforums.org/showthread.php?t=415363&highlight=vgn-b1xp+sound)

Before restarting I also installed the latest updates from the notification bar... and after the restart the system failed to load X. it just stopped in a console mode asking me to give username and password
I reported that there was no image to resume from and stuff, which is strange cause that was right after a clear restart...

When I log in and use startx command, the X system loads up but this time the volume control reports that there is no device. However the lspci command still reports the AC'97 audio controller present. Also I cannot log out, restart or shut down through the graphical interface. I need to Exit the graphical interface and restart from the console.

What a mess right??? any help with that pls?

---

### Post by Daz_S on 2009-01-16
I know it's not inside the forums here, but I used the instructions here:

[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/]("http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/")

Looked like it cleared whatever the conflict was on my install (not saying there was one... I may just have screwed up...) but my sound works great now!

---

### Post by jerome1232 on 2009-01-16
If all you did was add that line to the end of /etc/modprobe.d/alsa-base remove the line you added. BTW sound has changed ALOT since feisty.

Just log in to the console, type "sudo nano /etc/modprobe.d/alsa-base" Remove the line you added, hit ctrl+o to save, ctrl+x to exit, then reboot, "sudo reboot"

---

### Post by escozul on 2009-01-19
What I did was to run the following 2 lines:

> sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

> sudo apt-get install linux-sound-base alsa-base alsa-utils

Then I rebooted...
And that's when the problems started pouring in...

I still go to console when I log in :(

Any other Ideas?

---

### Post by hyper_ch on 2009-01-19
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by escozul on 2009-01-19
Hmmm... right...

So could an admin change the subject of the thread to "VGN-B1XP Vaio Sound not working on Ubuntu 8.10"?

Also the lines that were not in code tags were copied that way from the corresponding thread. Anyway, I added the code tags.

Hope that would help... maybe I should start another thread?

---

### Post by escozul on 2009-01-21
Ok this post is abandoned. I reposted here: [http://ubuntuforums.org/showthread.php?p=6589291#post6589291]("http://ubuntuforums.org/showthread.php?p=6589291#post6589291")

If you can help me please follow that thread cause I've better analysed the issue there. Thank you

---

