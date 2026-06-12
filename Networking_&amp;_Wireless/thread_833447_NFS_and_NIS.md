---
title: "NFS and NIS"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by EXCiD3 on 2008-06-18
So ive got workstations using NIS and NFS to login and mount /home from the server. I would like to use local accounts on the machines just in case the server was to go down and i am not able to come and fix it right away. Is there any way for me to configure this? I used the tutorials in the Wiki to set them both up and am using automount for the NFS share.

---

### Post by EXCiD3 on 2008-06-18
I think ive managed to get the problem down to this: if the workstation cannot mount an NFS share at /home...then the /home folder isntead of using what is in the root directory at /home (my local user account home folders) it makes /home empty. Is there any way i can get around this?

**UPDATE: **I just found this tutorial for solaris: [http://support.attachmate.com/techdocs/1831.html](http://support.attachmate.com/techdocs/1831.html) does this work with ubuntu and/or does anyone have a link to a tutorial like this for debian/ubuntu?

---

### Post by EXCiD3 on 2008-06-18
8-[ bump 8-[

---

### Post by Hieu on 2012-01-06
I have the same problem when both **network users** (via NIS/NFS) and **local users** of my work station need the folder */home/* to use.

Is there any method to redirect the $HOME of local users to */local_home/ *(or $HOME of network users to */net_home*) for example ?

Thank you,

---

### Post by Hieu on 2012-01-06
I find the solution by using the command:
 #usermod -d /home_local/username -m username

---

