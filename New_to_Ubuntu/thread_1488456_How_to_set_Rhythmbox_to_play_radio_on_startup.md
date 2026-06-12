---
title: "How to set Rhythmbox to play radio on startup"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by Amida on 2010-05-20
Hi,

I recently installed Lucid. It is a wonderful OS and I use it with a great pleasure. I have only one very small issue:

it there any way to set Rhythmbox to start playing an added radio station, after I boot up my laptop and press play on the Rhythmbox tray icon (i have tried shutting down with played radio, hoping that Rhythmbox will remember the played state)

Thank you in advance.

---

### Post by tubunu on 2010-06-06
I would also like to know that. You can try Gnome-schedule to start Rhythmbox on each reboot, however, I don't know the command for starting a particular radio station with it on reboot. Maybe someone else could help.

---

### Post by tubunu on 2010-06-06
Actually, I've just figured out a way around that. 

Forget gnome-schedule, it doesn't seem to do what it was designed for. Try this: go to System/Preferences/Startup Applications and click on Add Startup Program. In the Command box type the following: 
```
rhythmbox-client --play-uri=http://your.radio.station.address.here
```

For example, if you'd like a Jazz FM radio station in London, try the following: 
```
rhythmbox-client --play-uri=http://mp3-jazz.as34763.net/listen.pls
```

To have the song/artist name pop up while playing:
```
rhythmbox-client --play-uri=http://mp3-jazz.as34763.net/listen.pls --print-playing
```

This will launch Rhythmbox upon each boot/log in and you don't even need to press the play button. :guitar:

---

### Post by chris78323 on 2013-04-14
#!/bin/bash
rhythmbox-client --play-uri=http://www.abc.net.au/res/streaming/audio/mp3/local_brisbane.pls username 9 # JOB_ID_33 

# after the commard i put the username to run the program and a number from what I can tell this tells bash that it is running an X-application

---

### Post by lisati on 2013-04-14
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

