---
title: "Can only access samba share on SOME Windows7 computers"
date: 2014-04-06
forum: Networking &amp; Wireless
---

### Post by Tony_Lillie on 2014-04-06
I have Ubuntu 12.04 running with a Samba share configured that can be seen on all of my other computers, some Ubuntu some Win7. This is a public type share that does not require a password. 

The problem is one Win7 machine demands login credentials (none of the others do). I've restarted all the machines and double checked my smb.conf file and can't seem to fix it. What could be causing this??

For reference, when setting up the share, I followed this tutorial exclusively: [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

---

### Post by carl4926 on 2014-04-06
That is odd
I'm no expert with samba
In fact I gave up setting it up on my box and now just use the facility in my router for attached USB storage

---

### Post by Tony_Lillie on 2014-04-06
Yes, very odd and irritating. Since I have not yet found the cause or a solution, I attempted entering some credentials in the login dialog that the one Win7 machine presents, and I was successful when entering the fully qualified username and password for the share i.e. username: myuser@myshare & password: myuserpassword. Though I am glad it worked, I hate having a loose thread hanging and REALLY want to know why this is happening on a share that is totally public and accessible from ALL my other machines (regardless of OS) without login credentials.

Anyone?? Ideas? Thought?

---

