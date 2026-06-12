---
title: "nfs mount tool"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by node2network on 2010-10-09
I am not good at English.

I try to mount using nfs.
My environment is below. Each OS is ubuntu10.04. PCb and PCc are samba servers.
PCb's samba directory is mounted by PCa, and PCc's samba directory is mounted by PCa.

PCa <- PCb(samba)
PCa <- PCc(samba)

I want to copy the files which are in PCb to PCc.
When I copy the files which are in PCb to PCc, which Case is the correct answer?

Case1.

PCb -> PCa -> PCc (PCb's file is copyed on PCa temporarily for copygin to PCc.)

Case2.

PCb -> PCc (except PCa)

---

### Post by Jose Catre-Vandis on 2010-10-09
Er, you cannot mount samba shares using nfs??

Either serve the files with nfs (search forum for howto) and then mount

or

use samba on client machines to connect or samba shares you have created (again a good howto for this is on the forum)

I serve both nfs and samba to my client machines (nfs on windows is just too hard, when samba works fine)

---

