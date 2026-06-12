---
title: "how do updates work"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by dd1313 on 2010-01-29
Hi Guys

Can ubuntu be setup to automatically update.Does this also work from one Major release to another.

THanks
Dev

---

### Post by Rex Bouwense on 2010-01-29
Sure enough.  Go to System>Administration>Software Sources  and then to Updates.  Under automatic updates you have your choice.

---

### Post by dd1313 on 2010-01-29
> **Rex Bouwense said:**
> Sure enough.  Go to System>Administration>Software Sources  and then to Updates.  Under automatic updates you have your choice.

Does this also apply to updates like version 8.0 to 9.0
etc

THanks
Dev

---

### Post by chaanakya_chiraag on 2010-01-29
I don't think that can be configured to occur automatically, because those a) take a lot of time and b) could be interactive, in which case the automating thing wouldn't work anyway.  When you are ready to upgrade to the next release, go to System->Administration->Update Manager and click the button at the top next to "New Release Available"

---

### Post by Rex Bouwense on 2010-01-29
That is an upgrade and I do not know if it will automatically upgrade for you.  That will only happen every six months anyway.  Let me see if I can find out anything else.
That didn't take long.  See previous posting (#4)

---

### Post by dd1313 on 2010-01-29
Thanks Guys

So how long is a release supported for.I mean lets take version 7.0
Is it still supported with updates.

Dev

---

### Post by snowpine on 2010-01-29
> **dd1313 said:**
> Thanks Guys

So how long is a release supported for.I mean lets take version 7.0
Is it still supported with updates.

Dev

Most Ubuntu releases are supported 18 months, except for the LTS (long term support) releases, which are supported 3 years. 10.04, coming in April will be LTS.

8.04 is the oldest release that is still supported.

---

### Post by tom.swartz07 on 2010-01-29
> **dd1313 said:**
> Thanks Guys

So how long is a release supported for.I mean lets take version 7.0
Is it still supported with updates.

Dev

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history)

Hope this helps!
Anything before 8.04 is unsupported.

---

### Post by Rex Bouwense on 2010-01-29
> **dd1313 said:**
> Thanks Guys

So how long is a release supported for.I mean lets take version 7.0
Is it still supported with updates.

Dev
I believe that the LTS releases are supported for three years and a normal release is supported for 18 months.

---

### Post by dd1313 on 2010-01-29
> **tom.swartz07 said:**
> [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history)

Hope this helps!
Anything before 8.04 is unsupported.

What about 6.06.That should be supported till the middle of 2011

See the timeline at the link above

Dev

---

### Post by tom.swartz07 on 2010-01-29
> **dd1313 said:**
> What about 6.06.That should be supported till the middle of 2011

See the timeline at the link above

Dev

Thats the server edition, I was referring to normal desktop editions.

If you want to use Dapper server edition, more power to you!

For best support, I would recommend the newer versions though.

---

### Post by Rex Bouwense on 2010-01-29
That is only the server release.  The desktop release is no longer supported.

---

### Post by dd1313 on 2010-01-29
Thank guys..

Ok suppose I am using 6.06 LTS.Can that be setup to automatically
update till 2011 or will there upgrades along the way that would
require interaction.

Also how often do we get updates and how often do we get upgrades
with LTS

Also was 6.06 LTS based on debian ver 3.0 or 4.0



THanks
Dev

---

### Post by penguinv on 2010-01-29
> **dd1313 said:**
> Hi Guys

Can ubuntu be setup to automatically update.Does this also work from one Major release to another.

THanks
Dev

I just found out (by being stupid and just trying it) that it works on wubi-ubuntu too. Well it should work because it asked me to update it.

But when it auto-rebooted it gave me a blank screen and I thought, "All is lost!"  So I hard-shutdown and restarted and all is fine.

---

### Post by snowpine on 2010-01-29
> **dd1313 said:**
> Also was 6.06 LTS based on debian ver 3.0 or 4.0

Neither. Ubuntu is based on Debian testing/unstable, not a particular Debian stable release.

I would not recommend automatic updates for a server (which is the only type of 6.06 install that's still supported).

---

### Post by dd1313 on 2010-01-29
> **snowpine said:**
> Neither. Ubuntu is based on Debian testing/unstable, not a particular Debian stable release.

I would not recommend automatic updates for a server (which is the only type of 6.06 install that's still supported).

So when Debian says that it is not supporting a version anymore
it does not affect Ubuntu

[http://www.debian.org/News/2010/20100121](http://www.debian.org/News/2010/20100121)

Dev

---

### Post by snowpine on 2010-01-29
> **dd1313 said:**
> So when Debian says that it is not supporting a version anymore
it does not affect Ubuntu

[http://www.debian.org/News/2010/20100121](http://www.debian.org/News/2010/20100121)

Dev

Correct; there is no relationship.

---

### Post by dd1313 on 2010-01-29
how often do updates come out

Dev

---

### Post by snowpine on 2010-01-29
> **dd1313 said:**
> how often do updates come out

Dev

Daily at first, then they slow down over time as the release matures. I personally update once a week.

I feel like this is all leading up to something...  what is your actual question? :)

---

### Post by dd1313 on 2010-01-29
> **snowpine said:**
>   what is your actual question? :)

;)  None..I am just empowering myself with knowledge as I would need this when a client asks.

Also like what happens during an updates,Like with windows
sometimes it reboots,does that happen with ubuntu as well.
Do I have to start anything after the update,is it all automatic.?

Dev

---

### Post by snowpine on 2010-01-29
> **dd1313 said:**
> ;)  None..I am just empowering myself with knowledge as I would need this when a client asks.

Also like what happens during an updates,Like with windows
sometimes it reboots,does that happen with ubuntu as well.
Do I have to start anything after the update,is it all automatic.?

Dev

:)

Ubuntu does not automatically shut itself down after an update. (I hate that about Windows!)

If your update includes a new version of the kernel, you need to reboot into the new kernel for the change to take effect.

---

### Post by dd1313 on 2010-01-29
will a LTS system ever need a reboot update with the updates

Dev

---

### Post by snowpine on 2010-01-29
> **dd1313 said:**
> will a LTS system ever need a reboot update with the updates

Dev

As I mentioned, you will need to reboot if you wish to take advantage of a kernel update.

---

### Post by dd1313 on 2010-01-29
if I go cat /etc/*version  its tell me 4.0
I assume that this is ver 4.0 of debian.Is there
any information on what debian testing ver is linked to
Ubuntu

Thanks
Dev

---

### Post by snowpine on 2010-01-29
> **dd1313 said:**
> if I go cat /etc/*version  its tell me 4.0
I assume that this is ver 4.0 of debian.Is there
any information on what debian testing ver is linked to
Ubuntu

Thanks
Dev

Debian testing does not have "versions"; it is rolling release.

Normal Ubuntu releases come from Debian Unstable (Sid) and LTS releases from Debian Testing.

Maybe comparing these will give you a better idea:
[http://www.distrowatch.com/ubuntu](http://www.distrowatch.com/ubuntu)
[http://www.distrowatch.com/debian](http://www.distrowatch.com/debian)

---

