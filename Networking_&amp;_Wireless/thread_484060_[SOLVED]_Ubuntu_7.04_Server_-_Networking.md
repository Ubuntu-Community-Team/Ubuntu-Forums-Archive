---
title: "[SOLVED] Ubuntu 7.04 Server - Networking"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by kambrik on 2007-06-25
I have a weird situation on my hands that i'm not for sure how to fix.
I currently converted an E-machine that was running MS Windows Home Edition to Ubuntu 7.04, after doing so and installing samba, open ssh etc... i noticed that i was losing connection to the server via ssh every 2-3 hours, i would log into the server via console and notice that it had gotten a new ip.  Prior to putting linux on this machine, i noticed that internet would run really weird at times, but i did not put too much thought into it since it was still functing with no errors or significant problems in windows.  So i decided to disable the on-board ethernet controller and put in a pci network card, trying to see if it was infact the network card causing the loss of connection to the router.  Once i disabled the on-board card and installed the new card i was having a hell of a time getting the new card to load.  Since i'm new to linux i just thought i was missing some flag when using the modprobe.  After many hours of searching for a similar problem somewhere else i came across a post about checking your /etc/network/interfaces file and to make sure that auto eth0 etc was in there.  I checked that file and it was in fact in there.  So i was back to trying other modules (no luck) searching google (no luck), so at that point i had enough i was going to install ubuntu again and start over. Then a thought poped into my head. "HMMMM i wonder if linux for some reason is still holding that eth0 for the onboard ethernet controller, even though it is disabled in the BIOS).  So my next step was to add:
auto eth1 etc... to the /etc/network/interface file.  And guess what boom instant working.

So my question is why is this doing it like this.  Since i disabled the on-board one in the BIOS should not the new ethernet card be eth0?

How do i fix it so that it is eth0?

Thanx, Kambrik

---

### Post by kambrik on 2007-06-29
No one else has this problem?

---

### Post by t4thfavor on 2007-06-29
I had some funky issue where my onboard eth would be eth0 sometimes and my pci one eth1 while other times it would be reversed. I think it either fixed itself, or I just stopped noticing it.
Why does it matter which ethernet is which as long as it doesn't change, you should be all right.

---

