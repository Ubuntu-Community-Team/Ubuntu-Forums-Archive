---
title: "A n00b and her ssh. Help?"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by tarahmarie on 2010-11-27
Hi, all!

I'm not a n00b to nix, but I'm inexperienced with network issues. 

So, I have Comcastic service; I've got a dynamic IP but an OpenDNS account. Theoretically, my ssh daemon is running, but I'm not entirely positive.

I've uncommented the /etc/ssh/sshd_config lines.

How do I SSH into my home machine? I'm testing using my Android phone with ConnectBot.

Please feel free to ask me questions that may sound stupid; I've never done this before, and I can't find a good tutorial that doesn't take too much for granted.

I only just figured out that I needed a hostname. I presume that this is my username and my IP address, yes?

---

### Post by asmoore82 on 2010-11-27
To test if SSHD is running on the machine, open a terminal on the machine itself and ```
ssh localhost
```

---

### Post by karthick87 on 2010-11-27
To test your connection type the following in terminal

```
ssh localhost
```If the connection is successful you will get the similar output,

```
karthick@Ubuntu-desktop:~$ ssh localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is de:96:20:eb:91:26:ab:2e:07:f9:38:b2:02:e2:ce:19.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
karthick@localhost's password: 
Linux Ubuntu-desktop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

You have mail.
Last login: Sat Nov  6 13:07:24 2010 from localhost
```

To login to a remote SSH issue the following command in terminal,
```
ssh remoteuser@remotebox
```
In the place of remoteuser you should give the username of the remotebox and in remotebox you should give its ip address.(ie. ssh karthick@59.23.112.99)You will be asked for the password of the remote system.Enter the correct password and now you are connected.

---

### Post by tarahmarie on 2010-11-27
whew! Ok, I got that output.  Also, 'Warning: Permanently added 'localhost' (RSA) to the list of known hosts."


So, I guess that's running. Now, why is my ssh client (via Android over 3g) saying "Connection lost. 71.227 etc etc:22 - Connection refused."

---

### Post by karthick87 on 2010-11-27
Are you using firewall?If yes, are you allowing ssh connection in your firewall?

---

### Post by CharlesA on 2010-11-27
You would need to have port 22 forwarded on the router.

See here: portforward.com

Also what karthick87 said.

---

### Post by tarahmarie on 2010-11-27
> **karthick87 said:**
> Are you using firewall?If yes, are you allowing ssh connection in your firewall?

Errrr...NOW I am ;-)l

The connection is still being refused.

---

### Post by CharlesA on 2010-11-27
If you've got yer port forwarding set up correctly, try going [here]("http://canyouseeme.org/") and seeing if port 22 is open or blocked.

---

### Post by karthick87 on 2010-11-27
Post your output of this command
```
sudo ufw status
```

---

### Post by tarahmarie on 2010-11-27
> **CharlesA said:**
> If you've got yer port forwarding set up correctly, try going [here]("http://canyouseeme.org/") and seeing if port 22 is open or blocked.

I just forwarded the port. 22 still isn't being seen by canyouseeme.

---

### Post by karthick87 on 2010-11-27
Are you allowing port 22 in your firewall?If not you should allow it 
```

sudo ufw allow ssh
```

---

### Post by tarahmarie on 2010-11-27
> **karthick87 said:**
> Are you allowing port 22 in your firewall?If not you should allow it 
```

sudo ufw allow ssh
```

Yes, I forwarded it, allowed it under the firewall under UDP protocol, etc.

---

### Post by tarahmarie on 2010-11-27
What I'm wondering is if there's an issue with the DNS routing.

---

### Post by CharlesA on 2010-11-27
You are forwarding port 22 on the router, right?

ISP have been known to block that one, so you could try moving it to another port like 2222 and see if you can connect.

---

### Post by tarahmarie on 2010-11-27
> **CharlesA said:**
> You are forwarding port 22 on the router, right?

ISP have been known to block that one, so you could try moving it to another port like 2222 and see if you can connect.

