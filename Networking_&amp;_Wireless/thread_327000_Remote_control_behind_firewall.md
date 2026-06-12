---
title: "Remote control behind firewall"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by bamarob on 2006-12-28
I have a small, mixed network at home that includes a Westell DSL modem, Linksys WRT54G router, 2 Windows XP Home PCs, 1 Ubuntu 6.06 laptop, and my Ubuntu 6.10/Windows XP Pro dual-boot laptop.  My wife has become quite proficient using Ubuntu, but occasionally needs some help/guidance.  I'd love to be able to shadow her session (via VNC or other tool) from the office.  So, I'm interested in setting things up to allow this.  Now, I can easily get VNC working WITHIN my LAN, but being able to access it from work is the issue.  I'm open to suggestions on the best/easiest/secure way to set this up.  I suppose I could set up VPN on the Linksys WRT54G, but I have no idea how to do this, nor do I know if this is the best route to take.  The Ubuntu 6.06 laptop is connected to the Linksys via CAT5 cable and gets it's IP address via DHCP.  If I manually set the IP address, could I configure a tunnel through the firewall to allow VNC access to this laptop?  Would this be a huge security hole?

Any suggestions or pointers to relevant articles would be much appreciated.

Thanks,

Robert Aldridge

---

### Post by dbott67 on 2006-12-28
The easiest way is to setup reverse VNC on her computer (see my signature for the HOWTO).  This is dependent on you being able to forward ports on your work firewall to your desktop computer (so that you can receive the VNC session).

Just like normal VNC, this method only encrypts the password, not the session.  If you're looking at something more secure, we could setup VNC over SSH, but that would require setting up port-forwarding on your router (port 22 for SSH).  She would also need a static IP (or reserved/static DHCP address).

Let me know which option is best for you and I can help you through it.

-Dave

---

