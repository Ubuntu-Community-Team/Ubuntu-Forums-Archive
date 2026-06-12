---
title: "Display driver issue (S3 Unichrome Pro)"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by afbengochea on 2009-01-27
Hi guys, I just finished installing Ubuntu 8.10 and seem to have everything working except my display. Half of my desktop seems to be sitting outside the screen. Im not too familiar with the operating system but figured Id install it a play with it a little to see if I like it. I figured out that to see what video card Im working with Im supposed to type " sudo lshw -c display" in the terminal/command program. When I did, the information displayed was this:

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: latency=64 mingnt=2

Now, I dont know how to find the correct driver, nor how to install it. Thats where Im hoping someone can guide me. Thanks

---

### Post by anewguy on 2009-01-27
You can go to OpenChrome for a driver, but be forwarned - support for this igp is limited.  I had that in a Gateway laptop I had a few years ago, and had a heck of a time with it.  Never could get desktop effects working as the processor didn't support everything needed.

Dave :)

---

