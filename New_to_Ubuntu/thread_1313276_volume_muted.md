---
title: "volume muted"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by n.hinton on 2009-11-03
Just upgraded from Jaunty to Karmic. Now every boot up the volume is muted. Anyone know how to make it remember the volume level between boot ups.

---

### Post by mac9416 on 2009-11-03
Hi there!

Here is how I did it:

[LIST=1]
[*]Run 'alsamixer' in the Terminal
[*]Get the settings where you want them and press Esc to exit
[*]Run 'sudo alsactl store 0' in the Terminal
[*]Run 'sudo gedit /etc/rc.local' in the Terminal
[*]Add "/sbin/alsactl restore" to the end of that file and save it
[*]Reboot and test the results!
[/LIST]

If you are not familiar with alsamixer, there's some great info here: [https://help.ubuntu.com/community/SoundTroubleshooting#Using%20alsamixer](https://help.ubuntu.com/community/SoundTroubleshooting#Using%20alsamixer)

Good luck!

---

### Post by n.hinton on 2009-11-04
Thanks mac9416, rebooted and volume was not muted

---

### Post by n.hinton on 2009-11-13
The above has had intermittent success (sometimes muted sometimes not). Saw the following  post and gave it a try, and this has proved a permanent fix.

Posted by:   **eli_12345**
in post 6 of:**Honestly - why is sound muted by default?**

My Xubuntu 9.10 got the same issue - sound was always muted after booting the system. I just came across an easy solution that finally worked: comment out the line that contains 'mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1' in the file /etc/init.d/alsa-utils (it was line 378 on my system, just add # to make that line a comment, that's it).

---

### Post by mac9416 on 2009-11-13
Thanks, n.hinton, that worked like a charm!

---

### Post by Elviswind on 2009-11-13
I'm now running Xubuntu 9.10 and had the sound muting problem, but I was also suffering from crappy sound . . .  high frequencies did not sound correct.  I tried the edit to /etc/rc.local and that sort of worked to correct the muting problem, but the sound was still crummy.

What I found was, and I think this will work better in Xubuntu than other Ubuntu, that removing Pulseaudio solved all the problems.  

Look at post #4 in this [thread]("http://ubuntuforums.org/showthread.php?t=1313253") and give it a whirl.  Note: Becuase I'm running Xubuntu I didn't need to follow the last couple steps to install another mixer program . . . the one included with Xfce still works just fine.  :p

---

### Post by 84monte on 2009-11-18
When I execute 'sudo alsactl store 0' I get the error:

/home/myname not ours

Am I doing something wrong?


> **mac9416 said:**
> Hi there!

Here is how I did it:

[LIST=1]
[*]Run 'alsamixer' in the Terminal
[*]Get the settings where you want them and press Esc to exit
[*]Run 'sudo alsactl store 0' in the Terminal
[*]Run 'sudo gedit /etc/rc.local' in the Terminal
[*]Add "/sbin/alsactl restore" to the end of that file and save it
[*]Reboot and test the results!
[/LIST]

If you are not familiar with alsamixer, there's some great info here: [https://help.ubuntu.com/community/SoundTroubleshooting#Using%20alsamixer](https://help.ubuntu.com/community/SoundTroubleshooting#Using%20alsamixer)

Good luck!

---

### Post by mac9416 on 2009-11-18
Hey, 84monte,

No, that error occurred on my machine too. It is of no consequence. However, I would suggest using the method described by n.hinton instead.

[LIST=1]
[*]Open /etc/init.d/alsa-utils for editing...
```
$ sudo gedit /etc/init.d/alsa-utils
```
[*]Comment out the line that says...
> mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1 
...to look like...
> #mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1 
***Note:** you can search for the line using ctrl+f*
[*]Save the file, and reboot!
[/LIST]

Good luck!

---

### Post by ethos101 on 2009-11-20
> **mac9416 said:**
> Hi there!

Here is how I did it:

[LIST=1]
[*]Run 'alsamixer' in the Terminal
[*]Get the settings where you want them and press Esc to exit
[*]Run 'sudo alsactl store 0' in the Terminal
[*]Run 'sudo gedit /etc/rc.local' in the Terminal
[*]Add "/sbin/alsactl restore" to the end of that file and save it
[*]Reboot and test the results!
[/LIST]

If you are not familiar with alsamixer, there's some great info here: [https://help.ubuntu.com/community/SoundTroubleshooting#Using%20alsamixer](https://help.ubuntu.com/community/SoundTroubleshooting#Using%20alsamixer)

Good luck!

I did that and all the levels are up where I want them but alsamixer still starts with them all muted by default.  How do I have them unmuted at startup?
Thanks.

---

### Post by mac9416 on 2009-11-20
Hey, ethos101,

It turns out that commands in rc.local don't run at startup like they are supposed to. At least they don't for me. I ended up putting '/sbin/alsactl restore' in my Fluxbox startup script and it worked fairly reliably.

However, the best method is probably the one suggested by n.hinton that I described above ( post #8 ). Give it a try and tell me how it turns out.

Good luck!

---

### Post by ethos101 on 2009-11-20
> **mac9416 said:**
> Hey, ethos101,

It turns out that commands in rc.local don't run at startup like they are supposed to. At least they don't for me. I ended up putting '/sbin/alsactl restore' in my Fluxbox startup script and it worked fairly reliably.

However, the best method is probably the one suggested by n.hinton that I described above ( post #8 ). Give it a try and tell me how it turns out.

Good luck!

Yea, that was the first method I tried.  It didn't work at all.

---

### Post by mac9416 on 2009-11-20
> **mac9416 said:**
> 
[LIST=1]
[*]Open /etc/init.d/alsa-utils for editing...
```
$ sudo gedit /etc/init.d/alsa-utils
```
[*]Comment out the line that says...
> mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
...to look like...
Quote:
[QUOTE]#mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1 
***Note:** you can search for the line using ctrl+f*
[*]Save the file, and reboot!
[/LIST][/QUOTE]

So you tried the above method and it didn't work? If so, try running '/sbin/alsactl restore' and see if it restores your settings. If it does, we'll have to find some startup script that will run that command on bootup.

---

