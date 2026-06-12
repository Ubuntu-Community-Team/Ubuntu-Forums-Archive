---
title: "Network printing frustration."
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by squashpup on 2008-09-03
Wow.  Been working on this for two days.  

I have a bank of 5 computers that I maintain at my school for student use, plus a 6th that I use myself.  All run Xubuntu.  

Computer 0 is mine.  It is connected to a Deskjet 995C.  I can print locally without issue.  

Computer 1, 2, 3, 4, and 5 are all behind the same router. Computer 5 is connected to a Lexmark Optra printer.  Computer 5 prints fine locally.

I've been working for two days trying to get the remainging computers to print to either printer through the network. I've edited cups config files, I've changed iptables rules, I've installed and uninstalled, started and restarted, added and removed printers, etc.  I can't get any combination that results in a print.

The worst of it...I loaded a live CD of Mepis 6.5 on computer number 5.  It boots and immediately recognizes and automatically installs the Deskjet 995C that it finds through the network on computer 0!  Why can't it be this easy in Xubuntu?  i took a few minutes and locally installed the Optra that was connected to Computer 5.  Went to Computer 3, put the IPP address in, and it printed without issue!  

Why is something that is so conveniently done automagically with Mepis seemingly impossible with Xubuntu?  

I'm not new at this, BTW...been using Linux since '03 and managed to get those same computers to join a Windows domain here, which was WAY easier than this.  Just can't seem to get the seemingly simple step of printing out of the way, and I know it shouldn't be this hard!

Any suggestions about where to start or what to try?  I'm at my wits end here.

---

### Post by Iowan on 2008-09-03
I just got Xubuntu loaded on one of my machines.  Just started looking at printer configuration - seems more complicated than the Gutsy (Ubuntu) setup.  Gutsy (Ubuntu) was almost easy - only trick was using IP Address instead of printer name. If (When?) I find a quick/easy solution, I'll let you know.

---

### Post by squashpup on 2008-09-03
Experimented a little more.  Running Windows 2000 in a virtual machine, I entered the IPP address of computer 5 that's running Mepis.  Windows immediately detected that printer, let me install a driver for it, and printed to it.

What's going on?  Anyone have any ideas?

---

