---
title: "Is this possible?"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by liquidxit2 on 2011-02-07
ubuntu server VM (probably virtualbox) running ddclient as an ssh server? I would like to have my SSH server as a VM on my VNC box so my current ubuntu server can just be a web server (having issues with remote connecting using my dyndns hostname on the current stand alone box, yet perfectly able to remotely see /var/www/index.html). Thanks!

---

### Post by hansolo4949 on 2011-02-07
I think (with my limited knowledge if networking) that not only is it possible, I think I heard of someone doing that. I think. But a lot of things are possible in Virtualbox, so I bet that it will work, perhaps with a bit of settings tweaking.

---

### Post by liquidxit2 on 2011-02-07
I figured with the virtual adapter feature it would be possible. I guess Ill wait for more responses. Thanks.:)

---

### Post by hansolo4949 on 2011-02-07
Your welcome:). I hesitate to give out any advice networking related, because I may know a lot about some parts of Ubuntu/oses in general, I only know a little about networking, so I will have to bow out and let people more experienced than I in that department answer further questions. I hope it works for you!

---

### Post by liquidxit2 on 2011-02-07
Im hoping it is possible as I have a nice esata setup for off site storage for work that I want to use on my dell studio XPS. I would like to keep win 7 ultimate loaded as I have it setup as a nice media server for my xbox. This way I can use my 3+ year old dell as a web server and a VM for transfers from work to my home 2TB drive. 

Currently I have 10.10 server running gnome. I just installed it and Im able to do local SSH sessions, but cannot remotely access the box. I have the correct port forward on my firewall, and Im using a dynamic dns client (ddclient) linked to my dyndns hostname. I checked dyndns to see if they have the right IP and they do. I can however use any browser to remotely view /var/www/index.html. I have checked all ssh files (ssh_config, sshd_config, ddclient.conf, etc) and they match the settings I have on my work tunnel (minus user name, password and hostname). Since Im just now trying to get back into linux admin I cant for the life of me figure out why I can only LAN SSH to the server. I have a hunch its the lamp settings. 

So now I figure instead of tunneling to my ssh server and then hoping to my vnc server I could just ssh to a VM and transfer files from the tunnel to my esata. This way I can cronjob the transfer at the perfect time  and set it and forget it. Hopefully a virtualbox VM will work for this.

---

### Post by CharlesA on 2011-02-07
You can set it up with "bridged networking" and the VM will be on the same network as the host.

The lamp settings have nothing to do with SSH access. If port 22 is forwarded correctly on the router, and isn't being blocked by yer ISP, you should be able to connect fine.

---

### Post by Darkness Des on 2011-02-07
I have set up an SSH, FTP, Apache, PHP, and SQL server all in one VirtualBox Machine running Ubuntu Server. I assure you, it'll work just fine as long as you tell it to use your actual wireless/LAN card.

---

### Post by liquidxit2 on 2011-02-07
Thanks guys! Its on a laptop so I have 2 means of connecting to the network. Ill start the download of virtualbox and the 10.10 iso when I get home! The VM will be running 100% of the time but the only traffic will be the once a week cronjob transfer of my work .bak file. :guitar:

---

### Post by liquidxit2 on 2011-02-07
> **CharlesA said:**
> You can set it up with "bridged networking" and the VM will be on the same network as the host.

The lamp settings have nothing to do with SSH access. If port 22 is forwarded correctly on the router, and isn't being blocked by yer ISP, you should be able to connect fine.

I use port 2222 per my trusty 6.10 guide. The reason why i think lamp is causing an issue is that Im using dynamic dns and the hostname is being used for /var/www files. Granted I would like to think adding the ssh and :2222 modifiers that it wouldnt be an issue.

---

### Post by CharlesA on 2011-02-07
That sounds like a lot of work to make a backup.

It would be easier to just carry a thumb drive with you and use that for backups.

EDIT:

> **liquidxit2 said:**
> I use port 2222 per my trusty 6.10 guide. The reason why i think lamp is causing an issue is that Im using dynamic dns and the hostname is being used for /var/www files. Granted I would like to think adding the ssh and :2222 modifiers that it wouldnt be an issue.

How do you mean? You'd need to have port 2222 forwarded on the router to access it remotely.

