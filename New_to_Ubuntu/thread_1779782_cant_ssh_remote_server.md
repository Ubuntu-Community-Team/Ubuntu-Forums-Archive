---
title: "cant ssh remote server"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by 007casper on 2011-06-10
> ssh localhost
permission denied

I am having trouble setting up ssh.

I tried 
ssh -v moe@178.249.137.52
 OpenSSH_5.3p1 Debian-3ubuntu6, OpenSSL 0.9.8k 25 Mar 2009
 debug1: Reading configuration data /etc/ssh/ssh_config
 debug1: Applying options for *
 debug1: Connecting to 178.249.137.52 [178.249.137.52] port 22.
 debug1: connect to address 178.249.137.52 port 22: Connection timed out

I have an encrypted hard drive on the server. I also have physical access to the server. So, I am trying to set up ssh locally on the server in order to create a connection to my client computer at a different location.

I have tried to ssh the server a while back ago and created keys, and couldnt make it work.  So, I figured I should try to ssh without the keys first. I removed the openssh-client and the openssh-server on the server, and reinstalled.

it still doesn't work.

please help me out ...

---

### Post by Macskeeball on 2011-06-11
That looks like a public IP address. Is the server behind a router/firewall?

---

### Post by 007casper on 2011-06-11
yes it is a public IP address.  

The server is behind a router, and it has a firewall up.  


On the router I have
application    start   end   tcp/udp   ip address
ssh            22      22    both      192.168.1.8

the firewall I have 
ufw incoming deny & outgoing deny
allow 80 tcp
allow 22 tcp

then tried 
ssh localhost

I got
permission denied

when I disabled the firewall, and tried ssh localhost again... I got

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
f2:92:1d:da:81:2a:d7:16:0a:48:f0:43:20:1c:f4:b5.
Please contact your system administrator.
Add correct host key in /home/hiya/.ssh/known_hosts to get rid of this message.
Offending key in /home/hiya/.ssh/known_hosts:2
RSA host key for localhost has changed and you have request strict checking.
Host key verification failed. 


after that I enabled the firewall again

havent done "rm ~/.ssh/known_hosts" or "ssh-keygen -R hostname" yet

???

---

### Post by robsoles on 2011-06-11
Edit: You will have to fix your key problem first, replace the one rather than ditching the many if you have many.

> **007casper said:**
> ...

the firewall I have 
ufw incoming deny & outgoing deny
allow 80 tcp
allow 22 tcp

...

???

If you mean that this is the list, in it's order, of rules for UFW then it looks like you have matched the first rule to deny before you can match the third rule to allow.

It might help to see the response from the target server for ```
sudo ufw status numbered
```

---

### Post by 007casper on 2011-06-11
regarding keys...

I deleted my old keys from the .ssh/authorized_keys file. I also completely removed ftp.

in /etc/ssh... I still have the following files
moduli
sshd_config
ssh_host_dsa_key
ssh_host_rsa_key
ssh_config
sshd_config.default
ssh_host_dsa_key.pub
ssh_host_rsa_key.pub

should I delete the keys and files in /etc/ssh and only leave moduli, ssh_config?


> 
it looks like you have matched the first rule to deny before you can match the third rule to allow.


I am sorry but what is that mean?  Does it have to be in a specific order...

regarding sudo ufw status numbered... 
I cant do that right now.  Because I dont have access to the server at this moment.  I should be in front of the server in a few hours.

I have gui installed on the server, because of that I have gufw.  On gufw I enabled the firewall, then incoming deny; outgoing deny; allow 80 tcp ; allow 22 tcp in that order.

thank you for all your help.  I really appreciate it.

---

### Post by robsoles on 2011-06-11
That order is your problem, if I haven't missed something about ufw that would make me think it a less capable firewall. The better firewalls try to match the rules using the order of the rules as 'precedence', the usual convention is to try to match from top to bottom and disregard rules after the first match.

You may not need to be enabling ufw/gufw there. You describe this Server as being behind a router which has a firewall and uses port-forwarding to route specific Internet traffic to your LAN. Also, the 'natural' thing for a system to do is to reject traffic to 'unused' ports, so if you haven't got anything listening then you don't need to go out of your way to make sure the port is blocked.

In the good old days the first rule was 'related, established anything is allowed' middle rules allowed services to start 'relations' and the final rule denied everything.

If you don't suspect the router's firewall of being easily bypassed then the only point in running the firewall (ie; Enabling ufw) is to be specific about the remote IP addresses or even more specific stuff that ufw is capable of.

Checkout nmap, and similar port checking programs, and run one from another machine on the same LAN as the Server is on - kill ufw/gufw and scan the Server, if you can see anything you haven't purposefully got something listing on then find out what is listening there and kill it. If you can identify IP addresses or ranges from which you want to restrict access you can probably just as well add them to router's port-forwarding rules - otherwise this could make enabling ufw worthwhile.

Any good?

---

### Post by 007casper on 2011-06-11
when I brought the firewall down and tried ssh localhost,  I got (man-in-the-middle attack)! statement.  Isnt that intrusion?  

I got to figure out how to use nmap.  

I cant install another server/computer on the server LAN.

do you also think the files in /etc/ssh part of the problem?

in /etc/ssh... I still have the following files
moduli
sshd_config
ssh_host_dsa_key
ssh_host_rsa_key
ssh_config
sshd_config.default
ssh_host_dsa_key.pub
ssh_host_rsa_key.pub

---

### Post by 007casper on 2011-06-11
bump

---

### Post by VOT Productions on 2011-06-11
Take the firewall on the router (or use DMZ) and use the firewall on Linux (For example, Firestarter is downloadable.) The reason is that routers don't do good at firewalls.

---

### Post by 007casper on 2011-06-11
I was using ufw/gufw

Isnt ufw/gufw better? Because it is close to iptables set up.  Eventually, it will give me legs up on iptables.

---

### Post by robsoles on 2011-06-11
ufw/gufw is 'what to use' as far as I'm concerned.

> **VOT Productions said:**
> Take the firewall on the router (or use DMZ) and use the firewall on Linux (For example, Firestarter is downloadable.) The reason is that routers don't do good at firewalls.

Please research firestarter more before recommending it 'around' - I'm not going to re-research it without one hell of a prompt, I have written it off as abandoned due believing it was last updated in 2006.

> **007casper said:**
> when I brought the firewall down and tried ssh  localhost,  I got (man-in-the-middle attack)! statement.  Isnt that  intrusion?  

I got to figure out how to use nmap.  

I cant install another server/computer on the server LAN.

do you also think the files in /etc/ssh part of the problem?

in /etc/ssh... I still have the following files
moduli
sshd_config
ssh_host_dsa_key
ssh_host_rsa_key
ssh_config
sshd_config.default
ssh_host_dsa_key.pub
ssh_host_rsa_key.pub

Those are the server's files, the file you need to kill is on the computer you are using to connect to the server with and it's location is /home/<your-user-name>/.ssh/known_hosts.

[COLOR=Blue]On the Server, sorry.[/COLOR]   **[s]On your client machine[/s]** (assuming it is Ubuntu :))```
rm ~/.ssh/known_hosts
```Should ditch it a treat.

---

