---
title: "System resume on SMB connection."
date: 2010-08-31
forum: New to Ubuntu
---

### Post by t0mmyK on 2010-08-31
Hi There,
 
Is it possible to wake ubuntu server from suspend via incoming smb request?
 
I don't want to manually send WOL packets before each SMB access.
It shouldn't be a problem since it's often used in NAS devices based on linux kernels.
 
Regards,
t0mmyK

---

### Post by theDaveTheRave on 2010-08-31
+1 for this question.

also is possible to wake the system on specified ports?

I'm thinking auto wake up on port 80 (for a web server), and the ports for DHCP, DNS, mail server etc...

David

---

### Post by t0mmyK on 2010-09-02
Really no one who can lead on track here? ):P
 
Regards,
t0mmyK

---

### Post by DrPotoroo on 2010-10-26
I'm looking at this myself. My ethernet adapter in my server only supports wake on magic packets, so there has to be something on the network to detect the SMB connection and add a magic packet. I'm guessing I could modify my router/modem firmware to do it, but I think it would be supremely complicated.

---

