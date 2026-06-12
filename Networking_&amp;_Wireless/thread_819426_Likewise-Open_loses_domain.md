---
title: "Likewise-Open loses domain"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by oldmuttonhead on 2008-06-05
Hello!

I'm using 8.04 on a whitebox notebook with an ASUS V71A base connected to a SBS 2003 domain via likewise-open.

Well.. I was anyway.  :)

After installing likewise-open, I joined the domain with no problems.  I logged in a few times with no issues.  Now, for some reason, I get a "Domain Controller unreachable, using cached credentials instead.  Network resources may be unavailable."

The only thing that I've changed since installing likewise-open is that I added my DOMAIN\Username account to the sudoers list.  

I can ping the IP, computername, domainname.local, and computername.domainname.local.  I do have these in the HOSTS file because I could not ping them before installing likewise-open and the instructions I used to install likewise said to do that.  

I'm in the process of switching over to Linux from Windows and I'm still a noob so bear with me!  However, I am a Windows network admin and I am very proficient with networking and all that jazz.  

Thanks in advance!!

Rick

---

### Post by CheShA on 2008-06-20
Check that your local PC's date and time match the server - AD only lets you be a minute or two out before causing problems.

---

### Post by oldmuttonhead on 2008-06-20
I found out through the Likewise mailing list that the repository version of Likewise can be slow to find the domain.  They suggested I install the version on the likewise website.  I did and it fixed the problem.  On the old version, if I wanted about a minute or so before logging in, it would work.  Now it works immediately.

---

### Post by PardusLynx on 2008-10-08
Would you share with us how you installed the new version and joined the domain. Because I installed the new version from the website as you said but when I try to join the domain I get "Lsass Error".

---

### Post by oldmuttonhead on 2008-10-08
I just followed the steps in the install guide at:
[URL="http://www.likewisesoftware.com/resources/product_documentation/Likewise-Open-5-Guide.pdf"]
http://www.likewisesoftware.com/resources/product_documentation/Likewise-Open-5-Guide.pdf[/URL]

I used the section labeled: "Join Linux to Active Directory with the Command Line"

I'm a Linux newbie so anything beyond that is way outside my skill level.  :)

---

### Post by PardusLynx on 2008-10-08
Yes I did exactly as you pointed but it didn't work. I sent an e-mail to Likewise about this, if they get back to me with a solution I'll be happy to put it here. 

On the other hand, I found a solution in this forum. After assingning a static ip you can log on normally without any error. Of course it's not useful solution for a large network.

---

### Post by oldmuttonhead on 2008-10-08
The other option is to join the likewise-open discussion list at:

