---
title: "Kdenlive startup error"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by dmaxel on 2010-12-08
Hi everyone,

Whenever I start kdenlive, I get greeted with an error message:

File '/home/dmaxel/%i' is not readable

I installed the 0.7.7 from the repos, which had the problem, so I added the official PPA, upgraded, and still the same problem. So I completely removed kdenlive, removed any other configs, and installed again from the new PPA version. Yet I still have the problem.

Any help?

NOTE: For some super strange reason, when I launch it via the menu (I use the LinuxMint menu), I get the error. If I launch kdenlive from the new synapse launcher, I don't have the error. Weird?

---

### Post by Joshun on 2011-04-25
> **dmaxel said:**
> Hi everyone,

Whenever I start kdenlive, I get greeted with an error message:

File '/home/dmaxel/%i' is not readable

I installed the 0.7.7 from the repos, which had the problem, so I added the official PPA, upgraded, and still the same problem. So I completely removed kdenlive, removed any other configs, and installed again from the new PPA version. Yet I still have the problem.

Any help?

NOTE: For some super strange reason, when I launch it via the menu (I use the LinuxMint menu), I get the error. If I launch kdenlive from the new synapse launcher, I don't have the error. Weird?
Edit kdenlive's menu entry (right click on the menu button, click edit menu) and change it so that it just says 'kdenlive', without any % signs or anything. The newer versions of kdenlive aren't compatible with these commandline options, thus giving his error.

---

