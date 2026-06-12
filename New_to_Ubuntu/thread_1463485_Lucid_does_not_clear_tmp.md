---
title: "Lucid does not clear /tmp"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by mmasroorali on 2010-04-27
Dear All,
After I have upgraded to Lucid Beta, /tmp is no longer being cleared at boot. I have checked and found TMPTIME=0 in /etc/default/rcS. What else can I check? 

Thanks in advance.

---

### Post by wojox on 2010-04-27
It says this in 9.10 as well. It won't delete some folders and files, ( orbit, pulse, etc...)

---

### Post by mmasroorali on 2010-04-28
> **wojox said:**
> It says this in 9.10 as well. It won't delete some folders and files, ( orbit, pulse, etc...)

Thanks for the reply. Could you please elaborate.

Are you suggesting that lucid is selective in file deletion? But it is not deleting anything at all. Please see the attached list.

Any suggestion will be appreciated.

---

### Post by _0R10N on 2010-04-28
Instead of deleting the /tmp content at boot time, you can do it before exiting. If you want to try this alternative, you can to this:
```
sudo vi /etc/rc.local
```
If you never changed this file, you should see something pretty much like this:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```

Before the last line, add this one:
```
rm -rf /tmp/*
```
I'm suggesting this only as an detour. I use Karmic at home, so if it's a problem also present in 9.10, I promise to check this out.

Kind regards!

_0R10N >>

---

### Post by mmasroorali on 2010-04-28
> **_0R10N said:**
> Instead of deleting the /tmp content at boot time, you can do it before exiting. If you want to try this alternative, you can to this:
```
sudo vi /etc/rc.local
```
If you never changed this file, you should see something pretty much like this:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```

Before the last line, add this one:
```
rm -rf /tmp/*
```
I'm suggesting this only as an detour. I use Karmic at home, so if it's a problem also present in 9.10, I promise to check this out.

Kind regards!

_0R10N >>

I know that I can put something in rc.local and get that executed during boot time. But I want to find out why suddenly clearing of /tmp stopped in lucid. This has happened automatically over the years. I am somewhat perplexed.

---

### Post by wojox on 2010-04-28
That is a lot of files. I just downloaded 10.04 last night so let me check on my laptop.

---

### Post by _0R10N on 2010-04-28
> **mmasroorali said:**
> I know that I can put something in rc.local and get that executed during boot time. But I want to find out why suddenly clearing of /tmp stopped in lucid. This has happened automatically over the years. I am somewhat perplexed.

I also would like to know what is causing that behavior. I've only suggested that alternative, until we might reproduce the situation and find out what's causing it.

Kind regards!

_0R10N >>

---

### Post by barbz127 on 2010-04-29
If you have the ram why not load up temp in ram using a tmpfs.

More here [http://ubuntuforums.org/showthread.php?t=633776]("http://ubuntuforums.org/showthread.php?t=633776")

Paul

---

### Post by Kieron on 2010-05-04
I am also having this problem, causing a lot of errors with rtorrent's temporary socket which is stored there. Driving me mad, wishing I never upgraded my server now! I tried adding the line to rc.local, but now thats wrecked php! Erghh!

---

### Post by lotharmat on 2010-05-04
I'm running the 64 bit version of Lucid and apart from the usual folders in /tmp - it is practically empty..

---

### Post by mmasroorali on 2010-05-06
Finding no other alternative, I have added a line in rc.local. The /tmp was simply filling up.

---

### Post by philinux on 2010-05-06
> **mmasroorali said:**
> Finding no other alternative, I have added a line in rc.local. The /tmp was simply filling up.

Odd. Have you bugged it at launchpad?

If not. Probably like this.

```
ubuntu-bug linux
```

---

### Post by ukripper on 2010-05-06
Found a bug report going back to karmic - [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/524196](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/524196)

---

### Post by philinux on 2010-05-06
> **ukripper said:**
> Found a bug report going back to karmic - [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/524196](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/524196)

Aha. OP needs to subscribe to the bug report then use.

```
apport-collect 524196
```

They think it's fixed in lucid. Obviously not for some.

---

### Post by _0R10N on 2010-05-06
Someone has made any progress on this? My /tmp is being cleaned normally on each reboot, but it must be pretty annoying for those with this problem.

---

### Post by mmasroorali on 2010-05-08
Now I find that after an upgrade, the feature is working again.

I wish I could know the reason.

---

