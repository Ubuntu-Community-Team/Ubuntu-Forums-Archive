---
title: "Long delay in login with ssh"
date: 2015-12-21
forum: Networking &amp; Wireless
---

### Post by Hans_van_Leeuwen on 2015-12-21
Hi,

My system use Ubuntu 15.10 with kernel 4.2.0-21-generic.
When I login (for the first time after some hours) to that system from an other Ubuntu system it take more then a minute.
The second login takes only a few seconds.
When I stop (from the console) the sshd and start it manually with 3 times the debug flag "/usr/sbin/sshd -d -d -d" I see the location of the delay.

debug3: mm_share_sync: Share sync
debug3: mm_share_sync: Share sync end
debug1: PAM: establishing credentials
debug3: PAM: opening session
----------> DELAY OF 1 MINUTE
debug3: PAM: sshpam_store_conv called with 1 messages
User child is on pid 8657
debug1: SELinux support disabled
debug1: PAM: establishing credentials
debug1: permanently_set_uid: 1000/1000

So it seems that the delay is caused in the PAM module.sshd.debug.txt

See the attachments
-The output of /usr/sbin/sshd -d -d -d
-The file /etc/ssh/sshd-config
-The file /etc/pam.d/sshd

What could be causing this problem?
How can I solve this delay problem?

---

### Post by SeijiSensei on 2015-12-21
Usually the delay occurs because the client does both a forward and a reverse DNS lookup for the remote server.  Many times the reverse lookup either does not exist or does not match the forward lookup.

Add the server's IP and name to /etc/hosts and see if that speeds things up.

---

### Post by Hans_van_Leeuwen on 2015-12-21
The use if reverse DNS is already switched off by the parameter "UseDNS no" in the file /etc/ssh/sshd-config. See the attachment sshd-config.txt.

Do you mean the (ssh) client's IP in the /etc/host file of the (ssh) server?

---

### Post by SeijiSensei on 2015-12-21
The next problem might be the Debian, and thus Ubuntu default of
```
GSSAPIAuthentication yes
```
in the client's file /etc/ssh/ssh_config. The manual page for that file ("man ssh_config") has this at the top:
> 
     Note that the Debian openssh-client package sets several options as standard in /etc/ssh/ssh_config which are
     not the default in ssh(1):

           ·   SendEnv LANG LC_*
           ·   HashKnownHosts yes
**           ·   GSSAPIAuthentication yes**

Add the line 
```
GSSAPIAuthentication no
```
to the bottom of ssh_config and see if that helps.

I didn't mention this before because I didn't see anything about GSSAPIAuthentication in the log snippet you posted.  Then I realized it was the debugging output on the server whereas the problem's on the client.  Try running the client with "ssh -v" or even "ssh -vvv" for more verbose output. 

I think having GSSAPIAuthentication enabled by default just causes problems for ordinary users trying to connect with SSH.  I run ordinary CentOS and Ubuntu SSH servers and never have all that hoopla configured.

---

### Post by Hans_van_Leeuwen on 2015-12-22
Setting "GSSAPIAuthentication" to "no" in ssh_config on the ssh-client does not seems to help.

Only one ssh-server (with Ubuntu 15.10) has this "delay problem" and other ssh-servers (with Ubuntu 12.04 and 14.04) not.
So a ssh-client that connect to a Ubuntu 15.10 server has this "delay problem" and the same ssh-client that connect to Ubuntu 12.04 and 14.04 severs not.   


Setting "UsePAM" to "no" in sshd_config in the ssh-server (and restarting the sshd) seems to help.
But I do not know what the consequences are.

With "UsePAM" to "yes" I see a long delay in de ssh-client output. See below

debug1: Authentication succeeded (publickey).
Authenticated to ftpsec-intern ([192.168.0.246]:22).
debug2: fd 5 setting O_NONBLOCK
debug3: fd 6 is O_NONBLOCK
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
------> LONG DELAY
debug1: client_input_global_request: rtype [email]hostkeys-00@openssh.com[/email] want_reply 0
debug2: callback start
debug2: fd 3 setting TCP_NODELAY
debug3: packet_set_tos: set IP_TOS 0x10
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.

---

### Post by SeijiSensei on 2015-12-22
If you're using public-key authentication rather than logging in with a password, then UsePAM shouldn't matter and can probably be turned off.  If you have other clients who use a password, though, then they would need to start using keys instead.

[PAM]("https://en.wikipedia.org/wiki/Linux_PAM") stands for "pluggable authentication modules." It provides the standard framework in Linux for authenticating login requests.  It can use a wide variety of back-ends; the default is /etc/passwd.

---