---

### Post by liquidxit2 on 2011-02-07
> **CharlesA said:**
> That sounds like a lot of work to make a backup.

It would be easier to just carry a thumb drive with you and use that for backups.

EDIT:



How do you mean? You'd need to have port 2222 forwarded on the router to access it remotely.

The port is forwarded on my router/firewall. Here is what happens when I try to ssh from work 10.10 server to my home server:

Sent this command on my ssh server at work (obviously with the real username and address):

```
 ssh -vvv user@example.com -p 2222
```and it spit this back at me:

```
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to XXX.XXX.com [XXX.XXX.XXX.XXX] port 2222.
debug1: connect to address XXX.XXX.XXX.XXX port 2222: Connection timed out
ssh: connect to host XXX.XXX.com port 2222: Connection timed out
```Again the xxx's used to mask my sensitive data. But I can type in the address into a web browser anywhere and get index.html so I really think its the web server interfering. How its doing that? I dont know. But as of right now I have tweaked my config files many times even tried going completely back to port 22 and nothing. I even went through every SSH based system file and made sure it matched my work files (minus address and login info) and still nothing. I honestly am to the point where Im going to reformat and not include web server or anything else for that matter.

EDIT: As for a thumb drive, well Im not trying to backup my data but my office's .bak files. Should be somthing to the tune of 400GB. Basically going to be a weekend transfer until I can find something better for offsite storage.

---

### Post by CharlesA on 2011-02-07
So ssh is set to listen on 2222, and not 22, right?

What happens if you try to ssh to port 22?

---

### Post by CharlesA on 2011-02-07
So ssh is set to listen on 2222, and not 22, right?

What happens if you try to ssh to port 22?

---

### Post by liquidxit2 on 2011-02-07
> **CharlesA said:**
> So ssh is set to listen on 2222, and not 22, right?

What happens if you try to ssh to port 22?

Says cannot resolve user or hostname. I use 2222 for my work box and have for months without issues.

---

### Post by CharlesA on 2011-02-07
> **liquidxit2 said:**
> Says cannot resolve user or hostname. I use 2222 for my work box and have for months without issues.
Hrm, ok. 

First thing I'd check would be the firewall on the box.

```
sudo iptables -L
```

---

### Post by liquidxit2 on 2011-02-07
> **CharlesA said:**
> Hrm, ok. 

First thing I'd check would be the firewall on the box.

```
sudo iptables -L
```

Will do when I get home, and Ill compare to that of the running ssh box in use.

---

### Post by CharlesA on 2011-02-07
You can even use something like nmap to scan the host to make sure those ports are open.

Best of luck. :)

---

### Post by liquidxit2 on 2011-02-07
Using:

```
sudo iptables -L
```

I get:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

Used nmap and got the following:

```
nmap 192.168.1.7

Starting Nmap 5.21 ( http://nmap.org ) at 2011-02-07 20:36 EST
Nmap scan report for 192.168.1.7
Host is up (0.00048s latency).
Not shown: 990 closed ports
PORT     STATE SERVICE
53/tcp   open  domain
80/tcp   open  http
110/tcp  open  pop3
139/tcp  open  netbios-ssn
143/tcp  open  imap
445/tcp  open  microsoft-ds
993/tcp  open  imaps
995/tcp  open  pop3s
2222/tcp open  unknown
8080/tcp open  http-proxy

Nmap done: 1 IP address (1 host up) scanned in 0.11 seconds

```

I openned up both 22 and 2222 on my firewall and still nothing. Im moving on to the virtual machine ssh setup. Thanks for everyones help. :)

---

### Post by CharlesA on 2011-02-07
Well the port is open.

Try going here: [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

And seeing it port 2222 is open.

---

### Post by liquidxit2 on 2011-02-07
> **CharlesA said:**
> Well the port is open.

Try going here: [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

And seeing it port 2222 is open.

this is what I get:

```
[COLOR=red]Error:[/COLOR] I could **not** see your service on **173.64.113.59** on port (**2222**)
Reason: Connection timed out
```

---

### Post by liquidxit2 on 2011-02-07
Got the virtual machine up and running and doing remote SSH access within minutes of booting the first time. Problem solved and I have quicker access to my eSata drive!

---

