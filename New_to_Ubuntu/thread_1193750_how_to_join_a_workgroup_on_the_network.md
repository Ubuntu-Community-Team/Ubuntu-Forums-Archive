---
title: "how to join a workgroup on the network"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-06-21
64 bit Jaunty on amd64 installed from Jaunty live CD.

During installation I forgot to specify the workgroup.

Is there a way to join the workgroup from a terminal command, or must I re-install from the live CD?

I know it is not in System>administration>network tools.

Thanks in advance.

---

### Post by louieb on 2009-06-21
During the install you set a host name (default is Ubuntu) not the same as work group.

To join a work group look under places>network.

---

### Post by raymondvillain on 2009-06-21
Well, louieb, I looked under places>network but I don't see how to join.

Yes, I should have specified it when I installed Ubuntu, but I was hoping to correct the matter without having to re-install.

Am I missing something?

Will this problem go away after I install Samba?

---

### Post by Captain_Glen on 2009-06-21
```
sudo gedit /etc/samba/smb.conf
```

```
# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = workgroup
```

change what workgroup = to what you want it to be.

---

