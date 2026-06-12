---
title: "Only bring up wireless if regular ethernet is down"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by jcorbett on 2007-03-25
This doesn't seem to be a common question, I hope I can explain it well.  I want to be able to have my Ubuntu system automatically bring up my wireless, but only if the regular wired Ethernet's link is down.  And I want to have the wireless go back down if the wired link comes up.  I am constantly switching in my home between wireless and wired interfaces, and I don't like it.  I have plenty of scripting skills, but honestly I don't know where to look.  This seems to tie into both network startup, and something like udev (ok maybe not udev, but some type of event manager from the kernel).  Anyone have any ideas on how this could be accomplished?

Jason Corbett

---

### Post by kidders on 2007-03-25
Hi there,

> **jcorbett said:**
> This seems to tie into both network startup, and something like udev (ok maybe not udev, but some type of event manager from the kernel).I'm doubtful about that. You *could* maybe throw a script into /etc/network/if-up.d, etc.

The trouble is that blindly making a switch like that would interrupt active connections and confuse running applications. I've never actually *tried* what you're asking, so I may be being over-cautious, but it seems to me that swiping an active network connection out from under certain apps could have very nasty side-effects ... say you had an NFS/Samba share open, for instance. **Edit:** Ordinarily, if Samba, for example, has an open connection between your wireless interface and a server, that connection will _not_ happily tolerate the IP address change that comes with a change of network interface. Instead, it will just sit there and do nothing until it gets bored of timing out. The effect that would have on running apps that were using the share would be entirely dependent on how well-prepared they were for a filesystem resource to vanish without warning. :-?

Here's what _I'd_ think about doing:

[LIST]
[*]Using the various directories in /etc/network to spawn a script in the event your wired-up connection goes up or down.
[*]If it's about to come up, I would wait for certain active connections to terminate... outgoing HTTP for example.
[*]Then, I would maybe kill certain services (like Samba) and repeatedly try to dismount remote filesystems, until I succeeded.
[*]Then, I would take down the wireless interface, leaving my computer without any network connection for a moment, before bringing the wired interface up.
[/LIST]

The trouble is that cleaning up the mess when the reverse happens (ie your wired connection suddenly vanishes) could be nasty. :-(

I use OSX a lot, and Apple seems to have managed to keep changeovers between network interfaces reasonably clean. Finder (Apple's filesystem explorer) does get peeved when you do certain combinations of things though, and becomes unresponsive. All the same, perhaps it might be worth examining what tricks they've used.

Something else worth considering might be to create some sort of reasonably unobtrusive desktop notification that would let you cancel a network interface switch. I'm not very good with Gnome, but I do know that things like that are pretty straightforward in the KDE world. Say for instance you happened to be doing a system update, and your wireless connection became available for a moment. It would be nice to (a) wait and see if it *stays* available long enough to warrant a switchover, and (b) let the system update do its downloading undisturbed for a few moments, rather than killing the active TCP connection.

Anyhow, do you suppose it would be totally daft to have a script monitor the output of "netstat" for a few seconds & throw a notification on your desktop, before restarting local services, dismounting & remounting remote filesystems, and swapping network interface?

---

### Post by chili555 on 2007-03-25
Isn't this what NetworkManager is supposed to do? [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)
> The computer should use the wired network connection when its plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them; they should simply see uninterrupted network connectivity.You can find it and it's dependencies, on Synaptic.

---

### Post by kidders on 2007-03-25
Hmm... yeah. :-)

---

### Post by jcorbett on 2007-03-26
> **chili555 said:**
> Isn't this what NetworkManager is supposed to do? [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)
You can find it and it's dependencies, on Synaptic.


I have fiesty and so Network Manager, I'll try it.

---

### Post by jcorbett on 2007-03-26
Well it doesn't automatically use the Ethernet when it gets plugged in, but it is much easier to switch, thanks for the suggestion.

---