[http://lists.likewisesoftware.com/cgi-bin/mailman/listinfo/likewise-open-discuss/]("http://lists.likewisesoftware.com/cgi-bin/mailman/listinfo/likewise-open-discuss/")

They were very helpful to me when I was originally setting this up.

---

### Post by likeWiseGuy on 2008-10-08
> **PardusLynx said:**
> Yes I did exactly as you pointed but it didn't work. I sent an e-mail to Likewise about this, if they get back to me with a solution I'll be happy to put it here. 

On the other hand, I found a solution in this forum. After assingning a static ip you can log on normally without any error. Of course it's not useful solution for a large network.

Hi PardusLynx,

You do not need a static IP to join a domain. It works the same with a dynamic IP as well. If you want to share a little bit about what issues you saw in your domain join when it didn't succeed, please do. I'll be curious to see what happened in your environment.

Thanks.

---

### Post by PardusLynx on 2008-10-09
Hello, static IP solves the "Domain Controller unreachable" problem. I don't know why but after I set it, I never have this error message. Of course it is a better option if I can achive this with a dynamic ip.

Regarding new version, I get the following error when I try to join the domain:

Error: Lsass Error [code 0x00080047]

Error [code=-1] occured

If you need more information, please tell me.

---

### Post by likeWiseGuy on 2008-10-09
> **PardusLynx said:**
> Hello, static IP solves the "Domain Controller unreachable" problem. I don't know why but after I set it, I never have this error message. Of course it is a better option if I can achive this with a dynamic ip.

Regarding new version, I get the following error when I try to join the domain:

Error: Lsass Error [code 0x00080047]

Error [code=-1] occured

If you need more information, please tell me.

Have you tried running domainjoin-cli with the following flags?

```

domainjoin-cli --loglevel verbose --log /tmp/domainjoin.log join <domain fqdn> <AD account>

```
This should give you some good logging information for your domain join. If you need help understanding the log, please let me know. It would also help if you could share what you see in the logs, too.

Thanks.

---

### Post by nosedrum on 2008-11-28
Hi all,

I'm under RHEL4 and I have freshly installed likewise-open but when I wxant to join my domain the result is:

> [root@zeus Desktop]# domainjoin-cli --loglevel verbose --log /tmp/domainjoin.log join toto.fr Administrator

Error: Lsass Error [code 0x00080047]

Failed to lookup the domain controller for given domain

**_/tmp/domainjoin.log :_**
> 20081128151841:INFO:Domainjoin invoked with 8 arg(s):
20081128151841:INFO:    [domainjoin-cli]
20081128151841:INFO:    [--loglevel]
20081128151841:INFO:    [verbose]
20081128151841:INFO:    [--log]
20081128151841:INFO:    [/tmp/domainjoin.log]
20081128151841:INFO:    [join]
20081128151841:INFO:    [toto.fr]
20081128151841:INFO:    [Administrator]
20081128151841:INFO:Trying to load /opt/likewise/lib/liblsajoin.so
20081128151841:INFO:Checking status of daemon [/etc/init.d/npcmuxd]
20081128151841:INFO:Daemon [/etc/init.d/npcmuxd]: status [0]
20081128151841:VERBOSE:Looking for '/sbin/chkconfig'
20081128151841:VERBOSE:Found '/sbin/chkconfig'
20081128151841:INFO:Checking status of daemon [/etc/init.d/netlogond]
20081128151841:INFO:Daemon [/etc/init.d/netlogond]: status [0]
20081128151841:VERBOSE:Looking for '/sbin/chkconfig'
20081128151841:VERBOSE:Found '/sbin/chkconfig'
20081128151841:INFO:Checking status of daemon [/etc/init.d/dcerpcd]
20081128151841:INFO:Daemon [/etc/init.d/dcerpcd]: status [0]
20081128151841:VERBOSE:Looking for '/sbin/chkconfig'
20081128151841:VERBOSE:Found '/sbin/chkconfig'
20081128151841:INFO:Checking status of daemon [/etc/init.d/eventlogd]
20081128151841:INFO:Daemon [/etc/init.d/eventlogd]: status [0]
20081128151841:VERBOSE:Looking for '/sbin/chkconfig'
20081128151841:VERBOSE:Found '/sbin/chkconfig'
20081128151841:INFO:Initialized /opt/likewise/lib/liblsajoin.so
20081128151841:INFO:Checking status of daemon [/etc/init.d/lsassd]
20081128151841:INFO:Daemon [/etc/init.d/lsassd]: status [0]
20081128151841:INFO:Adding zeus (fqdn zeus.toto.fr) to /etc/hosts ip 192.168.254.37, removing zeus, zeus.toto.fr, zeus, zeus
20081128151841:INFO:Getting DC
20081128151841:ERROR:Lsass Error [CENTERROR_DOMAINJOIN_LSASS_ERROR]

Failed to lookup the domain controller for given domain

Stack Trace:
main.c:874
main.c:373
djmodule.c:215
djfirewall.c:732
djfirewall.c:655
djauthinfo.c:965

I don't understand why because the lookup is okay:

> [root@zeus Desktop]# nslookup -q=srv _ldap._tcp.dc._msdcs.toto.fr
Server:         192.168.254.29
Address:        192.168.254.29#53

_ldap._tcp.dc._msdcs.toto.fr    service = 0 0 389 mox-pearl.toto.fr.

Likewise-Open works like a charm under my Kubuntu 8.10 Box but under my freshly installed RHEL4 server (no iptables, no SElinux, just a samba server) it don't want to join the domain...

Any ideas ?

---

### Post by metale on 2008-12-02
I have the same "Domain Controller unreachable, using cached credentials instead. Network resources may be unavailable." message, randomly (more times than not). Once it works, it works until restart.

I use a static IP via network manager.

(btw, I'm new here so take it easy :) )


**Edit**: I found out that, if I boot/reboot the computer, it makes that error.

Then, if I log in as a local admin and do the likewise-open status, it IS running. I do the likewise-open restart, then logoff, then it works well, until reboot.


**Edit 2**: I added the "likewise-open restart" command to the post-network folder as a script. Now I just have to login into any used for it to work. I suspect the network manager is only setting up the network on the first login, when the nm-applet appears. After that, all is great. Shouldn't the network be setup before that? Before the login screen?

**Edit 3**: Found out that I can't ping that pc before login, but after it logins it pings-back right. Why isn't it loading the network on startup as it should?

---

### Post by grizzyfizzy on 2009-07-14
Hello I am new to Ubuntu and am having a problem with LikeWiseOpen install. When I do the install through the root user it says at 93% Problem running post-install step. Any help would be nice.

---

### Post by 696f6e6963 on 2009-07-14
Are you installing it from the repositories? or are you using the download provided by likewise.com?

---

### Post by woleium on 2010-05-25
> **PardusLynx said:**
> Hello, static IP solves the "Domain Controller unreachable" problem. I don't know why but after I set it, I never have this error message. Of course it is a better option if I can achive this with a dynamic ip.

Regarding new version, I get the following error when I try to join the domain:

Error: Lsass Error [code 0x00080047]

Error [code=-1] occured

If you need more information, please tell me.

I had this error, and it led me to this post.

the error was caused by incorrect case.

This errors:
```
 domainjoin-cli join domain.local administrator
```

This works:
```
 domainjoin-cli join DOMAIN.LOCAL administrator
```

---

### Post by eholcroft on 2010-06-23
Also was getting Lsass Error [code 0x00080047]

On 10.04 i386, this worked for me when I added the DC to /etc/hosts thus:

192.168.x.x dcname.domain.local

Note: We have multiple DCs on the domain and only when I added the DC that is on the same subnet as the client PC, did things work out.

---

### Post by PeteLong on 2011-01-28
Heres some more information that might be helpful, and covers the Error: Lsass Error [code 0x00080047] error

[Ubuntu - Joining / Logging into Windows Domains]("http://www.petenetlive.com/KB/Article/0000384.htm")

Pete

---

### Post by atworkwithjf on 2011-02-16
These issues are typically dns related.

Check your nsswitch to be sure there are no entries pertaining to mdns as you're likely not using multicast dns if you're using AD. 

Other culprits are as mentioned, time skew and failure of the network to be fully up when lsassd tries to start.  If your machine uses dhcp and there is a lot of latency you may not be getting an IP address for quite a while and if lsassd tries to start it won't be able to communicate with the DC when it initializes.  Trying to ping the machine as it's booting will give you a good indication of how long it's taking to pick up the address from your dhcp server.

I prefer to use dig instead of nslookup to see if the domain is being found.  dig doesn't suffer from nslookup's deficiencies, notably you can use either a domain name or an IP address to designate a name server. The default is to query the name servers in resolv.conf.  dig is smarter about arguments, too. You can specify the arguments in any order you like, and dig will figure out that mx is probably the type of records, not the domain name, you want to look up

However the nsswitch edit is usually the solution.

---

