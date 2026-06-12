---
title: "dual boot virus risk?"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by jimmy the saint on 2007-09-27
forgive my posting here, but it seemed like the best place for it.

I know that most viruses don't pose a threat to linux, so there is no real risk in dual booting in that direction.  But is it safe for windows?  Since ubuntu is typically run without antivirus software, couldn't malware wind up on your HD?  If this were to happen, would this then pose a threat to the windows installation?

I have no idea if this is risky or not.  I have heard it suggested that dual booting and only granting ubuntu (or linux in general) access to the internet provides huge security benifits.

Just looking for your thoughts.

---

### Post by spd106 on 2007-09-27
The Server and Security might have been a better place to post if you wanted a technical discussion. I'll just give you the high level view. 

Yes, there is the possibility of a virus getting across OSs via any shared file storage area. Viruses usually hide within data files, so you won't know it's bad until you use the file. Just because it doesn't affect Ubuntu doesn't mean it won't affect Windows once you transfer it across. 
The best advice is to be careful with data files from untrusted sources and use a virus scanner if you run Windows.

There are a few virus scanners available for Linux systems, they are usually aimed at those who are running a Linux server as a pass through to Windows systems, like a mail spam filter that also scans attachments. You can use these on desktop systems too.

---

### Post by lisati on 2007-09-27
The first virus I recall encountering was a boot sector "virus"  on an MS-DOS machine, something like 20 years ago. Most of the "malware" I'm aware of these days does its mischief in other ways, and tends to be targeted at Windows machines.

There is no substitute for being careful, regardless of which OS you are using, and using good sense is probably the first and best line of defense.

---

### Post by tturrisi on 2007-09-27
To answer you question more precisely:
NO, Windows cannot get infected when you are running Linux because Windows is on a separate partition than Linux.  To get infected, you would have to manually move or copy a malicious file onto your Windows partition and then execute (run) the program.

The only places these files could exist on the Linux partition are the browser cache or a downloads directory.  And most all Windows malware gets installed via ActiveX controls (which don't run in Linux browsers).  Windows rootkits can't install on Linux, so no need to be concerned with them.

Also, even if you somehow end up w/ malicious files on your Windows partition, they can do absolutely no harm until YOU execute the file.  (execute also implies opening email attachments)

Malware & viruses on Windows MUST be executed else they can do no harm, they typically excute at boot via a registry key or other "sister" program set to execute at boot.

You can test this & prove it out to be true.  You can run Linux (or even Windows itself) and download any virus or malware and save it to disk.  It can do nothing until YOU manually execute the file.

I have not used automatic (autoprotect) antivirus on Windows for 7 years.  If I have any doubt about a file I manually scan it.

---

### Post by jimmy the saint on 2007-10-07
Thank you for your input everybody. I'm trying to switch to linux after years of windows use.  My mindset has long since gone from paranoia to the acceptance that windows is practically unprotectable.  This can be debated but it is also my primary reason for making the switch.  
I'm trying to wrap my mind around he concept of safely connecting my computer to the internet!!

---

### Post by teabuntu on 2007-11-16

Hi,
I'm currently tyring to learn more about security risks with dual booting Windows XP Home Edition and Gutsy Ubuntu.  Since I'm totally new with things Ubuntu, Linux as well as computers in general, my question may seem like a no brainer, but I hope you would bear with me.  

Is it possible for anything like viruses or other nasties to migrate or transfer from one partition to another?  Eg: from Linux partition to Windows or vice versa?  

Does Linux OS and Windows XP share a "common" partition when both OS is installed on a single disk?  What about on seperate disks, such as having Windows OS on the main hard disk of a laptop, then installing Ubuntu on a USB flash drive?  Would security risk diminish if the 2 OS were to be installed on seperate disks?

Some one on this forum once stated that even if you have a password set on your Windows program, if you use Linux, you can "see" the password and the reason is, it's because the two operate differently.  If that is the case, then wouldn't having both OS pose a grave security risk when using the Windows OS?  Because Linux is installed, wouldn't it make it really easy for someone who knows an awful lot about Linux to use the Linux OS on my laptop to "see" things or even start taking control over my computer even with security program installed on Windows OS?

Lastly, the firewall program like Firestarter for Linux, does it work in the same way as other firewalls designed for Windows?  What about anti-virus programs for Linux like ClamAV?  Do they only block known viruse for Linux or does it also take care of viruses designed to attack Windows for people who are dual booting?

Thank you for any advice or help on this matter.

---

