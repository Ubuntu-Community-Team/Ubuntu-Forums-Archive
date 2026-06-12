---
title: "Network does not &quot;see&quot; new computer"
date: 2014-05-25
forum: Networking &amp; Wireless
---

### Post by Jacdeb6009 on 2014-05-25
Hi there,

I have been running Ubuntu for several years now and have never really had a problem getting a small home network working.

In the past I had a desktop running Ubuntu, another one (headless) running Fedora and two laptops, one running Ubuntu (dual boot with XP) and one running Windows 7.  

All of these were set up with "shares" to allow for files / folders to be shared, synchronised and so on and this always worked well.

Recently I could (eventually) get rid of the Windows machines and these were replaced with a new notebook computer on which I installed 14.04.  Despite a few initial minor issues, the machine is running well and is quite stable.

It connects to the internet (ethernet and wireless) without problems.  The problem is with the newtork.

It can see the Ubuntu desktop machine and the Vortexbox (headless Fedora music streamer) and it can access the shared folders, but the notebook itself is not visible on the network, and its shared drive does not show up.

The screenshot below shows what you can see when you click on networks in Nautilus (from either the notebook or the desktop.

[ATTACH=CONFIG]253430[/ATTACH]

On the notebook, clicking on "Windows Network" display an icon "WORKGROUP" and clicking on this causes Nautilus to shut down (or crash?).  Doing the same thing on the desktop displays a screen showing the machines "gandalf-desktop" and "votexbox".  The machine (?) "smb-server-" is only visible on the "Browse Network" screen.

I am not experienced with networking and in fact, until I set up the Vortexbox, had never managed to get a network running at home.  Since doing this (about 2 years ago) I have had this small network running without any problems.  Until now.

It is not a "deal breaker" as I can access the desktop and the vortexbox from the notebook (just not the other way around), and the desktop can still access the vortexbox.  This just means that when I update things on the desktop, I have to copy the updated files from the desktop using the notebook.

I wonder whether this is an issue with 14.04 and if installing 12.04 will resolve the problem (don't REALLY want to do that, I also can't believe that something apparently this basic would not be working).

Any help would be appreciated.

Cheers,

---

### Post by sudodus on 2014-05-25
- Can you see the computer with ping?

- Did you install a server in the new computer? Otherwise you cannot connect to it, only from it to another computer with a server program running.

A samba server is good in a network with Windows.

- Is there a firewall, that is blocking the connection?

-o-

I prefer the OpenSSH Server and to do the networking with SSH

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

There are tools (for example WinSCP and Filezilla) to connect from Windows to an SSH server.

-o-

I think that it is enough to have one server if it is your network at home. Keep the server running and connect to it from the other computers.

---

