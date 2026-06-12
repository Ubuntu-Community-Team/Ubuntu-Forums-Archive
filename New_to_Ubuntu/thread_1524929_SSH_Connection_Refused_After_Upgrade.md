---
title: "SSH Connection Refused After Upgrade"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-07-06
Just upgraded ubuntu, and I'm having problems with SSH. I *can* access SSH from the web: $ ssh url.com . However, when I try sftp or $ ssh local ip, I get the messages access denied or connection refused respectively. Could this be caused by the upgrade? Also, I just got finished setting up static local IPs.  Could this be caused from that?

---

### Post by EnigmaticCoder on 2010-07-06
I think maybe I can explain this better. SSH works from outside the network but not locally (connection refused). How can I fix it?

---

### Post by Yarui on 2010-07-06
Does it work if you try to connect from the server itslef via localhost?  I would be very surprised if it doesn't.

EDIT:  Also, are you absolutely sure you are using the correct internal IP and the right port when connecting from within the network?

---

### Post by marshmallow1304 on 2010-07-06
Can you ping the local IPs?

---

### Post by EnigmaticCoder on 2010-07-06
Doing ssh localhost gets me further. It says permission denied because the authorized_keys don't match. I think it's safe to assume that it ssh localhost works. The problem lies in connecting my laptop to my desktop.

"Can you ping the local IPs?"
Yes, I tried that. Pinging the local IP works, but pinging the computer name does not. (i.e. ping 192.168.1.4 works bu ping MyDesktop does not)

---

### Post by Yarui on 2010-07-06
When you say it works over the internet did you test that out on both machines or just one?  In my experience when you get an access denied error with any kind of server it often means that the server wasn't found at all.  This frequently seems to be caused when you are trying to access the server through the wrong port.

---

### Post by EnigmaticCoder on 2010-07-06
By the way, when I set up static IPs, I changed the IP of the server. Could this affect the SSH Fingerprint or the publickey privatekey pair? Would generating new keys solve this problem?

---

### Post by Yarui on 2010-07-06
I don't have the slightest idea.  I have never bothered to deal with static IP stuff.  Have you read through the openSSH server page here?

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html)

Also, have you read over the man page for sshd_config?  It could just be something goofy in the config that isn't allowing connections from certain sources.

---

### Post by EnigmaticCoder on 2010-07-06
> **Yarui said:**
> When you say it works over the internet did you test that out on both machines or just one? 

Well I connected from my laptop to my desktop through my website url which resolves to my external IP. So, if I understand you, I only tried it out on one machine.

---

### Post by Yarui on 2010-07-06
Okay, well that answers my question.  I was just unsure whether or not you had successfully connected from your laptop at all.  Are you able to connect to anything like shared folders over the network?  Any other servers of any sort that you are able to connect to that could give you some idea of whether it's a network problem or a server configuration problem?

---

### Post by marshmallow1304 on 2010-07-06
> **EnigmaticCoder said:**
> By the way, when I set up static IPs, I changed the IP of the server. Could this affect the SSH Fingerprint or the publickey privatekey pair? Would generating new keys solve this problem?

Possibly.  On the client, try
```
mv ~/.ssh/known_hosts ~/Desktop
```
before sshing.


[QUOTE=EnigmaticCoder]Pinging the local IP works, but pinging the computer name does not. (i.e. ping 192.168.1.4 works but ping MyDesktop does not)[/QUOTE]

Do you need to update your /etc/hosts?  Also try
```
ping MyDesktop.local
```

---

### Post by EnigmaticCoder on 2010-07-06
I found the source of the problem but not the solution. This is definitely caused by using the local static IPs, When I switched back to DHCP, SSH worked just fine.

Does anyone know why using static IPs would cause SSH to refuse my connection?

Attached is a screenshot of the way I set up static IPs on the server.

---

### Post by Yarui on 2010-07-06
It's possible you have to set up your SSH server to use static IP even if your network is doing it right.  Try researching a bit about SSH and static IP, look over the man page of sshd_config and see if there is any setting where you need to let it know that you are using static IP.

---

### Post by EnigmaticCoder on 2010-07-06
I've got some more information. Only the laptop needs to use dhcp in order for ssh to work locally. And the login banner has changed from a quote from the matrix to "Ubuntu 10.04 LTS". Must've changed when I upgraded. Was my entire config file overwritten? Also, when I login in, it says this:

"Last login from MyLaptop*.home*"

I exited and came back and the message was:

"Last login from MyLaptop*.local*"

When I used to log in, it would just say that MyLaptop was connected no local or home suffix added. I don't know if this means anything, but maybe it'll help us figure this thing out.

In regard to your message. Good ideas. I looked through the man page but didn't find anything about static local IPs. I'm guessing there's no keyword argument for it. I'll keep googling, though.

---

### Post by EnigmaticCoder on 2010-07-07
Since SSH works with a client that uses DHCP and a server that uses a static IP, I'm going to put this problem to rest. Thread solved.

---

### Post by naarkhoo on 2011-03-24
I can't figure out how did you fix it,

I am also struggling to ssh by an internal IP, but doesn't work

---

