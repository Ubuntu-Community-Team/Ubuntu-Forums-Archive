---
title: "DDWRT - SMB shares"
date: 2015-05-30
forum: Networking &amp; Wireless
---

### Post by simon89 on 2015-05-30
I've had this problem for a while and I haven't been able to find a solution.

The problem is that when I create SMB shares in ubuntu (tried in both 14.04 and 15.04), the shares are not browseable on any of my windows clients (yes, browseable has been set to yes for the shares). However, I can access the shares directly via IP

I'm wondering if there might be any settings on my ddwrt router that may be preventing them from being browseable on windows?


I ask because a number of months ago, my NAS was running openmediavault ([http://www.openmediavault.org/](http://www.openmediavault.org/)) and SMB shares were working fine, everything was browseable

A few months after that I decided to try out ubuntu on the NAS instead, and then I ran into this browseable issue

At that point I tried reinstalling OMV on the NAS and nothing was working anymore

The only thing I can think of between having everything work on OMV, to nothing being browseable (on either ubuntu or OMV), is I flashed my router with ddwrt firmware

So could there be router related issues that can cause this? Maybe dhcp related? I'm completely new to networking so really have no idea what may be the problem

---

### Post by bab1 on 2015-05-30
Browsing of SMB shares is a separate issue from accessing SMB shares.  There are several things that will cause browsing to fail.

Are all of the machines on the same network? What is the IP address you are using to access the shares?  What is the IP address of the Windows machine you are mapping the shares to (.e.g  the Windows machine)?

Are the 2 Samba daemons running?  Post the output of this```
pgrep -l mbd 
```

Can you browse the shares on Ubuntu from that same machine?  Post the output of```
smbtree -d3
```

I doubt that the router is a problem.  You have connectivity if you can access the shares by using the IP address.  It appears to be a naming service problem.  Post the outputs that I asked for and we will diagnose what your problem is and how to fix it.

---

### Post by SeijiSensei on 2015-05-30
Browsing is tricky unless you have a nameserver on the network.  You can have Samba function as a "domain master" and provide Netbios name services for browsing.  Read the section called "Configuring Workgroup Browsing" in [https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html](https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html).

---

### Post by bab1 on 2015-05-30
> **SeijiSensei said:**
> Browsing is tricky unless you have a nameserver on the network.  You can have Samba function as a "domain master" and provide Netbios name services for browsing.  Read the section called "Configuring Workgroup Browsing" in [https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html](https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html).

You don't need a "namesever" per se as much as you need to have successful NETBIOS resolution.  This can be done via LAN bcast if nmbd can't resolve the /etc/hosts mapping.  The only real need for a nameserver (i.e. WINS) is if you have a multi-segment (multiple subnet) network.  The very first line in your reference is prety clear about that> [COLOR="#0000FF"]To [/COLOR]configure [COLOR="#FF0000"]cross-subnet[/COLOR] [COLOR="#0000FF"]browsing[/COLOR] on a network containing machines in a workgroup ... 

If the user has a single subnet network then, by default, the master browser should always be accessible via bcast.  The default setting in the smb.conf file for local master and domain master is okay.

[COLOR="#0000FF"]Edit:  In the section above the your reference section is this sentence that sums it up pretty well[/COLOR]> In the case where there is no WINS server, ***all name registrations as well as name lookups*** are done by UDP broadcast. 

---

