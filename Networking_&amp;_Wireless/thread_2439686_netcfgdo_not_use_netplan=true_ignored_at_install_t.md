---
title: "netcfg/do_not_use_netplan=true ignored at install time"
date: 2020-03-31
forum: Networking &amp; Wireless
---

### Post by nurbles on 2020-03-31
With people trying (and required) to work from home due to COVID-19, I need to set up a machine dedicated to an OpenVPN bridge (external Windows clients bridged to a simple Windows workgroup -- no WINS or domain controllers) for our very small office.  Unfortunately, it appears that any documentation I find has just been relabeled as being for Ubuntu 18.04, because it ALL uses /etc/network/interfaces to set things up.  I finally found this:
> [COLOR=#242729][FONT=Arial]At install time, a user can opt to use        ifupdown by preseeding netcfg/do_not_use_netplan=true.        This is done by adding the preseed line to the command line when        booting the installation media (i.e. at install media boot menu,        press F6, type ‘e’, and add to the command line).[/FONT][/COLOR]
In [https://netplan.io/faq#how-to-go-back-to-ifupdown](https://netplan.io/faq#how-to-go-back-to-ifupdown) but I have been unable to get the installer for 18.04.4 to recognize (or obey?) the setting. I am seeing many comments about netplan not working well (or at all?) with bridging set ups, plus I have yet to encounter even ONE OpenVPN document for 18.04 that uses netplan files, and I am not nearly expert enough (or at all, really) to completely roll my own set up.

I have also read that there are quite a few issues and very tricky bits to trying to remove netplan and roll back to the older network/interfaces system, so if I cannot get the installer to respect the setting to install the old system, it would seem that I must find a 16.04 install just to do what I need.

Please tell me there is a better way.

---

### Post by webaake on 2020-03-31
You can always make the adjustment after installation (as long as you have functioning network and internet). But that might require to run without VPN initially. A bit down in this thread there's a more complete answer:

[https://askubuntu.com/questions/977243/ubuntu-17-10-disable-netplan](https://askubuntu.com/questions/977243/ubuntu-17-10-disable-netplan)

PS: I'm running updated 18.04 without Netplan using "interfaces" old style.

---

### Post by nurbles on 2020-03-31
Thanks for the link to those instructions.  Unfortunately, I do no trust myself to complete that much work without messing it up in the cramped location where the server physically exists and I'm pretty sure it would be a bad idea to attempt these changes over an SSH connection.  So I have installed 16.04.  By the way, I got a note from the OpenVPN folks when I complained that all of their supposedly 18.04 documentation is just rebranded 16.04 documentation that doesn't refer to netplan and their response was simply, "We do not support netplan here."

---

