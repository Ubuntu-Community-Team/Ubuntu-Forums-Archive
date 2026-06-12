---
title: "Which is the most stable Ubuntu Server OS version?"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by tdapower on 2010-12-02
I need to know which is the most stable Ubuntu Server OS version? Is 9.10 or 10.04? And also I need to know the end date of support period of Ubuntu Server OS 9.10.

---

### Post by theDaveTheRave on 2010-12-02
tdapower.

If you are running a server version I would recomend going with one of the LTS (long term support = 5 years of updates) versions. This means either 8.04 or 10.04 see the [documentation pages for more info]("https://help.ubuntu.com/") just follow the relevant links.

If you are setting up a 'server system' you will need to have some form of redundancy so here is my advice.

If you are doing a clean install choose either of the options for your system (maybe starting with 8.04 would be a good idea anyway for the reasons I am about to suggest below).

Set up you 'primary' system so as everything works the way you want it, make extensive notes on what you have done and any config changes you needed to make.

Now set up your secondary system, refer to your notes, and it shouldn't take as long to get it to the same state as your first system - you can check that everything works as is should by substitution of this with your first server.

You may now set up a 3rd server knowing that everything is working as you would like, this server becomes your 'updates test bed' you perform all updates on this server and check that nothing breaks before performing them on the other 2 (remember do them 1 at a time). When you are ready you can then take server 3 up to the next LTS version, and document all the problems that you have with the upgrade.

Remember to check all the mission critical stuff works, such as databases links on web pages (I came unstuck with an install of mysql that stopped working on my last desktop upgrade).

I also advise not going over to any version untill it has been out for a few months, then check the forums for problems (the mysql eror that was above had apparently been 'solved' but not for me, which I assume was due to an install from source rather than from the repositories :shrugs:)

Why do I recomend 8.04 over 10.04 ??

Well I know that in the more recent version of the Linux Kernel there is a move to 'upstart' as opposed to the old fashioned 'sysV init.d' run level stuff - Ubuntu and Debian are both starting to use these versions. My experience would suggest that things aren't fully 'ironed out' with upstart at this moment in time. However if you are performing a clean install, your experience may be different.

Also if I was going to be setting up a server system from scratch I would probably use debian, rather than ubuntu, but that is just personal preference. If I was installing for someone else I would install ubuntu as debian has the image of a 'difficult distro' or should that be 'more of an Linux experts distro' compared to Ubuntu.

The choice however is always yours to freely make. Just as is everything Linux / GNU.

Good luck

David

---

### Post by mastablasta on 2010-12-02
Another option would be to go Debian for server as it is very stable and supported for long time.

---

### Post by tdapower on 2010-12-06
Thanks

---

