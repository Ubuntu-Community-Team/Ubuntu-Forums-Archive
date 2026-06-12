---
title: "Building a mini-LAN with Ubuntu"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by Happy Dave on 2007-07-27
Hi Folks

So, my new wife and I are about to move into a place of our own for the first time, and I've inherited an old windows PC.  I've also got a couple of large external hard drives (250gb and 100gb respectively), and a netgear router.

We're moving into a place that already has broadband set up, so what I really want to do is set this PC up as a miniature wireless LAN (i.e. not connected to the web), hooking it up to the two hard drives for storage.  My wife and I both have Mac laptops (mine dual-booting Ubuntu Fiesty) and I'd like to automatically back them up (wirelessly, through the router) each night, as well as streaming our media collections from the server.

Where do I start?  A lot of the advice I'm finding online centres on things like running your own home webserver, which I don't want to do (yet) - I just want our own little LAN.

Any pointers?

---

### Post by noob12 on 2007-07-27
Pretty open-ended question.  Not sure what you're after exactly.

Whatever you do is probably going to look something like this:
[LIST=1]
[*]Put the wireless router on the net without the WAN side connected; disable the DHCP in the router, since it sounds like you probably have DHCP from another one on that net already.

[*]Install the PC with ubuntu.  In your situation, I'd probably still use the desktop edition and install a few server packages on it.

[*]Share files using samba or netatalk.

[*]You might want to install something like daapd to provide music to your Macs

[*]Not sure how you plan to do backups.  One thing you might find is that wireless can be slow for backups depending on whether you're doing incremental or full ones, and what kind of content you tend to edit (small files or large).  For backing up mac files with their resource forks and all metadata, I'd suggest doing disk images via MacOS X hdiutil or other backup software like SuperDuper rather than straight Samba copies.
[/LIST]

---

### Post by swampdweller on 2007-07-27
Hi Happy.   :)

Like Noob said, not the most specific question.
You'd probably do well to set up the connectivity first,
then worry about how to use it (or justify it?).

If the existing broadband gateway is a wireless router,
you may have no real need of your spare router.

Not that that's any reason not to use it.
I fully understand the desire to use it.
I have six routers in my little house.
I mention that not to underscore the obvious fact
that I'm insane, but to explain why your project
makes perfect sense to me.  Who wouldn't want to
set up their own little miniature network?

It's sort of the male equivalent of putting new
cupboards in.

But it won't be very convenient if your computers
have to change access points to move from the internet
to your mininet, so like Noob said, you'll likely want to
connect your router to the existing gateway.

Also, like Noob said, you'll want, for starters at least,
to go with the simplest case where you don't use the
WAN port at all, in other words you downgrade the
device from NAT-capable router to mere switch.

And if you're attaching it to an existing router,
well then you can think of it as a mere hub,
or uhm, fancy double female cable connector.   :)

No, maybe the only way to justify it *is* to make it a
separate access point that you switch to when you want to
get off the internet and wirelessly access your shared storage.

Oh, who needs to justify it?
Just plug the bugger in and use it as a night light.
:)

---

