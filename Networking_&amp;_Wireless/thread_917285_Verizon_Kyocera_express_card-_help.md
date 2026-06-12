---
title: "Verizon Kyocera express card- help"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by wgarider on 2008-09-11
I've read a few of the posts here about folks trying to get their Verizon broadband cards going - mine's a KPC680......

I've loaded Gnome PPP and gone through most of the postings about this but I think I am having a fundamental problem. I am new to ubuntu so bear with me please.

When I run lsusb, this is the output:
au@remote:~$ lsusb
Bus 006 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0c88:180a Kyocera Wireless Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
 
The output tells me the Kyocera card is at address 0c88:180a, right? Does that also indicate that it's at USB3 ?

When I'm using Gnome PPP, and I use the setup and detect, it finds nothing. One post suggested I modify the /etc/wvdial.conf - I did that too but I think the config line that the poster used "modem = /dev/ttyACM0" won't work because my Kyocera device is not at  /dev/ttyACM0, correct?

Any help would be really appreciated.
Thanks

---

### Post by wgarider on 2008-09-12
I'm guessing not many have run into this - can anyone who has set this up successfully offer any help?

---

