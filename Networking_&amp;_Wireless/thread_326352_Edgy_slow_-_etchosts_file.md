---
title: "Edgy slow - /etc/hosts file?"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by 2CV67 on 2006-12-27
Greetings Network & Wireless!

I have a problem thread in the beginner's forum ([http://www.ubuntuforums.org/showthread.php?t=323151](http://www.ubuntuforums.org/showthread.php?t=323151)) with no solution, but in searching other threads I think the solution MAY be in /etc/hosts file & I would like your expert advice please!

My problem:
I notice very slow performance, typically opening new applications, whenever the wifi or ethernet connection is OK (even when no internet applications are running) but much quicker behaviour when the connection is no good, either by physically disconnecting the cable or by disabling 'Connection' in Network Settings.

Examples of slow performance. (Quick performance with connection disconnected - in brackets)
Login to clean desk - 60sec (11sec)
Open 'System Monitor' - 12sec (1sec)
Open 'Terminal' - 12sec (1sec)
Open OOotext - 23sec (12sec)

I noticed several other threads with same or similar symptoms & mention of changing the contents of /etc/hosts file to fix the problem:
[http://www.ubuntuforums.org/showthread.php?t=317242](http://www.ubuntuforums.org/showthread.php?t=317242)
[http://www.ubuntuforums.org/showthread.php?t=296625&highlight=%2Fetc%2Fhosts](http://www.ubuntuforums.org/showthread.php?t=296625&highlight=%2Fetc%2Fhosts)
[http://www.ubuntuforums.org/showthread.php?t=311276&highlight=%2Fetc%2Fhosts](http://www.ubuntuforums.org/showthread.php?t=311276&highlight=%2Fetc%2Fhosts)
[http://www.ubuntuforums.org/showthread.php?t=309931&highlight=%2Fetc%2Fhosts](http://www.ubuntuforums.org/showthread.php?t=309931&highlight=%2Fetc%2Fhosts)
[http://www.ubuntuforums.org/showthread.php?t=309544&highlight=%2Fetc%2Fhosts](http://www.ubuntuforums.org/showthread.php?t=309544&highlight=%2Fetc%2Fhosts)
etc etc

But none of the instructions/explanations are quite simple enough for a noobie like me...

Could somebody please explain what SHOULD be in /etc/hosts and what SHOULD NOT be in there - in nice simple terms please! please!

My current /etc/hosts looks like this
127.0.0.1 localhost
127.0.1.1 DESKTOP..NEUGARTHEIM
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

What should it look like?

Thanks a lot guys! :)

---

### Post by dbott67 on 2006-12-27
It may be related to IPV6.  Take a look at this thread (post #3):

[http://www.ubuntuforums.org/showthread.php?t=323747](http://www.ubuntuforums.org/showthread.php?t=323747)

-Dave

---

### Post by 2CV67 on 2006-12-27
Thanks dbott67 - I forgot to subscribr to this thread (!!) so did not see your reply immediately...
In the meantime, blindly, I tried re-arranging /etc/hosts (actually working through Networking Settings GUI).
The final result is excellent - "with connection" now as fast as "without connection" - but I was surprised at when it occured.
For information (& I would be interested to understand...) these are the stages I went through:
:::::::::::::::::::::::::::::::::::
ORIGINAL[I]
127.0.0.1 localhost
127.0.1.1 DESKTOP..NEUGARTHEIM

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/I]
:::::::::::::::::::::::::::::::::::::::
FIRST ATTEMPT (NO EFFECT)[I]
127.0.0.1 localhost DESKTOP..domain.com

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/I]

NOTE: I didn't put the "domain.com" there - Ubuntu did it..

::::::::::::::::::::::::::::::::::::::
SECOND ATTEMPT (NO EFFECT)[I]
127.0.0.1 localhost DESKTOP..domain.com

# The following lines are desirable for IPv6 capable hosts[/I]
:::::::::::::::::::::::::::::::::::
SUCCESSFUL VERSION[I]
127.0.0.1 localhost DESKTOP.

# The following lines are desirable for IPv6 capable hosts[/I]
::::::::::::::::::::::::::::::::::::
I did not try putting any of the prior items back, to see what effect that might have.
Does this make any sense?

Is there any risk with that set-up?

I'm happy anyway.

---

### Post by 2CV67 on 2006-12-27
Well - out of interest I did go back & put all the ip6 stuff back in - and it was still OK!

I then put the* 127.0.1.1 DESKTOP..NEUGARTHEIM* line back - and still OK!!

Finally, I put back the original first line *127.0.0.1 localhost *- and SLOW again.

I tried switching that line a couple of times & it follows 100%.

Conclusion:

From an original /etc/hosts file of[I]
127.0.0.1 localhost
127.0.1.1 DESKTOP..NEUGARTHEIM

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/I]
all I needed to change was to add the actual hostname (DESKTOP.) to the first line:
[I]
127.0.0.1 localhost DESKTOP.[/I]

Does this make any sense?

What went wrong to get me into the SLOW state??

Happy anyway :D

---

### Post by dbott67 on 2006-12-27
I don't know why it's happening.  My hosts file is as follows:
```
dbott@thedrake:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       thedrake

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I'm running Dapper 6.06 (although I ran Edgy for a while and didn't have any issues with this particular problem).

Good work solving your problem, though.

-Dave

---