Hmm. No matter what I do, it seems like canyouseeme doesn't find an open port. Even a port I know is open and works with NAT testing--it still isn't finding an open port.

---

### Post by CharlesA on 2010-11-27
How do you have your port forwarding set up?

Post a screenshot, if possible.

---

### Post by tarahmarie on 2010-11-27
> **CharlesA said:**
> How do you have your port forwarding set up?

Post a screenshot, if possible.

Thar ye be.

---

### Post by CharlesA on 2010-11-27
That looks right.

Try changing the starting port to 2222 and see if that lets you connect.

---

### Post by adamjkok on 2010-11-27
> **tarahmarie said:**
> I just forwarded the port. 22 still isn't being seen by canyouseeme.
Some ISP's will block port 22, try calling customer service to ask. However, double-check your terms of service first, you don't want to find out the hard way that your ISP doesn't allow you to run servers (some don't, I have Cox and they don't) and confess to a TOS violation.

HTH

---

### Post by tarahmarie on 2010-11-27
> **CharlesA said:**
> That looks right.

Try changing the starting port to 2222 and see if that lets you connect.

So, the command that I'd be using to test that is:

ssh [email]tarahmarie@71.etc.etc[/email].101:2222

Right?

---

### Post by tarahmarie on 2010-11-27
> **tarahmarie said:**
> So, the command that I'd be using to test that is:

ssh [email]tarahmarie@71.etc.etc[/email].101:2222

Right?

Cuz if so, it ain't working.

---

### Post by msandoy on 2010-11-27
I have been fiddeling around a bit with SSH, and it is easy to get yourself stuck, thinking everything is as it is supposed to be. So Lets step back, and do a check:
1. SSHD_CONFIG has changed port to 2222
2. UFW has open port 2222 not 22
3. Your router seems to have port 22, not 2222 open.
4. Your broarband modem might have a firewall, you might need to give your router the DMZ from broadband modem. ( Might need pass and user from ISP.)

When all this has been checked, hopefully it works. :-)

---

### Post by tarahmarie on 2010-11-27
> **msandoy said:**
> I have been fiddeling around a bit with SSH, and it is easy to get yourself stuck, thinking everything is as it is supposed to be. So Lets step back, and do a check:
1. SSHD_CONFIG has changed port to 2222
2. UFW has open port 2222 not 22
3. Your router seems to have port 22, not 2222 open.
4. Your broarband modem might have a firewall, you might need to give your router the DMZ from broadband modem. ( Might need pass and user from ISP.)

When all this has been checked, hopefully it works. :-)

1. What is sshd_config? I know that it's a file that exists, I can see it, but I don't know what I'm supposed to do to it.

2. Yes, the firewall is properly configured.

3. Yes, the router is forwarding 2222.

4. That's possible, but it's unlikely this issue is popping up after years of using the same modem.

---

### Post by Jlayman on 2010-11-27
Maybe you could try ```
$nmap youripaddress
``` to see if the port is actually open

when i do it results are ```
nmap 192.168.1.2

Starting Nmap 5.21 ( http://nmap.org ) at 2010-11-27 18:05 EST
Nmap scan report for 192.168.1.2
Host is up (0.0062s latency).
Not shown: 998 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
5900/tcp open  vnc

```

---

### Post by msandoy on 2010-11-27
> **tarahmarie said:**
> 1. What is sshd_config? I know that it's a file that exists, I can see it, but I don't know what I'm supposed to do to it.

2. Yes, the firewall is properly configured.

3. Yes, the router is forwarding 2222.

4. That's possible, but it's unlikely this issue is popping up after years of using the same modem.

1. You have to edit /etc/ssh/sshd_config, and change the port from 22 to 2222 and restart sshd, or the computer, which ever is the easiest. Then ssh will listen on the port you have configured in your firewall.

2. good.

3. good.

4. hopefully no need to change anything.

To connect from your android, you need to do ssh -p 2222 username@ipadress

---

### Post by CharlesA on 2010-11-27
> **tarahmarie said:**
> 1. What is sshd_config? I know that it's a file that exists, I can see it, but I don't know what I'm supposed to do to it.

