---
title: "Pidgin won't connect to AIM"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by 11010110 on 2009-01-27
Hi everyone, 

I havent used pidgin in a while but when i tried to sign on today it  started fine but when it was connecting it lagged for a while and then eventually said that "username" disconnected could not connect to authentication server: connection timed out. now i have no idea what to do. Anyone have any ideas?

Thanks to everyone in advance

---

### Post by mhh91 on 2009-01-27
maybe it's something with your connection

a weak connection to the internet causes this sometimes,or maybe the server is busy,or even unavailable

---

### Post by 11010110 on 2009-01-27
I dont think that i could be the connection, I am at about 80-100% connection and its on a high speed connection. I couldnt imagine the entire AIM server going down... Any other ideas?

---

### Post by mhh91 on 2009-01-27
try kopete for a change?

---

### Post by talsemgeest on 2009-01-27
Does it happen every time, and are you having problems with any other net-aware programs?

---

### Post by 11010110 on 2009-01-27
I tried kopete and thats not working either. same thing... it just says connecting... indefinately and then after a few minutes says "username" disconnected unknown error. Everything else that uses the internet works just fine. Its just AIM related things.

---

### Post by LowSky on 2009-01-27
you say your on a wireless connection, does the same thing happen if your connected by wire?

Also are you running any other applications while trying to start AIM?

---

### Post by 11010110 on 2009-01-27
This is really strange... It works just fine under a wired connection but when wireless it does not... Even though I have full strength connection on a high speed cable line. Would there be some way to remedy this? I normally dont sit anywhere near an ethernet cord lol. 

Thanks for your help so far!

normally Im running firefox or maybe songbird too. It all depends but I just verified that it doesnt matter what other programs are running at the time it still doesnt wanna play nice with my wireless...

---

### Post by talsemgeest on 2009-01-27
Since the problem is with the wireless networking and not the program, try setting up your connection using [wicd](http://wicd.sourceforge.net/). I have not tried it, but I hear that it is a superior replacement for the ubuntu network manager.

---

### Post by Muffinabus on 2009-01-27
> **11010110 said:**
> I dont think that i could be the connection, I am at about 80-100% connection and its on a high speed connection. I couldnt imagine the entire AIM server going down... Any other ideas?

I do remember a time a few years ago where the entire AIM servers did go down (:  Not ENTIRELY implausible!

---

### Post by XanTrax on 2009-01-27
You could be denying all ports and only allowing web traffic through port 80.  AIM uses 5190.  I have seen wireless blocking connections to all ports except 80 before.  Wired, everything was unblocked.

---

### Post by 11010110 on 2009-01-27
I figured out the problem. Sorry it took me so long to get back but the university was having issues with its system... the domain server went down and everythigns been screwed up lately. I got it fixed for me at least and everyhting works swimmingly. Thanks for all of your help everyone!


P.S. I would love to mark it solved but for some reason mark as solved isnt under the thread tools anymore... strange

---

### Post by XanTrax on 2009-01-27
> **11010110 said:**
> 
P.S. I would love to mark it solved but for some reason mark as solved isnt under the thread tools anymore... strange

Ya, and I cant seem to find thanks anymore either :( lol

---

### Post by talsemgeest on 2009-01-27
> **11010110 said:**
> P.S. I would love to mark it solved but for some reason mark as solved isnt under the thread tools anymore... strange

> **XanTrax said:**
> Ya, and I cant seem to find thanks anymore either :( lol

Yes, both the thanks and [solved] plugins have been temporarily disabled, until the forums are stable again.

---

### Post by XanTrax on 2009-01-27
> **talsemgeest said:**
> Yes, both the thanks and [solved] plugins have been temporarily disabled, until the forums are stable again.

Didnt realize they were unstable :neutral:

---

### Post by talsemgeest on 2009-01-28
> **XanTrax said:**
> Didnt realize they were unstable :neutral:
Take a look [here](http://ubuntuforums.org/showthread.php?t=1039481) for more info.

---

### Post by XanTrax on 2009-01-28
> **talsemgeest said:**
> Take a look [here](http://ubuntuforums.org/showthread.php?t=1039481) for more info.

Thanks.  I just recently started hanging around so I missed that :p

---

### Post by talsemgeest on 2009-01-28
> **XanTrax said:**
> Thanks.  I just recently started hanging around so I missed that :p
No problem. :D

---

