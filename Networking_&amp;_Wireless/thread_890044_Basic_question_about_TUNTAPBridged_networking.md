---
title: "Basic question about TUN/TAP/Bridged networking"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by besson3c on 2008-08-14
Hello,

My bridged network is working. I have a vnet0 and br0 interface, and everything seems to be fine. Would there be any point, any particular advantage for me to setup a TUN/TAP interface? Why is it that many guides available online detail using TUN/TAP for enabling bridged networking? In my case, this is in the context of providing networking to VM guests.

---

### Post by bab1 on 2008-08-14
A rose by any ther name is still a rose...

I think it is just a naming convention.  The bridge (br0) is to connect the virtual interface to the real hardware.

Edit: In doing a bit of reading, it looks like your vnet0 is the equivalent of the tun/tap arrangement.

---

### Post by besson3c on 2008-08-15
> **bab1 said:**
> A rose by any ther name is still a rose...

I think it is just a naming convention.  The bridge (br0) is to connect the virtual interface to the real hardware.

Edit: In doing a bit of reading, it looks like your vnet0 is the equivalent of the tun/tap arrangement.


Interesting... I don't know where that came from, but maybe I'm basically already doing TAP using different terminology, like you said?

---

### Post by bab1 on 2008-08-15
Originally KVM used QEMM libs and TUN/TAP to create the virtual NIC.  TUN is the IP tunnel and TAP is the Ethernet frame (tap to the NIC).  These to virtual entities are then bridged to the physical network. TUN/TAP for the guest and the br0 to the host network.

---

### Post by besson3c on 2008-08-15
So how is it that I have networking without an explicit TAP interface on the host machine? If these are for the guest, where exactly are these interfaces maintained?

---

### Post by bab1 on 2008-08-15
TUN/TAP is virtual!  It only exists in the software.  :-)  Another example of a virtual interface is the loopback interface (it's 127.0.0.1).

---

### Post by besson3c on 2008-08-15
So why is it that some guides for setting up bridged networking involve setting up this device node, whether others (and the one I used) simply require some ifconfig commands to bring up the br0 interface?

---

### Post by bab1 on 2008-08-15
I'll bet the conf file sets up the device.  It's all software.  You would have to look at the underlying code to see how it is done.  The end result is the same.  You must be useing the latest version of KVM.

---

### Post by besson3c on 2008-08-15
Yup, although the same technique I used for setting up my networking also works in Xen as well...

Maybe it's just a matter of the software improving so that bridged networking is less complicated to setup.

---

### Post by bab1 on 2008-08-15
Yep, I'm sure of it.  Later versions are usually improvements; but not always.  ;-)

How 'bout you mark this solved!

---

### Post by besson3c on 2008-08-15
Thanks for your input!

---

