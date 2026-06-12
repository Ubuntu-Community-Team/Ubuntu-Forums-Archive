---
title: "[SOLVED] No Network!!!"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by Liv3dN8as on 2008-10-13
Please Help! My newest problem is no network at all. I followed advice from [post=5958688]here[/post]. This was a thread from my original problem. 
When I do this ```
sudo dhclient eth0
``` I get this ```
/lib/dhcp3-client/call-dhclient-script, ...): permission denied
``` on the bottom line. 

Any outputs needed, let me know.
Thanks in Advance!

---

### Post by Liv3dN8as on 2008-10-13
Wife will be home any minute. No time to fix things after that. Please and Thank you!!!

---

### Post by Iowan on 2008-10-13
First time I've seen that one... Navigate to /lib (in a terminal) issue **ls -al |grep dhcp**. see if permissions match mine (which is drwxr-xr-x). Inside the directory is just the one file - mine looks like: ```
-rwsr-xr--  1 root dhcp  2956 2007-09-07 10:32 call-dhclient-script
```

---

### Post by Liv3dN8as on 2008-10-13
Hi. Sorry it took me so long, like a said my wife was on her way home and now Heroe's is on. But here is what I got: drwxrwxrwx

And it is not owned by root it is owned by me.

---

### Post by Iowan on 2008-10-13
S'pose I coulda/shoulda mentioned /lib/dhcp3-client is owned by root root. If  call-dhclient-script is owned by your group, it should probably be **chgrp**'d to **dhcp**. I suspect **dhclient** runs as that user/group.

---

### Post by Liv3dN8as on 2008-10-13
Ok so I tried this ```
sudo chgrp -hR root dhcp3-client
``` and ```
sudo chown root dhcp3-client
``` and now when I do ```
ls -al|grep dhcp
``` I finally get ```
drwxrwxrwx 2 root root 4096 Date Time dhcp3-client
``` Thanks for getting me this far, what can I do next?

---

### Post by Liv3dN8as on 2008-10-13
Everything is starting to look better, thanks Iowan. Unfortanetly it is time to go to bed. I have classes tomorrow in Madtown at MATC so I might not be back till late. 
I ran ```
sudo dhclient eth0
``` and everthing looked better, except one part. I will have to post the output tomorrow since I found out my flashdrive doesn't work either but it is listed in /etc/fstab. I saw some threads that look promising for an answer to that one.
Thanks again so far!

---

### Post by Iowan on 2008-10-14
> **Liv3dN8as said:**
> Thanks for getting me this far, what can I do next?Depends on whether **dhclient** works (or what part doesn't...)
If it's still getting the "permission denied", try **ls -al /lib/dhcp3-client** If line is not similar to the one in post #3, (Specifically the group) you may need to **sudo chgrp dhcp /lib/dhcp3-client/call-dhclient-script**

---

### Post by Liv3dN8as on 2008-10-15
Thanks Iowan, I will try that, but my permissions are so messed up that I think the only way around it is to back up my important data to an external and start over. That is why I marked it solved. None of my files belong to root and changing them all back is too time consuming for my schedule.
Thanks though, I appreciate all your help. And am sure I will need it in the future. Thanks again!

---

