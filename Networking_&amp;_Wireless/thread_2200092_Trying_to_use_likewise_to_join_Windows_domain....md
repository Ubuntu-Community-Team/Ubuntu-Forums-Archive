---
title: "Trying to use likewise to join Windows domain..."
date: 2014-01-17
forum: Networking &amp; Wireless
---

### Post by Raiden616 on 2014-01-17
Hi all, 

I'm trying to use likewise to join an Ubuntu machine to my work's domain. The domain is hosted on a Windows Server 2003 PC. If I try disabling the firewall there is no difference to my problems. the domain is called nmsws.local.

**The problem is** if I run:

 ```
sudo domainjoin-cli join nmsws.local *username*
```

... i receive the following error:

```
Error: Lsass Error [code 0x0000000b]

The OU format is invalid.
```

If I try it without the ".local", I get "a bad packet was received from a DNS server...", which I take to mean that the domain name server cannot not be referenced like that.

nmsws.local is specified in the "Search domains" field in Network Manager, I have added the IP address to the hosts file and I have tried removing mdns4_minimal and mdns4 from nsswitch.conf.

Does anyone have any suggestions? I can't find the OU format ANYWHERE.

Thanks!

---

### Post by lolotux on 2014-03-04
Hi

I've got the same issue with Windows 2008R2 server and likewise-open_6.1.0.406-0ubuntu5.1_amd64.deb on a Ubuntu 12.04 !

domainjoin-cli join ourdomain.local administrateur
Joining to AD Domain:   ourdomain.local
With Computer DNS Name: ubuntu.ourdomain.local

[email]administrateur@OURDOMAIN.LOCAL[/email]'s password: 

Error: Lsass Error [code 0x0000000b]

The OU format is invalid.

Need help !

---

### Post by Aubrey_Robertson on 2014-06-25
Anybody have any luck with this error?  I'm having the exact same problem with a fresh install of Ubuntu Server 14.04 on a VM!  So frustrating.  I am using the newest build (Power Broker 8), and same stupid message about the OU.  I tried this because it said it would take minutes instead of hours (for Samba config).  Yet it's taken 4 hours of my day, with no luck, and absolutely no where could I find an answer on the interwebs!

---

### Post by prashantjois on 2014-07-28
Same issue here with Server 2012 R2.  Any ideas? Getting AD to work is a pain.

---

### Post by WRStone on 2015-01-30
Well, here's my pain.  I'm seeing the same thing:

We use PowerBroker Identity Services Open (PBIS Open) to join our Linux servers to Windows domains.  PBIS Open is the successor to Likewise Open.

We&#8217;re observing problematic behavior when attempting to join any Linux VM in MS Azure to a domain hosted by our Azure Win2K12r2 servers.

Connectivity between any Linux box and the DCs is unfettered.  Pings reply  back in about 1ms.  Telnetting to port 445 from the Linux servers immediately returns data.  I have temporarily disabled the firewall on the PDC just to make sure there&#8217;s absolutely no interference.

The output of the join command is:

-----

[ubuntu@MSSEFILEPRO02 ~]$ sudo /opt/pbis/bin/domainjoin-cli join submittalexchangeazure.net bill.stone
Joining to AD Domain:   submittalexchangeazure.net
With Computer DNS Name: mssefilepro02.submittalexchangeazure.net

[email]bill.stone@SUBMITTALEXCHANGEAZURE.NET[/email]'s password:

Error: Lsass Error [code 0x0000000b]

The OU format is invalid.

-----

I get the same output at both the command line and in the logs when attempting to join using a different Domain Admin account.

On the AD side, a computer account object for the machine gets created in the default Computers OU.  However, Linux won&#8217;t authenticate.  Other PBIS commands show that locally it doesn&#8217;t consider itself on the domain.

I&#8217;ve altered the Linux configs to override the Azure-provided DNS suffix.

I&#8217;ve done a ton of Google searching, and there are a few references to this error.  Unfortunately, no one appears to have a fix for it.

I&#8217;m a little surprised about this.  In the last two months, I&#8217;ve joined about 100 boxes to two different domains for our AWS Public VPC and GovCloud.  In a prior job, I ran a project where I joined three hundred Linux boxes to domains.  I&#8217;ve never seen this error.  This is literally the first time I&#8217;ve ever had any problem with it.

Verbose log output is below.  I'm stumped.

-----

