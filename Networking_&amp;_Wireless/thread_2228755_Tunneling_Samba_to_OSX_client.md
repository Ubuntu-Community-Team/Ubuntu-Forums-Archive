---
title: "Tunneling Samba to OSX client"
date: 2014-06-09
forum: Networking &amp; Wireless
---

### Post by Steve_Manes on 2014-06-09
I've been Googling this for a couple of days and I haven't found a clear recipe on how to do this with Ubuntu 14.04 and OSX 10.9.  I've seen a couple for Ubuntu -> Windows but I'm having difficulty doing this with Ubuntu -> OSX.

With OSX's sketchy support for NFS and its deprecation of AFP and adoption of Samba2, I want to move my dev network to this protocol.  I develop on the Mac but use Ubuntu for hosting and a W7 VM for MS compatibility testing.

Has anyone run across a link for doing this or, better, are you doing Samba over SSH with an OSX client now?  I got sshfs to work but it's very slow on the Mac -- possibly due to the legacy software I needed to get it running on the Mac side.

---

### Post by bab1 on 2014-06-09
> **Steve_Manes said:**
> I've been Googling this for a couple of days and I haven't found a clear recipe on how to do this with Ubuntu 14.04 and OSX 10.9.  I've seen a couple for Ubuntu -> Windows but I'm having difficulty doing this with Ubuntu -> OSX.

With OSX's sketchy support for NFS and its deprecation of AFP and adoption of Samba2, I want to move my dev network to this protocol.  I develop on the Mac but use Ubuntu for hosting and a W7 VM for MS compatibility testing.

Has anyone run across a link for doing this or, better, are you doing Samba over SSH with an OSX client now?  I got sshfs to work but it's very slow on the Mac -- possibly due to the legacy software I needed to get it running on the Mac side.

Is this a LAN setup?  Have you successfully networked OSX's version of SMB/CIFS and Ubuntu Samba?  Apple's CIFS implementation does not use Samba on the latest OSX versions.  Apples implementation is incompatible with Samba.  I would first get file sharing with Samba working and then implement encrypted tunneling.

If this is a LAN, why do you fell you need the added overhead of an encrypted tunnel?  If this is a WAN set up  then you will be better off using a VPN rather than SSH to do this.    The VPN  provides the tunnel and then you bridge the 2 subnets to allow for NETBIOS broadcasts.  Samba is really a LAN application and the VPN simulates that.

---

### Post by lukeiamyourfather on 2014-06-09
Edited, didn't see that you were tunneling.

---

### Post by Steve_Manes on 2014-06-09
> **bab1 said:**
> Is this a LAN setup?  Have you successfully networked OSX's version of SMB/CIFS and Ubuntu Samba?
Yes.  Samba is working fine.  I've used Samba on Ubuntu/OSX since 2009.  Then I used NFS until it stopped working in Lion.  Then I did sshfs because I occasionally need filesystem access outside my LAN.  Except it's slow and sometimes flakey.

> **bab1 said:**
> Apple's CIFS implementation does not use Samba on the latest OSX versions.

Beg to differ:

