---
title: "404 error when updating Ubuntu?"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by PumaMania on 2011-07-15
I'm using 10.04 LTS Lucid Lynx (I believe that's right) and I am an absolute noob at this. Basically I use Update Manager to update everything and so far it's working well, but for some reason I get the error that says:

"Failed to fetch [http://ppa.launchpad.net/https/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/https/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

Some index files failed to download, they have been ignored, or old ones used instead."

I think this is the main one that updates my version of Ubuntu, and it's been broken like this for 47 days. How do I fix this? Please use simple terms. Again I'm slow at this stuff :P Me installing Ubuntu without breaking my computer is a miracle.

---

### Post by wildmanne39 on 2011-07-15
Hi, thats because it is not on the server, you might try to get the package from another source.

---

### Post by varunendra on 2011-07-16
> **PumaMania said:**
> ....for some reason I get the error that says:

"Failed to fetch [http://ppa.launchpad.net/https/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/https/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

Some index files failed to download, they have been ignored, or old ones used instead."

I think this is the main one that updates my version of Ubuntu.
First off, this appears to be an incorrect ppa url (a faulty line in your /etc/apt/sources.list file). Secondly, System-critical updates, like kernels or ubuntu version-upgrades are not associated with ppa sources :). They come from main (or regional) ubuntu servers. So you don't have to worry about critical updates (provided you haven't disabled default repositories/updates).

If this all seems too confusing, just browse to this file: [s]/etc/apt/resolv.conf[/s] **([COLOR=Red]correction:[/COLOR] /etc/apt/sources.list)** , open it and post its contents in your new post. To make it more readable, select (only) the pasted text, then click on the '#' icon at the top of editing box to wrap it into [ code] and [ /code] tags.


An 'off the track' advice for you: Although the update manager shows you latest available version of Ubuntu and provides an 'Upgrade' button next to it, it is always recommended to try a Live CD of that version first (to see if it supports your hardware properly), and then make a 'Fresh' installation using the same Live CD. Updating packages is fine and recommended, but "Upgrading" Ubuntu via update manager often causes problems.

---

### Post by PumaMania on 2011-07-26
> **varunendra said:**
> First off, this appears to be an incorrect ppa url (a faulty line in your /etc/apt/sources.list file). Secondly, System-critical updates, like kernels or ubuntu version-upgrades are not associated with ppa sources :). They come from main (or regional) ubuntu servers. So you don't have to worry about critical updates (provided you haven't disabled default repositories/updates).

If this all seems too confusing, just browse to this file: /etc/apt/resolv.conf , open it and post its contents in your new post. To make it more readable, select (only) the pasted text, then click on the '#' icon at the top of editing box to wrap it into [ code] and [ /code] tags.


An 'off the track' advice for you: Although the update manager shows you latest available version of Ubuntu and provides an 'Upgrade' button next to it, it is always recommended to try a Live CD of that version first (to see if it supports your hardware properly), and then make a 'Fresh' installation using the same Live CD. Updating packages is fine and recommended, but "Upgrading" Ubuntu via update manager often causes problems.

Thanks for the other tip, that's a good idea since I plan on putting Ubuntu on a laptop I'm getting soon :P

But back on topic, I go into the etc/apt folder and I only see "apt.conf.d", "preferences.d", "sources.list.d", "trusted.gpg.d", (the first four are folders that don't have "resolv.conf" in them), "secring.gpg", "sources.list", "sources.list.distUpgrade", "sources.list.save", "trustdb.gpg", and "trusted.gpg". Case in point, I don't have that resolv.conf file :/

---

### Post by oldos2er on 2011-07-26
I think varunendra meant to type /etc/apt/sources.list

---

### Post by varunendra on 2011-07-27
> **oldos2er said:**
> I think varunendra meant to type /etc/apt/sources.list
Oops!! You are right oldos2er, I think my mind got mixed up in multiple posts while writing that one.... (hope I didn't type "sources.list" in some network related post.. :D).

@PumaMania,
it was a mistake as oldos2er pointed out, please make it **/etc/apt/sources.list**. I'm including the same correction in my previous post.

---

