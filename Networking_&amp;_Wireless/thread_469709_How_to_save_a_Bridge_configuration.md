---
title: "How to save a Bridge configuration"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by Harry_Callahan on 2007-06-10
Hello to all,

I'm stuck for another month with a ADSL router that has only one ETH port, since I have a Dlink Access Point and need wireless connectivity, I decided to try a bridge with 2 ETH cards. I found this guide:

[http://linux-net.osdl.org/index.php/Bridge](http://linux-net.osdl.org/index.php/Bridge) (Manual configuration at step 5)

Everything works fine, but I have a little problem: everytime I shutdown Ubuntu, the bridge disappears...I have to use the procedure again

Is this situation normal or did I mess up somewhere? Is it possibile to save the bridge configuration somehow?

Ubuntu 10.06
bridge-utils installed
1 ETH PCI Adapter
1 onboard ETH

Thanks to all

---

### Post by thelinuxguy on 2007-06-10
Put the commands in /etc/rc.local to execute them at boot time.

---

### Post by Harry_Callahan on 2007-06-10
> **thelinuxguy said:**
> Put the commands in /etc/rc.local to execute them at boot time.

Thanks for the reply, there is another problem I forgot to mention in my first post:

rebooting several times I have noticed that the ETH PCI Adapter gets "called" eth1 and sometimes eth2. After putting the commands in rc.local, on the first reboot it didn't work because the commands had eth2 and Ubuntu assigned eth1 to that card. The 2° time I rebooted, Ubuntu assigned eth2 to the card and all is working fine. Is there anyway to fix this problem?

Thanks and best regards

---

### Post by thelinuxguy on 2007-06-10
For assigning fixed network interface names, you need Udev rules. 

Look at [http://www.mepis.org/node/13039](http://www.mepis.org/node/13039) or
"Examples using udev" section at [http://www.debianadmin.com/rename-network-interface-using-udev-in-linux.html](http://www.debianadmin.com/rename-network-interface-using-udev-in-linux.html)

A general howto on writing udev rules can be found at [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

### Post by Harry_Callahan on 2007-06-10
> **thelinuxguy said:**
> For assigning fixed network interface names, you need Udev rules. 

Look at [http://www.mepis.org/node/13039](http://www.mepis.org/node/13039) or
"Examples using udev" section at [http://www.debianadmin.com/rename-network-interface-using-udev-in-linux.html](http://www.debianadmin.com/rename-network-interface-using-udev-in-linux.html)

A general howto on writing udev rules can be found at [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

Thanks again, everything is working great now! I had a little trouble working on the /etc/udev/rules.d directory, then I simply added the MAC address of the PCI ETH Adapter to the iftab file in /etc and BINGO

I called the PCI card eth3 to make sure the changes were correct, after I changed the bridge configuration

Thanks again!

---

### Post by thelinuxguy on 2007-06-10
You are welcome.
Just to clarify, you had to write the udev rules AND add the MAC address to the iftab file?
Or was it one of them? Which one?

---

### Post by Harry_Callahan on 2007-06-10
> **thelinuxguy said:**
> You are welcome.
Just to clarify, you had to write the udev rules AND add the MAC address to the iftab file?
Or was it one of them? Which one?

the udev rules didn't work(local rule file in /etc/udev/rules.d), so I delete that file and added "eth3 mac 00:xx:xx:xx:2F" in the iftab file. So, the the 2° procedure in [http://www.mepis.org/node/13039](http://www.mepis.org/node/13039)  does the job

thanks

---

