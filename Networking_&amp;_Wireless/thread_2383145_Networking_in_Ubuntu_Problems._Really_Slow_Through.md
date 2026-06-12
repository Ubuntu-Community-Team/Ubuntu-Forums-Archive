---
title: "Networking in Ubuntu Problems. Really Slow Throughput"
date: 2018-01-21
forum: Networking &amp; Wireless
---

### Post by jbamford92 on 2018-01-21
Hi,

Im back again with networking issues in Ubuntu. I am not seeing gigabit throughput speeds. Ive tried different drivers for the Intel Ethernet card but still slow problems. Now its got worst im only getting 26mb/sec yet in Windows i get 101megs when ever im copying or writing files to the Server what can be the problem here? Ive tried Ubuntu 16.04 and the latest version 17.10. I also have the same problem with Realtek on my Laptop. Ive different Ethernet cards & different Drives also different protocol. SMB, NFS but still the same problem. In windows i can copy over a TB within an hour or so. Does Networking suck for anyone else? Because i cant seem to solve this issue. 

Any ideas?

Thanks.

---

### Post by jbamford92 on 2018-05-20
> **jbamford92 said:**
> Hi,

Im back again with networking issues in Ubuntu. I am not seeing gigabit throughput speeds. Ive tried different drivers for the Intel Ethernet card but still slow problems. Now its got worst im only getting 26mb/sec yet in Windows i get 101megs when ever im copying or writing files to the Server what can be the problem here? Ive tried Ubuntu 16.04 and the latest version 17.10. I also have the same problem with Realtek on my Laptop. Ive different Ethernet cards & different Drives also different protocol. SMB, NFS but still the same problem. In windows i can copy over a TB within an hour or so. Does Networking suck for anyone else? Because i cant seem to solve this issue. 

Any ideas?

Thanks.

Can be marked as (Solved). Fixed the problem by using NFS instead of SAMBA on Workstations and Servers.

---

### Post by yarlagdd on 2018-05-20
Can you share details on how you did that? I am facing exactly the same issue with really slow network speed on desktop running Ubuntu and other non Ubuntu devices are running fine.

---

### Post by jbamford92 on 2018-05-29
> **yarlagdd said:**
> Can you share details on how you did that? I am facing exactly the same issue with really slow network speed on desktop running Ubuntu and other non Ubuntu devices are running fine.

Hi sorry for late reply. Work has been hectic.

So what are you sharing from? Windows to Linux or Linux to Windows? Samba from Ubuntu to Windows is quick. 
I use NFS in both Windows and Linux. 
Where do you have your shares? 
Note Only Ultimate or Enterprise versions of Windows 7 or 10 has support for NFS. My primary OS is Ubuntu but i have Clients that uses both NFS and SAMBA so my setup is kinda complicated.

---

### Post by geeky-1 on 2018-06-07
I have the same problem. Ubuntu 16.04 computer to Ubuntu 18.04 server copies at 800 kBps max using Files utility and Samba. Ubuntu 16.04 computer to Windows 10 laptop copies at the same speed in Files. However, if I do the same copy from Ubuntu 16.04 to Windows using the Window File Manager, it copies at 100 MBps. Windows says it will copy 16 GB in 7 minutes, but Files utility says it will take 9 hours to do the same copy!

I could try and learn NFS, but it seems much more complicated and harder to have to use the command line than simply being able to drag and drop files/folders in the Files utility.

---

### Post by jbamford92 on 2019-01-02
> **geeky-1 said:**
> I have the same problem. Ubuntu 16.04 computer to Ubuntu 18.04 server copies at 800 kBps max using Files utility and Samba. Ubuntu 16.04 computer to Windows 10 laptop copies at the same speed in Files. However, if I do the same copy from Ubuntu 16.04 to Windows using the Window File Manager, it copies at 100 MBps. Windows says it will copy 16 GB in 7 minutes, but Files utility says it will take 9 hours to do the same copy!

I could try and learn NFS, but it seems much more complicated and harder to have to use the command line than simply being able to drag and drop files/folders in the Files utility.


800kbps on a SAMBA transfer is really bad. How are you connecting both Computers together? via a Router, Switch or Firewall? Have you setup Static IPs both ends?

---

