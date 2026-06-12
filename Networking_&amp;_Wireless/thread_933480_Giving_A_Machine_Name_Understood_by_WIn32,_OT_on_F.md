---
title: "Giving A Machine Name Understood by WIn32?, OT: on Forum Accessibility"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by vtatila on 2008-09-29
Hi, I'm new to Linux but have been using computers some dozen years and programming the last 7:
One thing I know next to nothing about, despite having written simple socket apps in C and Perl, is networking at the user level, <blush>, so here we are:

Question: How do I give my LInux machine using DHCP a name that my Windows box can understand, so as to avoid having to check the current Linux IP and manually type it in on the Windows machine?

I just learned on googling windows doesn't use DNS names arrgh, but its own system called SMB that's not really an inet standard - I never knew that. I also read about creating a hosts file in windows but that's no good, because the IP address of the LInux laptop is determined dynamically after all, apparently by the bootup order of my three machines.

Just out of curiosity, howabout the other way around, can I easily make my Windows machine have a DNS name that Linux understands? For that, feel free to reply off-list or point me to a link, rather than duplicating existing., OT:ish Win info on a LInux forum. I'm not interested in Windows file sharing as such.

Fluff: What I'm actually trying to do, though you needn't know that to answer, is running Emacs for Windows with a portable Lisp-based screen reader called SPeechd-el. But as Windows doesn't have a compliant SSIP server for speech synthesis, I need to use my Linux machine, already happily running EMacs, for speaking. The Windows environment variable determining the server name to  connect to wants a DNS name, rather than an ip address, I think, and I'm trying to think of an easy way of setting it up so that it won't break when the Linux server IP changes. In a way you could think of the machine name as a symlink to whatever IP the machine happens to have. My question is still quite generic and I'm sure this is one of the most frequent Qs around. My GOogling didn't bring up anything definite so thought I'd try here. especially seeing how friendly the Ubuntu forums are and how often they crop up in Google search results anyway.

Accessibility: OT: Where Can I give accessibility feedback on the platform this forum is run on? I just found out the registration forms were not correctly labelled, an didn't respect my custom colors, either, breaking Web content accessibility guidelines and making the registration with a screen reader/magnifier rather tedious. Not good business, considering Ubuntu should be big on accessibility.

I don't like the BB code editing from the keyboard, either, thus my rather old-schoolish emoticons, but this is not the place for ranting about wanting to stil use usenet for superior keyboard efficiency and a fully textual UI. Especially since there's no Ubuntu NG to begin with: else I wouldn't be here, <grin>.

---

### Post by jimcooncat on 2008-11-06
I know I'm late in responding to your post, but maybe this will be interesting to you anyway.

You don't say what kind of network you have, so I'll guess you have a router with a windows box and a linux box plugged into it, and both are pulling ethernet addresses from the router's dhcp.

Although you can do it with some complicated dhcp and dns updating, or using an external dns nameserver and dynamic dns scripts (dyndns.org, for example) there's a much easier way.

Assign each computer a static IP and hostname, with a gateway address of your router. On my gutsy machine I have to remove network-manager for the static IP to stick.

Then make entries in the hosts file for both machines.

---

