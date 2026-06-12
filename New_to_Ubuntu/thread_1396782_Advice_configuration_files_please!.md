---
title: "Advice configuration files please!"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by listerdl on 2010-02-02
Hi, i am following this popular tutorial to try and install sound - im using Karmic and have never been able to have sound. (Yes I have tried the mute controls to no avail).

This comes from here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

[B]All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.

1. Backup (and then delete) your previous configuration files:
Code: [/B]

```
 $ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ rm -r ~/.pulse ~/.asound* 
$ sudo rm /etc/asound.conf
```

Sorry to be so ignorant but do I literally copy and paste the output so that I save the files?

Thanks !

---

### Post by nothingspecial on 2010-02-02
You copy and paste it into your terminal one line at a time ommitting the initial $.

It would be an idea to try and understand what commands do before you just copy and paste willy nilly off the internet though.

That looks fine btw

---

### Post by listerdl on 2010-02-02
Thanks. In fact I am trying out this tutorial to fix my sound....HOWTO: PulseAudio Fixes & System-Wide Equalizer Support - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

When I did this: 

```
 $ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/

```

This happened:

```
mkdir: cannot create directory `/home/henry/pulse-backup': File exists

```

Any ideas? That means that the File does exist right.....? I am trying to find this file to delete it. To fix the sound issue, a popular tutorial advises us to "Backup (and then delete) your previous configuration files" using the above code but that doesnt seem to work....

How do I fix this? Thanks!

---

