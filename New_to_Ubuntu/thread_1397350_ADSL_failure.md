---
title: "ADSL failure"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by jtiriey on 2010-02-03
Hello,
 
After years of reliable service, my internet DSL failed. My premium ISP provided a new ADSL router and technical help but they could not assist with Ubuntu. They report the connection never failed and in fact, my current Windows computer runs just fine. The new ADSL ran as plug and play on the Windows machine but the Ubuntu laptops failed to connect.
 
ERROR: Failed to fetch--could not resolve security.Ubuntu.com
 
Of course, all reboots, reviews of network pulldowns, and a read of all postings have been done, over and over again.
 
This is a business. I am not a recreational computer user. I switched to Ubuntu as a security measure only and am looking for good Alaska support for which I will pay. The system had also had problems opening and running disks lately. These problems began shortly after I downloaded the recent list of security patches.
 
ERROR: Failed to mount
 
Please help--I have work to do, James

---

### Post by tom4everitt on 2010-02-03
Okay, so just for clarity: You are connecting your laptop directly to the modem (no router in between) and you get that error message when what? What happens if you open firefox and try to open a web page?

Your other problems (with mounting) makes it sound like it is actually something wrong with your ubuntu system (caused by updates). Sometimes this is caused by a kernel update, in which case you should press either Escape or Shift during boot (depending on which ubuntu version you use), and choose an older kernel in the list. 

If choosing an older kernel doesn't help, you should try booting from an ubuntu live cd (just download the latest from ubuntu.com). This will tell you whether it is merely a software error or if its something wrong with your hardware.

---

### Post by jtiriey on 2010-02-03
Hello,
 
Thanks for the reply.  Yes, hookup is direct to the ADSL--there is no net or other sytems involved.     All programs boot up OK but remain off line.  Manual selection and command produces a long attempt time and then the notice, " disconnected--work off line."   Yes, I suspect an update problem.   However, without a connection, there is no download ability as there is only Ubuntu loaded.  I would have to download to disk on my Windows machine and then tranfer to the Ubuntu computer where I an also having problems with reading disks.  The machine is loaded with medical and accident files, most have been backed up to disk but I do not want to format and reload.   Is 9.10 on a disk in back of a magazine?  That's where I got my current program.  A local in Alaska advertized Ubuntu support for a fee but it turned out he could only load, not debug.     Maybe I need a new Windows laptop by reason of the excellent Windows tech support from my local coop ISP/Phone Co.         James

---

### Post by TBABill on 2010-02-03
Having worked many years as a dipatched technician for a phone company and troubleshooting DSL, telephone, digital subscriber loop systems, T-1, ISDN and many other technologies, your problem does sound as though it is on your computer end. If it ran in Windows it should run in Ubuntu...true statement. But, the assumption is your install of Ubuntu does not contain errors, driver problems, etc. It sounds like you are leaning toward a reinstall to confirm and for a new user it would be the easiest to try. However, if your install disk is corrupted you may not have any luck reinstalling from a bad media.
 
Your ADSL modem communicates via Ethernet so it will work properly regardless of what OS and machine you connect it to. That is not to say the computer itself will work properly, but if you reconfigure, reinstall, etc., your modem operation will not change.
 
I would suggest trying the reinstall if you had little trouble getting the first install going. If you are more experienced, troubleshoot your ethernet card and settings with Ubuntu to see why it is not communicating properly. On most installations the wired side works out of the box, but I have seen messages posted from users who could not get either working in the beginning.
 
Good luck. Worst case, reinstall Windows so you can use the OS to get online, download whatever you may need (like a new Ubuntu 9.10 .iso to burn a CD from) and to just use till you get Ubuntu running. Dual booting is a great idea unless you need the HD space Windows takes up. There's surely nothing wrong with using both to meet your needs.

---

### Post by jtiriey on 2010-02-03
Thanks for the info.
 
I had come to the same conculsion and will now do a full house cleaning tonight. It will take many hours to review and copy image and text files. This failure was concurrent with serious multiple winter storm power spikes. My backup power source also failed. After years of service, the batteries were failing and the auto swtiching was found to have failed after new gel cells were installed. My backup (Windows) computer was off line and off power as a backup security measure so it survived without incident. I expected this system to be more resistant to problems than Windows but I must accept that every system had its limits. Thanks again.
 
Jim

---

