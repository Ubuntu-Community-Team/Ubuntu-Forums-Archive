---
title: "View Open Shares"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by seawolf167 on 2010-05-30
I have some files shared in Ubunutu (made by right-clicking the folder, checking the "share folder" box, also checked the "Guest Access" box). Is there a way to view who is viewing the share files and what they are viewing? 

Additionally, is there a way to kill their open share (for example if they are holding a document open but you need to edit it and want to kill their open version, preferably without having to un-share the folder, then re-share the folder after I'm finished)

I know about the 'w' command to see who is logged in / running processes, but the people accessing the shared files do not have an account on the computer hosting the shares.

---

### Post by mikewhatever on 2010-06-01
There are logs in /var/log/samba, named after usenames and ip addresses of users that connected or tried to. I don't know of any way to tell what files they viewed, etc.

---

