---
title: "Absurd Samba situation: Fiesty server, WinXP can access it, Gutsy can't?!?"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by Jim March on 2007-11-03
Yeah, read that title again.  I have a server up and running in Feisty.  Works great, SMB shares created, seven WinXP boxes happily using it.  All on the same network, DHCP access behind a dedicated firewall/router.

The one Gutsy machine on the 'net (also behind the firewall, DHCP) cannot see the Fiesty server.

WTF?

Like help?

I've been RTFMing for hours.  With no fixed IP addresses a lot of the "Linux to Linux" tools fail.  But I should still be able to see the SMB shares, right!?

What I need here is a fixed mount point to a single share.  I figure once I have something like /media/share/appname or whatever I should be able to link to that mountpoint from within VirtualBox and an XP virtual machine - the end goal of this excercise.

And yes, I've got networking established in Virtualbox 1.5.2 ("full edition" not "OSE") but only by way of NAT, not a "straight shot to the host Ethernet hardware".  Therefore the Virtual Machine XP can't browse the network (and find the server) either.

At one point while trying to make that work I followed directions here:

[http://www.virtualbox.org/wiki/Advanced_Networking_Linux](http://www.virtualbox.org/wiki/Advanced_Networking_Linux)

They're kinda crude as instructions go.  For a little while something on this page, not sure what, allowed Ubuntu to "network browse" all the way through "Windows Network">"MSHOME">myservername but clicking on the server gave an access error, no prompt for a password.

I call this situation "absurd" because you'd think Ubuntu would have an easier time getting into an Ubuntu box than friggin' WinXP would, right?

Any clue appreciated...'cuz I'm just stumped.  Pretty much every other Samba-related thread covers Windows failing to get into an Ubuntu-based share, and since the SEARCH ENGINE IS BROKEN around here I've got to yell for help.

Thanks,

Jim

---

### Post by ghandi69_ on 2007-11-03
Ok man, not sure immediately what your issue is, but I would start by doing the following things.

Make sure smbfs (I think?) is installed on your gutsy machine.
Make sure that the gutsy machine is part of the correct workgroup (MSHOME in your case)
Post your smb.conf file from the fiesty server so we can look and possibly find something.

Know that it can be done, I just recently setup a gutsy server (last night actually) that has 4 XP machines and 2 ubuntu machines browsing it with no problem.

Hopefully we can get you through this.

---

### Post by suchawato on 2007-11-03
I may be going out on a limb here,
but this may have something to do with this bug:
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/134712]("https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/134712")
Some sort of gparted mounting issue that's basically making a lot of external drives particularly usb drives not mount properly when they worked fine in Fiesty.
I don't know itf this is directly related to your issue, but it may be a clue.

---

### Post by Jim March on 2007-11-03
Ghandi's message actually gave a clue.  Once I paid more attention to smb.conf I realized there were two per machine, and didn't match.  Sigh.  A bit of hand-editing and all was well.

Hey, found a bonus: make a folder under /media for each share, hard-link it in fstab, and then in VirtualBox share it with the virtual machine.  Once in XP, link drive letter to "local" Linux share (actually /media/sharename) and you get full networking in XP.

Once it's set up this way it's actually safer for XP than if you linked XP straight to the Ethernet card and let it do it's own networking.  In the setup I have with VirtualBox feeding a NAT connection to XP, Ubuntu is acting as a "super-firewall" around XP protecting it better than Snortin' Utilities ever could.

---

### Post by suchawato on 2007-11-04
**Update:**
Apparently its not the gparted thing, because apparently that was fixed in Gutsy. And should no longer be an issue.

---

