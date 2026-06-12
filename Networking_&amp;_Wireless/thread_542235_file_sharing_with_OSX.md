---
title: "file sharing with OSX"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by zorkerz on 2007-09-03
so there are a number of threads around about sharing files between computers. What solutions do people use? Here is my situation. I have a gutsy laptop that I jump onto my friends wireless networks with. I would like to be able to share files between our computers. I have not had any problems sharing between a windows computer or another ubuntu machine but I have had no success with macs.

What is the preferred method for this? I would like both my ubuntu laptop and another mac computer to be able to see and share each others files. I am already using samba to share with windows so I would think this would make sense for the macs also, but i will use any method that works without too much trouble.

thanks

---

### Post by kidders on 2007-09-04
Hi there,

OSX's Samba implementation works fine with Linux.

Personally, I find the limitations of the Microsoft networking protocols rather irritating though, so I like to avoid using them where neither party to a file exchange is a Windows box. For instance, it seems silly to tangle a Mac and a Linux box up in the file naming limitations of an operating system alien to both machines.

Macs can, of course, handle NFS ... but it can be a little irritating to use, in practice. AFP seems the logical choice.

What to choose is entirely up to you, really. Simply using Samba for everything would be easier, but it's always seemed preferable to me to arrange things so at least one of the computers in a client/server pair is speaking its own language.

My suggestions:

**Solution 1: **Lowest common denominator - Use Samba across the board.

**Solution 2: **Keep the clients happy - Share over Samba, AFP & NFS simultaneously, so clients can always use their native protocol.

---

### Post by zorkerz on 2007-09-04
Thank you for that reply kidders if im not mistaken my gutsy box comes able to share samba (smb) and NFS. Is this right and if so how can I share AFP? 

Im really at baseline about Mac filesharing so that added explaining is great for my understanding.
thanks

---

### Post by kidders on 2007-09-04
Hey again,

I'm not sure about Gutsy ... I haven't tried it yet ... but installing NFS, Samba or AFP support is a snap, if it's not there already. The problematic part is always the post-install configuration.

If you've never used Apple's file sharing protocols before, here are a few hints, off the top of my head...
[LIST]
[*]Unlike Windows filesharing, AFP uses "Bonjour" (aka mDNS) to advertise itself, which is quite nice. The same technique is used to advertise iTunes Libraries, and so on.
[*]It's configuration in Linux is a little overcomplicated, due primarily to a variety of advanced (but infrequently used) things it can do, many of which you can totally ignore.
[*]The Linux AFP app (called **netatalk**) has a sensible default configuration that works out of the box, so you can put off customising it for a while. Creating extra shares is a matter of adding a single line to the right file, though.
[*]If you do decide to try it, it's worth noting that a very slow (10-30 seconds) first startup, while netatalk autodetects a few things, is normal ... so don't get worried.[/LIST]There are lots of very minor up-sides to using AFP (particularly if your Mac is a laptop) that, if you ask me, add up quite quickly.

A Mac can still access shares, even if they don't show up in Finder ... but you might as well make life easy for your users. If you install an mDNS service on your Linux box, you can use it to advertise pretty much anything to your Macs (photos, browser bookmarks, etc.), as well as your AFP shares. Gnome also has some basic mDNS support, allowing you to pick up on services being offered by any Macs on your LAN.

Basically, whether to opt for Netatalk or Samba depends on how much you value Mac-specific functionality that MS protocols won't be in a position to give you. As you can probably tell, I value it greatly ... but that doesn't mean you have to!

Just as a quick aside, NFS is the odd one out of the three, really. It is purely a file sharing protcol, with no frills whatsoever. Although it offers clean, 100% native sharing between Linux & OSX boxes, it isn't anything like as pretty as Netatalk & Samba, so it might not be a good choice if your Mac users don't have a degree in networking hehe.

---

