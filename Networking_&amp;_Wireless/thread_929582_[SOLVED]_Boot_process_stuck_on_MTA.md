---
title: "[SOLVED] Boot process stuck on MTA"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Orange_and_Green on 2008-09-25
Hello everyone. 

This is not really a "problem" anymore as I managed to solve this, but I struggled to find any advice fitting my case on the internet so I thought I'd share the experience. I hope it's OK.

This morning I switched on my laptop and everything seemed normal until the progress bar of the splash screen loaded up to about 80-85%, then hung there for a while, then dropped to text mode. The last two lines of the output were reading:

Starting cups                  [OK]
Starting MTA

And it would just sit there. I panicked, hard-resetted, ran recovery mode a couple of times, always with the same outcome. I then discovered that the boot process wasn't really hung, but would just sit on that MTA line for about 2 minutes, then continued as normal and the computer would take me to the login screen.

I found some advice on various forums (booting with "profile" option, cleaning up /etc/hosts, uninstalling exim altogether), but nothing helped.

I then remembered that I had set a static IP and an extra DNS server for temporarily connecting to a network. I switched the network settings back to DHCP (roaming mode) and deleted the foreign DNS and everything came back to normal :)(happy)

Bottom line, if you get stuck with a "Starting MTA" message:
1)Don't panic. The computer is bound to boot up, just be patient.
2)If you have set up any unusual static IP addresses / DNS servers, clean them up and try again.

Have a nice day everyone:KS

---

