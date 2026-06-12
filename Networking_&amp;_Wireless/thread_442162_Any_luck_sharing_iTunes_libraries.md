---
title: "Any luck sharing iTunes libraries?"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by king_arthur on 2007-05-13
Hi there everybody,

I was just wondering if this is a problem with my setup or it is common to somebody else.

I have installed Ubuntu Feisty on a PC and (almost) everything works like a charm.

I can connect via my WiFi home LAN to my iMac and share files, both directions no prob however, sharing music seems to be more difficult.
I can see the Ubuntu BOX running Banshee and play the shared songs (hence the avahi daemon works) from the Mac but reversing the process doesn't work.
I can see the networked mac running as a Samba share but cannot see the music libraries broadcasted by iTunes 7.02 in sharing mode.

Is this something deliberately crippled by Apple?
Are there any workarounds to it?

Or do I have to check something else in my set-up on either end of the network?

I have tried switching to RithmBox and Amarok but to no effect.

Thanks in advance for any hint.

/P

---

### Post by kmslinux on 2007-05-13
Try using gtkpod. If you want the AAC support, your command would be 'apt-get install gtkpod-aac'

---

### Post by king_arthur on 2007-05-13
Thank you for the swift reply however, I can't see how this can be done with gtkipod. :confused:

Sorry for asking but are you sure there is a "sharing" feature available?
I have been browsing the preferences but can't find any way to enable this, neither a suitable plugin.

It works fine with iPod which is what it was designed for, but no sign of networking.

/P

---

### Post by tgalati4 on 2007-05-13
Apple changed their sharing protocol in iTunes 7.  (Insert appropriate language.)  The hashing algorithm used has not been reverse-engineered.  

So what are your options?  Move back to iTunes 6.whatever.  This means wiping your database and starting again.

Grab a used, cheap shuffle and copy your tracks in groups of 1GB.  Move the shuffle to your Ubuntu machine and import them using gtkpod.  This is tedious as well, but at least your music will be free to share with other Linux machines on your network.

You are not alone in your frustration.

---

