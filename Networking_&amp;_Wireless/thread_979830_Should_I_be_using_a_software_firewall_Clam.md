---
title: "Should I be using a software firewall? Clam?"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by Tom_ZeCat on 2008-11-12
I've networked 3 PCs, an Ubuntu 7.10 one, an Ubuntu 8.04 one, and a Windows XP one.  They're networked via a simple D-Link ethernet router.  I'm using Samba and have at least one shared folder on each machine.  I elected not to install the driver that allows Windows XP to access ext3 drives.  As a result, each Ubuntu machine can take files from the shared folders on the Windows XP PC, but the Win XP PC cannot access any folders on either of the Ubuntu PCs.  That's fine.  That's how I want it.  

On the Win XP machine I'm using Kapersky Internet Security, including its firewall.  That's a no brainer.  It's necessary to protect Windows machines to the hilt.  

On the Ubuntu PCs I'm using the free AVG antivirus for Linux, but no software firewall.  Should I be using one?  I haven't done any configuring to use the ethernet router as a firewall.  Should I?  Or is such a router automatically a firewall soon as I hook it up?  

I'm not sure I like AVG.  I downloaded a file to one of the Ubuntu PCs and scanned it with AVG.  It found no malware.  However, as soon as I copied it over to the Windows PC, Kapersky screamed that it was a virus and killed it.  I've installed Clam Antivirus via the Synaptec Package Manager several times, but I always have problems with it.  I can't download the definitions from the GUI, and when I try to download them from the terminal, it squawks that it's not the latest version of Clam and refuses to download the definitions.  I'm annoyed that the package manager doesn't install the latest version.  I'm also annoyed that Clam refuses to download the latest defs if the programs version isn't the newest one.  

I found the page with instructions on how to install the latest Clam manually.  Is it worth doing?  Is Clam any better than AVG?  My main reason for putting antivirus on my Linux PCs is to protect my Windows one, which is obviously the PC that's most vulnerable to malware.  It's also a "just in case" for the Linux PCs.  Even though they're unlikely to get attacked, I don't want to let my guard down just in case some goober finds a way to hijack Linux boxes.  Sometimes I download torrents via Opera on one of my Linux PCs.  

So my questions are:
1. Should I use a software firewall on my Linux PCs?  
2. Should I go through the trouble of manually installing Clam on my Linux PCs?
3. Is my ethernet router already working as a firewall or do I need to do something to enable that function?

Btw, I also looked into Kapersky for Linux, and it's over $200 (USD) and isn't tested for Ubuntu.

---

### Post by superprash2003 on 2008-11-12
basic routers with firewalls arent that great.. always safe to install software firewalls.. for ubuntu machines you could use firestarter ( by default ubuntu has iptables, firestarter is just the gui).. iptables is the firewall for ubuntu.. to install firestarter type sudo apt-get install firestarter in the terminal.In linux, i've used avg and it hasnt been a problem for me..

---

### Post by Tom_ZeCat on 2008-11-13
Thanks for the help.

---

### Post by randy78 on 2008-11-13
Firestarter is seriously outdated and development has ceased... the preferred app is UFW and its GUI frontend GUFW.

Also, an anti-virus should only be used in Linux to scan files for Windows based viruses (99.999% of all viruses out there are for Windows), because it's next to impossible to get infected in Linux unless you either do it to yourself on purpose or download shady software from untrusted sources... a quick search of the forums reveals all this and more...

This thread will explain everything ;) [http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

---

