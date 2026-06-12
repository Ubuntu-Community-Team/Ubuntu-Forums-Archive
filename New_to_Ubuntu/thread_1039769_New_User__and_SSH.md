---
title: "New User  and SSH"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by lumpyone on 2009-01-14
I hope this is getting posted in the right place. I’m new to linux and have recently installed Ubuntu 8.10 on the recommendation of a friend.  I’ve finally got it up and running after dealing with a GRUB 18 error, and now I’m working on getting my SSH settings established. However, every time I attempt to connect to the computer remotely through PuTTY I’m unable to establish a connection.

I’ve a cable connection going through a Netgear WNR3500 wireless router.  I was reading on setting up the SSH and my understanding is that the SSH in Ubuntu is already turn on, correct?  I wanted to make sure and know how one tells if its turned on? Is there a process view or something that will tell me if its running?

So here is what I’ve done to allow me to connection to my computer remotely using SSH:

1) I’ve set up a dynamic DNS with dynDNS.com so I can find the computer on the web, since I get a dynamic IP with my provider. 

2) I’ve configured my router’s port forwarding and Dynamic DNS settings to allow the computer to be reached.  

3) I’m using PuTTY to make the connection remotely. I’ve created a connection profile, using the domain name I set up with dynDNS, and the port number (I’m just using the default 22 at the moment).  However, every time I attempt the connection I get the following error - Network error: Connection Refused.

I’m at a loss of where the issue may be. I’ve checked all the settings I can think of and all seems to be okay but I’ve this feeling I’m missing something small. 

Are there permissions I need to set or change that I’ve missed or is there something with the router that I’m missing?

TIA

---

### Post by Iowan on 2009-01-14
> **lumpyone said:**
>  I was reading on setting up the SSH and my understanding is that the SSH in Ubuntu is already turn on, correct?  I wanted to make sure and know how one tells if its turned on? Is there a process view or something that will tell me if its running?**ps aux** should show **sshd** if the "server" is running.  The SSH client comes installed, but the server may need to be installed separately.

---

### Post by Temposs on 2009-01-14
The quickest way to set up the ssh server daemon on ubuntu is to go to System->Preferences->Sessions

We're going to add the ssh daemon as a startup program, so that it will always be started when the computer boots up.

Click Add. Then fill in the name field with:
```
SSH Daemon
``` 

The Command field should be:
```
/usr/sbin/sshd
```

The comment can be whatever you want. Then click "Save". Then make sure the "SSH Daemon" entry is checked in the Startup Programs list(the one you're looking at already). Once you restart the computer, you should be able to log into the computer, assuming your router is allowing the right port and such.

---

### Post by lumpyone on 2009-01-15
> **Temposs said:**
> Once you restart the computer, you should be able to log into the computer, assuming your router is allowing the right port and such.

Still getting the connection refused error in PuTTY. I'm not sure, but I'm thinking it must be something between the computer and the router?  

I've checked the sshd_config file to make sure the port was indeed 22 and it is listed there. It looks like everything is right and should work but I don't see it.  Please let me know if there is any other info I should include to assist.

---

### Post by b0b138 on 2009-01-15
did you install openssh-server?

---

### Post by hyper_ch on 2009-01-15
(1) you need to install openssh-server
(2) you need to forward port 22 from your router to your "server"

---

### Post by lumpyone on 2009-01-15
> **hyper_ch said:**
> (1) you need to install openssh-server
(2) you need to forward port 22 from your router to your "server"

2. Yes, I have forwarded the port from the router to the server. 

1. Okay, I didn't do that, but that seems to be the problem!  I got it installed and that has fixed the issue. Thanks to both of you for the help!

---

### Post by albinootje on 2009-01-15
> **lumpyone said:**
> 
1. I've not installed openssh-server. Again, I was under the impression this should already be there? If I'm mistaken, how do I go about installing openssh-server?

The openssh client package is installed by default.

But the openssh-server package is by default not installed on the desktop edition, and in the server edition you would have to choose it.

Install it with this command :
```

sudo apt-get install ssh

```

---

