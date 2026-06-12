---
title: "I am confused what is going with this setup"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by asifsehzaad on 2008-05-14
I am all confused now....here is the setup of my system.
1.) I have virtualBox from virtualbox.org having ubuntu 8.0 server installed as one of the guest OS running on my laptop with windowsxp ( i am on a wireless network/adsl at home 192.168.1.*)
2.) While installation of ubuntu i selected the networking part to use dhcp... ( which gives it a 10... range ip address) and it can update itself over the internet (all this while my laptop is on the home wireless network)

I want to connect to ubuntu from my windowsxp... telnet/ssh into it... so i change the ```
/etc/network/interfaces
``` to reflect that the interface eth0 should be static ip (192.168.1.12 and all the network stuff i got that from [http://www.ubuntugeek.com/...]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html"))

and i update my windows host file to say 192.168.1.12 is "mydevhost" and from windows i am not able to ssh into ubuntu on virtualBox.

---

### Post by ilrudie on 2008-05-14
Can you ping the Ubuntu VM?  Did you setup sshd on the VM?

---

### Post by asifsehzaad on 2008-05-14
I can't ping both ways.... from VirtualBox to my desktop and desktop to my virtual box...

but when i put the configuration in /etc/network/interfaces as dhcp instead of static... I can access the internet though...

I just want to access my virtualBox from windows and vice versa... accessing internet from ubuntu... is a very secondary thing for now...

---

### Post by asifsehzaad on 2008-05-14
> **ilrudie said:**
> Can you ping the Ubuntu VM?  Did you setup sshd on the VM?

During installation I selected the openssh... option... so Yes.. i installed the sshd... and withing the VM i can do a 

```
ssh localhost
```successfully... but since i can't ping the VM ...my guess is that i can't even... ssh to it..but didn't touch any of the config files....

---

