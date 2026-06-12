---
title: "[SOLVED] ethernet not working - how do I fix"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by charonred on 2008-10-02
Posting this for a friend who lives 70km away.

I installed Hardy a couple of weeks ago and all was working fine till this morning.

I was on phone talking them through wireless network problem, but in process uninstalled 'Network Manager' (NM) before installing 'wifi-radar'.

Anyhow, upshot is there is now no ethernet connection, and as such can't download any packages, nor re-install NM.

How do I get ethernet working again? (without installing Ubuntu from scratch).

---

### Post by doas777 on 2008-10-02
> **charonred said:**
> Posting this for a friend who lives 70km away.

I installed Hardy a couple of weeks ago and all was working fine till this morning.

I was on phone talking them through wireless network problem, but in process uninstalled 'Network Manager' (NM) before installing 'wifi-radar'.

Anyhow, upshot is there is now no ethernet connection, and as such can't download any packages, nor re-install NM.

How do I get ethernet working again? (without installing Ubuntu from scratch).

you can probably install network-manager off the live or alternate cds.
just enable the source in your sources list.

---

### Post by charonred on 2008-10-02
they tried that already - after adding CD source, Synaptic needs to reload repositories list, but with the ethernet offline it reports errors, and as such can't install NM - so need another way of installing/reinstalling NM.

I'm not that familiar with using terminal scripts, but will give any recommended scripts a shot; but remember it's not me actually doing it, I have to instruct friend over the phone how to do this, and they have only been introduced to Linux 2 weeks ago, so as simple as possible advice please.

---

### Post by doas777 on 2008-10-03
> **charonred said:**
> they tried that already - after adding CD source, Synaptic needs to reload repositories list, but with the ethernet offline it reports errors, and as such can't install NM - so need another way of installing/reinstalling NM.

I'm not that familiar with using terminal scripts, but will give any recommended scripts a shot; but remember it's not me actually doing it, I have to instruct friend over the phone how to do this, and they have only been introduced to Linux 2 weeks ago, so as simple as possible advice please.

have you tried disabling all repos except the disc?

---

### Post by charonred on 2008-10-03
Thanks, going to try that next - tomorrow morning when I phone them. 

Also found the 2 NM packages at Ubuntu; downloaded them and forwarded to an email address they can access from nearby PC for downloading to a thumb drive - hopefully your suggestion of disabling other repositories will work first.

---

### Post by charonred on 2008-10-06
Update:
tried both the suggested methods above, but system still tried to connect with web (even with everything but CD resource unticked); and the script resulted in same sort of error (couldn't check dependencies online or something).

So friend then used Live CD to connect and accessed her email via webmail for the 2 NM files; transferred them to a thumb drive, then rebooted and ran them - fixed the problem - instant network, then she went off to try her hand at fixing the 2 boy's PCs wireless connection.

Love the way the Live CD just works :)

[http://packages.ubuntu.com/hardy/net/network-manager]("http://packages.ubuntu.com/hardy/net/network-manager")

[http://packages.ubuntu.com/hardy/net/network-manager-gnome]("http://packages.ubuntu.com/hardy/net/network-manager-gnome")

---

