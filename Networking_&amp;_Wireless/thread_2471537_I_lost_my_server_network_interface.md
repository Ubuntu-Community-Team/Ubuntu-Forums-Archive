---
title: "I lost my server network interface"
date: 2022-02-02
forum: Networking &amp; Wireless
---

### Post by fab2022 on 2022-02-02
I am a young ICT SYSTEM ADMINISTRATOR and very new to Ubuntu. I install Ubuntu server 20.04 LTS on one of our dell power edges R710 server, after installing and configuring the GUI on the server and some other like, cockpit, openssh, mysql, I notice that the server network interface was disable, which is stopping me from going forward with the configuration, But it was working before. Can anyone help me with the process to enable it?
Enable Ginger*Cannot connect to Ginger* Check your internet connection
 or reload the browserDisable in this text fieldRephraseRephrase current sentenceEdit in Ginger×

---

### Post by The Cog on 2022-02-02
First, use the command **[FONT=Courier New]ip address[/FONT]** to show the interface addresses. Check that the interface says LOWER_UP meaning that the cable is plugged in and detected, and also check that the interface has an IP address. If it doesn't say LOWER_UP, use the command **[FONT=Courier New]sudo lspci -v[/FONT]** and look to see if the interface has a driver in use.
Where to go from there depends on the results of these checks.

---

