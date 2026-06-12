---
title: "Citrix Receiver Installation Troubles (64bit)"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by cj-123 on 2010-02-04
I am having problems with installing the Citrix Receiver client. I have tried following suggestions of various threads to no avail. So first the specs:

New build, clean install of 9.10 Desktop, 64 bit edition.
Pentium(R) Dual-Core  CPU      E5400  @ 2.70GHz
installed:
Open Motif 2.3.1-2
LibXaw7

Also, per post noted below, files from libmotif3_2.2.3-2_i386.deb were extracted to /usr/lib32.

I am having problems with the client not finding its dependencies.. Here is the ldd output:

$ ldd ${CLIENT_EXEC} #CLIENT_EXEC="/usr/lib/ICAClient/wfcmgr"
	linux-gate.so.1 =>  (0xf773b000)
	libXm.so.4 => not found
	libXp.so.6 => not found
	libXpm.so.4 => not found
	libSM.so.6 => not found
	libICE.so.6 => not found
	libXmu.so.6 => not found
	libdl.so.2 => /lib32/libdl.so.2 (0xf7726000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf770c000)
	libc.so.6 => /lib32/libc.so.6 (0xf75c7000)
	/lib/ld-linux.so.2 (0xf773c000)
	libXt.so.6 => not found
	libX11.so.6 => not found

And yet, /usr/lib/ contains all of the dependencies which are missing.  So I am not sure, 1.where the client is looking for the 'not found' dependencies, and 2. how to correct the problem.

I tried the solution at this thread:
[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

Which hasn't seemed to get me anywhere.

Any thoughts?

---

