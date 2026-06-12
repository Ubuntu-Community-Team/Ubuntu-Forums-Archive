---
title: "CUPS remote printing problem..."
date: 2005-11-19
forum: Networking &amp; Wireless
---

### Post by piffy on 2005-11-19
** If this is in the wrong forum, please let me know. It crosses a few boundaries and I believe its a network related setup problem **

I sure hope someone can lend a hand on this. I've been banging my head against the wall for ages trying to get this figured out.

My primary workstation has an HP DeskJet 930C connected to it over USB. I have KDE all setup and able to print to it using CUPS. No problems there. I have enabled browsing and so I can connect to [http://localhost:631](http://localhost:631) without a problem.

Now, on another machine I can't connect to http://<printServerIP>:631. When I do an NMAP of the print server I get this:

PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

However, when I do an NMAP of the print server FROM the print server I get this:

PORT      STATE SERVICE
22/tcp    open  ssh
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
783/tcp   open  hp-alarm-mgr
32770/tcp open  sometimes-rpc3

What could be causing port 631 to not broadcast across the network?

--piffy

---

### Post by piffy on 2005-11-19
[QUOTE=piffy]** If this is in the wrong forum, please let me know. It crosses a few boundaries and I believe its a network related setup problem **

I sure hope someone can lend a hand on this. I've been banging my head against the wall for ages trying to get this figured out.

My primary workstation has an HP DeskJet 930C connected to it over USB. I have KDE all setup and able to print to it using CUPS. No problems there. I have enabled browsing and so I can connect to [http://localhost:631](http://localhost:631) without a problem.

Now, on another machine I can't connect to http://<printServerIP>:631. When I do an NMAP of the print server I get this:

PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

However, when I do an NMAP of the print server FROM the print server I get this:

PORT      STATE SERVICE
22/tcp    open  ssh
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
783/tcp   open  hp-alarm-mgr
32770/tcp open  sometimes-rpc3

What could be causing port 631 to not broadcast across the network?

--piffy[/QUOTE]
I finally got the problem fixed. It was a configuration problem with the allow/deny statements in a few different places. Started over, took it from the top and just thought my way through it.

---

