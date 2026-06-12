---
title: "Find length of a song in terminal"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by superprash2003 on 2010-11-07
Hey,
     I've been working on a small script part of which requires me to get the length of a song in seconds or minutes . So the input would basically be a path for the song and the output should give me the length of the song .
  Now i want to do this without playing the song because this script works on a lot of files and it does a certain task based on the length of the song . 
  At this point of time i can think of only one way where i run an instance of rhythmbox and then use  rhythmbox-client --print-playing-format=%td  to get the length. But this requires me to play the song and hence i hear music in the speakers . I would want a way to get the length of the song without actually playing the song.
  Any help on this would be appreciated. Thanks..

---

### Post by rampageoberon on 2010-11-07
Hi,

Have you tried sndfile-info (available in the sndfile-programs) package or ecalength (available in ecasound package)

Cheers,

---

### Post by superprash2003 on 2010-11-07
@rampageoberon
  thank you so much for the reply.. That was the output that i was looking for , but is there a way to do this without installing any package cause for ecalength to work i need to do a sudo apt-get install ecasound to install the package first and then use it and i will be running this script on multiple machines and i do not want to wait for the package to install and not to mention the sudo password which needs to be entered.

---

### Post by superprash2003 on 2010-11-08
any other suggestions? would really like some help... :)

---

### Post by rampageoberon on 2010-11-08
There is another tool you can use (sox but would need to install libsox-fmt-all)

```
sox /path/to/audio/file -n stat | grep -i length
```

But with regard to installing the extra packages, it is only a one off thing and I don't know of any other tools unfortunately.

---

### Post by superprash2003 on 2010-11-12
i guess there is no other way than to install the package.. and sox is much more accurate than ecalength..Thanks a lot rampageoberon..

---

