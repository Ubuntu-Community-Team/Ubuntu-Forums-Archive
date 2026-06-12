---
title: "SIOCSIFADDR No such device eth0 error while getting interface flags"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by kpm on 2006-09-10
I just installed a minimal server to set up XEN so I can play with virtual machines for a test... all seemed to go fine (I am following along in the Orielly book 'Ubuntu Hacks') but then after the server reboot, I lost the network... can't ping it or get out from it to anywhere.  Can anyone offer up some trouble shooting hints...

Thanks

---

### Post by blorgblorg on 2007-10-26
I have the same problem.  Here are more details for my account:

Base install of minicd network install, found here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Installing to a VMWare guest image.

The installer *was* able to connect via dhcp to the network (I believe this was to get an updated package list?).

When I reboot, it is not on the net, even though /etc/network/interfaces looks includes this:
auto eth0
iface eth0 inet dhcp 


dmesg | grep -i eth0 tells me it is registered as PCnet/PCI II 79c970a.
lsmod shows pcnet32 module loaded.

sudo ifup eth0 says "SIOCSIFADDR no such device" and several "eth0: ERROR while getting interface flags: no such device".

It also seems to be launching a dhcp client and it complains that there's already a dhclient pidfile.
I see no process whose name implies dhcp in the ps ax output.

vmware shows that the ethernet device is on in bridging mode.  I use this same configuration for a full ubuntu desktop install, which *does* correctly connect automagically.

What gives?  Why could the installer connect but no the installed?

---

### Post by modifiedmind on 2007-10-27
I am in the exact same situation. 

I know in my case I've mad a duplicate of a working vm directory and changed the file names and manually edited the vmx file. I also remember when asked by vmware server to change the identifier strings I said yes at the time I loaded the new vm. 

essentially I changed the nic out from under the OS and it doesnt recognize the "new hardware"

Where do I we change the new mac address and identifier strings to make this os like this new nic config? 

thanks.

---

### Post by modifiedmind on 2007-10-27
ok I found my answer. Hope this helps.

/etc/udev/rules.d/70-persistent-net.rules contains the MAC address to eth device mappings. Delete the lines like below, noting the module name on the "# PCI device" line:

1. PCI device xxxxxx:xxxxxx (module)

SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="xx:xx:xx:xx:xx:xx", NAME="eth0"

This removes the MAC to eth device mapping info. Now we need to restart udev to allow the change to take effect:

/etc/init.d/udev restart

Next step is to "bounce" the kernel module for the ethernet device. Use the module name from the 70-persistent-net.rules file noted above:

modprobe -r module
modprobe module

"ifconfig" should now show the eth0 interface as up and running.

---

### Post by mizar001 on 2007-10-31
Hi. 

I have the same problem (at least i think) . 

I don't find however this file 70-persistent-net.rules

What can i do ?

And furthermore , is that in the host or in the guest OS ?

Thanks.

---

### Post by modifiedmind on 2007-11-01
the the 70 was different from the original steps I found. I looked at the content of the file and it was the same. look for something with the "persisten net rules" in it.

---

### Post by wkoorts on 2008-04-26
Fantastic, I had this same problem and it helped me too thanks very much.

One thing to note for what worked for me though: in the persistent net file mine kept re-detecting the NIC as eth1 so my static options in /etc/network/interfaces weren't working.  I just changed eth1 to eth0 in the persistent net file, restarted udev, unloaded the module and reloaded it as explained above and mine worked fine.

Thanks a lot.

Regards,
Wayne

---

### Post by lokispundit on 2008-05-14
Thanks for help! 
The only difference I made was when I ran the modprobe it setup my new MAC as eth2. You have to go and edit the file back to eth0.
After that ifup came back great.

Thanks again

---

