---
title: "vmware on gutsy"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by sefs on 2007-10-25
Hey all anyone has vmware running on gutsy?

I have a problem since the upgrade from feisty whereby I can get unto the internet from the VM machine.  I can how ever ping the host and other computers on the network.  I can also browse other computers on the network if they have shares and see them in network neighbour hood.  
But 
1) can't browse the net
2) can't ping router.  getting a ping time out.

---

### Post by veloce on 2007-10-25
how are your virtual networks set up?  If you installed from tar ball it will have asked you to re-set them all up.  Did you do this the same as your previous install?

---

### Post by sefs on 2007-10-26
Well I just reran the config.pl script.  And when it got to the networking part I told it to reconfigure it fresh.  Is that what you mean?

---

### Post by sefs on 2007-10-28
ok its a bug between vmware and the latest kernel in gutsy.  The temporary fix is here [http://communities.vmware.com/message/761031#761031](http://communities.vmware.com/message/761031#761031) until vmware gets around to officially fixing it.

---

