---
title: "SSH from Windows with PuTTY connection refused after restart"
date: 2015-08-11
forum: Networking &amp; Wireless
---

### Post by Brandon_Doyle on 2015-08-11
I've been trying different things and can't find a solution, so I thought I'd just ask and see what the experts think.

I restarted Ubuntu and now I can't SSH on port 22 from my Windows machine on the same network with PuTTY. The following message appears:

[IMG]http://i59.tinypic.com/1424io1.jpg[/IMG]

Now this is fairly common as I've seen from the dozens of sites that mention it (even here on Ubuntu's forums, but I haven't found the solution in them yet).

What I've tried:

1). restart ssh service:

```
/etc/init.d/ssh restart
```

I tried the same thing with sshd but that doesn't exist on my system and can't be located with apt-get -- just mentioning that because I've seen it on a few of the forums I've read so far.

2). make sure port 22 is open in firewall.

```
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

3). restarting, and that obviously hasn't worked.

Please let me know if you'd like me to post the output from various commands, will do so promptly.

Thank you for your time,
Brandon Doyle

---

### Post by SeijiSensei on 2015-08-12
> **Brandon_Doyle said:**
> I tried the same thing with sshd but that doesn't exist on my system and can't be located with apt-get -- just mentioning that because I've seen it on a few of the forums I've read so far.
That's exactly the problem.  Your Linux box isn't running the SSH *daemon*, sshd, which listens for incoming connections.  You need to install **openssh-server**.  It will automatically set itself up to start at boot.

---

### Post by Brandon_Doyle on 2015-08-12
I've tried that actually, I've installed openssh-server and that didn't work, even after a re-boot. I've tried what the following two answers have suggested:

[http://askubuntu.com/questions/403936/ssh-connect-to-host-localhost-port-22-connection-refused](http://askubuntu.com/questions/403936/ssh-connect-to-host-localhost-port-22-connection-refused)
[http://askubuntu.com/questions/51925/how-do-i-configure-a-new-ubuntu-installation-to-accept-ssh-connections](http://askubuntu.com/questions/51925/how-do-i-configure-a-new-ubuntu-installation-to-accept-ssh-connections)

Neither have worked. I just found that I cannot **ssh localhost** either, and now I have minimal access to the web server as well, which is weird (i.e. the pages won't open on my home network). I have no idea what is going on, but it seems the further I go along with this distribution of Linux, the more things don't work. It's probably just my lack of understanding, however. I've had no trouble managing other distributions, however, such as CentOS 6, which was installed on this server previously.

---

### Post by Brandon_Doyle on 2015-08-12
I just tried this after relentlessly reading multiple forums and for some reason it worked:

[http://askubuntu.com/questions/308107/cant-ssh-localhost](http://askubuntu.com/questions/308107/cant-ssh-localhost)

In short, I used apt-get purge openssh-server and re-installed it. Now I am able to ssh from both my Windows machine with PuTTY and the localhost on the Ubuntu machine. Now I'm gonna work on the other problems I'm having.

Thanks for your help!

---

### Post by SeijiSensei on 2015-08-13
Glad you found the answer, Brandon.  Did you really not have an /etc/ssh/sshd_config file?  The [package installer should create]("http://askubuntu.com/questions/627017/how-do-i-recover-the-default-version-of-some-configuration-file") the default version of that file.

"apt-get purge" is a good method to remember when you have a balky package. I usually keep copies of any configuration files I have created including ones that broke the program.  You can use diff to compare the files with the command "diff old.conf new.conf" and see what customizations are missing from new.conf.

---

### Post by pc44062 on 2015-09-08
I have a similar problem, and the solution doesn't work!  I recently had to reload my Linux server and did so with 15.04.  I've been using Ubuntu for several years and have never had a problem with SSH before, but some of the assumptions appear to have been changed.  I loaded sshd onto the server, then purged and reloaded it.  Here's what happened.

When first loaded, when I tried to access the server using SSH, I got the key mismatch error.  I corrected this by adding a Ciphers line and a MACs line.  This resulted not in the key mismatch error but rather the connection refused error.  Our IT department suggested that Ubuntu may have disallowed the Password Authorization, so I uncommented the Password Authorization yes line and got the same connection refused error.  Trying "telnet <servername> 22," I get the connection refused error; trying the "ssh <user>@<serverIP>" command from the server, same result -- connection refused.  

When I do "ufw status" I get port 22 and SSH allowed both on v4 and v6.  When I look at iptables -L, it would appear that ssh is open on udp and tcp ports.  When I look at /var/log/auth.log I get the following very long pair of lines:
Sep  8 13:59:08 earth polkitd(authority=local): Registered Authentication Agent for unix-process:2567:1481425 (system bus name :1.11 [/usr/bin/pkttyagent --notify-fd 5 --fallback], object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)

Sep  8 13:59:08 earth polkitd(authority=local): Unregistered Authentication Agent for unix-process:2567:1481425 (system bus name :1.11, object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)

I'm at a loss as to what these mean, but I suspect that they contain the information required to open port 22 to ssh.  Can anybody advise what I still need to do?  And is this a problem others have had with 15.04?

---

### Post by Deanimator on 2015-10-11
> **pc44062 said:**
> I have a similar problem, and the solution doesn't work!  I recently had to reload my Linux server and did so with 15.04.  I've been using Ubuntu for several years and have never had a problem with SSH before, but some of the assumptions appear to have been changed.  I loaded sshd onto the server, then purged and reloaded it.  Here's what happened.
I'm also having a similar problem.

A friend rebuilt his web server (14.04LTS, 64bit), after which SSH no longer worked from the outside.  It works on the LAN.  It's inaccessible from the outside, either by public IP or fqdn.

Ufw is not running.

Although his router is configured to forward port 22 to the server's IP, nmap from my [identically configured, with the same ISP] server to his shows port 22 closed.  

I noticed that his router was issuing DHCP addresses which overlapped the server IP, so I fixed that.  An odd thing was that after he edited /etc/network/interfaces for a static IP, he no longer seemed to be able to find the default gateway, either by IP or fdqn.  Renaming the file and recreating it from scratch fixed that problem.

It almost certainly isn't the ISP, since we both have the same one and I'm able to SSH into my own system from remote locations.

Everything worked before he reloaded the OS for an unrelated problem.  I reloaded again last night from the same server install disk that I used for my system.

---

### Post by Deanimator on 2015-10-12
> **Deanimator said:**
> I'm also having a similar problem.

A friend rebuilt his web server (14.04LTS, 64bit), after which SSH no longer worked from the outside.  It works on the LAN.  It's inaccessible from the outside, either by public IP or fqdn.

Ufw is not running.

Although his router is configured to forward port 22 to the server's IP, nmap from my [identically configured, with the same ISP] server to his shows port 22 closed.  

I noticed that his router was issuing DHCP addresses which overlapped the server IP, so I fixed that.  An odd thing was that after he edited /etc/network/interfaces for a static IP, he no longer seemed to be able to find the default gateway, either by IP or fdqn.  Renaming the file and recreating it from scratch fixed that problem.

It almost certainly isn't the ISP, since we both have the same one and I'm able to SSH into my own system from remote locations.

Everything worked before he reloaded the OS for an unrelated problem.  I reloaded again last night from the same server install disk that I used for my system.
I resolved this problem yesterday.

My friend's domain name is hosted with GoDaddy.  During my search, I found a solution from somebody else with a similar problem who also had GoDaddy.  It turns out that his domain name was pointing to GoDaddy's IP address instead of the physical server.  When he modified the A record at GoDaddy to point to the public IP of the actual server, the problem was resolved.  Likewise, when I pointed my friend's A record to the right IP address, SSH worked, and no doubt so will his Apache when his WordPress installation is finished.

So, the lesson is: If you keep getting a "connection refused" message and EVERYTHING else is right, make sure you're pointing at the right address.

---

### Post by SeijiSensei on 2015-10-12
The quickest way to check that is to try and connect directly to the IP address:
```
ssh user@10.10.10.10
```

---

### Post by mr8kc on 2016-05-27
Slightly behind this thread, but thought I could add a little.....

I had exactly the same problem and had tried everything suggested in this thread and others. I spent some time investigating and then after purging and reinstalling, I spotted that an OpenSSL config change had broken the openssh-server installation.

Worth checking if the install executes correctly and that the keys can correctly be generated during that install.

---

### Post by gopu02 on 2017-02-11
@[COLOR=#DD4814][COLOR=#000000][Brandon_Doyle]("https://ubuntuforums.org/member.php?u=1995906") [/COLOR][/COLOR]Thank you so much. I had the same problem but now solved it with your answer. You did awesome work.

---

