---
title: "File Server Shared Folders"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by zuccs on 2007-08-02
hey all,

I have a ubuntu file server, and currenly I have it working with 1 directory I shared. I have since installed 2 more hard drives, and both come up in ubuntu, and I have added these to the smb.conf file with my other one that is working, but I cannot seem to connect to them from any other computer.

This is my file:

```


[global]
workgroup = HOME
interfaces = eth0
unix charset = UTF-8
security = user
map to guest = bad user
guest account = nobody
printing = cups
printcap name = cups
wins support = no

[share]
path = /home/daniel/share
wide links = no
case sensitive = no
strict locking = no
guest ok = yes
read only = no
create mask 0644
directory mask = 0755
available = yes
browsable = yes
public = yes
writable = yes

[data]
path = /media/disk-1
wide links = no
case sensitive = no
strict locking = no
guest ok = yes
read only = no
create mask 0644
directory mask = 0755
available = yes
browsable = yes
public = yes
writable = yes


```

Any reason why the first one works but the second one won't?

I get the error message on my mac: "Could not connect to the server because the name or password is not correct."

The second one is mounted as I can browse it in Ubuntu, but is not mounted when I start my computer. I haven't added it to FSTAB as yet, but I don't think that should matter..

Thanks for any help. I also have to add another hard drive, and a printer to my smb.conf, so any pointers to get this working would be ace, thanks.

---

### Post by dmizer on 2007-08-02
it matters a great deal if it's added to fstab or not.

if you do not mount disk-1 in fstab, the samba server daemon starts before the disk-1 is mounted, and samba will have no way of knowing that the disk is active.

if you are concerned about adding it to fstab, you can do the following:
```
sudo /etc/init.d/samba restart
```
after you manually mount your disk-1, and then you should be able to reach it on your network.

---

### Post by zuccs on 2007-08-02
Yeah I have done that a hundred times. After every time I have been adjusting the smb.conf file to try to get it work I have been restarting the samba daemon. Thanks for the suggestion though, it actually fits the problem perfectly.

I'll add to fstab and try again now. Thanks.

---

### Post by zuccs on 2007-08-02
Ok, I think I got it working...I have no idea why after I have been stuffing around with it for days. 

I added them both the hard drives to fstab, and restarted BOTH computers, and now the other computer can connect to both shares fine....

Thanks for your reply dmizer..

Now, how do I set permissions on ALL files and folders on these drives so every computer can use them? I noticed if I chmod recursively then it works. But when I add new files from another computer, the new files do not have the same permissions. How can I keep it consistant so everyone can access them at all times?

I usually do something like the following each time I try to fix it:

> sudo chmod -R 755 /dir/dir/dir 

Another thing...

Is my method for smb.conf above secure enough? It seems pretty open to me. I have a router with 128k WEP, is that enough, or should I put user security on the shared drives too?

---

### Post by dmizer on 2007-08-02
to solve your user problems, take a look at the first link in my sig (you'll need to add the force user, force group options).

as far as security is concerned, wep is fairly easy to crack so i wouldn't call it secure.  anyone gaining access to your local network will have access to your shares, so it is a concern if you're in a location where you may be in danger of getting your network cracked wirelessly.  but as long as you have a hardware firewall (router) between your server and the web, you shouldn't have to worry about being hacked from the web.

---

### Post by zuccs on 2007-08-03
Great reply thanks, I will look into the user security problems.

I read about how WEP can be poor, but one of the computers doesn't have (xp) SP2 installed so it doesn't support WPA. I might look at upgrading that, and then run WPA which I have read is much more secure since it is dynamic, correct? I don't think I am in a bad area since all my neighbours are old and probably never heard of the intraweb, but I think it is worth doing properly anyway

---

