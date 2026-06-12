---
title: "autostarting ssh and mpd on boot"
date: 2016-07-11
forum: Networking &amp; Wireless
---

### Post by delooper on 2016-07-11
Greetings, 

I am setting up a LUbuntu music server.  I have the ssh daemon, and mpd configured to autostart. . . but if I try to ssh into the music server immediately after it boots, I get the response:

```
ssh: connect to host 192.168.1.88 port 22: No route to host
```

similarly if I use an mpd client I get a EHOSTUNREACH error. 

But if I log-in to my music server locally, I can then log-in remotely with ssh, and similarly, the mpd daemon is now reachable with a client. 

I suspect what's going on is either ssh and mpd only load when a user logs-in locally, or they aren't listening on the ports until a user logs-in locally. 

Is there a way to fix this, ideally without auto-logging in a user? 

edit:

Oh!  I was looking at this all wrong.  

I think what's going on is my music server is connected to the network via wifi.  And wifi authentication is user-centric, so it only happens when a user logs in.   

So what I need to do is get LUbuntu to log into the wifi network at startup.  

I'm getting a bunch of hits on Google for this search but I have not quite found an answer yet.

edit 2: Ridiculously simple solution.  Step 1: log in to the Lubuntu GUI.  Step 2: click on the network connections button.  Edit wifi.  Step 3: click on "all users can use this".  Step 4: reboot.  

It works fine now.

---

