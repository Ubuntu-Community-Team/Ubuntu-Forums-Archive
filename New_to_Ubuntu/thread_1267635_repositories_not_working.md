---
title: "repositories not working"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by rgroene on 2009-09-16
Okay, this is really weird. I can't seem to access the Ubuntu repositories anymore. I think it started when I reinstalled Ubuntu and since I've come to college. The Internet connection is working fine, and I am able to download from other websites easily. But when I try to download certain packages it will go super slow (usually about 1200 bytes per second or slower--usually it just says "unknown"), making it virtually impossible to download anything. I have tried this on two different installations of Ubuntu (one on my main hard drive and one on my external enclosure), and both had the same problem. Also, I tried selecting several alternate repositories (mirrors) in Synaptic, but all of them had the same problem. In fact, when I did this, the information for the repository wouldn't even load so that all it shows in Synaptic are packages that I currently have installed.

Does anybody know what the problem might be?

---

### Post by scrooge_74 on 2009-09-16
How about installing from command line? 

Still weird problem,  I just updated a machine no speed problems

---

### Post by AlexenderReez on 2009-09-16
perhaps it is cause by your college internet restriction ..it is painful...but you need to bear on it...please update by using command line...error log is source of solution for each problem.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Geoff918 on 2009-09-16
I would imagine that your college's firewall may be restricting access to the domain.

What you may wish to try is to go into the terminal and ping some of the servers. It's certainly not the repositories, I've been using them and they're as fast as ever.

Also, your DNS servers may really stink. Do any other web sites or ftp sites take a while before it gets a response?

If any of that is the case, you could always add the actual IP of a repository to your hosts file. Alternately, you could try a different DNS server--there are tons out there.

I personally use Comodo Secure DNS servers because they're fast as heck. Others don't necessarily trust that they're not being "monitored" by the security group. Some others would be 4.2.2.2 (I believe this is an ISPs DNS), just Google for one or multiples. This may clear up your problem.

Let me know if you need any help from here.

---

### Post by QIII on 2009-09-16
If it's a laptop, does it have a wifi card?

If it doesn't can you borrow one (or a dongle) from a friend?

Do you have a coffee shop with complimentary wifi within a couple of blocks?

Do you like coffee?

---

### Post by rgroene on 2009-09-16
I've tried installing from the command line using sudo apt-get install [program], and that is just as slow. I do have a wifi card, but that is irrelevant because most of my testing so far has been through an Ethernet connection (can't remember if I tried it over wifi yet; there's no wifi in the dorm rooms and in the lobby I usually only get 1 bar, being on the 4th floor). The even stranger thing is that there are some things that download alright from the repositories. I had this problem a little bit last year at my college, but it didn't seem to be as bad then.

---

### Post by QIII on 2009-09-16
"Some things" may actually translate into "some times", depending on the bandwidth available and the amount of traffic at the time you are trying to download "some things" -- say when you are in your dorm when everyone else is, too.

If you are getting a weak signal in the lobby, try finding out where the source is and move closer.

Or go to a wifi coffee shop near campus.

I really think your issue is bandwidth and the variable nature of the traffic that is using it.

That would be at least worth a try.

---

### Post by rgroene on 2009-09-18
I don't think that's really the problem because there are certain packages that I have tried at many different times, including late at night when most things are downloading at 2-3 MB per second.

---

