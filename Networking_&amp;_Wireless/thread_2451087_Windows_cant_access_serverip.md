---
title: "Windows cant access \\serverip"
date: 2020-09-26
forum: Networking &amp; Wireless
---

### Post by Dave_Davis on 2020-09-26
I have a Ubuntu server running **samba**.  IP Address 10.0.0.230

The same server is running VirtualBox with an instance of Ubuntu running **samba**. IP address 10.0.0.231

I have installed and reinstalled this entire setup four or five times.

From Windows 10, when I try to access samba on the bare medical machine, **Windows reports it cannot access 10.0.0.230**

However, **Windows has no problem accessing 10.0.0.231.  **

The ubuntu installs were done on the same day using the same ISO.

Since I have done several re-installs and the problem remains, I must be missing something.

I have posted here rather under virtualization because the virtual box is working fine.  I would appreciate any and all suggestions.

---

### Post by TheFu on 2020-09-27
All connection problems come down to 4 things:
[LIST]
[*]IP connectivity - the systems can ping each other by name and by IP address
[*]Firewalls aren't blocking - there should be logs for any blocked firewall packets
[*]Compatible protocol used between the systems - Win10 bumped up the smb protocol required about 4-6 months ago. On the Linux side, the samba server needs to be setup to support that version.  If there are any old samba devices also trying to access the same samba shares, this can be difficult, since Win10 wants smb3 and an old android device from 8 yrs ago wants NT1 (and that setting requires a few others come with it). OTOH, some settings mandated by NT1 cannot be used for other protocol versions. 
[*]Authentication; Correct userid, AD domain, and password
[/LIST]

Assuming you followed these instructions: [https://ubuntuforums.org/showthread.php?t=2434383](https://ubuntuforums.org/showthread.php?t=2434383)  and it isn't just working, then much more data is necessary.

To get help, the samba config needs to be posted.  **testparm** will output the config being used. Post that.

Samba creates logs when bad things happen. They are in /var/log and /var/log/samba - look at those. See the errors. Paste those into google for help.

Bare medical?  ;) Thanks. That was good.

---

### Post by Dave_Davis on 2020-09-29
Thanks for the suggestions.  I had been over your four items numerous times and could find no problems.

Finally, I tried yet another re-boot of the windows machine.

As I suspected, the problem wasn't with Samba, but rather with windows.
After the reboot and the **problem is apparently solved at least for now**.  Windows is not my friend.  I'm three apps away from ditching it completely.

---

