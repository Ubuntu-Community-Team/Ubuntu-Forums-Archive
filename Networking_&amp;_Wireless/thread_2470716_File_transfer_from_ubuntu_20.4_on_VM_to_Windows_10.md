---
title: "File transfer from ubuntu 20.4 on VM to Windows 10"
date: 2022-01-08
forum: Networking &amp; Wireless
---

### Post by bubbashag on 2022-01-08
Let me apologize at the outset, Im pretty basic, maybe awfully basic in my ability to operate in Linux, so sorry for my terrible ignorance.

I have a Windows 10 Pro machine that has VM 6.1 running on it with ubuntu 20.4 running on the VM. I had this set up so I could transfer files from ubuntu to Windows. This worked flawlessly for me for a couple years but now is broken. I think the latest Windows update put the kibosh to it. The problem is that what skills I developed to cobble that setup together are now rusty to say the least. I assume this will take some time to fix. But as Im old and retired I luckily have the time.

I have followed a couple tutorials, unfortunately I keep getting to a step that does not replicate in my world so Im just stuck. I know I have the latest Samba installed and running in ubuntu, beyond that Im not confident of much.

Where to start?

---

### Post by TheFu on 2022-01-08
Win10 supports ssh/scp/sftp. Those are the network protocols that should be used.
[https://winscp.net/eng/docs/guide_windows_openssh_server](https://winscp.net/eng/docs/guide_windows_openssh_server)

I have no idea what VM 6.1 is.  Is that a microsoft thing or some other vendor?  On Linux, we tend to use virtualbox or KVM+libvirt as our hypervisors.

If you seek a method that is part of the hypervisor to transfer files, 
a) you'll want to read the manual for the hypervisor
b) almost all of those methods are full of serious security considerations (failures).
Using normal network protocols for file transfers means that normal network hardening and firewalling can be used to limit the access to/from only the specific machines that need this extra access.

Rather than pushing files to the host from the guest VM, perhaps having the host pull the files from the guest would work better?  
IDK.  I've never touched Win10 myself.

When setting a up a VM under a hypervisor, there are multiple different types of networks. NAT, Host-only, Guest-LAN and bridged.  Each hypervisor has a slightly different take on what those mean, but NAT means connections can only come FROM the guest out.  
Guest-LAN means that all guest VMs are on the same LAN, but cannot communicate outside that (good for security lab work), 
Host-only means that the guest can't see any other guests or the internet, but just the host hypervisor system.  
Bridged means it is just like any other system on your subnet/router and has full access to all other systems on that LAN, plus any upstream systems and perhaps the internet.

Regardless, read the manual for the hypervisor to see what it supports ... or be very clear about the hypervisor actually used. Don't make us guess what you have, since we'll have different expectations, often wrong, for what someone would do.

---

### Post by bubbashag on 2022-01-09
VM in this case means Virtual Machine (VirtualBox) 
Ubuntu 20.4 is running on Oracles Virtual Machine 6.1 which is running on Windows 10.

I used to be able to move files from Ubuntu to a folder on Windows. 

Thanks for the reply. This hobby of mine seems to have become exponentially more difficult. Clearly Ive got some reading to do.

---

### Post by KBar on 2022-01-09
Have a read through [this]("https://www.virtualbox.org/manual/ch04.html") documentation. It explains how you can achieve what you want.

---

### Post by TheFu on 2022-01-09
[https://blog.jdpfu.com/2008/10/26/virtualbox-host-drive-access](https://blog.jdpfu.com/2008/10/26/virtualbox-host-drive-access) has my last effort at doing Ubuntu guest to Windows host disk access. The trick is they spell the disk device funny.  "vboxsf" and they don't follow Unix standards for /dev/{device name}, but rather use "whatever you entered in Windows" as the name.

BTW, 20.4 should be 20.04.  The format is {yy}.{mm}.  Other distros do it different.

---

### Post by Morbius1 on 2022-01-09
What is not clear - to me - about your post is if you have VirtualBox Shared Folders defined for the Ubuntu VBox guest.

On Win10:

Open the VirtualBox application.

Right click the entry you have for the Ubuntu guest then select Settings > Shared Folders 

What do you see? 
Do you have any shared folders defined?
And how are they defined? ... Read Only? Auto-mount? Mount point?

---

