---
title: "network tweaking tips and tricks?"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by troutbum13 on 2008-02-27
I have been looking at network throughput and playing with some settings..

 My LAN consists of a gutsy server (on-board gigabit NIC), a gutsy workstation (on-board gigabit NIC), netgear gigabit switch and cat6 cabling...4 media players, 2 laptops on a WAP.

Background:I tested using a 1.1GB test file.  I am using LVM on the server side and hdparm shows read rates ~ 50MB/s for server and client...1-2 samples for each scenario is all I took.

So here is out of the box performance
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=60989&stc=1&d=1204135851[/IMG]

Download speeds suck, and any drag and drop through nautilus was really bad...

After some reading I disabled IPv6
```
 
$sudo gedit /etc/modprobe.d/aliases

```
you need to edit 
```

alias net-pf-10 ipv6

```
to 
```

alias net-pf-10 off

```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=60990&d=1204135847[/IMG]
This seemed to make a big difference for download speeds, nautilus is still pretty damn slow...especially if you are using smb over a mount.

I wanted to try jumbo frames, but my server nic wont do 9000 MTU so I had to set it to 7000 MTU
```

trout@server:~$sudo ifconfig eth0 mtu 7000
and
trout@workstation:~$sudo ifconfig eth0 mtu 7000

```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=60991&d=1204135847[/IMG]

Iperf showed a decrease in upload speeds and a bump for download but the deltas in terms of real performance were not very significant...with one exception nautilus w/ smb got lots better.


Anyway I am just a hack when it comes to networking, but I think I will go back to 1500MTU, jumbo frames didn't seem to have a very big effect, ipv6 did...It seems it is better to use CLI to move files on the network as opposed to drag and drop...

anyone else have any tips or tricks for tweaking network performance? I would like to see sustained 300mbps if possible.

---

### Post by troutbum13 on 2008-02-27
I mounted the shares with NFS instead of CIFS or SMB and retested, results seem decent.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=61038&stc=1&d=1204157663[/IMG]

---

