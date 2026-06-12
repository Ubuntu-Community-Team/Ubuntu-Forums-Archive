---
title: "How Do I: Remotely connect to my Ubuntu server via SSH gateway?"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by jqs on 2008-11-14
Hello everyone, I've got a pickle that I thought would be an easy thing to figure out, but not so much (at least for me)...

I'm trying to access (X via SSH) an ubuntu server I've setup at home from my office. The kicker is that I've an intermediary machine that runs SSHd that I have to go through.
I *could* change my network topology and make the Ubuntu box the SSH gateway but I'd like to see what my options are first.
I ran a few searches but could only come up with turotrials for forwarding X over SSH provided you are SSHing into the machine you want to forward X from...
Does anyone have a solution for me?

Thanks in advance!

---

### Post by nixscripter on 2008-11-14
As an alternative suggestion, what about having the intermediate machine forward a port to ssh on the other machine? In other words, have the intermediate machine run:

```
ssh -NL 1234:destination:22 you@destination
```

And then you get to the other machine with: ```
ssh -p 1234 you@intermediate
```

I'm assuming, however, you're not paranoid about security (letting that internal machine have anyone connect to it).

---

### Post by jqs on 2008-11-14
> **nixscripter said:**
> As an alternative suggestion, what about having the intermediate machine forward a port to ssh on the other machine? In other words, have the intermediate machine run:

```
ssh -NL 1234:destination:22 you@destination
```

And then you get to the other machine with: ```
ssh -p 1234 you@intermediate
```

I'm assuming, however, you're not paranoid about security (letting that internal machine have anyone connect to it).

I kinda did what you suggested.

```
ssh -NL 2200:destination_on_remote_lan:22 me@remote_lan_gw
```

Then I can forward my X as appropriate liek so:

```
ssh -p 2200 -X me@127.0.0.1 pidgin
```

It works, but it is incredibly slow (most likely due to my remote network being a crap connection)...

Thanks for the help with the proof of concept!

---

### Post by nixscripter on 2008-11-15
I find X is slow even over a 1 Mbps LAN.

I'm glad I could help. Please mark this thread as solved (under thread tools).

---

