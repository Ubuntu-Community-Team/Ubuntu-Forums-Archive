---
title: "SSH problem; permission denied, publickey"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by saphire199 on 2011-05-11
Hi, I am a newbie - I just set up a webserver and I had ssh fully working between client and server and vice versa. I then had to change my DNS subdomain, which changed the user/host name on the server. I can no longer log-in with ssh to the server, but I can log into the client with ssh from the server. This seems to me to be a setting I missed somewhere in changing over. I've read the posts pertaining to this, but can't seem to kick it, can anyone help out?

---

### Post by Grenage on 2011-05-11
If you changed the username of the server, would you not need to migrate the authorized_keys entry across to the new user?  That's assuming that you're using a public key.

---

### Post by blind2314 on 2011-05-11
> **saphire199 said:**
> Hi, I am a newbie - I just set up a webserver and I had ssh fully working between client and server and vice versa. I then had to change my DNS subdomain, which changed the user/host name on the server. I can no longer log-in with ssh to the server, but I can log into the client with ssh from the server. This seems to me to be a setting I missed somewhere in changing over. I've read the posts pertaining to this, but can't seem to kick it, can anyone help out?
 
 
If you changed users then you need to copy your keys over from the user that was working to the new one, or generate a new set of keys under the new user and authenticate them.

---

### Post by wlraider70 on 2011-05-11
why did changing DNS domains require you to change users?

---

### Post by saphire199 on 2011-05-11
Hi, let me be more specific - the username of the server is:
 
*myname@*server*. (static IP)*
 
*The hostname of the server (through dynamic dns) is:*
 
*mysubdomain.dyndns.com - this has my ISP address.*
 
*The way I set up ssh to the server was:*
 
*ssh [EMAIL="myname@mysubdomain.dyndns.com"]myname@mysubdomain.dyndns.com[/EMAIL].*
 
*I did this on purpose because eventually I want to ssh from a remote terminal using tunneling and dynamic dns, so I wanted to be able to do it on the local network first.*
 
*I had to change the domain, so it became:*
 
*myname@mynewsubdomain.dyndns.com.*
 
*Once I did this, ssh would no longer get me to the server - nor could I use the ip address to log on either. The server WILL ssh to the client with IP address tho. What I am wondering is if anyone can think of some settings I might have missed to cause this behavior. Hope this helps.*
 
*Also, I checked the pub key on client and it is the same pub key that is in authorized_keys on the server.*

---

### Post by blind2314 on 2011-05-11
> **saphire199 said:**
> Hi, let me be more specific - the username of the server is:
 
*myname@*server*. (static IP)*
 
*The hostname of the server (through dynamic dns) is:*
 
*mysubdomain.dyndns.com - this has my ISP address.*
 
*The way I set up ssh to the server was:*
 
*ssh [EMAIL="myname@mysubdomain.dyndns.com"]myname@mysubdomain.dyndns.com[/EMAIL].*
 
*I did this on purpose because eventually I want to ssh from a remote terminal using tunneling and dynamic dns, so I wanted to be able to do it on the local network first.*
 
*I had to change the domain, so it became:*
 
*myname@mynewsubdomain.dyndns.com.*
 
*Once I did this, ssh would no longer get me to the server - nor could I use the ip address to log on either. The server WILL ssh to the client with IP address tho. What I am wondering is if anyone can think of some settings I might have missed to cause this behavior. Hope this helps.*
 
*Also, I checked the pub key on client and it is the same pub key that is in authorized_keys on the server.*
 
 
That doesn't sound like a keys problem, it sounds like something isn't configured correctly with DNS. Run ```
ssh -vv [EMAIL="username@server"]username@server[/EMAIL]
``` and post the results. WARNING: There will be quite a bit of information.

---

### Post by saphire199 on 2011-05-12
OK, I ran ssh with -vvv(just to make sure i got it all). One thing I noticed is that it looks like rsa identification, but I set up dsa with keygen.

I also changed my server computer name so that it is matching my domain, and changed all the appropriate files, well, at least I think I changed all the files needed!

Here is the file for output.

---

### Post by saphire199 on 2011-05-12
OK, I found out what was going on - I am beginning to find that if things are not acting normally, you did something abnormal to begin with. I uninstalled Openssh and then checked to make sure I had no files left - i found another set of files in root dir. I think this is because I used sudo keygen instead of just keygen? Anyway, that was what was screwing things up. I got rid of files and dir,  reinstalled Openssh, ran keygen, all files were in correct place and it signed right into the server after copying pubkey over. Thanks for help anyway, your suggestions pointed me in the right direction.

---

