---
title: "Cannot connect using Network Manager after changing partitions"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by krandun on 2007-07-10
There are lots of threads on problems after changing partitions. I've read quite a few of them, and they were helpful up to a point, but now I'm having another problem.

From the top:
When I installed Ubuntu (7.04) I made the following partitions: 1GB swap, 10 GB /, 14GB /home, 14GB /usr.
Recently, I started running Windows XP in a virtual machine, which was stored in my /home by default.
I started running a little low on space on /home, and decided to combine the /, /home, and /usr partitions into one large partition at /.
I asked a friend for advice on this, and he suggested booting from a live CD, mounting all the partitions in the correct place in a temp folder, cp -R the whole lot to an external HDD, re-partition, cp -R everything back, update fstab to ignore the removed partitions.
I did that, and apparently all my folders were somehow chown root:root. My first boot ended with an error about not being able to write to $HOME/.dmrc
Alt-F1 to a terminal and chown -r me $HOME/ to restore my ownership (for each user account).
Reboot. New error "mkdtemp: private socket dir: Permission denied"
Found a thread covering this that suggested chmod -R 777 /tmp, which allowed me to boot into my session.

SO! Where I am now. After all that, Network Manager won't connect to my Wi-Fi or wired routers. The icons animate as if it's trying to connect, but it never goes anywhere.
I would REALLY hate to re-install. I've done a lot of work on this installation and I'm not sure I'm up to starting from scratch just now. I still have the backup of all the files I copied, but they are all chown root:root, too.

Thank you for any help you can offer.

---

### Post by krandun on 2007-07-10
Bump.

---

### Post by krandun on 2007-07-11
Anyone?

---

