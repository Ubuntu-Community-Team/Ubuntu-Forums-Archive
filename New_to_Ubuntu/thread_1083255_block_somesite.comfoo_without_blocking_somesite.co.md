---
title: "block somesite.com/foo without blocking somesite.com"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by hanzj on 2009-02-28
Hello,

We would like to prevent access on our computer to  somesite.com/foo without blocking access to somesite.com. How can we do this?

---

### Post by chrisod on 2009-03-01
I think this will work...

Open /etc/hosts in a text editor. Add the following line, save and close.

```
127.0.0.1   somesite.com/foo
```

You may need to restart the browser to get it to activate. That should cause your system to look on the local host for somesite.com/foo. Obviously it is not there, so it will throw an error in the browser instead.

---

### Post by Xiong Chiamiov on 2009-03-01
Using 0.0.0.0 will be faster than 127.0.0.1, as it won't wait for it to load.

You might need to restart networking or something to make sure it takes effect.  I'd also add another line that blocks a full site domain so that you can tell whether the hosts file changes haven't taken effect yet, or if it's just the syntax in that line that isn't working.

---

### Post by jerrrys on 2009-03-01
# How should I format the whitelisted (or blacklisted) addresses?
This is a complete url address: [http://procon.mozdev.org](http://procon.mozdev.org)
So, the best and most efficient way is to write it in the whitelist (or in the "Blocked Sites" list) as procon.mozdev.org
That will make sure that even if the site is accessed using a secure protocol (httpS) it will be recognized as a trusted site. However, you should consider that procon.mozdev.org is a sub-domain of mozdev.org and, that if you want to include all other sub-domains of mozdev.org, you would whitelist mozdev.org rather than procon.mozdev.org.

NOTE: mozdev.org will whitelist all pages that come from it, but will not include external domains, as mozdev.COM, mozdev.NET, mozdev.WHATEVER. So if you want to include these other, you should consider whitelisting mozdev. or .mozdev. (whith the dots) as a better alternative. 

[http://procon.mozdev.org/](http://procon.mozdev.org/)

---

### Post by hanzj on 2009-03-02
when I tried
> 0.0.0.0 somesite.com

Browser blocked [http://somesite.com](http://somesite.com)
but it allowed
[www.somesite.com](www.somesite.com)

---

### Post by carml on 2009-03-02
If you want to stop javascript or applet or similar,you can install a plugin for Firefox called Noscript,or another with similar intent.I don't know if these plugins are avaible for others browers.
I hope I nailed the question.):P

---

### Post by hanzj on 2009-03-02
One site I'm trying to block is google reader ([www.google.com/reader](www.google.com/reader)).

I've put into /etc/hosts

> 
0.0.0.0         google.com/reader
0.0.0.0         [www.google.com/reader](www.google.com/reader)
0.0.0.0         [www.google.com/reader/view/](www.google.com/reader/view/)
0.0.0.0         .google.com/reader*

but google reader is still accessible.

---

### Post by chrisod on 2009-03-02
Did you restart networking or reboot the computer? I believe a restart or reboot is required as its read into memory at start up.

---

### Post by hanzj on 2009-03-04
Yes, Chrisod,
I have tried rebooting. Can I ask you to try this out on your ubuntu box, too? Try to block Google Reader ([www.google.com/reader](www.google.com/reader)) while not blocking google.com or any other google service.

---

### Post by unoodles on 2009-03-04
It could be easier to set up dansguardian, then messing with the hosts file.

---

### Post by kanikilu on 2009-03-04
Have you tried clearing the browser cache? The last time I tried to do this, it was on Mac OS X, but I recall needing to clear the cache before it worked. 

Oddly enough, it was also with Google Reader as a little prank on my co-worker who has an unhealthy addiction to RSS feeds :twisted:

---

### Post by hanzj on 2009-03-04
unoodles,
there are just a few things I would like to add to hosts file, so it won't be that difficult.

---

### Post by hanzj on 2009-03-04
[kanikilu]("http://ubuntuforums.org/member.php?u=87527"),
yes, tried clearing browser cache. Can you do it on your hosts file, and when you're able to block Google reader while keeping other google services working, can you post a copy of your hosts file?

---

### Post by kanikilu on 2009-03-04
I'll give it a shot...

// Edit - Hmm...I'm not able to get that working either :-/

---

### Post by chrisod on 2009-03-04
I just tried it - not working for me either. However, I have other entries in my hosts file that are working. Very odd...

Maybe Google has decided it won't be blocked :)

---

### Post by hanzj on 2009-03-04
chrisod,
for those other entries that you have that are working: are they in the form of somesite.com/subfolder?

---

### Post by chrisod on 2009-03-05
No. There are some subdomains such as spa.snap.com but nothing in the convention of foo.com/bar

---