Check the number next to port number to 2222.

```
gksudo gedit /etc/ssh/sshd_config
```

Save it, then restart ssh:

```
sudo service ssh restart
```

---

### Post by tarahmarie on 2010-11-27
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-11-27 15:36 PST
Interesting ports on c-71-etc-etc-101.hsd1.wa.comcast.net (71.etc.etc.101):
Not shown: 997 closed ports
PORT     STATE SERVICE
23/tcp   open  telnet
80/tcp   open  http
8080/tcp open  http-proxy

Nmap done: 1 IP address (1 host up) scanned in 1.44 seconds


Aha. So, it seems that 22 isn't open. In fact, forwarding the other ports doesn't seem to be working either.

---

### Post by msandoy on 2010-11-27
From the picture you posted of your router, you are behind a firewall. Try a
```

sudo ufw disable

```
and then try again to connect. Just to test the connection from your android.
It seems there is some confusion regarding port 22 and 2222.

---

### Post by tarahmarie on 2010-11-27
> **CharlesA said:**
> Check the number next to port number to 2222.

```
gksudo gedit /etc/ssh/sshd_config
```

Save it, then restart ssh:

```
sudo service ssh restart
```

Port 2222
AddressFamily any
ListenAddress 0.0.0.0
ListenAddress ::


I've changed that in the sshd_config file, 2222 is forwarded through the router, and I'm rebooting now.

Er...Ok. I have rebooted. Port 2222 isn't being shown as open.

---

### Post by msandoy on 2010-11-27
Ok, so sshd_conf has port 2222, router has forwarded port 2222 to your computer, you have done a "sudo ufw disable". And still no open ports if you do "nmap yourIP"?

---

### Post by tarahmarie on 2010-11-27
> **msandoy said:**
> Ok, so sshd_conf has port 2222, router has forwarded port 2222 to your computer, you have done a "sudo ufw disable". And still no open ports if you do "nmap yourIP"?

Yes.

---

### Post by Jlayman on 2010-11-27
show results of nmap yourusername@yourip minus your real static ip address, this way the rest of us can see the results.  it may help.

---

### Post by tarahmarie on 2010-11-27
> **Jlayman said:**
> show results of nmap yourusername@yourip minus your real static ip address, this way the rest of us can see the results.  it may help.

I already posted it above.

---

### Post by msandoy on 2010-11-27
Try running a nmap on your internal IP, 192.168.etc.etc Seems your modem might holding you back.

---

### Post by tarahmarie on 2010-11-27
> **msandoy said:**
> Try running a nmap on your internal IP, 192.168.etc.etc Seems your modem might holding you back.

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-11-27 16:32 PST
Interesting ports on 192.168.1.4:
Not shown: 997 closed ports
PORT     STATE SERVICE
111/tcp  open  rpcbind
631/tcp  open  ipp
2222/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.12 seconds

what have we here?

Why is 2222 showing internally but not externally?

---

### Post by msandoy on 2010-11-27
Hmmm, on the screenshot you posted from your router, you have IP address 192.168.1.3 for ssh, on nmap, you have 192.168.1.4. Therein might be your problem.

---

### Post by Jlayman on 2010-11-27
my greatest apolgies, i must have overlooked it.  So being that the are as stated.  are you trying to acces it through ***L***ocal ***A***rea  ***N***etwork.  Sorry if i am asking questions you already answered.  Also you hsve to be sure your ssh the correct "username@networkip"   Also on the computer you want to ssh into go to the network connection(looks like a up and down arrow) righ click and go to connection imformation and make certine you have the correct ip address

---

### Post by tarahmarie on 2010-11-27
> **msandoy said:**
> Hmmm, on the screenshot you posted from your router, you have IP address 192.168.1.3 for ssh, on nmap, you have 192.168.1.4. Therein might be your problem.

Um, yeah. That was my problem ;-)

---

