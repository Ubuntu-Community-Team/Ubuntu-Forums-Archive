---
title: "Will adapter for USB 2.0 work in my 1.1?"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by flybiwire on 2008-08-19
I've got an old toshiba running Hardy right now and am trying to install a Belkin USB wireless adapter.  I've heard it's meant to work 'out of the box', but when I plug it in, nothing at all happens.  Before I try other options, I wanted the community's opinion on whether or not this would even work since my USB port is a 1.1 and the adapter is a 2.0.  Any ideas if it will work?

Thanks!

-FB

---

### Post by cariboo on 2008-08-19
We need a little more information what is the output of:

```
lsusb
```

with your adapter plugged in, and what is the output of dmesg when you plug the device in.

Jim

---

### Post by flybiwire on 2008-08-19
Jim, here's the output from the lsusb:

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 050d:705e Belkin Components 
Bus 002 Device 002: ID 06cb:0002 Synaptics, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Looks like it recognizes that something from belkin is plugged into the port.

---

### Post by flybiwire on 2008-08-19
Oh, and dmesg gives:

--see attachments parts 1 and 2

This looks like farci to me, can you make any sense from it?

-FB

---

### Post by flybiwire on 2008-08-20
Does this output tell me that the wireless adapter for USb 2.0 will work in the usb 1.1 port on my box?

Thanks!

---

