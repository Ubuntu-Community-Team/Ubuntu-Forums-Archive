---
title: "Mount autoupdate script with nfs"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by Anton_Bracke on 2013-09-30
Hello,

I have a big problem and realy need your help.

We have about 30 Netbooks and 50 PCs. All of them running linux.
And now my boss wants me to setup a system that the devices mount a update script and run it (for example to update the wifi passwd).
I tried to solve this by using NFS and mount the script to /etc/init.d/.

Do you have any other ideas?

I only need a easy way to run a script on the devices and I need something to choose which devices or a group of devices run it.


Pleas help me.

Thank you.

Anton

---

### Post by Kirk Schnable on 2013-09-30
> **Anton_Bracke said:**
> We have about 30 Netbooks and 50 PCs. All of them running linux.
Not bad.  The network I am working on has almost 1,000 computers, with about 800 running Linux.

> **Anton_Bracke said:**
> And now my boss wants me to setup a system that the devices mount a update script and run it (for example to update the wifi passwd).
Definitely can be done, but I think you're thinking about it in an inefficient way.  Please also consider the side effects of **using the WiFi network to distribute a new WiFi password**, which sounds like a pretty bad practice.

> **Anton_Bracke said:**
> I tried to solve this by using NFS and mount the script to /etc/init.d/.
This sounds incredibly _dangerous_ if you value the reliability of your machines.

> **Anton_Bracke said:**
> Do you have any other ideas?

I only need a easy way to run a script on the devices and I need something to choose which devices or a group of devices run it.
Take a look at some of the configuration managers such as [Puppet]("http://puppetlabs.com/").

Puppet can [push out scripts]("http://docs.puppetlabs.com/references/latest/type.html#file"), [execute scripts]("http://docs.puppetlabs.com/references/latest/type.html#exec"), [manage cron jobs]("http://docs.puppetlabs.com/references/latest/type.html#cron"), and [do lots of other cool stuff]("http://docs.puppetlabs.com/references/latest/type.html").

You can pick up Puppet's Open Source Edition [here]("http://info.puppetlabs.com/download-puppet-open-source").

Kirk

---