### Post by tarahmarie on 2010-11-27
I thought that those router IP addresses WERE services; I thought they all had to be different--and different from my internal IP. No wonder I was having issues ;-)

I have successfully SSHed from an external location into my home box. Badass. Thanks!

PS: What do I do when my dynamic IP address changes? I have an OpenDNS account, but what does that mean? How do I use it? I went and added my network, but does that mean that OpenDNS just KNOWS when my IP changes and even though my current address is XXX.XXX.XXX.XXX, it will auto-forward?

---

### Post by msandoy on 2010-11-27
Glad to be of assistance, but make sure you have a strong password when you have ssh exposed to the world. You will get a bit less hammering from bots since you changed the port from 22 to 2222. 
You should also have a look at the security sticky in the security discussion. Alot of good advice there.

---

### Post by msandoy on 2010-11-27
Now you have gone into a territory I know nothing about since I have a static IP address. I have never tried OpenDNS, but I'm sure there are someone in here able to answer this too. :-)

---

### Post by tad1073 on 2010-11-27
> **tarahmarie said:**
> I thought that those router IP addresses WERE services; I thought they all had to be different--and different from my internal IP. No wonder I was having issues ;-)

I have successfully SSHed from an external location into my home box. Badass. Thanks!

PS: What do I do when my dynamic IP address changes? I have an OpenDNS account, but what does that mean? How do I use it? I went and added my network, but does that mean that OpenDNS just KNOWS when my IP changes and even though my current address is XXX.XXX.XXX.XXX, it will auto-forward?

AFAIK OpenDNS only allows you a different dns server to use for name resolution, they don't give you dns names. What you are looking for probably is DynDNS, they allow 2 second level domains ie. somename.dyndns.org, etc.

example: my website tdttechnology.dyndns.org
               my ftp site thomthomftp.dyndns.org

---

### Post by tarahmarie on 2011-01-15
So, I have a new router, a Vizio. I've forwarded the ports in that configuration, and canyouseeme finds that the relevant port is open. However, nmap myinternalIPaddress does not see the open port.

```

Starting Nmap 5.21 ( http://nmap.org ) at 2011-01-15 15:52 PST
Nmap scan report for 192.168.1.102
Host is up (0.00030s latency).
Not shown: 993 closed ports
PORT     STATE SERVICE
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
901/tcp  open  samba-swat
2049/tcp open  nfs
8080/tcp open  http-proxy

Nmap done: 1 IP address (1 host up) scanned in 0.10 seconds

```

I have tried to use iptables to open the port internally; 
```

sudo iptables -A INPUT -p tcp --dport XXXXX -j ACCEPT

```

But it still doesn't show when I use nmap to check to see if that port is open.

How do I open a port internally?

---

### Post by tarahmarie on 2011-01-15
And 'sudo ufw allow XXXXX' doesn't seem to do it either. Yes, I restarted the ufw service.

---

### Post by CharlesA on 2011-01-15
Make sure ssh is listening:

```
netstat -l | grep ssh
```

---

### Post by tarahmarie on 2011-01-16
> **CharlesA said:**
> Make sure ssh is listening:

```
netstat -l | grep ssh
```

```

/ Hello! $netstat -l | grep ssh
unix  2      [ ACC ]     STREAM     LISTENING     8803     /tmp/ssh-CwQTsE1252/agent.1252

```

I don't actually know how to interpret that. Is 8803 the process number or the port?

---

### Post by CharlesA on 2011-01-16
sshd isn't actually running.

Try running this:

```
sudo service sshd start
```

---

### Post by tarahmarie on 2011-01-16
> **CharlesA said:**
> sshd isn't actually running.

Try running this:

```
sudo service sshd start
```

sshd is an unrecognized command; in init.d where the rules are kept, it's ssh. However, starting ssh gives "...is already running", and a restart to change the process number, which it did.

```

/etc/initsudo service ssh start
start: Job is already running: ssh
/etc/init.d Hello! $sudo service ssh restart
ssh start/running, process 23927
/etc/init.d Hello! $pgrep sshd
23927
/etc/initnetstat -l | grep ssh
unix  2      [ ACC ]     STREAM     LISTENING     8803     /tmp/ssh-CwQTsE1252/agent.1252


```

