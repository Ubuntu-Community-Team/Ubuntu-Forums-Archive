---
title: "Security"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by old_dope on 2009-03-06
I really am a Linux newbie and i have been told on a number of occasions that i don't need the likes of an anti-virus program or even a program such as rkhunter when using a Linux distro. So could someone wise me up on this issue please.
Thanks

---

### Post by ClaytonOT on 2009-03-06
You don't. Not to say that viruses don't exist on Linux, but running into one is very unlikely especially compared to Windows when your system is bombarded by that crap all the time. Most people spend their time developing scripts for a popular OS. Windows has the most users therefore crackers will go for the most potential. 

Viruses are also avoided on Linux by having a limited access filesystem. As you may have already encountered, the 'sudo' command acts as a temporary root in order to change core files. 

Viruses or malicious scripts still can appear on your home folder, but they do not have root access unless you give it to them / execute the script. If you're at a reputable site it's highly unlikely you'll run into malicious scripts anyways, moderation teams are pretty good at IP banning people that violate that rule quickly. If it makes you happy get clamav and never use it. :P

---

### Post by Bearly Able on 2009-03-06
I installed clamav because (a) we're dual-booting with XP and (b) I'm of a nervous disposition!  That said, I feel so safe with Ubuntu I almost never think to run it.  However, a friend sent me what seemed to be an innocuous e-card.  I duly visited the site to view it, but when I clicked the appropriate button, Firefox offered to open it with clamav, which surprised me.  I let it go ahead, and was even more surprised when clamav identified spyware.  It was only at that point that I realised the site was "offering" to install a toolbar in my browser.  It may not have been anything sinister, but I was glad I had clamav just for that.

---

### Post by billgoldberg on 2009-03-06
> **old_dope said:**
> I really am a Linux newbie and i have been told on a number of occasions that i don't need the likes of an anti-virus program or even a program such as rkhunter when using a Linux distro. So could someone wise me up on this issue please.
Thanks

You don't need anti-virus or anti-rootkit scanners.

There are no viruses in the wild that will infect an up-to-date Ubuntu install.

Just keep your machines updated an you will be safe.

--

You should still take the same precautions you did on Windows.

Don't visit dodgy porn/warez/... sites, don't open email attachments, ...

Not that you'll be infected or something, it's just good practice.

---

### Post by freesitebuilder on 2009-03-06
I found this site helpful:
[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/)

---

### Post by hyperyoda on 2009-03-06
> **old_dope said:**
> I really am a Linux newbie and i have been told on a number of occasions that i don't need the likes of an anti-virus program or even a program such as rkhunter when using a Linux distro. So could someone wise me up on this issue please.
Thanks

Short answer: you don't have to worry *much* if you keep an uptodate system and don't do foolish things.

Longer answer, read these sites:
[http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux]("http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux")
[http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/]("http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/")
[http://www.michaelhorowitz.com/Linux.vs.Windows.html]("http://www.michaelhorowitz.com/Linux.vs.Windows.html")
[ftp://ftp.software.ibm.com/linux/pdfs/SecurityReport050604.doc]("ftp://ftp.software.ibm.com/linux/pdfs/SecurityReport050604.doc")

Zach

---

### Post by 3rdalbum on 2009-03-06
> **Lesley Lutomski said:**
> However, a friend sent me what seemed to be an innocuous e-card.  I duly visited the site to view it, but when I clicked the appropriate button, Firefox offered to open it with clamav, which surprised me.  I let it go ahead, and was even more surprised when clamav identified spyware.

Most "E-cards" are malware these days, if you have to visit a site or run an attachment in order to view it. Make sure you don't download any on your Windows partition!

I would offer similar advice to what has been said here regarding virus scanners, except that if you are running any world-facing services you should have an anti-rootkit program or run one from a live CD every so often. For instance, if you have ssh enabled and your router set up to forward the SSH port, then you have a potential method for a rootkit to be installed. Rare, but potential. The same goes with web server software, FTP server software, Samba, or CUPS if you have enabled internet printing.

One of the rootkit hunting programs pulls in exim as a dependency. Exim is a mail server or an MTA as far as I know. Make sure you are running a firewall if you install this software; there's no sense in creating a vulnerability in your attempt to check for rootkits! :-)

---

