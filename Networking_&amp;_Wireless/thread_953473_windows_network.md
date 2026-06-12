---
title: "windows network"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by yanosj on 2008-10-20
I know I'm going to feel stupid when I get it, but I can't get to my windows network.  Samba is up and running but when I PLACES/NETWORK I get a windows network but when I open it, it's empty.  There are 4-5 machines in the Workgroup on the LAN.  I tried making the domain name for the wired network the same as the workgroup, but that didn't do it.  Help.

Thanks

---

### Post by pedro_orange on 2008-10-20
Can you ping the other machines using IP address?
Do you have an IP address that fits with the others along with the Subnet Mask?
Have you tried connecting via smb://xxx.xxx.xxx.xxx ? 
(x's being the IP address)

Have you setup any shares on the Windows machines?

---

### Post by yanosj on 2008-10-21
Thanks for the help.

There are windows shares set up and the other machines see them.

I can ping other machines.

I miss the IP question.  The router has dhcp and reassigns the IP's every once in a while, so they change.

---

### Post by pedro_orange on 2008-10-21
It changes their IP every x hours? 
Weird.

Well, just do an ipconfig on the Windows boxes to acquire their IP, ifconfig on Linux to get the sae sort of output. 

Check they've got the same subnet etc.

Can you connect using smb://ipaddress?

---

### Post by Florida Cracker on 2008-10-21
I have also been trying to solve this issue. There seems to be little help available. I installed lineighborhood and can now see the shares on the other computers but still unable to access them. I'm new to Linux so sorry I'm no help, but maybe someone else will chime in with a solution. I have been contemplating setting up static IP's for all the computers on the LAN but have been hoping there is another solution.

---

### Post by Florida Cracker on 2009-02-18
I finally solved my problem.
I did a sudo gedit on my nsswitch.conf file and added wins in front of dns in the hosts:files line. Now all windows shares show up and are easily accessed. Hope this helps others with same problem.

---

### Post by tjwilli on 2009-02-21
Editing nsswitch.conf didn't seem to help for me. I've had this issue intermittently for awhile now. 

What I did find useful for me was to kill the gvfsd-smb-browse process when this happens. After I kill it, when I try to access the shares on the Windows workgroup, everything shows up.

---

### Post by tjwilli on 2009-02-23
> **tjwilli said:**
> Editing nsswitch.conf didn't seem to help for me. I've had this issue intermittently for awhile now. 

What I did find useful for me was to kill the gvfsd-smb-browse process when this happens. After I kill it, when I try to access the shares on the Windows workgroup, everything shows up.

It looks like I spoke too soon. The other day had the same problem, so I killed gvfsd-smb-browse. No luck. Killed all gvfsd* processes. Still no luck.  I'm not sure, but part of it may be a firewall issue on the Windows side.

---

### Post by Florida Cracker on 2009-02-23
You also have to set the IP address in hosts tab in networking (through system/administration) for each machine you want to access. Windows firewall should not be a problem...I have not altered it on any of my computers and is works fine.

Do what this video shows [http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)
put the wins in front of the dns like I posted in a previous post above, and add the ip addresses in hosts tab in network and you should be good to go.

---