---

### Post by CharlesA on 2011-01-16
Hrm. Can you post the output of this:

[code sudo lsof -i[/code]

---

### Post by CharlesA on 2011-01-16
Hrm. Can you post the output of this:

```
sudo lsof -i
```

---

### Post by tarahmarie on 2011-01-17
> **CharlesA said:**
> Hrm. Can you post the output of this:

```
sudo lsof -i
```

The relevant part of the list:

```

sshd      23927       root    3u  IPv4 438393      0t0  TCP *:22255 (LISTEN)
sshd      23927       root    4u  IPv6 438395      0t0  TCP *:22255 (LISTEN)


```

And that's the weird part. I know sshd is listening on the correct port.

---

### Post by tarahmarie on 2011-01-17
Interesting. It would seem that the problem isn't with my SSH setup at home; it's with my dynamic DNS provider. I have OpenDNS set up with my home network. My ddclient is properly updating my account at OpenDNS; IP address changes happen instantly. I have pointed my subdomain name (the one I chose to represent my home network) to the OpenDNS IP address.

When I hit my home IP address directly, all is well. When I try to hit it through the FQDN as represented by OpenDNS, nada.

What might be the problem? Obviously I need to figure it out before the next IP address switch at home, thanks to my Comcastic ISP.

---

### Post by CharlesA on 2011-01-17
I didn't think openDNS did dynamic DNS.

I've used dyndns.org for that.

Does the FQDN resolve the the correct ip address?

---

### Post by CharlesA on 2011-01-17
I didn't think openDNS did dynamic DNS.

I've used dyndns.org for that.

Does the FQDN resolve the the correct ip address?

---

### Post by tarahmarie on 2011-01-17
> **CharlesA said:**
> I didn't think openDNS did dynamic DNS.

I've used dyndns.org for that.

Does the FQDN resolve the the correct ip address?

According to [http://www.************/find_ip_address_of_a_website.php](http://www.************/find_ip_address_of_a_website.php), yes. It resolves to one of the two IP addresses provided by OpenDNS (the one I pointed it to in the zone file); now, I am still a noob at this sort of configuration, so it's possible that I am overlooking something key. Still, the whole point of setting up a FQDN is to have a standard entry in all my putty/winscp/connectbot/whatever-uses-a-key apps. 

I am under the impression that you set up a domain (or subdomain, whatevs) to point to an IP address provided by a dynamic DNS provider. They then forward that FQDN to the IP address provided by whatever DD client you're running (and I'm running ddclient, which is configured properly and reporting my correct IP address to OpenDNS). Is this the case? If so, is the forwarding process stripping the headers or something?

---

### Post by CharlesA on 2011-01-17
Try using dig to do a lookup of the domain names.

dig [www.somedomain.tld](www.somedomain.tld)

---

### Post by tarahmarie on 2011-01-17
> **CharlesA said:**
> Try using dig to do a lookup of the domain names.

dig [www.somedomain.tld](www.somedomain.tld)

I did, but it only says that my domain name is pointed to the correct IP. Why use a different tool to do what I already know?

---

### Post by CharlesA on 2011-01-17
Something isn't working right, as you said you can connect fine if you are using the ip address, but not if you use the domain name.

If the domain name resolves to the correct IP there shouldn't be a problem.

---

### Post by CharlesA on 2011-01-17
Something isn't working right, as you said you can connect fine if you are using the ip address, but not if you use the domain name.

If the domain name resolves to the correct IP there shouldn't be a problem.

---

### Post by tarahmarie on 2011-01-17
> **CharlesA said:**
> Something isn't working right, as you said you can connect fine if you are using the ip address, but not if you use the domain name.

If the domain name resolves to the correct IP there shouldn't be a problem.

I have a support ticket in to OpenDNS now to see why my FQDN resolves to the correct IP address but does not permit me to ssh into my home box.

---

