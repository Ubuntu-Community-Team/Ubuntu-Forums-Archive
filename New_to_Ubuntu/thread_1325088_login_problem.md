---
title: "login problem"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by h20boynz on 2009-11-13
Howdy all...
Just installed ubuntu 9.10 for the first time...total novice but it seemed to work well and up until this very moment I was happy.
Now I was playing around last night...got access to my router and internet. Shut it down thinking all is well in the world.
So I tried starting it up tonight...enter encrption passphrase: works ok and comes to the host login.
i.e myhostname login:
I enter the username that has been working up until now no problems.
then password:
After hitting enter it just sits there and eventually get the 60sec timeout.
if I enter in an incorrect user name i get an error but regardless of what password i enter it times out.


This was all working perfectly when I turned it off last night! ???

I know what you will say...you forgot your password...but i assure you with 100% confidence that I have not.

Any ideas what on earth I have done???

Thanks

---

### Post by stoogiebuncho on 2009-11-14
Even if you didn't forget your password, you could try following this guide to reset it and see if that works:

[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by kelvin.illa on 2009-11-14
I don't exactly know if this is your problem, but mine gets timed out when the wireless security setting is wrong (WEP (2 kinds), WPA (2 kinds)) or the wifi signal's low.

---

### Post by KIAaze on 2009-11-15
Can you login on a virtual terminal?
Press ctrl+alt+f1 to get to one and try logging in there with your username and password.

I know that being low on disk space (for / or /tmp) can throw you out of a session, but I think it gives you an error message in this case.
You can check the available diskspace with:
```
df -h
```

---

### Post by h20boynz on 2009-11-19
Thanks for the advice folks...

In the end i just reinstalled the whole OS...its a bit of work but I'm a real noob so i can use the practice :)  Though i dont wont to do it everytime i mess something up :)

---

### Post by Megamind on 2010-12-10
> **stoogiebuncho said:**
> Even if you didn't forget your password, you could try following this guide to reset it and see if that works:

[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

old thread...but i had installed Ubuntu 10.10 on my work laptop with Win and had username (forgot pw).

This worked like a charm. Many thanks!

---

