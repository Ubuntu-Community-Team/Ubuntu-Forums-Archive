---
title: "How do I make Samba shares writeable and login protected on Mythbuntu 8.04?"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by tominglis on 2008-08-24
Dear All,

I have Mythbuntu 8.04 on my media PC. I have enabled Samba in the control centre, and the MythTV music, videos, pictures, and recordings folders are shared.

I can open these folders and read the contents with any computer on my wireless network.

I would like to be able to make these folders login protected, and then when I login with my details to make them writeable. But I am not sure how to do this. I have tried editing options in the Shared Folders menu item, and also changing the permissions on the folders themselves.

Any help would be tremendously appreciated!

Many thanks,

Tom

---

### Post by bab1 on 2008-08-24
I believe this is doable, but difficult.  You will have to use a combination of Samba (smb.conf) configuration.  Read "Samba3 by Example" and Linux ACL's.

I don't think you can do it with a few mouse clicks.

---

