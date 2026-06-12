---
title: "4965 on T61P - modprobe why?"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by poorbadger on 2007-11-03
Running the live CD (7.10 i386) to see if I can get graphics, memory, video working before I fully commit (and I definitely want to - the T61P was bought with that specifically in mind).

On startup and after going into network manager to make the appropriate changes to connect to my AP (WPA encryption) - no good, no connection.

After running "sudo modprobe -r iwl4965" and then "sudo modprobe iwl4965" I can see access points through "iwlist wlan0 scan" and am able to pull up the website of my choosing.

Just running the 2nd command "modprobe iwl4965" doesn't seem to give me the same results - I have to first remove and then readd the module to kernel.

Why might that be?  I'm excited to have it working but as a new user to *nix I'd like to understand what's going on.

And provided I had Ubuntu installed how would I automate this (the modprobe cmds)?  Is it just a one time thing or does it go in some kind of startup/config file - and, if so, which & where?

Oh, WiFi beacon indicator on the laptop isn't lit up ever (indicating the WiFi radio is on) but I can live with that for now - just thought I'd mention it.

Thanks!!!

---

