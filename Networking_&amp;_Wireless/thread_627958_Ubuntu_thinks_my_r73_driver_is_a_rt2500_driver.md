---
title: "Ubuntu thinks my r73 driver is a rt2500 driver"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by dynamethod on 2007-11-30
Hey there im using the rt73 driver for my USB wireless adaper (D-Link DWL-G122 C1) however it thinks that its a rt2500 driver, how do i make ubuntu recognise that its actually a rt73 driver? thanks

---

### Post by kevdog on 2007-11-30
Can you post the following

lsmod | grep rt

---

### Post by dynamethod on 2007-11-30
lsmod | grep rt
rt73                  307584  0 
parport_pc             37412  1 
parport                37448  2 lp,parport_pc
agpgart                35016  2 fglrx,sis_agp
usbcore               138632  5 usbhid,rt73,ehci_hcd,ohci_hcd

---

### Post by kevdog on 2007-12-01
Im not sure how you came to the conclusion why you think the rt2500 driver is being used.  The only driver being loaded is the rt73 driver as supplied by your output!

---

