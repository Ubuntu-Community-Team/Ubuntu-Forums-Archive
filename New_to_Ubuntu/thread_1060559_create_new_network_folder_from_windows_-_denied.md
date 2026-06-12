---
title: "create new network folder from windows - denied"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by powel212 on 2009-02-04
Hi

I want to allow anyone on my network to create a new folder on my file server. It is a Ubuntu file server with 4 windows boxes connected to it. I have it shared now and can transfer files but I can not create new folders on the Ubuntu file server from the windows boxes. I can create files but not folders.

How to fix?

Thank you

---

### Post by powel212 on 2009-02-05
My interim solution.

assign new user ownership of parent folder on file server. assign password to folder and ownership. 

from windows connect to network folder as the newly assigned user with password.

I would still like to allow all users to access this folder and don't know how.

Any help is appreciated.

powel

---

### Post by Kellemora on 2009-02-05
Hi Powell

I'm probably not the best person to answer this, as I had to stumble through the same thing recently.

First, each user must be listed in the sambausers folder!
Then you have to set the permissions for each user individually under system administration users and groups.  Make sure ACCESS External Storage Devices is checked as well as Share files with local network.

Under Properties for your File Server Folder, here too it it must show create and delete files for the Group.  Read and Write!

Then go down to Others and make that line read Open Only and Read Only.

I can't remember now if there was anything else I had to change.

I may have had to do a chown command to that folder from root.
Here is what I THINK it was, so don't use it until someone verifies it is correct!
```
sudo chown -R group:group /media/sdb/File-Server
```
It could also have been I used
```
sudo chown -R user:group /media/sdb/
``` and made the whole hard drive usable by the group.
However, the ONLY Shared Folder on this drive is the folder named File-Server, which makes all folders inside it shared.

I write this stuff down, but when the writing gets cold, I can't read or understand it anymore, hi hi............

TTUL
Gary

---

### Post by powel212 on 2009-02-06
Thank you.

I'll have a look into those options.

Thanks.

---

### Post by pqqp on 2009-02-06
<object width="480" height="295"><param name="movie" value="http://www.youtube.com/v/9J9J6fpWGfg&hl=en&fs=1"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/9J9J6fpWGfg&hl=en&fs=1" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="480" height="295"></embed></object>

---

