---
title: "[SOLVED] Network printing via Windows"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by ezramorris on 2008-01-23
Hi,
I'm trying to print over a wired network connection to an HP Deskjet 3940, connected to a Windows XP computer.

I got it to work by plugging the printer directly into the Ubuntu laptop, and following the printing wizard.

However, I have not been able to set it up over the network connection. I have tried 2 different methods:

- Adding the printer as a Samba printer - when printing, on the Ubuntu machine, it gave "spooling" for a period of time, then on the XP computer, it sat as "printing", but all it did was whirred and printed nothing. I tried cancelling this, but the only way to get rid of it was to unplug the printer and plug it in again.

- Adding the printer as an LPD printer. I enabled "printing services for Unix" on the XP computer, and added the printer. This gave the error "Error - Printing" in Windows after it had cleared from Ubuntu.

Any ideas how I can get this to work?

Thanks in advance.

---

### Post by linuxwizard on 2008-01-23
See if these will help

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

---

### Post by ezramorris on 2008-02-01
> **linuxwizard said:**
> See if these will help

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

Hello.
Thank you for your reply. The 2nd link solved my problem. I disabled bidirectional support, and the problem was solved.

Sorry I haven't repiled sooner, but I haven't had a chance to try it.

Thanks again.

---

### Post by linuxwizard on 2008-02-01
You're Welcome Glad to hear that it helped you and it is now working for you. Please mark thread SOLVED.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by ezramorris on 2008-02-03
> **linuxwizard said:**
> You're Welcome Glad to hear that it helped you and it is now working for you. Please mark thread SOLVED.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Aha. That's what I was looking for. Thanks.

---

