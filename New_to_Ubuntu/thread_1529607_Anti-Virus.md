---
title: "Anti-Virus"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by dcforeman on 2010-07-12
Hi, I know that Linux doesn't really need an anti-virus application installed. However one of my intents, behind installing a duel booting Windows/ Kubuntu system was that when the inevitable virus strikes. I could boot into Linux and run a virus check from there without windows locking files and generally getting in the way.

I've found Klamav which as already found 2 viruses my usual Windows scanners missed. I'm wondering if anyone knows of any other free linux virus scanners with a KDE interface? If you can't think of one with a KDE interface, then a terminal interface will do.

Many thanks.

---

### Post by Crunchy the Headcrab on 2010-07-12
I don't think viruses are inevitable.  With modern Windows operating systems if you practice safe surfing/downloading you are unlikely to get a virus.  Especially if you have antivirus.  There's also the chance that those "results" are false positives.

---

### Post by techunit on 2010-07-12
KlamAV is the KDE interface... ClamAV is the normal version.

---

### Post by marshmallow1304 on 2010-07-12
[Avast!]("http://www.avast.com/linux-home-edition") makes a Linux version.  So does [AVG Free]("http://free.avg.com/us-en/download.prd-afl").  I've only ever used ClamAV from the command-line, so I can't comment as to the quality of either of the above.

Edit: Also, ClamAV does give some false positives.  I always use [Jotti's malware scan]("http://virusscan.jotti.org/") to check any suspicious files.  It gives scan results from many different scanners.

---

### Post by dcforeman on 2010-07-12
> **Crunchy the Headcrab said:**
> I don't think viruses are inevitable.  With modern Windows operating systems if you practice safe surfing/downloading you are unlikely to get a virus.  Especially if you have antivirus.  There's also the chance that those "results" are false positives.

You name me someone who practices safe surfing and downloading and I'll show you a saint!

My systems vulnerable to viruses because I turn UAC off, it's a pain in the bum and causes endless problems when I'm trying to write software. I also work for a company providing technical support from home, this means getting user attachments, extracting and executing them.

So I'm afraid my system is at risk from viruses to the point where I typically make it policy to completely reinstall my hard drive every 3 months just to be sure.

---

### Post by dcforeman on 2010-07-12
> **marshmallow1304 said:**
> [Avast!]("http://www.avast.com/linux-home-edition") makes a Linux version.  So does [AVG Free]("http://free.avg.com/us-en/download.prd-afl").  I've only ever used ClamAV from the command-line, so I can't comment as to the quality of either of the above.

Edit: Also, ClamAV does give some false positives.  I always use [Jotti's malware scan]("http://virusscan.jotti.org/") to check any suspicious files.  It gives scan results from many different scanners.

Thank you, I'll have a look at these.

---

### Post by Crunchy the Headcrab on 2010-07-12
> **dcforeman said:**
> You name me someone who practices safe surfing and downloading and I'll show you a saint!

My systems vulnerable to viruses because I turn UAC off, it's a pain in the bum and causes endless problems when I'm trying to write software. I also work for a company providing technical support from home, this means getting user attachments, extracting and executing them.

So I'm afraid my system is at risk from viruses to the point where I typically make it policy to completely reinstall my hard drive every 3 months just to be sure.
In that case I recommend running windows inside of a virtual machine in either Linux or Windows.  Then when the virtual machine gets infected it won't touch the rest of your pc and you should run normal without the need to reinstall every few months.

---

### Post by gandaran on 2010-07-12
> **dcforeman said:**
> Hi, I know that Linux doesn't really need an anti-virus application installed. However one of my intents, behind installing a duel booting Windows/ Kubuntu system was that when the inevitable virus strikes. I could boot into Linux and run a virus check from there without windows locking files and generally getting in the way.

I've found Klamav which as already found 2 viruses my usual Windows scanners missed. I'm wondering if anyone knows of any other free linux virus scanners with a KDE interface? If you can't think of one with a KDE interface, then a terminal interface will do.

Many thanks.
try out bitdefender, it's the best linux antivirus and has a nice gui that works exactly the same in gnome or kde.
get it [here]("http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/")
it comes with 30 days trial period but the bitdefender linux is free for personal use, all you have to do is register at bitdefender website for a free licence.

---

### Post by bodhi.zazen on 2010-07-12
> **dcforeman said:**
> Hi, I know that Linux doesn't really need an anti-virus application installed. However one of my intents, behind installing a duel booting Windows/ Kubuntu system was that when the inevitable virus strikes. I could boot into Linux and run a virus check from there without windows locking files and generally getting in the way.

I've found Klamav which as already found 2 viruses my usual Windows scanners missed. I'm wondering if anyone knows of any other free linux virus scanners with a KDE interface? If you can't think of one with a KDE interface, then a terminal interface will do.

Many thanks.

In general the best way to remove a virus from Window sis with the various windows tools.

Typically the only option with Linux tools is to delete the affected files and Linux does not (that I know) allow you to easily edit the windows registry, a step often required for virus removal.

---

