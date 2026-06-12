---
title: "Ubuntu 7.10 hard freezing during large file transfers"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by Arachnotron on 2007-11-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/147464](https://bugs.launchpad.net/ubuntu/+bug/147464) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Whenever I try to copy a large file (500MB+) to a mounted NFS share, Ubuntu hard locks. I don't get any flashing keyboard lights and the system is left completely unresponsive. My only recourse is to bring my laptop down hard. Nothing unusual appears in the logs. 

The laptop in question is a Dell Inspiron 1420n. Nothing unusual about the hardware config.  There is a bug report regarding this issue. Any ideas?

---

### Post by robertonix on 2007-11-06
I'm thinking in the same direction after Ubuntu 7.10 froze during a large file transfer using the (wireless) network. A hard reset was needed. 
Repeating the same task after the reset resulted in the same complete system freeze.

System: hp 6710b laptop with Ubuntu 7.10 (updated beta)

---

### Post by kevdog on 2007-11-06
I had the same experience with feisty trying to transfer a 2gb file using the cp command over a wireless connection.  The remote directory however was mounted with samba.  I cant remember the exact limit it would begin slowing down and eventually freeze, however it did it everytime.

---

### Post by txtwatson on 2007-11-07
I have the same problem whether I use nfs or samba. I wish someone could shed some light on the problem. Is there a parameter we need to tune?

TIA

---

### Post by Arachnotron on 2007-11-08
I also have a friend who just reported the same issue to me, although the offender wasn't NFS or samba, it was torrent traffic. Any ideas? Anyone?

---

### Post by cjastram on 2007-11-08
I've had this issue in the server version.  for me, it was (is) a buggy ethernet driver, and it causes a kernel panic.  Actually, it has to do with sustained high-volume network traffic rather than specifically a large file.

Try switching to console 1 or 8 (ctrl+alt+F1 or F8, F7 gets you back to the GUI) and copying the large file.  The kernel should dump the panic messages to your screen.

Chris

---

### Post by Arachnotron on 2007-11-08
> **cjastram said:**
> I've had this issue in the server version.  for me, it was (is) a buggy ethernet driver, and it causes a kernel panic.  Actually, it has to do with sustained high-volume network traffic rather than specifically a large file.

Try switching to console 1 or 8 (ctrl+alt+F1 or F8, F7 gets you back to the GUI) and copying the large file.  The kernel should dump the panic messages to your screen.

Chris
I've always gotten flashing keyboard lights with a kernel panic. I'll give this a try when i get home.

---

### Post by SjRaptor on 2007-11-09
I have the same problem as well, but when copying a 100MB+ file to an NFS drive. (remote file system is XFS, btw)

Tailing /var/log/syslog, I get the following:

Oct 27 23:41:31 thinker kernel: [39005.008000] nfs: server 192.168.1.40 not responding, timed out
Oct 27 23:41:31 thinker kernel: [39005.012000] nfs: server 192.168.1.40 not responding, timed out
Oct 27 23:41:31 thinker kernel: [39009.412000] nfs: server 192.168.1.40 not responding, timed out
Oct 27 23:41:31 thinker kernel: [39009.412000] nfs: server 192.168.1.40 not responding, timed out
Oct 27 23:41:31 thinker kernel: [39009.416000] nfs: server 192.168.1.40 not responding, timed out


This is also printed to tty1 and does not stop. I have to issue an (Alt-SysRq)+REISUB to safely reboot my system. If I wait too long though, not even that magic reboot sequence will work and requires a hard reset.

---

