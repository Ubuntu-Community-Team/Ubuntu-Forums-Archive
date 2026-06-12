---
title: "Yet Another Samba Problem"
date: 2015-10-19
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2015-10-19
After having to rebuild a Virtualbox VM on my two-box LAN, I'm finding it impossible to connect from any of my VMs on "mehitabel" to either printer located on "xubuntu2." Both boxes are running Xubuntu 14.04 LTS, fully updated. I discovered yesterday that my recent clean install of 14.04 onto xubuntu2 did not install samba by default, which was the cause of a number of problems I encountered in my troubleshooting attempts, but even after installation and restarting, the printer connection still fails. Vbox on mehitabel is still at version 4 and has not been updated recently so far as I can recall; I'm running version 5 on xubuntu2 but that should not be relevant to this problem.

Here's what I get when checking what's happening, at xubuntu2 (from which I'm posting this). I'll add captures from mehitabel shortly. 

```
jk@xubuntu2:~$ smbclient -L localhost
Enter jk's password: 
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (xubuntu2 server (Samba, Ubuntu))
	print$          Disk      Printer Drivers
	EPSON_Stylus_NX300 Printer   EPSON Stylus NX300
	HP_LaserJet_1320_series Printer   HP LaserJet 1320 series
	HP_LaserJet_1320_series_USB_00CNHC61K1HP_HPLIP Printer   HP LaserJet 1320 series
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.6-Ubuntu]

	Server               Comment
	---------            -------
	NEWPUB3              
	XUBUNTU2             xubuntu2 server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            XUBUNTU2
jk@xubuntu2:~$ 

```
NewPub3 is the recently rebuilt VM on mehitabel, running a copy of WinXP (yes, I know it's past EOL, but it's required for some of the work I do). Note that I **AM** able to print on all three printer shares, from mehitabel, using CUPS. From this, I conclude that no firewall is in the way between the two boxes themselves, though I'm not so confident about the path from the VM through its defined gateway (mehitabel itself, which runs a full DNS server in addition to being the router for my LAN). 

Mehitabel hosts a number of other VMs, although I normally have at most one of them running at any specific time; their printer connections also vanished, presumably at the same time, so none of them are now able to print directly. I'm working around the problem temporarily by "printing" from the VM to a PDF file located in my home directory of mehitabel, then doing the actual printing from the PDF file, but this is not a viable long-term solution.

The error messages I get when attempting to install any of the printers into NewPub3 is simply that the wizard is unable to connect. From the other VMs, any attempt to view printer preferences or properties fails with the message that the request cannot be fulfilled. In neither case is there any error code.

Attempting to browse for a printer, from NewPub3, fails to show the existence of "xubuntu2" at all despite the fact that it's registered as the master browser for samba.

Suggestions?

EDIT: Here's the printer wizard's actions from mehitabel:
[CENTER][ATTACH=CONFIG]265048[/ATTACH][/CENTER]

---

### Post by JKyleOKC on 2015-10-21
Turned out to be a whole collection of configuration problems, caused mostly by too many clean installs. The workgroups were not identical, the printer share names were not consistent at each end (some had underlines instead of spaces while others had hyphens), and two critical lines were missing in smb.conf at the xubuntu end.

Most of it appears to be some significant changes in samba along the way, with the newer versions of smb.conf missing a few defaults that were included in the older versions. However all is working once again.

---

