---
title: "Wireless issues on Dell XPS 13 developer edition"
date: 2015-03-21
forum: Networking &amp; Wireless
---

### Post by andrew_waite2 on 2015-03-21
Hi,

I've been struggling with flaky wifi for a while now, but finally decided to see if anyone can help.

I've got a Dell XPS 13 developer edition (9333).  It has an Intel wifi card.  It came pre-loaded with Ubuntu 12.04 LTS and it worked perfectly, but by then 14.04 LTS was already out.  I upgraded to 14.04 (and now I'm on 14.10) and i get some strange behaviour from the wifi in these versions.


[LIST]
[*]Often (about 1 in 5 times) the laptop will refuse to connect to wifi after resuming from suspend.  I have multiple home networks.  Sometimes changing network will help.  Sometimes deleting the network and re-adding it will help.  Most of the time, I need to restart the computer several times before it will connect again.
[*]5 GHz networks worked in 12.04 and 14.04, but now don't work in 14.10.  It will connect and work for a a few seconds, but then no traffic gets through despite being connected.
[*]Once connected to a 2.4 Ghz network, it's fine and everything is super reliable.
[/LIST]

After I've had wifi issues, my laptop will display a "crash" message on start-up.  I looked in /var/crash and found the following files:


[LIST]
[*]_usr_bin_ibus-daemon.1000.crash
[*]_usr_bin_nm-applet.1000.crash
[*]_usr_lib_ibus_ibus-ui-gtk3.1000.crash
[*]susres.2015-03-19_23:29:45.339234.crash
[/LIST]

I'm not sure if these are related, or how to use them to help fix the error.  I Googled for their names and found nm-applet to be network manager applet so I'm guessing they are related?


Any help greatfully appreciated :)

Thanks,
Andrew

---

