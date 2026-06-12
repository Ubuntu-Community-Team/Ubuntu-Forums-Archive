---
title: "Need some help tring to figure what the best way to is?"
date: 2005-11-08
forum: Networking &amp; Wireless
---

### Post by kelean on 2005-11-08
I have two computers hooked up to a dynex cable router that is hooked to a comcast cable modem.  

Comp #1 is a dell optiplex GX-110 667 mhz p-3 with 256 megs of ram.  dual boot  with win2k and ubuntu dapper.

Comp #2 is a dell optiplex GX-1 450 mhz p-3 with 128 megs of ram running Ubuntu breezy.

What I would like to do is be able to share files between the 2 computers and between the win2k and ubuntu on the same machine.

After looking here on the forums and doing google search I am getting really confused.  Im not sure if i need to run samba, bind, something else, or a combiation of things.  

When I did whatismyip.com on both computers I wet the same ip address.  Is that the ip address of the router or the cable modem

Any help would be greatly aprieated.

Thanks Kelean

---

### Post by ltmon on 2005-11-08
Best option for multiple computers with windows is Samba.  You can find howtos on wiki.ubuntu.com and ubuntuguide.org.  Probably some on this forum.

To find the internal IP address of any computer you have, type:

> ifconfig

at a command prompt.  The IP will be in the output somewhere or other, and will most likely be 192.168.0.x (where x is different for each machine).  Your router will be providing this.

The whatismyip.com is your external IP address, basically the cable modem.  Your router will have it's own internal IP address also (check your router docs to find that).

You can modify your /etc/hosts file also to give a hostname to each address so you don't have to remember them.

On such a small network I wouldn't bother with bind or anything like that.

L.

---

### Post by mips on 2005-11-09
[QUOTE=kelean]

What I would like to do is be able to share files between the 2 computers and between the win2k and ubuntu on the same machine.
[/QUOTE]

If you simply want to activate sharing over the network for the Ubuntu machines then use NFS server & client.

If you want to share between Ubuntu & Windows across the NETWORK then use SAMBA.

If you simply want to access the Windows partition from Ubuntu and dont need access via the network then simply mount the windows partitions in Ubuntu to gain access. With NTFS you will only have read access, FAT32 will give youu read/wright. I dont know of a way to access the Ubuntu partitions from Windows if you have that in mind.

Hopefully this helps a bit.

---

