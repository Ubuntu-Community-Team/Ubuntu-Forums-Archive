---
title: "A web browser that does not use the home directory"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by DrCoolSanta on 2008-04-13
The title is a bit confusing but what I wanted to say is that I want a web browser that does not touch the home directory of any user, eg: firefox uses the home directory to save it's log files . . .

In our network, a machine has specific /home, /opt and /usr/local directory, shared over the whole network, they have a common home directory. Now in this scenario, if one machine has firefox open, the other machines complain that firefox is already open and not responding. I changed to epiphany, but a different problem arises, epiphany seems to save the web site you are at somewhere in the home directory or the other two shared one. Now it would tell me whether I want to open the last session that was being worked with if I start it simultaneously on two machines. When I was thinking this isn't a big problem, but it might cause some problems while logging in somewhere. And even if that does not happen it doesn't look so neat...

If you have something to fix the problem or a recommendation for a browser, just tell me.

---

### Post by chewearn on 2008-04-13
You can create multiple Firefox profiles, one profile per machine.

In gutsy, this will run the profile manager, which allows you to manage the profiles:
```
firefox -ProfileManager -no-remote
```

To start firefox with a particular profile:
```
firefox -P <profile> -no-remote
```

Replace <profile> with a name.
The -no-remote option might not be needed.

---

### Post by DrCoolSanta on 2008-04-15
thanks, I'll just check if this works ^_^.

---

