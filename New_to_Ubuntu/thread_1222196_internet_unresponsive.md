---
title: "internet unresponsive"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by freeediver on 2009-07-24
I dont know if this belongs  to ubuntu, firefox, or my ISP.
I am loosing my ability to switch between internet sites or
click links in sites, they do not load. Watching my status bar
it never goes to 100% when I am having this problem.
Yesterday I needed to stop and refresh 3-4 times to get here.
Getting to my Hotmail account was just as bad.
Using my favorites now is almost impossible, sometimes they 
work, sometimes not. Stop, refresh,stop, refresh is getting to be
a regular dance.
Does anyone know what is happening?
I checked LaunchPad and I am not the only one with this "new issue".
I am using Hardy my wife is using Vista and also having the same issue, this problem started about 1 week ago.

---

### Post by cgb on 2009-07-24
If the vista box is having issues then it is either a problem with your ISP or your switch/router.  Not sure if you have any local shares going between the computers but if so make sure to test if you are ever having problems connecting locally between computers when these problems occur.  If your local connections are all fine then it is not a problem with your lan (switch/router) but a problem with your ISP/modem.  I would possibly give your ISP a call and have them test your connection and see if they discover any problems.

---

### Post by Durden on 2009-07-24
Type "about:config" in your url bar in Firefox. Search for "ipv6" It should say something like "network.dns.disableIPv6" set it to "true"

See if that solves it.

---

### Post by LewRockwell on 2009-07-24
seems like Firefox might be the common denominator here...hmmm...

.

---

### Post by freeediver on 2009-07-25
Thanks for the idea, I checked and made the change to True, I'm not sure it helped.
My status connect bar still does not reach 100% my web page connection never completes. In order to check this forum I was forced to stop my previous connection/process then re-select Ubuntu forums again in order to make the connection. It has taken
a couple minutes after I arrived here and the connection just reached 100% ( 2-3 min ).

I'm sure now, it did not help. It was a great thought, O well.

---

### Post by mgmiller on 2009-07-25
If you are on a cable modem, have you tried restarting it by pulling its power plug for a few seconds and letting it restart?  Also, try restarting your router the same way.

---

### Post by freeediver on 2009-07-25
Just did that and spoke with AT&T, they said the issue was not in my house. I now have a repair/tech ticket and waiting on another
call. At least it now sounds like it's not me.

---

### Post by Papa-san on 2009-07-25
Do you think you could do a traceroute to yahoo? Make sure all of your browsers are closed when you do it:
System>Administration>Network Tools
The fourth tab is traceroute. Put [www.yahoo.com](www.yahoo.com) in the address box and trace it. I'm interested in how many milliseconds it takes for each 'Hop' Number 1 is within your own system. #2 is within your router, and #3 is the first one to your ISP. You really don't need to run it for too many more hops, so stop it at 4 or 5. If you can post a screenshot it would be nice... 

That will at least let us know where the bottleneck is...

---

