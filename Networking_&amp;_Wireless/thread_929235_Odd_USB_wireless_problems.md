---
title: "Odd USB wireless problems"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by Swimerdude on 2008-09-24
Hello all,
Sorry to bug peeps but I'm at a loss.  I installed ubuntu on a Presario 2100 about 6 months ago.  The boardcom wireless didn't work out of the box and after 2 weeks I gave up on it and bought a dwA 140(i think A).  I installed the windows wireless driver program, installed the window drivers and it worked like a charm.  2 days ago the network settings stalled while putting in a wep key, so I forced a quit.  After that whenever I plug in the adapter, it now flashes at me the whole time, and gets insanely hot, as if it was in constant use.  No new programs will populate the desktop after I plug it in.  To also not my network configuration page goes blank also after plugging this adapter in.  When starting up with the adapter in UBUNTU hangs up on a deamon printing system or something similar.  When shutting down, it also hangs at times and I have to just hold the power button down to get the computer to shut off.
When running the recovery off of the the ubuntu start I get that there are no broken packages.  The below errors

Errors
ERROR:root:Could not find def gateway info in /proc 
Traceback (most recent call last): 
  File "/usr/share/hwtest/scripts/internet_test", line 132, in <module> 
    sys.exit(main(sys.argv[1:])) 
  File "/usr/share/hwtest/scripts/internet_test", line 118, in main 
    host = route.get_default_gateway() 
  File "/usr/share/hwtest/scripts/internet_test", line 81, in get_default_gateway 
    t1 = self._get_default_gateway_from_bin_

If anyone has any ideas on what I can check or do to fix this problem I'd appreciate it a lot. 
Thanks,
Swimmerdude.
 P.S. UBUNTU ftw, and sorry about my English, I can read but not write well.

---

### Post by Crafty Kisses on 2008-09-24
I'd like to see the results of this command:
```
lsusb
```

---

### Post by Swimerdude on 2008-09-24
Bus 001 Device 003: ID 07d1:3b11 D-Link System 
Bus 001 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse 
Bus 001 Device 001: ID 0000:0000  
jonathan@Beastie-laptop:~$

---

### Post by Swimerdude on 2008-09-25
Hello anyone else know anything?

---

### Post by Swimerdude on 2008-10-06
Hello all, so I killed the adapter.
THanks for your help.

---

