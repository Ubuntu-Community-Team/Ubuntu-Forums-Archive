---
title: "SSH n00b"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by KdotJ on 2010-03-21
Hey I have some n00b questions regarding ssh,

I have a server at home running Ubuntu Server 9.10,
And I have a laptop running ubuntu and a desktop running openSUSE.
How do I ssh into the server?

i have tried:
```

ssh username@address

```

where username is obviously the username and address is the IP address of the machine I want to ssh into.
However, I keep getting the message "Connection Refused" when I attempt it.
Do I need to enable or allow the connection on the server box? or am I just being a total n00b and missing lots of things?

any help would be great!

---

### Post by cariboo on 2010-03-21
Do you have openssh-server installed on the server. TO use ssh you must have the ssh into the user on the server eg: IF the user's name is frank, you would type:

```
ssh frank@server
```

from the remote system. For more on ssh, have a look [here]("https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html").

---

### Post by KdotJ on 2010-03-21
all sorted now, thanks for the help :)

---

### Post by asmoore82 on 2010-03-21
I love SSH, I wish someone had told me when I was a n00b that you can use
SSH, sFTP, X11, VNC, and rsync through this one magical service/port ;).

Remote file access with SSH is as easy as "Places -> Connect to Server" and choose "SSH" as the "Service Type"

---

