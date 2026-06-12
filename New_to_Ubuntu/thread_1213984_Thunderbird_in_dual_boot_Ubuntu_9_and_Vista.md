---
title: "Thunderbird in dual boot Ubuntu 9 and Vista"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by il pepe on 2009-07-15
I got Thunderbird on both Ubuntu and Vista.
I would like to get the same accounts in both programs so that i can receive mails in both OS's.

Any help?

My original Thunderbird was Vista based so the documentation is on a NTFS disk.
I got Thunderbird in Ubuntu referring to the same account but now i get constantly the message that Thunderbird is already running whilst it isn't...

---

### Post by master_kernel on 2009-07-15
I can answer your first problem, not the second.

In both Ubuntu and Vista, edit the account settings (Edit > Account Settings in Ubuntu). Pick your account, go to Server Settings, and check 'Leave messages on server'. This will leave all your messages on the server. You can also check 'For at most __ days' if you want them to be deleted from the server after a number of days.

---

### Post by csabo2 on 2009-07-15
Are you trying to share a single profile between both OS's?

---

### Post by oldfred on 2009-07-15
Not sure about Vista, I have been dual booting XP and Ubuntu for 2-3 years and set up both Firefox and Thunderbird in a shared FAT partition. I used FAT because back then NTFS support in ubuntu was not as reliable as it is now. It has worked without any real problems since including all updates on both systems.
There is a flag file that gets set when you open Thunderbird and deleted when you close it. Perhaps you did not shut down correctly before rebooting?

---

### Post by il pepe on 2009-07-15
> **csabo2 said:**
> Are you trying to share a single profile between both OS's?
jup,

and i got it working only once, just after i put some changes in to place.
And now i always get an error that says thunderbird is already running whilst it isn't...

---

### Post by oldfred on 2009-07-15
This site has information on how to correct the problem. Could be a variety of issues but I guess it is the lock file.
[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

---

### Post by Arand on 2009-07-15
I think I have experienced the same message simply when TB is unable to access the profile, this usually caused by not having mounted the partition where it resides.

- Arand

---

