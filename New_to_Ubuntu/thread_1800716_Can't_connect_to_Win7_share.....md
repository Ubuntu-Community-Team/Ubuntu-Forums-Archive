---
title: "Can't connect to Win7 share...."
date: 2011-07-09
forum: New to Ubuntu
---

### Post by J B on 2011-07-09
Ok, I have searched and searched, and nothing I have run across yet has solved this issue.  I'm a complete noob here.  I've installed Natty on my laptop, and need to hit a couple of shares on my Win7 box.  Initially, the workgroup never even showed up under "Network".  After re-sharing a share, the computers on my network all showed up.  Clicking on the Win7 box in network gives me an error: "Unable to mount location, failed to retrieve share lift from server."

Trying to hit it from file, connect to server only leaves me with "Could not display "smb://[user]@[server]/[share]/"."

Any ideas?

---

### Post by mrhhug on 2011-07-09
its most likely a windows sharing issue. make sure that on the windows share your users are set. if you want to make this public just add the user "everybody" under the share and give them the permissions you want. I think 7 has a password protected sharing thing somewhere in the network setting. I feel it is easier to go from a linux server and let windows share from there.

---

### Post by J B on 2011-07-09
I've followed every recommendation I've seen, save for not having password protected shares.  I might try that, but it seems as if there is another issue.  This machine serves as my file server and HTPC.  I'm not opposed to running Ubuntu on it....once I'm comfortable with Ubuntu and I can have all the same functionality.

But I'd really like to get this issue with shares figured out.

---

### Post by mrhhug on 2011-07-09
if you can setup a test share without passwords. then add users later

---

### Post by Morbius1 on 2011-07-09
And what happens when if instead of this:
> smb://[user]@[server]/[share]You use this:
> smb://[user]@[ip-address-of-server]/[share]

---

### Post by J B on 2011-07-09
Well I'll be damned.  That worked.  Previously, it didn't.  I'd get a similar error to using the server name.  But that was before I did the re-share operation that actually allowed the computers to show up on the network.  

Problem solved.

---

