---
title: "Having trouble updating from 7.04 Feisty"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Nato99 on 2009-03-08
I'm trying to use the update manager to go from dist 7.04 to 7.10 and I'm getting the following error:

"Getting upgrade prerequisites failed
The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.
Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport."

I went in the bug report answers and found that someone suggested the I try updating from the command line which i tried with no luck. Due to the fact that Feisty is fairly old I haven't filed out a bug report yet.

Also, I'm getting an error if I try to download software from the repositories saying the following:
"http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz: 404 Not Found"

Any suggestions? I have no problems getting on the internet.

---

### Post by taurus on 2009-03-08
Edit /etc/apt/sources.list and replace your **deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)** with **deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu)**.  

Save it and see if you can upgrade now.

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by hansdown on 2009-03-08
Hi Nato99.

Support for 7.04 and 7.10 is no longer available.

Have you considered moving to something newer?

8.04 LTS is very solid.

---

### Post by mikechant on 2009-03-08
> Support for 7.04 and 7.10 is no longer available.

Actually 7.10 is supported until next month (18 months from release); but of course, it doesn't make sense to move to a version which will be out of support this soon anyhow.

---

### Post by ugm6hr on 2009-03-08
> **Nato99 said:**
> Due to the fact that Feisty is fairly old I haven't filed out a bug report yet.

Feisty is more than fairly old - it is now unsupported.

As Taurus pointed out, the repositories have officially been taken down; hence you cannot connect to them.

Unofficially, they have just been moved (so are technically still available).

---

### Post by snowpine on 2009-03-08
Canonical does not support its releases longer than 18 months unfortunately (except for LTS) so I really recommend backing up your personal data and then reinstalling 8.04 or 8.10 from scratch. There is a work around as mentioned above, but you would have to go in steps from 7.04->7.10->8.04->8.10 which would not be very fun.

---

