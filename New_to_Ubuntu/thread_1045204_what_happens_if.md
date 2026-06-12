---
title: "what happens if"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by chethankrish on 2009-01-20
i have XP and ubuntu installed on my system..

i have installed startup manager in my system..in startup manager under boot options tab i have these options:

Ubuntu 8.10,kernel 2.6.27-9-generic

Ubuntu 8.10,kernel 2.6.27-9-generic(recovery mode).

Ubuntu 8.10,kernel 2.6.27-7-generic

Ubuntu 8.10,kernel 2.6.27-7-generic(recovery mode).

Ubuntu 8.1, memtest86+

Microsoft Windows Xp Professional

Last Used.


can someone tell me, what happens if i choose the third  option 
Ubuntu 8.10,kernel 2.6.27-7-generic  instead of the first option.. please help me with the difference between the two options...

and there is an option called 

use timeout in bootloader menu.. 
what happens if i uncheck that option 

if i choose 0 or 1 sec next to time out in seconds..will i or will i not be able to enter recovery mode next time ,if something serious happens to my system. please help me out with the same... thank you...

---

### Post by chethankrish on 2009-01-20
please somebody help........ please

---

### Post by overdrank on 2009-01-20
> **chethankrish said:**
> please somebody help........ please

Hi and first of all be patient. 7 mins for a response. :)
[COLOR="Red"]Ubuntu 8.10,kernel 2.6.27-9-generic
[/COLOR] Is the newest kernel update
Ubuntu 8.10,kernel 2.6.27-9-generic(recovery mode). is if you have issues with the newer kernel this will allow you to maybe boot and repair your system.

Ubuntu 8.10,kernel 2.6.27-7-generic This is the older kernel and maybe need if your system has issues with the update kernel

Ubuntu 8.10,kernel 2.6.27-7-generic(recovery mode).

If you change the time, you will have to use the esp key to be able to show the grub loading and then choose recovery mode.

[http://web.telia.com/~u88005282/sum/index.html](http://web.telia.com/~u88005282/sum/index.html)

---

### Post by Terl on 2009-01-20
> **chethankrish said:**
> i have XP and ubuntu installed on my system..

i have installed startup manager in my system..in startup manager under boot options tab i have these options:

Ubuntu 8.10,kernel 2.6.27-9-generic

Ubuntu 8.10,kernel 2.6.27-9-generic(recovery mode).

Ubuntu 8.10,kernel 2.6.27-7-generic

Ubuntu 8.10,kernel 2.6.27-7-generic(recovery mode).

Ubuntu 8.1, memtest86+

Microsoft Windows Xp Professional

Last Used.


can someone tell me, what happens if i choose the third  option 
Ubuntu 8.10,kernel 2.6.27-7-generic  instead of the first option.. please help me with the difference between the two options...

The third option is the older version of the kernel.  It is like a failsafe if something went awry with the kernel update (the first entry)  As for booting into, why would you if the current version is just fine.  I edit mine out so they don't display.

> and there is an option called 

use timeout in bootloader menu.. 
what happens if i uncheck that option 

if i choose 0 or 1 sec next to time out in seconds..will i or will i not be able to enter recovery mode next time ,if something serious happens to my system. please help me out with the same... thank you...

I leave mine with a few seconds so I have time to choose.

You need to learn patience.  You barely posted it and less than 10 minutes later you bump the thread. ;)

---

### Post by hyper_ch on 2009-01-20
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by chethankrish on 2009-01-20
sorry for not being patient..was afraid of me loosing my post(thread)..where can i find my threads????

(technical side) what if i uncheck the option "use timeout in bootloader menu"?

---

### Post by Miljet on 2009-01-20
Have a little patience my friend.

You can boot using either kernel. Whenever the kernel is updated with a new one, the old kernel is left in case the new one causes problems with your hardware.

You can set your timer to a small number and still boot into recovery, but you will have to be fast. If you set it to 0, you won't have time to select anything except the default (first option.)

You can find all your posts using the search feature at the top of this screen.

---

### Post by chethankrish on 2009-01-20
thanks for your help... 
i am sorry for not being descriptive... 

sorry for not being patient...

---

### Post by drs305 on 2009-01-20
> **chethankrish said:**
> sorry for not being patient..was afraid of me loosing my post(thread)..where can i find my threads????


At the top of most screens is a Search link. If you click it, options include "Find All Your Threads" and "Find All Your Posts".

---

### Post by snova on 2009-01-20
> **chethankrish said:**
> sorry for not being patient..was afraid of me loosing my post(thread)..where can i find my threads????

Up at the top, is the User CP (Control Panel). If you go into **Edit Options**, a bit furthur down is the "Default Thread Subscription Mode" option. Here you can have ubuntuforums.org send you email notifications of new posts in your threads, or (my preference), select "No email notification".

Then you simply visit the User CP now and again and your subscribed threads (every one you post in, or manually add) will show up here if there are any posts in them.

---

### Post by donkyhotay on 2009-01-20
As mentioned the old one is pretty much for emergencies. I've been exclusively linux for about 3 years now and only ever needed the old kernel versions once, but it completely saved my system that one time (i was attempting to patch my kernel by hand). I recommend keeping it around, it doesn't hurt anything and although the chances of you needing it are less then getting struck by lightning you just never know. (Especially if you get the urge to patch your kernel by hand (c; )

---

