---
title: "Wireless Catch22 - can't install ndiswrapper from CDRom"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by nikkkko on 2007-04-24
I've been here before and it wasn't any fun so this time I thought I'd check that ndiswrapper was on the desktop cd before I installed, thus avoiding the, 'I need wireless to download ndiswrapper so that I can get wireless', Catch 22.

However, when I apt-cdrom add and then apt-get update, the CDRom is ignored! Why? Please put me out of my misery by either pointing me to an ndiswrapper .deb I can download and move across on a mem stick, or tell me what I'm doing wrong.

Here's the beginning of my sources list:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main restricted
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty main restricted
etc, etc,

And here's the relevant output from apt-get update:

Ign cdrom://Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) feisty Release.gpg
Ign cdrom://Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) feisty/main Translation-en_US
Ign cdrom://Kubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417) feisty/restricted Translation-en_US

---

### Post by chili555 on 2007-04-25
I believe that's normal. Apt read in the package list when you did *apt-cdrom add* and I don't think the list has changed since then, or ever will.

The key question is, what happened when you did *sudo apt-get install ndiswrapper*? Obviously, it will complain mightily when it can't reach the on-line sources, but does it find and install ndiswrapper on the CD?

You can also find anything you need, by distribution, here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

