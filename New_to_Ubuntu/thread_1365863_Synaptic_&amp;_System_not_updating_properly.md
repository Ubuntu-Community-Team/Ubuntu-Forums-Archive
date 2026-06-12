---
title: "Synaptic &amp; System not updating properly"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by faron45 on 2009-12-27
Can anyone please explain to me how the "reload" & "mark all upgrades" buttons work in synaptic package manager ? I do not think the package manager is being automatically updated like I thought it was supposed to because when I look inside,things like Firefox,etc. are not quite up to date.What's funny about that is that I get notified of updates to the product quite a bit & I always download them.Yet the package manager says that I am still running version 3.0.16.

Same thing with Xubuntu-I remember about maybe 6 months ago I was asked if I wanted to update to the latest version of Xubuntu...I said yes.Well,I have found by entering the code lsb_release -a in a terminal that I am running version 8.04 Hardy Heron.When I ran that code I was also told "no LSB modules are available" Whatever that means.

When I try the "reload" button I seem to get a download but it doesn't seem to stick.Because the next time I open Synaptic & try this again I get the exact same download.Before trying this today I used to get errror messages.Anyone have any useful information for me ?? Please ???

I have so many issues with this system I'd like to just throw it out the window but $$$$$$ forbids it.Like flash too for instance.Flash really is lousy.But,now,I went to a different site today & instead of Adobe flash my system ran Totem.A little dark but FANTASTIC otherwise.Totem did say that what was playing were windows codecs,if that makes a difference.


                    THANK YOU ALL

---

### Post by marshmallow1304 on 2009-12-27
In Synaptic, Reload does the same as
```
apt-get update
```
[quote=man apt-get]
           update is used to resynchronize the package index files from their
           sources. The indexes of available packages are fetched from the
           location(s) specified in /etc/apt/sources.list.[/quote]

This does not change any currently installed programs, but simply synchronizes the list of available programs.

Marking all upgrades doesn't do anything until you hit Apply.

Generally, Update Manager is easier than Synaptic for upgrading packages.

---

