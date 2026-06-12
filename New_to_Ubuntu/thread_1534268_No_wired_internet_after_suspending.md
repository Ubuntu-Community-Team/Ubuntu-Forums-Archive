---
title: "No wired internet after suspending"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by sb5551 on 2010-07-19
Hey everybody,

  I haven't had a problem with my ubuntu installation in a while and I must say I love it. I do seem to have one problem that I was playing with to see if I could fix. 

After, closing the lid of my laptop of letting it go into hibernation the wired internet always says disconnected and won't reconnect. The wireless picks up where the wired stopped though. I have searched a few things, but couldn't find any definitive fixes. 

After this happened one time, I typed: > sudo ifconfig eth0 down
which then got rid of the wired network when typing > ifconfig
I then typed > sudo ifconfig eth0 up
but came up with the error that not enough memory can be allocated. After this I became extremely confused and don't know where to go from here.

Any ideas, would be greatly appreciated. I am unfortunately at work so can not do anything until I get home to my computer.

---

### Post by sb5551 on 2010-07-20
Well, I am guessing this is why my search didn't yield any help.

---

### Post by anewguy on 2010-07-20
Well, let's try to start at getting it to come up manually.  Since you say it says not enough memory, please post back the specs on your system - cpu/memory/disk space/swap space.

Also, I didn't think you could have a hard wired connection and a wireless connection going through the same router to the internet - this may just be me missing something - but I have never gotten that to work.  So, what I'm wondering is if on the wake up from suspending if your wireless is waking up and making the connection first.  So, try disabling wireless in network manager, then let the PC go into suspension, then wake it and see if the wired connection is there.

Dave ;)

---

### Post by sb5551 on 2010-07-20
Hey Dave
  
The specs on my system are AMD dual core 2.2 ghz give or take, 4 gb ram, 320 gb hd but ubuntu only has 20 gb with about 14 free. The swap space was what ubuntu recommended when installing which was about 700 kb but I have never used it yet. 

I am not sure how I set up the wireless and ethernet together. I just connect to my wireless network and whenever I am near the router I plug right into it. I will try actually disabling the wireless card like you stated when I get home. 

I believe it is just set up so the ethernet has priority. I know in my windows 7 drive I have to disable the wireless connection if I want to use the ethernet because for some reason the wireless connection has priority.

---

### Post by dineshs on 2010-07-20
Have you tried this?
[http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217)
Post #3 maybe helpful(You may have to add [COLOR="Blue"]sudo[/COLOR] before each command)

---

