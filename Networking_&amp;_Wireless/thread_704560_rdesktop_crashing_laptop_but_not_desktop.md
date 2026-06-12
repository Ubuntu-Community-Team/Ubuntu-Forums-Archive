---
title: "rdesktop crashing laptop but not desktop"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by dumbkiwi on 2008-02-22
Hi,

I have a strange problem with rdesktop and it's various front ends (tsclient, gnome-rdp and krdc).  

I am trying to connect to my work's terminal server running windows server 2003.  I connect using the cisco vpn client.  When I start rdesktop, I get a terminal server window and login dialog, and can login.  The windows desktop then starts painting, but part way through, the kernel panics and I'm left with a dead laptop, and flashing numlock/capslock lights.  I tried with tsclient, and I got further, but once i started opening applications in the remote session, it did the same.  I've tried several different screen sizes, and colour depths, and have tried with and without compiz running.  I've checked the kernel logs (/var/log/messages) and it dies without logging anything.  The last entry before the crash relates to loading the cisco vpn module.

The strange thing is that my desktop computer with a very similar setup can connect to the terminal server just fine, no problems at all.

Both laptop and desktop run kubuntu-gutsy.

Anyone got any ideas on what the issue might be on the laptop?

---

