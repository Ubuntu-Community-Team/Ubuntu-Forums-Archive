---
title: "Can no longer connect to remote server..."
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by daynesh on 2008-05-23
Greetings to all.

I've been trying to get vlc to stream video over the internet & I've finally got it to work.  What i do is ssh into my server at home 
(e.g., myserver.com) from my parents house via my laptop, run vlc to stream to my IP address where I'm located -- myparents.com. Then from a local terminal on same laptop, run vlc to receive the video stream.  Perfect...

...Until I try exiting out of the ssh session!  The session seems to be hung.  So i do a kill on the pid.  And when I try to ssh back into myserver.com, I can't!  I try pinging myserver.com but can't do that either.   However, I CAN surf the web and ping yahoo.com with no problem.

When I got back to my home, the first thing I did was try pinging myserver.com but it seems to be working fine now.  So does ssh.

Not sure what is going on but could really use some help :confused:

---

### Post by daynesh on 2008-05-24
Ok...did some more troubleshooting and can now refine my problem to what I think is going on.

When I ssh into a remote server & it stops responding regardless of the reason, I need to exit out of the session.  But sending the exit command does not work.  So what I did what kill the process but once I do this, it seems I cannot ssh back into the server.  

Anyone have suggestions on how to be able to ssh back into my home server without having to drive back to my home and restart the router?

---

