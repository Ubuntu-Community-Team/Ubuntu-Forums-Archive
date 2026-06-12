---
title: "Internet disconnects when i use Pidgin"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by InRainbows001 on 2008-02-22
really bizarre problem. i'm using a dell dimension 3000, using ubuntu 7.10 and using a belkin 802.11g USB adapter. internet stays connected for as long as i want when using everything else, but when i start using Pidgin instant messenger, it stays connected for about 10 minutes and then drops, and i wont reconnect. i have to restart the computer in order to connect again. does anybody know why this might be happening?

---

### Post by dca on 2008-02-22
If Pidgin is connecting to AIM/AOL, you can try going into 'accounts -> add/edit -> modify -> advanced' and change port from 5190 (I think) to #443...  Also make sure server is set to:  login.messaging.aol.com and my proxy type is set to 'No Proxy' from the default I think is 'Use environment settings'...  I hope this works for you, cuz it's a long shot.

---

### Post by InRainbows001 on 2008-02-22
hi, thanks for the reply, i've only used an msn account with it so far though. does that make any difference?

---

### Post by dca on 2008-02-22
Unfortunately, yes, I think, they use different ports...

---

### Post by InRainbows001 on 2008-02-22
hmm, i've been using kopete messenger instead now for a few hours and it hasn't yet disconnected, how damn strange..

---

### Post by dca on 2008-02-22
That's even more peculiar.  Are you running Ubuntu or (K)ubuntu?
 
Does this bug sound like what you're going through?
[https://bugs.launchpad.net/gaim/+bug/97591](https://bugs.launchpad.net/gaim/+bug/97591)

---

### Post by InRainbows001 on 2008-02-22
that bug sounds similarish, seems as though it's a bug in pidgin.
i'm using ubuntu 7.10, gutsy gibbon, with all the latest updates

---

