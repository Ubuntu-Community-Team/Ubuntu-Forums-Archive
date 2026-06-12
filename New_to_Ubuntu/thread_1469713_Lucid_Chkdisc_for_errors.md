---
title: "Lucid Chkdisc for errors"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by jnmjr on 2010-05-02
Hey all, since I upgraded to Lucid all has been great but this morning when I turned on the computer got this before the OS started....Ubuntu checking disk for errors....it took a good 1/2 hr for this "check" to complete then it finished booting fine, is this something new with Lucid? Is it built into the Os to check disc periodically? If so can it be turned off? and finally is there a log I can look up to see the results of this "check"?.....THX :)

---

### Post by mikewhatever on 2010-05-02
> **jnmjr said:**
> ...is this something new with Lucid?> 
No. The feature has been in Ubuntu for quite some time.

[quote]Is it built into the Os to check disc periodically?
As said, it's a feature. It's not built in.

[quote]If so can it be turned off?
Yes, but do you understand the consequences?

> and finally is there a log I can look up to see the results of this "check"?.....THX :)
/var/log/fsck
Don't try looking for Chkdisc or whatever it is.

---

### Post by madjr on 2010-05-02
30 mins?

thats probably one time

it's pretty later on and not very often

i say dont turn it off

---

### Post by jnmjr on 2010-05-02
> **mikewhatever said:**
> [QUOTE=jnmjr;9218253]...is this something new with Lucid?[quote]
No. The feature has been in Ubuntu for quite some time.


As said, it's a feature. It's not built in.


Yes, but do you unserstand the consequenses?


/var/log/fsck
Don't try looking for Chkdisc or whatever it is.

I appreciate your response, please do not answer a question with a question, obviously I'm not as knowledgeable as you are otherwise I wouldn't be asking, try being less patronizing in the future it would reflect better on yourself.

---

### Post by jnmjr on 2010-05-02
> **madjr said:**
> 30 mins?

thats probably one time

it's pretty later on and not very often

i say dont turn it off

OK, so you've experienced this before and obviously by your post it took allot less time, I've used Karmic since Dec.09, and never saw it, only when Upgraded to Lucid and that after using it for 2 days, checked logs as per previous poster and nothing there maybe due to not finding any errors, could you explain why this may be such an important feature that it should not be turned off?....THX

---

### Post by mc4man on 2010-05-02
> it took a good 1/2 hr for this "check" to complete then it finished booting fine, is this something new with Lucid?
Yes, this is a new 'feature' with lucid (and quite improper

Saw the same here just before the release, resolved locally by removing quiet and splash from grub
(with nvidia-current the splash only lasts 2-3 sec's, don't need.

You can also press the esc button after the fsck reaches 70+% and slows to a crawl

Went to file a bug and found this already filed

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571707](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571707)

---

### Post by jnmjr on 2010-05-02
> **mc4man said:**
> Yes, this is a new 'feature' with lucid (and quite improper

Saw the same here just before the release, resolved locally by removing quiet and splash from grub
(with nvidia-current the splash only lasts 2-3 sec's, don't need.

You can also press the esc button after the fsck reaches 70+% and slows to a crawl

Went to file a bug and found this already filed

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571707](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571707)

Thank you very much, your post is most illuminating, unlike the other poster you were precise and to the point rather than being patronizing and obscure, I will try the workaround for now until this bug is resolved, thanks again :guitar:

---

### Post by QwUo173Hy on 2010-05-03
> **mc4man said:**
> 
Went to file a bug and found this already filed

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571707](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571707)
Thanks, I 'me too'ed it. Karmic used to fly through the disk check and I'm glad to see the bug is confirmed and effecting enough people to warrant some attention.

---

### Post by mc4man on 2010-05-09
There is a fix for this now in the proposed repo - mountall 2.15
> [ Steve Langasek ]
  * Only send plymouth a progress update when there's actual progress to
    report; otherwise we flood plymouthd with redundant events, and the
    progress will spin for minutes after the fsck itself is finished.  Thanks
    to Tero Mononen and Anders Kaseorg for the patch.  LP: #571707.


I would suspect it will make it to the main repo shortly - if wanting to update from proposed would suggest not allowing all the proposed updates to install - just pick the mountall one.

---

### Post by QwUo173Hy on 2010-05-09
> **mc4man said:**
> There is a fix for this now in the proposed repo - mountall 2.15

I would suspect it will make it to the main repo shortly - if wanting to update from proposed would suggest not allowing all the proposed updates to install - just pick the mountall one. Thanks mc4man. I think I'll wait for it to come through to the main repo, but it's a relief to know it's on the way. By the way, that's a good suggestion on the proposed updates. Keep things simple :)

---

### Post by StefQube on 2010-09-07
**Too slow or too fast !!??**
That same boot up screen lasts ~**0.2 seconds** -- once it was max. 0.5 s -- on my PC. so I could not clearly tell what it was. I am experimenting new settings now, so I expect bad things at every boot. 

I have 10.04 lucid & standard updates, that installed **"mountall 2.15", confirmed by "Synaptic"** tool.
...this must be why the check is so fast.
...I am very happy it is not "1/2 hr" like reported above by jnmjr.

Before I got a solid view of that flashing screen, I tried:
(-in gnome-) > System > Administration > Log..File..Viewer
...and it says nothing! That  /var/log/fsck/*  (from big boss above) is not even there !

As soon as Google gave this thread, I looked in the "**/var/log/fsck**" folder (thanks boss...),
...Two files are there: "checkfs"  and  "checkroot", yet, the only thing in those is this exact text:
**(Nothing has been logged yet.)**
_...not the exact helpful and detail report one would be hopping for !_

*I have the conviction Linux (Ubuntu) will be much better in the future, it is already quite impressive. The expert programmer does not see basic problems, he see subtle ones. Newbies and testers are needed to see the forest rather than the treeZ.*:)

---

