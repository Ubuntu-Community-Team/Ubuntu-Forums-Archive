---
title: "Ubuntu 21.10 - hundreds of DNS requests to ubuntu.localdomain"
date: 2022-02-18
forum: Networking &amp; Wireless
---

### Post by ch33zw1z on 2022-02-18
Hi,

I run a couple pihole servers on Ubuntu server, and one of them started querying ubuntu.localdomain hundreds to 1000+ times during a 10 minute duration.

I posted a thread over at pi-hole forums, but don't really think it's specifically pi-hole related. link to thread:

[https://discourse.pi-hole.net/t/2-piholes-primary-started-seeing-hundreds-of-requests-for-ubuntu-localdomain-from-secondary/53707](https://discourse.pi-hole.net/t/2-piholes-primary-started-seeing-hundreds-of-requests-for-ubuntu-localdomain-from-secondary/53707)

Here's what changed yesterday 2/17

> I've been using pihole for about 2 years in this way, not specifically on RaspberryPi's, but a combination of 2 devices running ubuntu with the Primary on a LTS release.

I will typically run OS updates once per month, starting with the secondary and if all keep humming along then a few days later or maybe a week I'll go update the primary.

Yesterday, 2/17 about 6AM EST, I did this on the secondary. I run OS updates, rebooted, verified all looked good, then ran sudo pihole -up.

I checked the piholes this morning, and noticed that the primary started logging hundreds of requests every 10 minutes from the secondary to ubuntu.localdomain. This started about 12 hours after I updated the OS and pihole (7PM EST)

I went ahead and reloaded the secondary from scratch this morning, installed all updates / upgrades (sudo apt update / upgrade), then installed pihole.

The primary is still logging the same requests from the secondary.

I'm looking for some advice on what logical next steps are in order here.

---

### Post by TheFu on 2022-02-18
What is ubuntu.localdomain? Where should that resolve?  Looks like something isn't configured that needs to be configured.

---

### Post by ch33zw1z on 2022-02-19
Yes, I agree, but what and less importantly why.

---

### Post by TheFu on 2022-02-19
> **ch33zw1z said:**
> Yes, I agree, but what and less importantly why.

Er ... something that was installed, but not configured?  There are lots of packages that have to be configured after they are installed. Thousands.  

Do you expect a web server to "just work" after you install it?  That isn't how it goes. It needs setup, configuration, data files and if there is a web-app, those will need to be tied into the web-server install correctly.  If an MTA was installed, perhaps as a dependency to some other package, it wouldn't be configured either.

What's the hostname?  Is is "ubuntu"?
What's the domain man?  Is it "localdomain"?

Have you looked for those terms under /etc/?  That's likely where the configuration is needed. You'll likely want to perform a recursive grep in all the files under /etc/ to find those things.

---

### Post by ch33zw1z on 2022-02-19
I've been trying to figure it out. The question here is what changed? Something in ubuntu changed during the last update I did on 2/17. The only role this plays is a pihole server, and it's been fine for 2 years without any additional fiddling.

So thanks, I guess?

Since it's super easy to just load another OS and try out pihole, I'll probably go that route.

Here's a nice little add-on. I reloaded again and used the last LTS version instead. Now, the secondary isn't just spamming requests to the primary, it's also spamming itself. The pihole gui reports "localhost" incrementing by hundreds per minute.

---

### Post by TheFu on 2022-02-19
There is a log of all updates under /var/ somewhere.
I'm patching my 20 systems now. I patch weekly, never automatic. The things updated this week are ssh-related. Most of my systems don't have GUIs, so there aren't usually many updates. I install the 'ssh' metapackage for convenience whenever I do a fresh Ubuntu install.
```
openssh-client openssh-server openssh-sftp-server ssh
```

My pi-holes were just updated. I run them in LXD containers. Not seeing any issues. The pihole logs aren't showing anything odd either.  Blocked queries are still blocked. Allowed queries are working.  They are also the local DNS servers for my LAN --- those are working too.

Have you looked at other systems that might be making all the queries?

I do see some updates for 20.04 that my 18.04 systems didn't get.
```
  linux-headers-5.4.0-100 linux-headers-5.4.0-100-generic
  linux-image-5.4.0-100-generic linux-modules-5.4.0-100-generic
  linux-modules-extra-5.4.0-100-generic
The following packages will be upgraded:
  base-files cryptsetup cryptsetup-bin cryptsetup-initramfs cryptsetup-run
  firefox firefox-locale-en language-pack-en language-pack-en-base
  libarchive13 libcryptsetup12 linux-firmware linux-generic
  linux-headers-generic linux-image-generic linux-libc-dev python-apt-common
  python3-apt python3-distupgrade snapd ubuntu-drivers-common
  ubuntu-release-upgrader-core
22 upgraded, 5 newly installed, 0 to remove and 0 not
```
Looks like Canonical is pushing new update stuff in support of the 22.04 release in a few months.
Appears that my 20.04 systems will need a reboot. The 18.04 systems do not.

---

### Post by ch33zw1z on 2022-02-19
From the primaries view, the IP making all the queries to ubuntu.localdomain is the secondary.

From the secondaries view, it's all localhost queries now.

Since I haven't had to do much with them, I'm not really sure what I would need to configure to stop it from the huge amount of queries.

For reference, my home network gets 50k queries on a busy day. The Primary is reporting 2x-3x that now, and the secondary (which is usually not busy at all), has 15k in the last hour...almost all to localhost.

---

### Post by TheFu on 2022-02-19
The pihole.log file has what was requested, who requested it and what was returned.  That should nail down the IP for the requestor system.  After that, you'll need to hunt down which process is making the calls.  I'd look at all the network stuff.

I suppose the first step would be to disable DNS queries from the client - don't let them hit the pi-hole.  That will ensure you have the correct client system.

Next, I'd simplify the DNS setup on that client system - remove resolvconf and/or systemd-resolved from the chain. Look at all the network stuff. Use **netstat** and **lsof**.

---

### Post by ch33zw1z on 2022-02-19
yes, the pihole logs is what I'm looking at. the pihole servers have static dhcp reservations, they are always the same, ip addr show confirmed. I'm certain of the secondary pihole's role in this.

I'm down a similar path, reading about how to disable resolvconf and systemd-resolved.

But it doesn't change the fact that this wasn't happening prior to 2/17, and started just about 12 hours after I completed updates. Very strange...

here's what has changed right now, after the reload to the last LTS version, the secondary has pretty much stopped spamming the primary, and is now just spamming itself. There 62,000 queries to localhost (changed it to pihole-2), in 3 hours.

---

### Post by TheFu on 2022-02-19
There's something different in your setup. I'm not seeing any of that.  My base OS is Ubuntu 18.04.6 LTS. It runs as a container under lxd. If you have specific questions, I'm happy to look up the answer.
For example, here's the disk used from inside the container:
```
$ df -Th
Filesystem            Type  Size  Used Avail Use% Mounted on
lxd/containers/pihole zfs    11G  1.2G  8.9G  12% /
```

The 11G is shared with a number of other, unrelated, lxd containers.

---

### Post by ch33zw1z on 2022-02-20
I appreciate the help so far! For now I won't be touching the primary. It runs 20.04.3 LTS and has some updates pending, with pihole updates waiting as well. I'm going to keep fiddling with the secondary and see what happens, currently loading raspberry pi OS lite 64-bit (bullseye) to see what happens. Looks like it's debian based as well.

I ordered another micro sd card and am willing to reload 20.04.3 LTS onto it and see what happens, since the symptom changed but DNS queries still incremented 2-3 per second. after 18 hours, the secondary had 300,000+ queries to itself for localhost

I'm not sure what commands or information would be pertinent, but maybe comparing services running, packages installed, etc...

---

