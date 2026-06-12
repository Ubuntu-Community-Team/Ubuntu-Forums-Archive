---
title: "Cannot login using ssh"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by unix_user on 2010-11-10
Hi,
I am using Ubuntu 10.04 and recently powered down my server at home, now after rebooting it does not let me login using its hostname, it allows login when used with 192.168.x.x.

Here are things I have checked after reboot.

a) /etc/init.d/ssh restart 
b) ps -ae | grep sshd        # shows sshd processes
c) I can ssh to Ubuntu from Windows Laptop using 192.168.x.x ip address fine
e) I cannot login with its hostname
f) firewall allows ssh on port 22
g) sudo ufw status    # shows      22/tcp Allow Anywhere
h) cat /var/log/auth.log  shows entries when I stop and start sshd but does not show my attempt to login from Windows laptop
i) Following lines show in /var/log/auth.log
servername sshd[7856] Server listening on 0.0.0.0 port 22           <---- Could this be an issue


Any other suggestions to try, 

Thanks in advance,

---

### Post by unix_user on 2010-11-10
Following lines show in /var/log/auth.log

servername sshd[7856] Server listening on 0.0.0.0 port 22.

---

### Post by brian mcgee on 2010-11-11
Sounds like a DNS issue. Sorry if you've already evaluated that or I misread! If you have another Ubuntu/Debian box on the network, try the command:

```
host servername
```dig will also work

Or in Windows, maybe just try and ping by hostname.

---

### Post by CharlesA on 2010-11-11
> **brian mcgee said:**
> Sounds like a DNS issue. Sorry if you've already evaluated that or I misread! If you have another Ubuntu/Debian box on the network, try the command:

```
host servername
```dig will also work

Or in Windows, maybe just try and ping by hostname.

Yep, it's a name resolution thing.

---

### Post by HermanAB on 2010-11-11
Howdy,

Define the IP address in /etc/hosts on each machine you use, or set up a DNS.

---

### Post by The Cog on 2010-11-11
> **unix_user said:**
> i) Following lines show in /var/log/auth.log
servername sshd[7856] Server listening on 0.0.0.0 port 22           <---- Could this be an issue

No, that is the normal entry. 0.0.0.0 is a "wild card" meaning it's listening on all the addresses the box has been assigned with. Port 22 is the normal SSH port.

Although I agree it may well be a DNS name resolution issue, I don't actually see definitive proof of that in your postings. Can you try and ping the Ubuntu box from the windows box (by name), and check the IP address the windows box then says it is doing the pings to? If it's a DNS issue you will be able to see that windows has resolved the name to the wrong IP address.

---

### Post by unix_user on 2010-11-11
Here is response when I ping from Windows laptop at home

ping myserver         # replace with actual server name
Reply from 192.168.x.x.    with 0% loss


ping server.dyndns.org    # this is the actual server name
Ping could not find host server.dyndns.org

BTW, I have seen unsuccessful ssh attempts to login in /var/log/auth.log, it is just not accepting when I ssh with servername.dyndns.org

Will look into later when I return.

Thanks for advice.

---

### Post by CharlesA on 2010-11-11
You'd need to use port forwarding on the router to allow connections from the internet.

---

### Post by bioterror on 2010-11-11
Kinda confusing.
You say you can connect if you use 192.168.... ip address but if you use your dyndns host it doesnt.

Well, dyndns should not work for your computers if you're behind a NAT, unless you are port forwarding from the router to a correct ports and so on.

Like I have a port forwarding from my router hostname.dyndns.org:443 -> 10.0.0.2:22 (one place where I work blocks port 22 in their firewall ;)

Edit: CharlesA, damn you're faaasssttt!!! ;D

---

### Post by The Cog on 2010-11-11
It looks like you have an issue with the Ubuntu server not updating dyndns with the IP address for some reason. I'm afraid I can't help you there as I've never used dyndns. I believe that they blacklist servers that try to do to many updates too quickly though, so first off I would check their logs or you might wase a lot of time trying to debug a working script.

You should be aware that you will probably not be able to ping/ssh the server by its public name from within your home network. The Network Address Translation the router has to do probably only works for connections coming in from the internet, and probably doesn't work from within your home network.

---

### Post by toekneewood on 2010-11-11
What about if you remove the cert from "~/.ssh/authorized_keys" using the following command
```

ssh-keygen -R YOUR-HOST-NAME-THAT-DOES-NOT-WORK

```

Then try ssh again

---

### Post by CharlesA on 2010-11-11
> **The Cog said:**
> It looks like you have an issue with the Ubuntu server not updating dyndns with the IP address for some reason. I'm afraid I can't help you there as I've never used dyndns. I believe that they blacklist servers that try to do to many updates too quickly though, so first off I would check their logs or you might wase a lot of time trying to debug a working script.

You can install ddclient to update dyndns info. I have my router (running dd-wrt) set to update my ip info every 10 days or so.

---

### Post by unix_user on 2010-11-16
Thanks for all the pointers on dyndns - it appeared my site was not communicating with dyndns . After restarting ddclient - it connects well now from internal and outside of network.

Appreciate all the feedback. I haven't been able to spend a lot of time on server lately.

I want to find out more on dyndns updates and logs, which I will start a new thread.

Thanks,

---

### Post by brian mcgee on 2010-11-16
> **unix_user said:**
> Thanks for all the pointers on dyndns - it appeared my site was not communicating with dyndns . After restarting ddclient - it connects well now from internal and outside of network.


Please mark this thread solved, if you feel it's appropriate. :)

---

