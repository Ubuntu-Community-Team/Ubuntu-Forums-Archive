---
title: "Jaunty 9.04 compiz drivers ATI 2600 Series"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by armoftheland on 2009-10-25
[LIST]
[*]I'm a true noob running Jaunty 9.04 and have been trying to run around and decode all of the threads related to compiz and unavailable drivers for the ATI Radeon 2600 hd series GC for the last two days :).Unable to activate extra desktop effects. I was wondering if there truly were no fixes for this? I know there have been multiple convos on this before but never really saw a final answer.
[/LIST]

---

### Post by armoftheland on 2009-10-26
Wondering if someone can help me: When trying to activate desktop effects a search for drivers comes up and then an error every time. What can I do to fix this?

---

### Post by Redmage913 on 2009-10-26
Would you mind giving a few details of what PC you're running it on? Especially the video card itself.

---

### Post by manoriax on 2009-10-26
There's a "Hardware Drivers"-item within the system's menu. Does it suggest any drivers for your video card?

---

### Post by overdrank on 2009-10-26
Threads merged. :)

---

### Post by armoftheland on 2009-10-26
Thanks for the merge :D
I have a Toshiba Satellite A200 Mr4 with ATI Radeon 2600 hd series GC. I've tried to DL drivers and came up with only one ATI but no dice. Is this unsupported?

---

### Post by humphreybc on 2009-10-26
I also have an Toshiba Satellite HD2600. I can clarify some things.

In Jaunty, there is a bug in the fglrx-installer package that means people with HD2600 cards cannot run anything higher than Catalyst 9.4

In Karmic, this has been fixed, and Catalyst 9.10 should work fine with an HD2600.

So, my advice is to wait for Karmic which comes out on Friday, or, to get in before the rush (advisable) you could upgrade to the Release Candidate by running update-manager -d in terminal. I'm running the RC and it's very stable, more so than the Jaunty final version.

Then, once you're running Karmic, to get the fglrx 9.10 Catalyst drivers, just activate the proprietary driver under System > Administration > Hardware Drivers. This will install the fglrx driver from the repos, which is the latest one, 9.10.

---

### Post by armoftheland on 2009-10-27
thanks so much humphreybc.thats exactly what i wanted to know! i downloaded the new release and lo and behold its all working!

---