20150130111950:INFO:Domainjoin invoked with the join command (remaining arguments will be printed later):
20150130111950:INFO:    [/opt/pbis/bin/domainjoin-cli]
20150130111950:INFO:    [--loglevel]
20150130111950:INFO:    [info]
20150130111950:INFO:    [join]
20150130111950:INFO:Domainjoin invoked with 2 arg(s) to the join command:
20150130111950:INFO:    [submittalexchangeazure.net]
20150130111950:INFO:    [bill.stone]
20150130111950:INFO:Adding mssefilepro02 (fqdn mssefilepro02.submittalexchangeazure.net) to /etc/hosts ip 127.0.0.1, removing mssefilepro02, mssefilepro02.submittalexchangeazure.net, mssefilepro02, mssefilepro02.submittalexchangeazure.net
20150130111950:INFO:Creating blank krb5.conf
20150130111950:INFO:Reading krb5 file /tmp/likewisetmpfeX4Md/etc/krb5.conf
20150130111950:INFO:Reading nsswitch file /etc/nsswitch.conf
20150130111950:INFO:Creating blank krb5.conf
20150130111950:INFO:Reading krb5 file /tmp/likewisetmpp4i5Xe/etc/krb5.conf
20150130111950:INFO:Distro Version 14.04
20150130111950:INFO:Found config file /etc/ssh/sshd_config
20150130111950:INFO:Found binary /usr/sbin/sshd
20150130111950:INFO:Reading ssh file /etc/ssh/sshd_config
20150130111950:INFO:Found open sshd version 6.6.1p1
20150130111950:INFO:Testing option ChallengeResponseAuthentication
20150130111950:INFO:Option ChallengeResponseAuthentication supported
20150130111950:INFO:Testing option UsePAM
20150130111950:INFO:Testing option PAMAuthenticationViaKBDInt
20150130111950:INFO:Option PAMAuthenticationViaKBDInt not supported
20150130111950:INFO:Testing option KbdInteractiveAuthentication
20150130111950:INFO:Option KbdInteractiveAuthentication supported
20150130111950:INFO:Testing option GSSAPIAuthentication
20150130111950:INFO:Option GSSAPIAuthentication supported
20150130111950:INFO:Testing option GSSAPICleanupCredentials
20150130111950:INFO:Option GSSAPICleanupCredentials supported
20150130111950:INFO:Found config file /etc/ssh/ssh_config
20150130111950:INFO:Found binary /usr/bin/ssh
20150130111950:INFO:Reading ssh file /etc/ssh/ssh_config
20150130111950:INFO:Testing option GSSAPIAuthentication
20150130111950:INFO:Sshd does not support -o
20150130111950:INFO:Testing option GSSAPIDelegateCredentials
20150130111950:INFO:Sshd does not support -o
20150130111954:INFO:Running module join
20150130111955:ERROR:Lsass Error [ERROR_BAD_FORMAT]

The OU format is invalid.

Stack Trace:
/builder/src-buildserver/Platform-8.2/src/linux/domainjoin/domainjoin-cli/src/main.c:1160
/builder/src-buildserver/Platform-8.2/src/linux/domainjoin/domainjoin-cli/src/main.c:554
/builder/src-buildserver/Platform-8.2/src/linux/domainjoin/libdomainjoin/src/djmodule.c:345
/builder/src-buildserver/Platform-8.2/src/linux/domainjoin/libdomainjoin/src/djauthinfo.c:857
/builder/src-buildserver/Platform-8.2/src/linux/domainjoin/libdomainjoin/src/djauthinfo.c:1226

---

### Post by WRStone on 2015-02-18
Well, they pulled me off this to stand up other virtualized environments, so I'm just swinging back to it.  I probably have today and tomorrow to get it working.

Any thoughts?  I'm still getting the same behavior.

At the command-line:

```

[root@MSSEADTEST /opt/pbis/bin]# ./domainjoin-cli --loglevel verbose join submittalexchangeazure.net bill.stone
Joining to AD Domain:   submittalexchangeazure.net
With Computer DNS Name: msseadtest.submittalexchangeazure.net

[email]bill.stone@SUBMITTALEXCHANGEAZURE.NET[/email]'s password:

Error: Lsass Error [code 0x0000000b]

The OU format is invalid.

```

From the logfile:

