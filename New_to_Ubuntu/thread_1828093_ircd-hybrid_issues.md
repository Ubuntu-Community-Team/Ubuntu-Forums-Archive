---
title: "ircd-hybrid issues"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by J-C.V on 2011-08-18
I am very unfamiliar with compiling programs so I am going to post this in beginner. 

I was able to use and connect to ircd-hybrid when I install it via apt-get. I wanted to be able to use ssl with it and after some reading found I had to download and compile it in order to get that support.

I followed the instructions in this post: [http://ubuntuforums.org/showpost.php?p=10624593&postcount=3](http://ubuntuforums.org/showpost.php?p=10624593&postcount=3)

After it was done I renamed the example.conf and removed the line in it to make sure I had read it. When I start the program I get 

ircd: version hybrid-7.3.0 
ircd: pid 13902 
ircd: running in background mode from /usr/local/ircd"

but a  ps -e | grep irc returns nothing running.

I noticed that it was reporting that it could not find openssl when doing ./configure even though I specified the path. Same error as in this thread: [http://ubuntuforums.org/showthread.php?t=1706006&highlight=IRCD-Hybrid+OpenSSL](http://ubuntuforums.org/showthread.php?t=1706006&highlight=IRCD-Hybrid+OpenSSL) I then tried to make it again without that but I have the same issues as before when trying to start it.

I know I have to be missing something, any help would be appreciated.

---

