---
title: "hard drives no longer automount"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by BklynKid on 2010-05-10
Help! My hard drives no longer automount. I didn't have to do anything when I first installed Ubuntu, my internal ext2-formatted drives just showed up on my desktop. Now I don't know what happened, I rebooted today and when I came back they weren't there anymore. I have to go into the Disk Utility to remount them manually but that's not ideal on a headless server.

Any ideas?

[edit] Should probably mention, this is on 10.04.

---

### Post by TheNerdAL on 2010-05-10
This might help: [http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html](http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html)

---

### Post by wdaim on 2010-05-10
go to ubuntu software centre and search for storage device manager, install that and then select the drive and click "Assistant" then make sure "the drive is mounted at boot time" is ticked. restart and enjoy

---

### Post by BklynKid on 2010-05-11
Thanks guys, that worked. 

Just perplexed that this went away somehow. What did I do that made it "turn off" in the first place?

---

