---
title: "Repository problem"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by navaneethan on 2009-09-05
I have the problem in my ubuntu hardy repository,so that i can't able to install any package in my hardy

just i need to reload my repository only like newer one

then i want to install the required packages in my hardy

Is any way?

---

### Post by natman on 2009-09-05
Have you tried running the following in a terminal?
> sudo aptitude update
sudo aptitude upgrade
This should just get you the latest safe updates, if it doesnt work perhaps post back whatever ever error message you receive.

---

### Post by s04bf1c2 on 2009-09-05
Edit: Solved

Hi,

Sorry not much help here... possibly encountering the same problem. Recently installed Hardy on a server, tried to run an update/upgrade but am getting:

```
Failed to fetch ....  Could not resolve '****.ubuntu.com'
```

Anyone encountering this of late? I've tried both my local mirror repository and the generic ubuntu.com ones...

Thanks.

---

### Post by k33bz on 2009-09-05
is your server by any chance connected to the internet, try pinging something
```
ping -c 4 www.google.com
```

---

### Post by NoaHall on 2009-09-05
Can you paste "/etc/apt/sources.list" here?

---

### Post by s04bf1c2 on 2009-09-05
Wow... it's the most obvious things! Sorry for wasting everyones time.

Piece of advice, don't use yellow ethernet cables in the playroom... children love them ;) 

Best to pop out and buy a non-attractive gray one :D

Btw thanks for the extremely prompt replies.

---

### Post by navaneethan on 2009-09-09
> **s04bf1c2 said:**
> Wow... it's the most obvious things! Sorry for wasting everyones time.

Piece of advice, don't use yellow ethernet cables in the playroom... children love them ;) 

Best to pop out and buy a non-attractive gray one :D

Btw thanks for the extremely prompt replies.



I had done successfully ...thanks for your answer

now in my friend's lap (jaunty) i can't able to install package 

i have done the above commands in his lap, it doen't work

and eventually i replaced the sourecs.list1(back up file) to the sources.list
again doesn't update

fetching failed .....

what is the solution??

---

### Post by zipperback on 2009-09-09
Can you surf the web from the computer in question?

- zipperback
:popcorn:

---

