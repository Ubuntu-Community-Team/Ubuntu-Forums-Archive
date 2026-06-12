---
title: "smb shares problem. left for awhile mounted doesnt start copying (Delay Problem)."
date: 2017-12-26
forum: Networking &amp; Wireless
---

### Post by jbamford92 on 2017-12-26
Hi folks. 

I have some strange issues with SMB shares from my Server in Ubuntu. When left connected to network shares for awhile i run into a issue upon copying to the Server it gets stuck on Prepairing Files & Music that is being played from the server stops for a second until the copying is started. This seems to be a issue in Ubuntu. Doesnt happen in Windows 7 or 10. However i have tried NFS Shares but doesnt work there is a problem upon mounting the Server then once mounting it will refuse to stay mounted so i scrapped NFS due to it doesnt work. Just need to fix the SMB problem. 

Sometimes when listening to music i have a issue where it paused then starts playing again.

I have also built & compiled my own Kernel but still have the issue with SMB Shares. 

I have modified the smb.conf file changed to SMB 3.0 speeds up files transfers a lot but still have a issue. Its like its gone to sleep then waiting for it to wake up. 

The Network card im using is a Intel 82572EI Single Port PCI-E Ethernet card i know thats not the issue as i have a few of these cards and tried others. I have tried onboard realtek Ethernet card on my Motherboard but still same problem. originally i thought it was a issue with the Realtek Stack but still the same problem with the Intel Card but i know that the Intel Stack in Linux is stable so i know its not the issue with the Drivers.



Any ideas & help would be appreciated.

Thank You.

Jack.

---

### Post by jbamford92 on 2018-05-20
> **jbamford92 said:**
> Hi folks. 

I have some strange issues with SMB shares from my Server in Ubuntu. When left connected to network shares for awhile i run into a issue upon copying to the Server it gets stuck on Prepairing Files & Music that is being played from the server stops for a second until the copying is started. This seems to be a issue in Ubuntu. Doesnt happen in Windows 7 or 10. However i have tried NFS Shares but doesnt work there is a problem upon mounting the Server then once mounting it will refuse to stay mounted so i scrapped NFS due to it doesnt work. Just need to fix the SMB problem. 

Sometimes when listening to music i have a issue where it paused then starts playing again.

I have also built & compiled my own Kernel but still have the issue with SMB Shares. 

I have modified the smb.conf file changed to SMB 3.0 speeds up files transfers a lot but still have a issue. Its like its gone to sleep then waiting for it to wake up. 

The Network card im using is a Intel 82572EI Single Port PCI-E Ethernet card i know thats not the issue as i have a few of these cards and tried others. I have tried onboard realtek Ethernet card on my Motherboard but still same problem. originally i thought it was a issue with the Realtek Stack but still the same problem with the Intel Card but i know that the Intel Stack in Linux is stable so i know its not the issue with the Drivers.



Any ideas & help would be appreciated.

Thank You.

Jack.

Can be marked as (Solved). Solved the problem switched to NFS on both Servers and Workstations. Although SAMBA is fine for Kodi :). I can saturate a 2gbp link over NFS which is great.

---