[http://appleinsider.com/articles/13/06/11/apple-shifts-from-afp-file-sharing-to-smb2-in-os-x-109-mavericks](http://appleinsider.com/articles/13/06/11/apple-shifts-from-afp-file-sharing-to-smb2-in-os-x-109-mavericks)

> **bab1 said:**
> Apples implementation is incompatible with Samba.  I would first get file sharing with Samba working and then implement encrypted tunneling.


That's what I'm asking: how to implement tunneling with Samba to OSX.

> **bab1 said:**
> If this is a LAN, why do you fell you need the added overhead of an encrypted tunnel?  If this is a WAN set up  then you will be better off using a VPN rather than SSH to do this.    The VPN  provides the tunnel and then you bridge the 2 subnets to allow for NETBIOS broadcasts.  Samba is really a LAN application and the VPN simulates that.

I'm just asking for advice from those who've successfully done this, not criticism of my requirements.  I know that tunneled Samba works and that's all that I need for my 3x/year meetings off-site.  A VPN would be overkill for that.

---

### Post by bab1 on 2014-06-09
> **Steve_Manes said:**
> ...
[COLOR="#0000FF"]Apple's CIFS implementation does not use Samba on the latest OSX versions.[/COLOR]
> 
Beg to differ:
[http://appleinsider.com/articles/13/06/11/apple-shifts-from-afp-file-sharing-to-smb2-in-os-x-109-mavericks](http://appleinsider.com/articles/13/06/11/apple-shifts-from-afp-file-sharing-to-smb2-in-os-x-109-mavericks)


From your own reference> *[COLOR="#0000FF"]For OS X 10.7 Lion, **Apple wrote its own software for Windows File Sharing **under the name "SMBX" to replace Samba, adding initial support for Microsoft's SMB2 at the same time. [/COLOR]*



This is not Samba
> 
I'm just asking for advice from those who've successfully done this, not criticism of my requirements.  I know that tunneled Samba works and that's all that I need for my 3x/year meetings off-site.  A VPN would be overkill for that.
Whatever rows your boat I guess.

---

### Post by Steve_Manes on 2014-06-09
Microsoft drives SMB development, it released SMB2 back in the Vista days, SMB2.1 runs on all W7 platforms and MS refers to it generically as "Samba".  SMB2 clients are functionally transparent to /usr/sbin/smbd and /etc/samba/smb.conf, a Samba client has been in every OSX release since 10.2 and I've successfully used it since 10.5.  You're free to call it whatever you like.  I'm just trying to get an answer to my question.

---

### Post by bab1 on 2014-06-09
> **Steve_Manes said:**
> Microsoft drives SMB development, it released SMB2 back in the Vista days, SMB2.1 runs on all W7 platforms and MS refers to it generically as "Samba".  

Microsoft says a lot of things.  Not all of it accurate.  Samba is not a generic name for the SMB/CIFS protocal.  Samba refers to that which Samba.org licenses.  The protocol at this point is SMB/CIFS and there is SMB, SMB2 and SMB3.  Apple created it's own implementation of SMB/CIFS as has Oracle (SUN) Solaris.  Neither Microsoft, Apple or Oracle own the Samba name.
> 
SMB2 clients are functionally transparent to /usr/sbin/smbd and /etc/samba/smb.conf, a Samba client has been in every OSX release since 10.2 and I've successfully used it since 10.5.  You're free to call it whatever you like.  I'm just trying to get an answer to my question.
What I call things is irrelevant,  but I'm sure that the folks at samba.org spend time to make sure that there good name and the licensing is protected.  The facts are the facts are the facts.  See [here]("http://www.cnet.com/news/say-adios-to-samba-in-os-x/") and [ here]("http://appleinsider.com/articles/11/03/23/inside_mac_os_x_10_7_lion_server_apple_replaces_samba_for_windows_networking_services") and [here]("http://apple-beta.slashdot.org/story/11/03/24/1546205/apple-remove-samba-from-os-x-107-because-of-gplv3").

In the end these are minor points, except to those that care about the licensing of their good name.  Hope you find the answer to your real problems.  :D

---

### Post by Morbius1 on 2014-06-09
Although I have samba working in both directions ( Ubuntu - OSX ) it's only been on a local lan where it's really very transparent but I've never used it through an SSH tunnel.

I've come across a couple of references that indicates that you need to make an alias to your loopback connection on the OSX client to pull this off. Here is one of the more coherent Howto's I've found: [Connect to Windows Samba Shares via SSH Tunneling from Mac OS X]("http://blog.lococobra.com/how-to-connect-to-samba-shares-over-the-internet-via-ssh-from-mac-os-x")

It's about a Windows server and those parts you can ignore but towards the bottom of the page ( after step 10 ) it starts talking about the OSX client. It's also somewhat dated since it talks about Leopard and references the wrong port ( 139 ) which smbx doesn't use but it might be a starting point.

Sorry, that's the best I've got.

---

### Post by Steve_Manes on 2014-06-09
Thanks, Mobius1.  I saw that one.  As you noted, Unix Samba doesn't appear to use the netbios-ssn port on #139 but the netbios-ns and netbios-dgn ports on #138 and #139 respectively for 'nmbd' with Samba's 'smbd' running on #445.  That's what's confusing me: which ports to tunnel.  I know it's possible to do this because I've read articles about it.  But I haven't seen any recipes for actually doing it on Linux.

---

### Post by Morbius1 on 2014-06-10
I just did a quick and dirty between an Ubuntu 14.04 samba server and an OSX Mavericks client through SSH. Now this was all internal through the lan not across the wan so ....

After creating the share on Ubuntu I followed - more or less - the procedure in the HowTo on the OSX client:

```
sudo ifconfig lo0 127.0.0.2 alias up
sudo ssh -L 127.0.0.2:445:192.168.0.104:445 tester1@192.168.0.104
```

Then I opened up Finder > Connect to Server and entered:
```
smb://tester1@127.0.0.2
```

192.168.0.104 = ip address of the Ubuntu Samba server
tester1 = my test user on that server

---

### Post by Steve_Manes on 2014-06-13
> **Morbius1 said:**
> I just did a quick and dirty between an Ubuntu 14.04 samba server and an OSX Mavericks client through SSH. Now this was all internal through the lan not across the wan so ....

After creating the share on Ubuntu I followed - more or less - the procedure in the HowTo on the OSX client:

```
sudo ifconfig lo0 127.0.0.2 alias up
sudo ssh -L 127.0.0.2:445:192.168.0.104:445 tester1@192.168.0.104
```

Then I opened up Finder > Connect to Server and entered:
```
smb://tester1@127.0.0.2
```

192.168.0.104 = ip address of the Ubuntu Samba server
tester1 = my test user on that server

Thanks, Mobius1.  This works perfectly.

---

