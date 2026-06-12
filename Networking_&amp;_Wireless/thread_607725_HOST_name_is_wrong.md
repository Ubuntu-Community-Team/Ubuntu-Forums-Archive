---
title: "HOST name is wrong"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by Peter09 on 2007-11-09
Hi,
I have a laptop whose host name is 'Toshlaptop' in the hosts file and in the network manager configuration. However in my DHCP router it is registered as  Toshibalaptop, This is an old host name which I have recently changed. Where else do I need to change the name of the machine.....?

---

### Post by noob12 on 2007-11-09
The router gets the name from the host itself during the DHCP interaction.

Check the value shown by ```
cat /etc/hostname
```.  Change it if needed.

Probably what is happening is that the lease keeps getting renewed so the router is keeping the old one.  It should go away if you reset the router and then get a new lease; a softer approach would be to try explicitly to release the DHCP lease from your ubuntu host and get a fresh new one as follows:
```

# This releases your current DHCP leases on all interfaces
sudo dhclient -r

# wait for the release to finish

# then the following to get a new lease
sudo dhclient

```

---

### Post by Peter09 on 2007-11-09
Thanks,
it doesn't seem to have helped. I am having a lot of trouble with DHCP at the moment and I'm sure that there is a bug drifting around somewhere, although no one seems to have raised it as an issue.

---

### Post by noob12 on 2007-11-09
You mean also after resetting the router it didn't change?

---

### Post by Peter09 on 2007-11-10
Thats right, all as was before the reset.

---

### Post by noob12 on 2007-11-10
Check that **cat /etc/dhcp3/dhclient.conf** has the line 
```

send host-name "<hostname>";

```
just like that.  It should send the same hostname returned by the command **hostname**.  If you've put an actual fixed name there, make sure it is the new one that you want.

Other than that I don't have any suggestions.

---

