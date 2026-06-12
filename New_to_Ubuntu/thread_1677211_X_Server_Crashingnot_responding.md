---
title: "X Server Crashing/not responding"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by Nickjpost on 2011-01-28
I just upgraded to 10.10 and unable to use the system GUI unless in safemode. *Sometimes, *and it is a rare occasion, I'm able to log in to the normal desktop environment but then after a bit, it freezes and is totally unresponsive. I'm able to switch to text via ctrl+alt+(F1, F5, F6) and use a different runlevel to reboot. I've tried restarting the x server as well as stopping then starting but no go. I'm using a Toshiba Satellite L25-S1217, intel celeron 1.6 ghz, 874 mb ram with a radeon video card. 
Please, I've been exhaustively trying to get this working....any help would be GREATLY appreciated. Please let me know if more info is needed.

---

### Post by mharrison on 2011-01-28
Have you tried running 
```
sudo apt-get update && sudo apt-get upgrade
```

to see if there are any additional updates that may resolve your issue?

---

### Post by Nickjpost on 2011-01-28
> **mharrison said:**
> Have you tried running 
```
sudo apt-get update && sudo apt-get upgrade
```
 
to see if there are any additional updates that may resolve your issue?
Thank you for replying, I truely am grateful!!
 
I tried that, but no go. I noticed in textual mode when I ran gdm, I get an error, 'Unable to load file /etc/gdm/custom.conf'. Upon further investigation, that file doesn't even exist on my file system. Should it? To my understanding, that file is necessary for normal GUI to work, correct? Can I manually rebuild it? I can't find an example file anywhere as reference.

---

### Post by mharrison on 2011-01-28
Looks like it might be a bug.

Check out 
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/500377](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/500377)

There is a workaround on how to get the file recreated...Hopefully this will help with your issue.

---

### Post by Nickjpost on 2011-01-28
> **mharrison said:**
> Looks like it might be a bug.
 
Check out 
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/500377](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/500377)
 
There is a workaround on how to get the file recreated...Hopefully this will help with your issue.
 I tried that too, but it won't let me change anything in the gdmsetup in safe mode, the only way I can access the GUI. I even tried to copy gdm.conf from /etc/init to /etc/gdm...fail
Then I tried to copy from /etc/dbus-1/system.d/gdm.conf, which when I viewed the contents looked a little like html code, tried it anyways and...................fail. *sigh*:confused:
 
Honestly, I think it could be a bug too. I really want to keep my desktop @ 10.10 and not give up on this, but I'm growing weary. Your diligence is heartening though, and thank you again.

---

### Post by mharrison on 2011-01-28
Perhaps you could try running the commands specified in the bug report in Recover mode?

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by Nickjpost on 2011-01-28
I cant change anything there, but it gav me an idea....I'm going to reinstall and set upmy username to autologin as that is what that bug report states to set and see if that makes a difference. i really don't have anything to loose since I have my files I need waiting for a successful install of 10.10 or reinstall of 10.04. I'll post my results in this thread when I'm done. Thanks mharrison

---

### Post by mharrison on 2011-01-28
> **Nickjpost said:**
> I cant change anything there, but it gav me an idea....I'm going to reinstall and set upmy username to autologin as that is what that bug report states to set and see if that makes a difference. i really don't have anything to loose since I have my files I need waiting for a successful install of 10.10 or reinstall of 10.04. I'll post my results in this thread when I'm done. Thanks mharrison

Good luck.  Sorry none of the above helped.  Sometimes you just have to give up, back up (or not, :P) and reinstall.

---

### Post by Nickjpost on 2011-01-29
> **mharrison said:**
> Good luck. Sorry none of the above helped. Sometimes you just have to give up, back up (or not, :P) and reinstall.
 Ok, so I reinstalled 10.10 and selected auto login but that didn't work either, so I reinstalled once more and still having the same issue. I have no clue why it's doing this but "GRRRRRRR!"
I'm not givinng up on this though, I think there is a solution somewhere and I'm determined to find it. When and if I do, I'll post the solution in a new thread so others don't have to suffer like I am now. I don't know why I can't just let this go and reinstall 10.04, but I simply can't. You were kind to give me your wisdom and I thank you

---

### Post by Nickjpost on 2011-01-29
Ok! I have a solution! Turns out is was the drivers (or the lack thereof) for my ATI video card.
Here is where to find them and configure them via open source drivers or proprietary drivers!
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
 
Two days of work well worth it and I couldn't have done it without some help....Thanks once more mharrison!

---

