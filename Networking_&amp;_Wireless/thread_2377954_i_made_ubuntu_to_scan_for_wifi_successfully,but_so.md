---
title: "i made ubuntu to scan for wifi successfully,but some times it does not."
date: 2017-11-18
forum: Networking &amp; Wireless
---

### Post by frequencyg on 2017-11-18
Hello.
I made my ubuntu to scan and detect my wifi card. I also did some script test to scan for wifi from them and it worked. But if i shutdown the VM or restart it. It will not respond. The wlan0 will be set to monitor by me sometimes cause thats how i made it to work. But its really annoying. It scans and then it does not?
Wireless script [http://paste.ubuntu.com/25987157/](http://paste.ubuntu.com/25987157/)

---

### Post by TheFu on 2017-11-18
Virtual machines usually have NOTHING to do with the actual hardware installed.  A VM will only see virtual network adapters, as setup by the hypervisor.  The best practice for VM use of networking is to use virtio network and disk drivers.  There are exceptions, but we can't really discuss those here.

So first question - is the wifi issue on the VM-host or inside a guestOS?

---

### Post by frequencyg on 2017-11-18
By restarting the VM i ment,rebooting ubuntu. My bad. Its only in Ubuntu guest OS

---

### Post by TheFu on 2017-11-18
> **frequencyg said:**
> By restarting the VM i ment,rebooting ubuntu. My bad. Its only in Ubuntu guest OS

So - a mistake?  Please mark the thread as solved to help others.  Would be helpful to clearly say what the issue was and whatever solution worked. Regardless of the reason, many people, me included, have been there.

---

### Post by frequencyg on 2017-11-19
Seems ok for now. I got to reboot ubuntu every time it happens.
So thats it

---

