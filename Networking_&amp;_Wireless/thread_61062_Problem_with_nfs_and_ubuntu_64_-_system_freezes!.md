---
title: "Problem with nfs and ubuntu 64 - system freezes!"
date: 2005-08-30
forum: Networking &amp; Wireless
---

### Post by ispmarin on 2005-08-30
Hello all.
I have just finished installing a athlon amd64 on asus sli with nforce 4 chipset. I configured correctly the nis (I hope so!) and configured also nfs. I have installed the nfs-common and the nfs-server-kernel. I am trying to mount a nfs home from a fedora 2 box. The filesystem is correctly mounted, and the directories are correctly listed, but when I try to access any file inside the nfs home, the terminal that I am using just freezes. When I open a new terminal, using the root account, the system is still responding, but the terminal with my normal user using the nfs home is completely freezed. I cannot even kill the pid for that process from the freezed terminal. I have also installed the nforce drivers from nvidia, and the network is working correctly. I have tried to uninstall and install again the nfs several times, and even tried to use the nfs-user-kernel, with the same results. Just now I am trying to compile a new kernel (2.6.13) to see if it helps, but I am afraid it will not.

Any ideas...
Update -  a fresh new kernel 2.6.13 with nfs compiled into it did not solve the problem...

Thank you!

Ivan

---