```

20150218110606:INFO:Domainjoin invoked with the join command (remaining arguments will be printed later):
20150218110606:INFO:    [./domainjoin-cli]
20150218110606:INFO:    [--loglevel]
20150218110606:INFO:    [verbose]
20150218110606:INFO:    [join]
20150218110606:INFO:Domainjoin invoked with 2 arg(s) to the join command:
20150218110606:INFO:    [submittalexchangeazure.net]
20150218110606:INFO:    [bill.stone]
20150218110606:INFO:Adding msseadtest (fqdn msseadtest.submittalexchangeazure.net) to /etc/hosts ip 127.0.0.1, removing msseadtest, msseadtest.submittalexchangeazure.net, msseadtest, msseadtest.submittalexchangeazure.net
20150218110606:INFO:Creating blank krb5.conf
20150218110606:INFO:Reading krb5 file /tmp/likewisetmpNh1Rws/etc/krb5.conf
20150218110606:INFO:Reading nsswitch file /etc/nsswitch.conf
20150218110606:INFO:Creating blank krb5.conf
20150218110606:INFO:Reading krb5 file /tmp/likewisetmpG6N3NQ/etc/krb5.conf
20150218110606:INFO:Distro Version 14.04
20150218110606:INFO:Found config file /etc/ssh/sshd_config
20150218110606:INFO:Found binary /usr/sbin/sshd
20150218110606:INFO:Reading ssh file /etc/ssh/sshd_config
20150218110606:INFO:Found open sshd version 6.6.1p1
20150218110606:INFO:Testing option ChallengeResponseAuthentication
20150218110606:INFO:Option ChallengeResponseAuthentication supported
20150218110606:INFO:Testing option UsePAM
20150218110606:INFO:Testing option PAMAuthenticationViaKBDInt
20150218110606:INFO:Option PAMAuthenticationViaKBDInt not supported
20150218110606:INFO:Testing option KbdInteractiveAuthentication
20150218110606:INFO:Option KbdInteractiveAuthentication supported
20150218110606:INFO:Testing option GSSAPIAuthentication
20150218110606:INFO:Option GSSAPIAuthentication supported
20150218110606:INFO:Testing option GSSAPICleanupCredentials
20150218110606:INFO:Option GSSAPICleanupCredentials supported
20150218110606:INFO:Found config file /etc/ssh/ssh_config
20150218110606:INFO:Found binary /usr/bin/ssh
20150218110606:INFO:Reading ssh file /etc/ssh/ssh_config
20150218110606:INFO:Testing option GSSAPIAuthentication
20150218110606:INFO:Sshd does not support -o
20150218110606:INFO:Testing option GSSAPIDelegateCredentials
20150218110606:INFO:Sshd does not support -o
20150218110611:INFO:Running module join
20150218110611:VERBOSE:eventlog:LwEvtOpenEventlog():/builder/src-buildserver/Platform-8.2/src/linux/eventlog/client/eventlog.c:174: client::eventlog.c OpenEventlog server=<null>)

20150218110611:ERROR:Lsass Error [ERROR_BAD_FORMAT]

The OU format is invalid.

Stack Trace:
/builder/src-buildserver/Platform-8.2/src/linux/domainjoin/domainjoin-cli/src/main.c:1160
/builder/src-buildserver/Platform-8.2/src/linux/domainjoin/domainjoin-cli/src/main.c:554
/builder/src-buildserver/Platform-8.2/src/linux/domainjoin/libdomainjoin/src/djmodule.c:345
/builder/src-buildserver/Platform-8.2/src/linux/domainjoin/libdomainjoin/src/djauthinfo.c:857
/builder/src-buildserver/Platform-8.2/src/linux/domainjoin/libdomainjoin/src/djauthinfo.c:1226

```

I also have a Wireshark capture from the DC the Linux client is communicating with, if it helps.

---

### Post by WRStone on 2015-02-19
Sorry.  Gotta bump this.  It's preventing us joining about 20 Ubuntu 14.04.1 servers to an Active Directory domain.

---

### Post by WRStone on 2015-02-20
As a test, I spun up a CentOS instance in Azure, then installed PBIS Open and attempted to join the domain.  I get similar results, the only difference being that the log is more detailed -- although no less revealing.

So this isn't an issue with Ubuntu.

Thoughts?

---

### Post by WRStone on 2015-02-20
I discovered the issue.

The Windows domain's NetBIOS name was in lower-case.  Apparently PBIS Open is very case-sensitive about that.

Once the NetBIOS was changed to upper case, everything went flawlessly.

---

