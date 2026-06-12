---
title: "machine not seen on network"
date: 2014-04-10
forum: Networking &amp; Wireless
---

### Post by wolfeagle99 on 2014-04-10
I have three machines, one rynning win8, one running win7 with vm of 12.4 ubu running, and one machine running ubuntu12.4. Ubuntu sees the other machines and connects to them no problems. However it does not see itself on the network and neither do the other machines inclubing the vm. I even imported smb.conf from working vm to replace the copy on the ubuntu machine but it changed nothing Any ideas on why it does not show up on the network. I'm not talking about shares but the machine itself being invisable on the network. Any help will be greatly appreciated.

---

### Post by Kirboosy on 2014-04-10
Welcome to the forums! :D

Do you have a firewall running on the computer?

Since you copied over the smb.conf I don't think its a matter of WORKGROUPS not being setup properly. Double check the setup of the workgroups and make sure they match on all machines.

```

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of  
 workgroup = WORKGROUP
```

Also, you must restart the samba service if you make changes to smb.conf

```
sudo service smbd restart
```

---

### Post by wolfeagle99 on 2014-04-10
Thanks for the response. The workgroup matches on all machines. Ive also retarted smbd a number of times.Still not working

---

### Post by tripp98 on 2014-04-10
What dns server are you using?  if it is your router, log into your router and make sure your ubuntu machine is shown in the dhcp address.  from the ubuntu machine can you ping the name of your ubuntu machine?  i.e.  ping my-ubuntu
does it respond with the same ip that is in ifconfig?

---

### Post by wolfeagle99 on 2014-04-10
pinging the machine name works on all machines but it still is not showing in any of the network veiws. Yes I'm using the router dns

---

