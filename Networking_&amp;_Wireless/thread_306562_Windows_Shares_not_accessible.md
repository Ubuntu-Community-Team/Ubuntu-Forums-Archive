---
title: "Windows Shares not accessible"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by HereInOz on 2006-11-25
I had a problem with an inability to access my Samba share, which is on my Ubuntu machine, from the Windows machines on the network.

So I went in to Synaptic and uninstalled anything relating to Samba that I could see and then re-installed it (I had already tried a "Mark for re-installation" but without success.)

During the uninstall process, I noticed that a list of other programs would also be uninstalled, and like an idiot, I didn't take note of what they were - just blithley uninstalled and trusted in providence.  Will I never learn.  One of the programs was gnome-cups-manager, that I can remember,but the others are gone forever.

With the re-installation, I got the Samba share accessible from the Windows network again, but I have now lost the ability to access the Windows shares from my Ubuntu machine.  Clearly I have removed something that is needed to do that, and it has not been put back, and some idiot like me cannot remember what it was.

When I try to set up a connection to a windows share, and then connect to it, I get the message smb://davenport%3Braenalan@192.168.1.2/raenalan is not a valid location.

Can anyone assist in giving me a list of the programs I need to have installed to access a Windows share and hopefully I can get this up and running again.

Hope someone can help.

---

### Post by HereInOz on 2006-11-27
Just in case anyone has this same problem, I reinstalled ubuntu-desktop which also re-installed libgnomevfs2-extra, and that solved the problem of not being able to access the Windows shares.

Looks like it was libgnomevfs2-extra which was needed to allow that to happen.

Cheers,

Alan

---

