---
title: "Ubuntu thumbdrive to clean Windows of virus ?"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by RotorRick on 2011-04-14
Ubuntu thumbdrive to clean Windows of virus/malware?


my friend has a WindowsXP computer that badly needs to be disinfected. Basically his anti-virus ran out six months ago, but he didn't tell me, and I suspect he's been on the internet with basically no or just little protection.

I have heard that you can use Ubuntu on a thumbdrive to clean Windows of virus/malware...how would I go about doing so?

I just installed a persistent Ubuntu10.10 on a large thumbdrive:
What/where do I get the programs that can clean Windows viruses from inside a Ubuntu booted straight from the USB drive?
Any tips for doing the cleaning and scanning? Or checks afterward?

After showing him Ubuntu, he may decide to try it out, he's liked what I've been able to tell him about so far! Thanks!

---

### Post by bhaverkamp on 2011-04-14
This is a great idea. I have run clamAV against window partitions from a dual-booted linux environment and found viruses but have never tried to disinfect the system. If this works it would be very useful. That said that might be a place to start (ClamAV). Are there any more mainstream AV products that run from linux?

---

### Post by earthpigg on 2011-04-14
Hi,

ClamAV is the open source anti-virus in the Ubuntu repositories. It generally doesn't get the same rave-reviews that commercial/proprietary antiviruses do (cleaning Windows viruses isn't a high priority amongst many open source volunteer programmers), but if the virus is over 6 months old it should do fine.

Boot from the Ubuntu LiveUSB on his computer, install ClamAV from the software center, and run it. :)

edit:

found this on google. [Four best $0.00 Linux Antivirus Programs]("http://www.makeuseof.com/tag/free-linux-antivirus-programs/").

---

### Post by Mark Phelps on 2011-04-14
An alternative, using a AV produce that DOES get rave reviews, is to go the Kaspersky website, download and burn their free Rescue CD.

Have your friend boot from that, and as soon as their system is up, have them do a definition update.  They can then run Kasperky AV from the CD and disinfect their system.

Also, if they don't want to pay for a Windows AV product, they should download and install Microsoft Security Essentials. It does a decent job of malware protection.

And after that, have them download and run MalwareBytes Anti-Malware.  That does a better job at finding spyware than most AV products.  And it, too, is free.

Given all the FREE AV stuff available for Windows today, there is simply no excuse for not using SOMETHING.

---

### Post by earthpigg on 2011-04-14
> **Mark Phelps said:**
> 
Given all the FREE AV stuff available for Windows today, there is simply no excuse for not using SOMETHING.

sure there is. practicing safe computing is both more effective than any antivirus suite, quicker, results in a more stable system, and does not slow your system down.

though, for those not interested in practicing safe computing: yes, AV is the route to go.

---

### Post by yetiman64 on 2011-04-14
Although you can check for infected windows files from Ubuntu using ClamAV or non OSS software like Avast4LinuxWorkstation (free to download, needs to be registered yearly, free for home use though).

I personally like the idea of using a bootale recovery cd from Kapersky (as previously mentioned) or AVG burnt to disk to fix a Windows XP install as they should also focus on any registry fixing requirements. Just removing an infected file from Ubuntu may not be enough for more complex malware infections in XP.

---

### Post by crispy_420 on 2011-04-14
BitDefender also offers a bootable LiveCD option too as does Dr Webb. I have used both Kaspersky, BitDefender and Dr Webb LiveCDs in extreme cases of an unbootable system but ultimately I have found a hands on approach in Windows can be the most effective method.

Depending on your level of dedication you could incorporate a few "free" scanners into a custom solution and build your own bootable CD.

---

### Post by wilee-nilee on 2011-04-15
This is what I'm using at this time, the windows installer is first, but if you look at the bottom of the page there is a linux installer, and look at the av included.

I would use the linux loader you avoid the wincontig defraggs.

---

### Post by mastablasta on 2011-04-15
> **earthpigg said:**
> sure there is. practicing safe computing is both more effective than any antivirus suite, quicker, results in a more stable system, and does not slow your system down.
 
though, for those not interested in practicing safe computing: yes, AV is the route to go.
 
 
what safe computing? any page (even trusted ones) can have malware on them. it can be put there by someone with bad intents.
 
in windows you need AV and a firewall. and then all is fine. You can get both of them for free (descent ones-Avast antivirus, Avira antivirus, Comodo Firewall, Zonealarm firewall). Sometimes they are even bundled together. Oh and it helps to close certain doors that are left open on windows by default.

---

### Post by HermanAB on 2011-04-15
Howdy,

In general, it is best to clean Windoze using Windoze.

There is a way to make a bootable Windows CD, called BartPE:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

The typical tools in my arsenal include:
ClamWin
Malwarebytes
Spybot Search and Destroy

Put them on a BartPE CD and you are good to go.

---

### Post by Paqman on 2011-04-15
> **earthpigg said:**
> 
for those not interested in practicing safe computing: yes, AV is the route to go.

So, about 99% of people then?

---

