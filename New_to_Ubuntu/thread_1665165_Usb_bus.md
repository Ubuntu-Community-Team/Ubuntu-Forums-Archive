---
title: "Usb bus"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by erinbanwell on 2011-01-11
I have 2 kinects which I am trying to run at the same time. The problem is, I need them to be on separate usb busses, but they always load onto bus 001. a wireless mouse I use, normally loads onto bus 003 (unless I run it through a external 4-way usb hub, in which case it loads onto bus 001). Some other devices automatically load to bus 002.
      Does anyone know if its possible to:
-assign bus 002 or 003 to a specific port
      or
-Make one of the kinects automatically load to a bus other than 001?

Thanks for any help.

---

### Post by erinbanwell on 2011-01-12
A few more details:
running ubuntu 10.4

when i run
code:
   lsusb
i get back:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 021: ID 045e:00f9 Microsoft Corp. Wireless Desktop Receiver 3.1
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 066: ID 045e:02ae Microsoft Corp. 
Bus 001 Device 065: ID 045e:02ad Microsoft Corp. 
Bus 001 Device 064: ID 045e:02b0 Microsoft Corp. 
Bus 001 Device 063: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 054: ID 045e:02ae Microsoft Corp. 
Bus 001 Device 053: ID 045e:02ad Microsoft Corp. 
Bus 001 Device 052: ID 045e:02b0 Microsoft Corp. 
Bus 001 Device 051: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


the sets of three "microspoft corp."'s in a row represent the kinect cameras. as you can see they are all assigned to Bus 001. the "wireless desktop reciever" is the wireless mouse. 
How can I get the kinect to Bus 002 or 003 or 004?
and I have tried every possible combination of ports. the kinects always come up as Bus 001.
A little help please?

---

### Post by erinbanwell on 2011-01-12
I'm surprised no one knows the answer to this question. Anybody know there way around the usb busses? please help!

---

### Post by erinbanwell on 2011-01-15
SOLVED!

OK. I figured it out. It turns out laptops are hardwired to only allow certain devices (mouse, keyboard, etc) to designated usb busses.

---

### Post by onizukal on 2012-05-21
It seem that is an old topic but i hope you can help me . 

I got the same problem with 4 usb cameras when i plug into USB port. They are all seeming under the a specific bus . How can i change it ? 

Thanks in advance

---

### Post by oldsoundguy on 2012-05-21
> **onizukal said:**
> It seem that is an old topic but i hope you can help me . 

I got the same problem with 4 usb cameras when i plug into USB port. They are all seeming under the a specific bus . How can i change it ? 

Thanks in advance

Get a handful of card readers .. under 10 bucks each on ebay .. will show as separate drives and save all of the plugging and unplugging wear and tear and save your batteries in your cameras.
I always carry one in the gadget bag when I need to download to some computer somewhere.  KNOW that there will be no port conflict that way.

---

