---
title: "internet radio stream"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by dansar99 on 2009-11-28
What would make a radio stream buffer every few minutes using 9.10 and work perfectly using XP on my dual boot system. I thought Linux worked better on older computers. Can anyone explain this? I am a end user and have to muddle thru problems. I tried reading the PulseAudio wiki. That left me confused. I downloaded medibuntu and the problem still exists. The stream works perfectly except for the buffering. There must be some techie tweak I need to do but I am no techie . Can anyone help?  Dan

---

### Post by halitech on 2009-11-28
What format are they streaming in? Do you have an example site others can test?

---

### Post by dansar99 on 2009-11-28
The website is WGR 550 Sports Radio. It plays, but it will buffer, usually within 2 or 3 min.  Dan

---

### Post by Old *ix Geek on 2009-11-28
I just listened for 5 minutes with absolutely no problems, buffering or otherwise.

Are you using the most recent version of Adobe Flashplayer? Have you checked its settings? Have you given the stream a large enough allotment of space that it can store information on?

---

### Post by dansar99 on 2009-11-29
Hi, thank you for replying. I have the latest flash but as far as allotting enough space I haven't a clue how to do that.  Dan

---

### Post by dansar99 on 2009-11-29
does this help?

   total       used       free     shared    buffers     cached
Mem:       1026644     383012     643632          0      24320     176472
-/+ buffers/cache:     182220     844424
Swap:      1043240          0    1043240

Dan

---

### Post by dansar99 on 2009-11-29
I just listened on XP for 30 minutes w/o interruption. Switched to Linux and was interrupted 3 times within 2 min. There must be a setting in Linux that I have wrong. Anyone willing to help? Dan

---

### Post by Old *ix Geek on 2009-11-29
> **dansar99 said:**
> Hi, thank you for replying. I have the latest flash but as far as allotting enough space I haven't a clue how to do that.  DanWhen you're listening to it, right click on the player. This should bring up the settings menu for Flashplayer.  There's a slider control you can use to adjust the amount of data you allow the site to store on your computer; adjust that way up and see if it helps.  If that's not it, it still has to be a setting...somewhere!  So post again.

Just out of curiosity, do you have the same problem if you're listening to other, completely unrelated stations?

---

### Post by dansar99 on 2009-11-29
Ok..I did the right click thing and went to settings. Unfortunately the name of that player is not in there unless it has a different name. Dan

I finally found the global storage settings and set it to unlimited. It still buffered within 5 min.  Earlier I listened to the same station on the same computer in Windows XP for 2 hours without any problem.

---

### Post by dansar99 on 2009-11-30
> **Old *ix Geek said:**
> When you're listening to it, right click on the player. This should bring up the settings menu for Flashplayer.  There's a slider control you can use to adjust the amount of data you allow the site to store on your computer; adjust that way up and see if it helps.  If that's not it, it still has to be a setting...somewhere!  So post again.

Just out of curiosity, do you have the same problem if you're listening to other, completely unrelated stations?

I listened to another station for 3 hrs without interruption. I sent a problem report to ENTERCOM. Thank you for your help. I think you pointed me in the right direction even tho the problem is not completely solved. Dan

---

### Post by Old *ix Geek on 2009-11-30
> **dansar99 said:**
> I listened to another station for 3 hrs without interruption. I sent a problem report to ENTERCOM. Thank you for your help. I think you pointed me in the right direction even tho the problem is not completely solved. DanGood! :D

---

### Post by dansar99 on 2009-11-30
This is the reply I got from ENTERCOM :

ur customer support team personnel has replied to your support request 

Thanks for your email,

The Linux OS is not officially supported at the moment. Try uninstalling and 
reinstalling the Flash Media player component from the latest build available 
for your Linux distribution.

Regards,
Streamtheworld Support


We hope this response has sufficiently answered your questions. If not, please 
do not send another email. Instead, reply to this email or login to your account 
for a complete archive of all your support request and responses.

---

