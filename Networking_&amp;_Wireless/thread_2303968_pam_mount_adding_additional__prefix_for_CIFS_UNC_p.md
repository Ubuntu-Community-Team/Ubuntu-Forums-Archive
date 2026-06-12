---
title: "pam_mount adding additional / prefix for CIFS UNC paths + multi-user configuration"
date: 2015-11-23
forum: Networking &amp; Wireless
---

### Post by Neil_Sherin on 2015-11-23
Hi,

I'm trying to configure pam_mount to automatically mount a home directory on a NetApp filer via CIFS. The version of Ubuntu I'm using is 15.04 MATE. I have configured Active Directory authentication on the Ubuntu machine.

I can ping the NetApp filer without issue either via IP address or Fully Qualified Domain Name (FQDN). Connecting via the Caja file browser or mounting the share via the command line works absolutely fine.

Having checked the logs in /var/log/auth.log, I am seeing the following message:

Nov 23 10:50:23 vmnsuadcifs sshd[2340]: (mount.c:72): Messages from underlying mount program:
Nov 23 10:50:23 vmnsuadcifs sshd[2340]: (mount.c:76): mount.cifs: bad UNC (///10.252.0.115/ua/SherinN)
Nov 23 10:50:23 vmnsuadcifs sshd[2340]: (pam_mount.c:522): mount of 10.252.0.115/ua/SherinN failed

Looking at the second line, it looks as if an extra / is being added to the UNC path. When specifying the path in pam_mount.conf.xml, the following behavior occurs:

With no / characters specified at the beginning of the UNC path, the result in the log file is:
(mount.c:76): mount.cifs: bad UNC (///10.252.0.115/ua/SherinN)

With one / character specified at the beginning of the UNC path, the result in the log file is:
(mount.c:76): mount.cifs: bad UNC (////10.252.0.115/ua/SherinN)

With two / characters specified at the beginning of the UNC path, the result in the log file is:
(mount.c:76): mount.cifs: bad UNC (/////10.252.0.115/ua/SherinN)

I cannot seem to trace where the extra / is being added. The relevant section of my pam_mount.conf.xml file is as follows:

<volume
    	user="sherinn"
    	fstype="cifs"
    	path="10.252.0.115/ua/SherinN"
    	mountpoint="/home/uni.ds.port.ac.uk/%(USER)"
    	options="username=sherinn,password=mypassword,domain=UNI,sec=ntlm,vers=3.0,file_mode=0700,dir_mode=0700" />

Also, is there a way I can configure pam_mount to mount the home directory of any user that has logged in using Active Directory authentication. This would obviously save having an entry for each user in pam_mount.conf.xml.

Thank you in advance for any help and advice. Apologies for the long post, but I thought it best to include as much information as possible.

Many thanks,
Neil

[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

