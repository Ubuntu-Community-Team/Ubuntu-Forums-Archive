---
title: "Who what? Linux live disk for software network firewall and anti virus?"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by herrell25v on 2014-02-18
First time poster here, my googlefu is sucking today bad.

i want to make a live disk with a 32 gb USB 3.0, that will hold a linux live disk that is small form factor distro for software firewall ect... i want to partion the USB 1/1 raito so it will be able to retain all of the info that will  be saved. it will all operate on a windows x32 based virtual box. how do i do this? its going to get me out of the next 3 months of CS this year and i realy need the help so i can pass my other classes, if anyone can help please do so.

---

### Post by TheFu on 2014-02-18
A tiny distro needs 100MB.  I don't understand the "1/1 ratio" comment. Please clarify.
There exist many Linux-based firewall distros already.  "linux firewall distro" - google that. There isn't enough information in the question to help more.

However, if this is for a real business, I'd strongly recommend using pfSense instead. It isn't based on Linux.

Making it work in virtualbox isn't too hard, provided you can export and import the "appliance" every time or can force the mount location to be identical on every since host machine.  Check into the **subst** DOS command.
Don't see what a firewall has to do with passing other classes.

---

