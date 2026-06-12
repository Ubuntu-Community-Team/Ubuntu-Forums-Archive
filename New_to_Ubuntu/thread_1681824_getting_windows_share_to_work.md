---
title: "getting windows share to work"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by degarb on 2011-02-04
I don't get it.  Windows Networking not working again.  I don't think anything of samba makes any sense.  Do I do passwords,  how to I just disable all things unix in the networking?  Do I allow unix. What , what, what?!!???  Do I need to install ntfs for samba?

TEST the thing and put out a distro that works!  I never have problems networking 2 xp machines, only ubuntu distros to xp.   I am clueless what to try.  I have read 20 hours tried 20 hours of stuff, and after 14 hours on one machine got it working, after 6 got working on other machine,  But third machine, STILL don't know what I did to get it working, and no IDEA where to start--turning switches in samba config to get a freakin simple thing that should be as easy as connecting a cord, to work.

---

### Post by fabricator4 on 2011-02-05
> **degarb said:**
> --turning switches in samba config to get a freakin simple thing that should be as easy as connecting a cord, to work.

I just did a fresh new install of 10.04 LTS (upgraded my hardware) and as expected, When I click on "Network" in places I can see my Windows network, and can access and read/write to any of the Windows shares.  When I access a share it gets mounted and is accessible from the Desktop.

This part of Samba works perfectly, with no configuration.  If you limit your operations to this mode then you need never bother with any configuration.  This works because Windows will give the shares to anyone who knows the workgroup name.  Since this is broadcast across the network, it might include anyone who hacks your WEP key or firewall.

Linux takes a different approach, mainly because it won't give free access to drives or any other resources.  This has to be managed through Samba shares, so yes, it takes a little more effort to configure.

I've always found [this]("http://www.linux.com/learn/tutorials/305771-quick-and-dirty-samba-setup") to be helpful.

Chris

---

