---
title: "Network Shares very slow and disapear constantly"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by bclinton on 2007-11-12
Just installed Ubuntu and finally got rid of windows. I have a Buffalo NAS with a share set up for Photos. This worked great from my Windows machine but not so far with Ubuntu. The share shows up fine and I can open it after a reboot of Ubuntu. After a while the share seems to go away. The icon is there but when I click it it takes for ever and tells me unable to open it. After a reboot it works for a while then does it again.

Here is my FSTAB entry - is there something I can try different?

//192.168.5.3/Photos /media/Photos   smbfs  auto,username=,password=,uid=1000,umask=000,user   0 0

TIA

---

### Post by Peter09 on 2007-11-12
I have just discovered that _**any**_ machine on the network which has IPV6 enabled will affect all the other machines, making them slow down and also stopping SAMBA from showing shares properly. 

This is still a bit of a test but today I modified a machine which I normally do not touch, it had IPV6 enabled. When I disabled that, suddenly my other machines performance improved and network shares show up properly.

Still no DHCP name resolution though.

UPDATE
after working for some hours the ability to see shares has disappeared again ..... puzzled.

---

### Post by bclinton on 2007-11-13
Anyone have any suggestions. I completely deleted windows and for the most part my shares are unusable.

---

### Post by Peter09 on 2007-11-14
Try replacing the samba link with a cifs link, my share in fstab looks like this.

//192.168.0.8/nas1share		/mnt/nas1/nas1share		cifs	lfs,rw,user=anyone,pass=anyone

---

