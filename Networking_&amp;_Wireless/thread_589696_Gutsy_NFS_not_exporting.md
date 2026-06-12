---
title: "Gutsy NFS not exporting?"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by IndieRockSteve on 2007-10-24
I just installed Gutsy on a new computer that I previously had another Debian based distro installed on. I had it along with another computer with Fiesty installed setup to share a couple directories between the two which worked great, but now I'm trying the same with Gutsy and while the directory mounts on the other computer, it lists as an empty folder.
I'm using the same exportfs and mount options as on my Fiesty computer which the Gutsy computer see's fine.

Am I missing something in how gutsy handles things now?

thanks!

---

### Post by IndieRockSteve on 2007-10-24
nevermind, I fixed it, apparently exporting a directory that was binding to a directory under the original mount caused the problem...

---

### Post by moon2js on 2007-10-26
Could you explain how you fixed it a bit more? I'm having the same problem.

I have a Feisty server with an NFS share and my desktop Feisty worked great with it, but now as Gutsy (on the deskop), whenever I open the share, it's empty. I didn't change anything on the Feisty server nor did I change anything on the Gutsy upgraded desktop. Fstab:

```
192.168.1.xx:/home/me /home/me/myshare nfs rsize=8192,wsize=8192,timeo=14,intr 0 0
```

---

