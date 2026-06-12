---
title: "Thunderbird localhost server not working on Ubuntu (ok on Windows)"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by AlterMind on 2009-08-08
Hello,

_Summary_: ***Thunderbird can't connect to localhost server for Yahoo Webmail mails when on Ubuntu 9.0.4, while that same TB 2.0.0.22 config works fine with Windows 7.***
_Question_: Which ports need to be opened on Ubuntu to allow TB's YahooWeb localhost server to work ?

I have set-up a computer with dual boot: either Windows 7, or Ubuntu 9.04. They both share the same NTFS data disk, where the Thunderbird mail profile resides, so that I can access a **single** mail environment from **both** worlds.  First of all, **congratulations** to all Thunderbird development folks, as it was so easy to migrate my TB config from Win XP to Vista and now to Win 7 !

From the **Win 7** partition I can access/fetch mails from all my accounts, which includes hotmail (via pop3.live.com), yahoo (two accounts via **pop on localhost:110**), gmail (via pop.gmail.com) and my Orange (ISP) pop account. 
However, on the **Ubuntu 9.04** partition I can only fetch mails from my pop accounts (hotmail, gmail,orange), while I get an immediate "**The localhost server has rejected the connection**" (this is translated from French) error for the Yahoo accounts.
I use WebMail Yahoo v1.4.4 (configured on "BETA" web mode) and WebMail 1.3.3b4

Looking at the **WebMail 1.3.3b4** configuration shows in the Server tab that its **POP server isn't working/started (shows a [COLOR=#ff0000]red ball[/COLOR])** (does this explain why it can't speak with the Yahoo WebMail component ?). Clicking on the green '+' button doesn't fire it off either. On the bottom of the dialogue box, there is a msg saying that "**ports below 1024 might be blocked by the system**". Could this interfere with the POP server being started ?
Finally, if this *actually is* the source of the problem and as I'm quite new with Ubuntu, could you advise me on **which ports** to (securely) open on Ubuntu and **how** ?
Please be reminded that under Windows 7 the same Thunderbird config ***does*** work (the Yahoo mails are actually fetched, and the localhost server shows a **[COLOR=#008000]green ball[/COLOR]**), so this would indeed point at an OS setting specificity/difference ?

Thank you for your patience and helping support.

---

### Post by bui89 on 2009-08-28
I had the same problem here.
Try to launch thunderbird with root, then everything works just fine
Type sudo thunderbird in terminal, thats all

---

### Post by LewRockwell on 2009-08-28
> **bui89 said:**
> I had the same problem here.
Try to launch thunderbird with root, then everything works just fine
Type sudo thunderbird in terminal, thats all

perhaps that is a temporary-fix to the trouble-call issue, however there is a reason that programs are given their NORMAL permissions as opposed to super-user.

.

---

