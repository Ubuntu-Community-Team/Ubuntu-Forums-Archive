---
title: "Ongoing troubles with systemd-resolved"
date: 2020-06-02
forum: Networking &amp; Wireless
---

### Post by thewoose on 2020-06-02
I have Ubuntu and Ubuntu Server installed on quite a few machines.  However, one thing (on Focal) is that systemd-resolved is INTENT to sabotage my networking.  It happens the same way every time I do a new install.  I boot up and find hosts are not found.  The first thing do I do is disable systemd-resolved as it has put a bogus DNS in my resolv.conf.  Then I delete the resolv.conf symlink and create my own, WORKING resolv.conf.  I just wonder if anyone else has this problem and why it seems resolved it determined to sabotage my connections.  And then if you add unbound, just forget it.  I've never gotten that to work.  I have to use Debian for those machines.  Debian doesn't mangle my resolv.conf.  I can't figure out why Ubuntu so blatantly ruins things.

---

### Post by TheFu on 2020-06-02
> **thewoose said:**
> I have Ubuntu and Ubuntu Server installed on quite a few machines.  However, one thing (on Focal) is that systemd-resolved is INTENT to sabotage my networking.  It happens the same way every time I do a new install.  I boot up and find hosts are not found.  The first thing do I do is disable systemd-resolved as it has put a bogus DNS in my resolv.conf.  Then I delete the resolv.conf symlink and create my own, WORKING resolv.conf.  I just wonder if anyone else has this problem and why it seems resolved it determined to sabotage my connections.  And then if you add unbound, just forget it.  I've never gotten that to work.  I have to use Debian for those machines.  Debian doesn't mangle my resolv.conf.  I can't figure out why Ubuntu so blatantly ruins things.

**[SIZE=6]TESTIFY!!!!  [/SIZE]**
Since resolvconf was introduced, resolving DNS has been totally, completely, screwed on Ubuntu.  I hoped systemd-resolvd would make it "just work", but it made it worse.  I remove systemd-resolvd, resolvconf, then manually edit the /etc/resolv.conf file to point at my primary and secondary DNS running in LXD containers.

Life keeps getting in the way.

---

