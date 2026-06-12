---
title: "connecting to remote folder"
date: 2013-10-14
forum: Networking &amp; Wireless
---

### Post by acquacheta on 2013-10-14
Hi everybody!
I'm trying to connect with my university remote filestore, but I'm can't..
[Here]("http://www.inf.aber.ac.uk/advisory/faq/95/") is explained what to do on Windows or Mac, and [here]("http://users.aber.ac.uk/en/resources/network-drives-linux.php") I found a guide about how to do it with ubuntu, but it's not working to me (at the end of all the steps, I can't access to the mounted folder).
I can access to the storage through Konqueror (I'm using KDE), but I would like to access to it also without it.

Thanks!
acquacheta
I used to wanna change the world. Now I just wanna leave the room with a little dignity.

---

### Post by acquacheta on 2013-11-01
No answers? Did I wrote anything wrong or unclear? 
Or should I post it somewhere else?
Please help me!

Thanks
acquacheta
[COLOR=#000000]I used to wanna change the world. Now I just wanna leave the room with a little dignity. (Justin Bond)[/COLOR]

---

### Post by drmrgd on 2013-11-01
Are all steps completing successfully or are you getting an error?  What do you mean 'can't access to the mounted folder' (are you getting a permissions issue (permission denied, operation not permitted, etc.) or a file or directory not found error)?  How are you trying to access that directory - through the terminal?

---

### Post by Lars Noodén on 2013-11-01
What happens when you open your file manager, press ctrl-L and then enter your URI?

```

sftp://university_username@central.aber.ac.uk/

```

You may have to adjust the path a little/

---

