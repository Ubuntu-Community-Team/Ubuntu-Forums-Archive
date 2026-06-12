---
title: "Problem with Terminal Server Client after Upgrade to 7.04 (Fiesty Fawn)"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by RangerRik1 on 2007-04-25
I'm new to Linux/Ubuntu but I'm an experienced computer user.

Several weeks ago I installed ubuntu without difficulty. I got my dell latitude notebook to dual boot (Ubuntu and XP) and ubuntu has been running amazingly well! I even got wireless working (WEP on my local WLAN) in Ubuntu. (It was real slow until I deselected the wired interface ... looks like I can't have both interfaces active at once) - By the way, any plans of a better wireless client with site survey / multiple networks capability?

A necessary part of my work includes the ability to connect to a windows desktop host running XP Pro and Remote Desktop. It had been working great for a couple of weeks. 

...Then I just upgraded to 7.04 (Fiesty Fawn). Since installing fiesty, I'm getting occassional disconnects when running the terminal server client. When I get kicked off the host, I get the following error message: an error has occurred. X error of failed request: bad atom (invalid atom parameter) - major opcode of failed request: 23 (X_GetSelectionOwner) - AtomID in Failed Request: 0x0 - the serial number of the failed request and output stream VARY each time, but are always the same. 

NOTE: I also get the error EVERY TIME I disconnect from the Host.

Anyone have any suggestions?

Thanks in Advance! I'm excited to be onboard with this OS!!!

--Rick

---

### Post by deadlines on 2007-04-25
My recommendation is, use gnome-rdp.  I use it every day and it basically works without a hitch, it also supports copying & pasting from remote clients to your local session, which terminal server does not (unless something has changed since I last used it).  Gnome-rdp is available through the official Ubuntu repos so it's cake to install too.

The only bug I've noticed with gnome-rdp is that on occasion when pasting data copied from a remote session into a local app, it can sometimes cause that appliation to hang for a couple seconds.   Specifically I notice this behavior pasting URLs into Opera that I copied from a remote host,  but I don't think I've run into it with any other apps so it could just be an Opera issue.  Frankly having the ability to copy & paste from the remote clients to my local machine more than makes up for any small annoyances I've had with it.

Cheers

P.S. If you try out gnome-rdp and continue to experience dropped RDP sessions, this may be a connection related issue.

---

### Post by RangerRik1 on 2007-04-26
Okay. I'll try that! Thanks for the advice!

--Rick

---

### Post by RangerRik1 on 2007-04-27
Just a note--> The Gnome RDP does the same thing! 

I ran some ping tests and didn't have any lost packets! I'm not sure what could be wrong with my connection... I'll guess the next thing I'll try is the wired interface and see if the error continues....

I wasn't getting this error before Feisty, I truly believe the upgrade to 7.04 has introduced this problem...

--Rick

---

### Post by deadlines on 2007-04-27
Ouch! Yeah, that sounds like something else is going on.  Would be interested to hear what happens when you try it on your wired nic.

---

### Post by eugenevdm on 2008-05-18
Thank you for your advice to use gnome-rdp. I have been sitting with the error:

X Error of failed request: BadAtom (invalid Atom parameter)
Major opcode of failed request: 23 (X_GetSelectionOwner)
Atom id in failed request: 0x0
Serial number of failed request: 4940
Current serial number in output stream: 4908

for six months until I saw this advice. No I have one less issue to worry about!

Question: Does gnome-rdp also do bitmap caching?

---

### Post by gpw797 on 2008-06-15
It was working for me in Heron.. then I started having this problems as well, gnome-rdp doesn't work either.

---

### Post by vuul on 2008-06-19
I used to get the BadAtom error too.
When I switched the connection protocol to RDPv5 on Terminal Server Client the problem went away.
Can somebody else try this to see if it will fix the error?
I am running Hardy.

---

