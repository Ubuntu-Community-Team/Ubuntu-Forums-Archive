---
title: "linux networking/hacking tools"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by serialbumpy on 2008-06-10
My hacker-simulation lab is moving from XP to Ubuntu. We need linux/ubuntu equivalents of any or all of the following, if anyone can recommend any. Must be free; gui is preferable. 

Super Scan
MerX Network Scanner
pwdump
l0phtcrack
BO2K
UPDFlood -- any DoS-ish program will do
FU Rootkit

Thanks in advance.

---

### Post by nixscripter on 2008-06-11
udp flood can be done in perl: [http://blog.ioshints.info/2008/03/udp-flood-in-perl.html](http://blog.ioshints.info/2008/03/udp-flood-in-perl.html)

All of these can be found in Ubuntu packages:

**john** - password cracking utility
**wireshark** - GUI-based protocol analyzer with complex pattern matching ability
**ettercap** - capable of ARP poisioning, man-in-the-middle-attacks, and password capture

For a rootkit, look into the [vmsplice() exploit]("http://www.isec.pl/vulnerabilities/isec-0026-vmsplice_to_kernel.txt") (though most have patched by now.

And I would suggest getting **wine,** with a cross-compiler. You might be able to recompile some of that stuff you have the source for, and run it on Windows natively (or wine itself).

Hope this helps.

---

### Post by serialbumpy on 2008-06-11
Ya, I found John the Ripper earlier today. That seems to be the way go with password cracking.

The tools/exploits don't necessarily have to be 'un-patched'. Because this is for demonstrative purposes, I could potentially 
reopen a hole.

Thanks for the suggestions; I'll look into them.

---

