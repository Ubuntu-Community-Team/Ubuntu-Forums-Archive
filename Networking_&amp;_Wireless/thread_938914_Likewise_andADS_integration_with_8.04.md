---
title: "Likewise andADS integration with 8.04"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by gmccord on 2008-10-05
Howdy.  This is my first post, so be kind!  I've been a redhat user for years and am in the middle of evaluating Hardy Heron. There are things I like, but Active Directory integration is not one of them (so far).:) Anyway, after hours of googling, I made it mostly work, but I still have a few issues I can't seem to solve. I also one things that seems to be important:
 My domain is a ".local". I found that I needed to edit nswitch.conf to eliminate all references to mDns (Avahi) or I would have all sorts of DNS problems and could never join the domain.
 

A question or two.

First, I have Likewise 5 installed, have joined to my AD and it more or less works. I was able to manually add one of the domain users to the local admin group so I can sudo from that account. I did this by editing the group file directly, as the users-admin gui tool seems to know nothing about the ADS users. Note that getent finds them all just fine. Once I did that, I noticed that whenever I open a gnome-terminal as a local admin group ADS user, it looks like my .bashrc is not getting sourced for that user. Rather than the usual bash prompt, I just get a "$". Any ideas as to why this is happening?

Second, the install is on a notebook and I use a wireless NIC for the primary IF. What I've noticed is that when I reboot, I can log in as an AD user if that user has previously logged in, but I cannot see any other users using getent except the other local users. If I log out and log back in, this is usually fixed, but not always. I guess its a chicken-and-egg problem in that Likewise needs an active network connection before it can enumerate the AD users? Is there a way around this?

Thanks!

---

