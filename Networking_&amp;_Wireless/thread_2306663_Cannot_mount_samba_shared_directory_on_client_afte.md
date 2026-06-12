---
title: "Cannot mount samba shared directory on client after restart"
date: 2015-12-17
forum: Networking &amp; Wireless
---

### Post by raac on 2015-12-17
Hello, I have a decent knowledge of linux although nowhere near an "expert", and I have a question for you guys.
I setup a personal server at home where I store all my files. The server is running Ubuntu Server 14.04.3 LTS on a 64 bit box.
I setup samba to share a directory for my internal network devices.

I have a laptop running Linux Mint 17.1 Rebecca and setup samba client on it, and it worked just fine (i.e. I was able to mount the drive and access the files located on the server).

This is the strange thing....after I restart my laptop (the client) and attempt to mount the shared directory from the server again I get the following error 

```
Retrying with upper case share name

mount error(6): No such device or address

Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


```

Now, if ssh into the server, the error goes away and I'm able to mount the drive (even if I don't do anything with the ssh session).


Something else I noticed is the following,

I'm also running plex media server on my ubuntu server box, after I turn on the laptop and use the browser the access the plex media, plex claims that it cannot find the files. However, after I ssh into the server (again without doing anything else with the session), all of a sudden plex can find the files.

I suspect is a configuration or something on the ubuntu server, any ideas on the cause of this?

Thanks

---

### Post by raac on 2015-12-17
[B]Something worth mentioning is that during the ubuntu server install, i chose the option to encrypt my home directory. The directory where plex is reading from and where the shared folder is located is under the home directory. 
Could that cause this behavior???[/B]

---

