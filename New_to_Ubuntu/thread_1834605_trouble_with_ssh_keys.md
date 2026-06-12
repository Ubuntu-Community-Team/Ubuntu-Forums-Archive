---
title: "trouble with ssh keys?"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by 007casper on 2011-08-27
When you move the ssh key to another computer, is it important which user, group the key belongs to? 

Does it have to be the same user, group on the other computer?  

Does the public key looking for a specific user on the private key?

How does it work on usb flash stick?

My laptop had issues, so I took the ssh keys and moved it to another computer.

When I tried to login to the server, it says the id_rsa.pub key is locked.  

I have both the private, and public keys.  I have the right permissions.  I opened up the id_rsa.pub key that is placed on the server on my desktop.

I found at the end of the line it ends with my laptop's previous user, and laptop's hostname.

Since, I cant login with the right pass-phrase.  Now, I am doubting the pass-phrase.  And also, wondering if the problem is the user, hostname issue.

thank you.

---

### Post by Rhizoid on 2011-08-27
Try this on the machine you've moved the key to.  Add the key to the ssh agent and retry your login to the server.

```
ssh-add /path/key_file #replace the /path/key_file with the path to and the name of the key
```

Let me know if that helps,

---

### Post by 007casper on 2011-08-28
I did
> 
ssh-add /home/user/.ssh/id_rsa
Could not open a connection to your authentication agent.

?

---

### Post by Rhizoid on 2011-08-29
Is the agent running?

```
ps ax | grep ssh
```You should see a line similar to:

```
user@machine:~$ ps ax | grep ssh
12110 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=classic-gnome
19995 pts/0    S+     0:00 grep --color=auto ssh
```

If you just see the second line then the agent isn't running - start it with the following:

```
exec ssh-agent /bin/bash
```

If you've started the agent ok, you can retry the ssh-add from my first post and see how it goes.

---

