---
title: "errors in the update process..."
date: 2011-05-26
forum: New to Ubuntu
---

### Post by werty2010 on 2011-05-26
i tried to update the software info first through the update manager and then through "sudo apt-get update".
after showing some lines where everything seems ok i got this:
```
...
Err http://archive.canonical.com natty InRelease                               
  
Err http://extras.ubuntu.com natty InRelease                                   
  
Err http://archive.canonical.com natty Release.gpg  
  Unable to connect to archive.canonical.com:http:
Err http://extras.ubuntu.com natty Release.gpg
  Unable to connect to extras.ubuntu.com:http:
Fetched 2,005 B in 2min 0s (17 B/s)
Reading package lists... Done
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/Release.gpg  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg  Unable to connect to extras.ubuntu.com:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

i doubt the cause of this to be newly installed software because i haven't installed anything new since 2 weeks ago.  
is there a problem with the servers or is it something affecting only me?
if it is me.how can i fix it?

---

### Post by beew on 2011-05-26
> **werty2010 said:**
> i tried to update the software info first through the update manager and then through "sudo apt-get update".
after showing some lines where everything seems ok i got this:
```
...
Err http://archive.canonical.com natty InRelease                               
  
Err http://extras.ubuntu.com natty InRelease                                   
  
Err http://archive.canonical.com natty Release.gpg  
  Unable to connect to archive.canonical.com:http:
Err http://extras.ubuntu.com natty Release.gpg
  Unable to connect to extras.ubuntu.com:http:
Fetched 2,005 B in 2min 0s (17 B/s)
Reading package lists... Done
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/InRelease  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/Release.gpg  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg  Unable to connect to extras.ubuntu.com:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.

```i doubt the cause of this to be newly installed software because i haven't installed anything new since 2 weeks ago.  
is there a problem with the servers or is it something affecting only me?
if it is me.how can i fix it?

Think it is the server, I have same problem with 11.04 and 10.10 all at the same time. Just wait.

---

### Post by audiomick on 2011-05-26
I think it looks like you are not reaching the server too. Just wait and try again later/ tomorrow/ next week.

If the problem goes on, then you can worry about it.

---

