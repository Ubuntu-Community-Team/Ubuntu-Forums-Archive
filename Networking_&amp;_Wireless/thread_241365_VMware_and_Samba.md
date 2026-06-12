---
title: "VMware and Samba"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by PipBoy on 2006-08-22
Hi,
I have problem with comunication between Win XP pro (vmware) and Samba(Dapper). When I copy files from Win(vmware) to dapper(samba) win freeze. When I copy files from Win (vmware) to other win (vmware or other computer) it is works. When I copy from win (other comp) to samba it works too.
Where is problem?

Thanks.

---

### Post by Kat of Zion on 2007-01-24
Stego_s_aurus and I are racking our brains about this too.  Its really annoying.  I want to copy files to my xP desktop (VMware) so I can do an install.  HOwever while I can access the shared folder, copying a 76kb file is done no problem.  However anything like 50MB....forget it.

---

### Post by rvmindstep on 2007-01-25
Hi

I had the same problems when I first tried to update my "Breezy Badger" workstation. Everything went fine until I reached the vmware troubles. After fighting days on this, I had to go back to my previous setup, which I still run today.

From my experiments, it looks like some packets lost their way between the host and the vm (I got consistent indications in vmware logs). I first detected it via samba, but that's not the only trafic that got badly effected; for some reason, this is very apparent on SMB. I tried weird things such as changing my physical network adapter (!) because I suspected something went wrong when the packets reach the driver. It actually had an impact (better), but still not good enough :( I also tried the two kinds of virtual network device with no luck.

I sent a report to vmware too, but to date, I did not have new elements to further understand this problem.

- herve

---

