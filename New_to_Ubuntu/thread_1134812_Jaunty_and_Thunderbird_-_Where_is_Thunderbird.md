---
title: "Jaunty and Thunderbird - Where is Thunderbird?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by crjackson on 2009-04-24
Okay, so I can't find Thunderbird in the repos now. What happened?

---

### Post by kanikilu on 2009-04-24
It's definitely there...are you sure you're able to connect to the repositories? I imagine there are probably still taking a beating from the release...perhaps try a different mirror?

```
sudo apt-get install thunderbird
```

Should work...but there's also the transition package mozilla-thunderbird.

---

### Post by jowilkin on 2009-04-24
The repos are crawling for me right now.  That's probably your issue.

---

### Post by crjackson on 2009-04-24
> **kanikilu said:**
> It's definitely there...are you sure you're able to connect to the repositories? I imagine there are probably still taking a beating from the release...perhaps try a different mirror?

```
sudo apt-get install thunderbird
```

Should work...but there's also the transition package mozilla-thunderbird.

Must be a repository thing... I can't get or find Java either..

```
charles@charles-neo4:~$ sudo apt-get install thunderbird
[sudo] password for charles: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package thunderbird has no installation candidate
charles@charles-neo4:~$ 

```

---

### Post by crjackson on 2009-04-24
Yeah, that was it. I tried a few servers and found one that gave it to me...

---

### Post by drs305 on 2009-04-24
Nevermind.

---

