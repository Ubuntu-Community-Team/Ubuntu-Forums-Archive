---
title: "copy and sync files from old file server to new file server"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by StrangeBrew on 2009-02-26
Here's my situation. I have old file server (server A, Win2k) that is in domainA. Then the new file server (server B, Win2k3) that is in domainB. I'm looking for a way to copy files modified after a certain date from server A to server B. I don't want everything from server A because there are a lot of old files that no one uses anymore. Then I need incremental copies done unitl can get all of the users moved from domainA to domainB. I was thinking an ubuntu box in the middle would best handle the job, I just need some help getting there.

thanks

---

### Post by Hospadar on 2009-02-26
Well, i sort of disagree that an ubuntu box would be the easiest way, although it's certainly doable.

Basically, if you used an ubuntu machine, you'd need to connect it to both machines somehow (probably with something like smbfs) and then read off the old machine check the dates in a bash script, copy the files to the new machine.

What seems like a lot easier solution would be to rip the drive out of machine A and stick it into machine B or the ubuntu machine, or just trash the windows servers altogether and put everything on a linux machine.  It can serve up windows shares and is much easier to administer and handle in general (in my opinion as a computer scientist and home server administrator).

---

### Post by OffAxis on 2009-02-26
I would use a **find **command and then pipe that into an **rsync** or **scp** (assuming you have remote terminal access capabilities to both machines).

Here's a good writeup on find (specifically the time functions):
[http://dsl.org/cookbook/cookbook_10.html#SEC143](http://dsl.org/cookbook/cookbook_10.html#SEC143)

and the man page for rysnc is rather comprehensive

```
man rsync
```

After the initial copy rysnc is probably the tool to use.

---

