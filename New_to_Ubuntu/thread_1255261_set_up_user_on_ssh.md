---
title: "set up user on ssh"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by desperado665 on 2009-09-01
How would I go about setting permissions for an ssh user to my pc to only see their home folder. I have given them a user account and login. To my surprise they are able to see my root folder. This isn't a good idea for several obvious reasons. 

Upon login I would like to be able to direct them to his created home folder an nowhere else. 

Any suggestions?

---

### Post by Bucky Ball on 2009-09-01
When you created a user account, did you do it through System->admin->Users and groups? You need to set the user to not have admin privileges at that point I'd say.

I'm on a client at the mo (my wife is using the ssh server) but it may have something to do with allow/deny files for ssh. We are using a slightly different setup with NFS and static IPs but will have a look later when I can get to the other machine.

---

### Post by desperado665 on 2009-09-01
Thanks for the reply Bucky.

Yes, I set them up as a user by using system>admin>users and groups. But I didn't see anywhere to deny admin privileges. Should I create a new group to put him in?

---

### Post by Bucky Ball on 2009-09-01
No. If you can delete the user and create another you will get the option on the account page 'User Profile'. Make that 'Unprivileged'. I think 'desktop user' might still be able to access the root. Not sure. I am using 8.04 so could be slightly different. 

Using NFS, I have setup a mount point and an icon to the server on the desktop of the clients. Then I setup in fstab only the folders on the server I wanted them to be able to mount at boot or any other time. It works great. My wife's computer can access her folder on my laptop server and nothing else and I can access just the partition I need to from my desktop. Cool. Tunneled through ssh so I could access remotely too I guess, though haven't needed to as yet.

Post back again when I am on the server. :)

This is from my wife's client machine fstab:

```
# Entry for /media/HPLappy/bigboy
192.168.0.111:/media/bigboy/Anna /media/hplappy nfs users,rsize=8192,wsize=8192,timeo=14,intr
```192.168.0.111=the server IP
 192.168.0.111:/media/bigboy/Anna=my wife's folder on the server
 /media/hplappy=the mount point for the 'Anna' folder on the client.

---

### Post by desperado665 on 2009-09-01
Thanks Bucky... that worked perfectly.

---

### Post by Bucky Ball on 2009-09-02
> **desperado665 said:**
> Thanks Bucky... that worked perfectly.

A pleasure. I like it when a plan comes together ... ;-)

On *my* desktop I have this in the /etc/fstab:

```
# Entry for /HPLappy/media/bigboy
192.168.0.111:/media/bigboy /media/hplappy   (permissions here).
```

Exactly the same as wife's desktop but just left off the 'Anna' part and mounts the 'bigboy' partition on the server to /media/hplappy rather than just the 'Anna' folder. Easy.

Good luck with it all.

---

