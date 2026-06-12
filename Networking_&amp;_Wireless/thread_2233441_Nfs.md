---
title: "Nfs"
date: 2014-07-08
forum: Networking &amp; Wireless
---

### Post by hashimoto on 2014-07-08
Could somebody please explain me what is going on with Ubuntu...

My ax to grind: I have a DNS-323 NAS and I connect with NFS. Everything was fine and working a couple of weeks ago before I went to vacation. I shut down the systems and plugged them off the wall. Today, I returned with the aim of saving all my vacation pics with Shotwell that is using the NAS. Nada. Nix. The NAS does not mount. Nothing was changed between the last shutdown and today, but still the NAS does not mount.

This same has happened a couple of times earlier with some upgrades, but so far I've been able to solve the issue. Now I'm at wits end trying to figure out what is the problem, but I can't figure it out.

So what the heck is going on? Why does my system seem to live a life of its own? Why does Ubuntu upgrades mess my setup every now and then? And where do I start to sort this mess out this time?

Hashimoto

---

### Post by tgalati4 on 2014-07-08
Since you have been a long-time user of Ubuntu, you are aware that updates to software cause regressions--things that used to work, now no longer work.  It is frustrating, but one must consider some time to fix breakage before installing updates.  Don't install updates until you have set aside time to fix expected breakage.

Typically network share problems are logged in /var/log.  Try going through the log files and see if you can find anything useful.

Sometimes share problems are really network problems.  How is your NAS connected to your network?  What is your network topology?

---

### Post by SeijiSensei on 2014-07-09
Can you ping the device from the client machine?

---

### Post by hashimoto on 2014-07-15
Well, it turned out that my DLink DNS 323 had, for some reason, lost the NFS configuration totally. Thus no mounting. But before I realized this, it took quite some time.

I humbly withdraw my accusations towards Ubuntu.

---

