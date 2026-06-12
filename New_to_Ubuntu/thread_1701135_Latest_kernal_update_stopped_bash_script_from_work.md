---
title: "Latest kernal update stopped bash script from working"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-03-06
I have an entry in startup applications for <banshee --hide> to run banshee in its hidden state and i have a bash script entry which sleeps for a few seconds to allow time for the login sound and then plays a random song. Its been working fine for ages but the last kernal update seems to have stopped them working, its a problem ive had before but its not happened since the launch of maverick, i cant seem to get it to work but i boot up my machine, then logout, it will work on all subsequent logins until i turn off my machine?? 

Any ideas why?
Heres the script, its only basic:```
#! /bin/bash
#This is a simple bash script to automatically play music

sleep 15 && banshee --play
```

---

