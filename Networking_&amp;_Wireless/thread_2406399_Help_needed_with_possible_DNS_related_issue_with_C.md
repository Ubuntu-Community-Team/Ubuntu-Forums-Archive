---
title: "Help needed with possible DNS related issue with Comcast mail servers"
date: 2018-11-20
forum: Networking &amp; Wireless
---

### Post by tomdkat on 2018-11-20
Hi!  Starting on Monday, November 19, 2018, Thunderbird on two Ubuntu systems I use can't connect to Comcast's POP3 mail servers.  One system is running Ubuntu 18.04 and the other Ubuntu 18.10.  Both are 64-bit systems and both are running Thunderbird 60.2.1.  Thunderbird issues a "Failed to connect to server mail.comcast.net" message and I can't retrieve new mail.   So, I did some research and experimentation and found the following:

[LIST]
[*]Thunderbird can connect to Comcast's IMAP servers just fine
[*]I can't ping mail.comcast.net
[*]I can do DNS lookups on mail.comcast.net just fine
[/LIST]

When I ping Comcast's mail server address, I get this:
```

tom@deathstar:~$ ping mail.comcast.net
ping: mail.comcast.net: Name or service not known
tom@deathstar:~$ 

```

When I do DNS lookups on "mail.comcast.net", I get addresses back:
```

tom@deathstar:~$ nslookup mail.comcast.net
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
mail.comcast.net	canonical name = imap.ge.xfinity.com.
Name:	imap.ge.xfinity.com
Address: 96.118.242.209
Name:	imap.ge.xfinity.com
Address: 96.118.242.197
Name:	imap.ge.xfinity.com
Address: 96.118.242.233
Name:	imap.ge.xfinity.com
Address: 96.118.242.225
Name:	imap.ge.xfinity.com
Address: 96.118.242.226
Name:	imap.ge.xfinity.com
Address: 96.118.242.217
Name:	imap.ge.xfinity.com
Address: 96.118.242.208
Name:	imap.ge.xfinity.com
Address: 96.118.242.230
Name:	imap.ge.xfinity.com
Address: 96.118.242.232
Name:	imap.ge.xfinity.com
Address: 96.118.242.218
Name:	imap.ge.xfinity.com
Address: 96.118.242.211
Name:	imap.ge.xfinity.com
Address: 96.118.242.242
Name:	imap.ge.xfinity.com
Address: 96.118.242.221
Name:	imap.ge.xfinity.com
Address: 96.118.242.196
Name:	imap.ge.xfinity.com
Address: 96.118.208.40
Name:	imap.ge.xfinity.com
Address: 96.118.208.99
Name:	imap.ge.xfinity.com
Address: 2001:558:fc11:9:f816:3eff:fee8:4f07
Name:	imap.ge.xfinity.com
Address: 2001:558:fc11:9:f816:3eff:fe7d:1b0c
Name:	imap.ge.xfinity.com
Address: 2001:558:fc11:9:f816:3eff:fe25:5ae5
Name:	imap.ge.xfinity.com
Address: 2001:558:fc11:9:f816:3eff:fef6:babc
Name:	imap.ge.xfinity.com
Address: 2001:558:fc11:9:f816:3eff:fe87:c172
Name:	imap.ge.xfinity.com
Address: 2001:558:fc11:9:f816:3eff:fee6:7a57
Name:	imap.ge.xfinity.com
Address: 2001:558:fc11:9:f816:3eff:fe0f:a4a
Name:	imap.ge.xfinity.com
Address: 2001:558:fc11:2:f816:3eff:fec7:cb93
Name:	imap.ge.xfinity.com
Address: 2001:558:fee2:1000:f816:3eff:fe42:4f14
Name:	imap.ge.xfinity.com
Address: 2001:558:fc18:0:f816:3eff:fe33:9aaa
Name:	imap.ge.xfinity.com
Address: 2001:558:fc18:0:f816:3eff:feb2:8c0d
Name:	imap.ge.xfinity.com
Address: 2001:558:fc18:0:f816:3eff:fef1:25a5
Name:	imap.ge.xfinity.com
Address: 2001:558:fc18:0:f816:3eff:febd:320a
Name:	imap.ge.xfinity.com
Address: 2001:558:fc18:0:f816:3eff:fe36:aba3
Name:	imap.ge.xfinity.com
Address: 2001:558:fc18:0:f816:3eff:fe3f:76f2
Name:	imap.ge.xfinity.com
Address: 2001:558:fc18:0:f816:3eff:fe45:1d1e

tom@deathstar:~$ dig mail.comcast.net

; <<>> DiG 9.11.4-3ubuntu5-Ubuntu <<>> mail.comcast.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15037
;; flags: qr rd ra; QUERY: 1, ANSWER: 17, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;mail.comcast.net.		IN	A

;; ANSWER SECTION:
mail.comcast.net.	15	IN	CNAME	imap.ge.xfinity.com.
imap.ge.xfinity.com.	12	IN	A	96.117.3.119
imap.ge.xfinity.com.	12	IN	A	96.117.3.96
imap.ge.xfinity.com.	12	IN	A	96.117.3.143
imap.ge.xfinity.com.	12	IN	A	96.117.3.145
imap.ge.xfinity.com.	12	IN	A	96.117.3.129
imap.ge.xfinity.com.	12	IN	A	96.117.3.148
imap.ge.xfinity.com.	12	IN	A	96.117.3.201
imap.ge.xfinity.com.	12	IN	A	96.117.3.136
imap.ge.xfinity.com.	12	IN	A	96.118.133.238
imap.ge.xfinity.com.	12	IN	A	96.117.3.128
imap.ge.xfinity.com.	12	IN	A	96.117.3.144
imap.ge.xfinity.com.	12	IN	A	96.117.2.238
imap.ge.xfinity.com.	12	IN	A	96.117.3.110
imap.ge.xfinity.com.	12	IN	A	96.117.3.140
imap.ge.xfinity.com.	12	IN	A	96.117.3.154
imap.ge.xfinity.com.	12	IN	A	96.117.3.132

;; Query time: 13 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Tue Nov 20 06:58:31 PST 2018
;; MSG SIZE  rcvd: 334

tom@deathstar:~$ 

```

I have no problems accessing mail through Comcast's website and other sites work fine.  I can access email on non-Comcast servers just fine.   On Sunday, November 18, 2018, Thunderbird *was* able to access Comcast mail via POP3 just fine.  Clearly, something changed and I think it was probably something on the Comcast side, with the POP3 mail server address being changed to a CNAME of the IMAP mail server address.

The reason I'm posting this is to find out how I can fix the "ping" issue and the "Failed to connect to server" issue Thunderbird is experiencing.  On a Linux Mint 18.3 system I also use, I'm able to ping "mail.comcast.net" just fine and Thunderbird (60.2.1) has no problems accessing my mail using Comcast's POP3 mail server.    So, I'm looking for help in troubleshooting and resolving what might be DNS lookup related issue that's preventing Thunderbird from accessing Comcast's POP3 mail server.

I'm using the "Ubuntu 18.04/18.10 stock" DNS related configuration settings, meaning I haven't changed anything.   My Ubuntu 18.10 system has an Ethernet connection to my TRENDNet router and I use a Netgear cable modem.  Outside of the Thunderbird issue, my Internet access works well.

My /etc/resolv.conf file contains the following:
```

tom@deathstar:~$ dir -l /etc/resolv.conf
lrwxrwxrwx 1 root root 39 Jan 15  2018 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf
tom@deathstar:~$ cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "resolvectl status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
tom@deathstar:~$ 

```

As part of my online research, I did find this article:

[https://moss.sh/name-resolution-issue-systemd-resolved/](https://moss.sh/name-resolution-issue-systemd-resolved/)

which basically states systemd-resolved doesn't support RRSIG and I was able to get some of the test results posted in that article on the Ubuntu 18.04 system I use.

In any event, this is where I'm at now.  What's the best way to diagnose the cause of both ping and Thunderbird's inability to contact Comcast's POP3 mail server "mail.comcast.net"?

Thanks in advance!

---

### Post by walts48 on 2018-11-20
It appears that tomdkat and I are the only Comcast users on Linux.

I have the same problem, get the same ping results and today my Verizon POP3 account connection fails in Thunderbird.

I'm wondering if any of the Bind9, systemd, libnss or any of the recent updates broke something?

---

### Post by lisati on 2018-11-20
@walts48:

Please be patient. The forum community is made up of people from all around the world who live in different time zones, who don't always get to see support requests when first posted.

---

### Post by cscheppner on 2018-11-20
I also use Ubuntu 18.04 and Comcast email w/ Thunderbird and I am experiencing the same issue (though I had been using pop.comcast.net port 995).  My Thunderbird w/ Comcast email worked fine for 4+ years on 3 LTS versions of Ubuntu/  It was working fine on Friday Nov 16. 1018.  I came into work yesterday Nov 19, 2018 and Thunderbird was unable to connect to the incoming Comcast mail server (though it could connect to outgoing smtp).

I did find a hacky workaround...

In a shell I did nslookup mail.comcast.net
I copied the IP of the first non-authoritative answer (there were only non-authoritative answers).
I pasted that IP into the Thunderbird Preference..Account Settings..Server Settings .. Server Name
(my other settings are SSL/TLS and port 995 because I use pop)
Then clicked OK.

Then when I tried to Get Messages, I got a popup error about a certificate not matching and did I want to override...
I did do a temporary override, then was prompted for and entered my email password, and Thunderbird retrieved my email.

Probably not the most secure safe way to get my mail, but I got my mail.

---

### Post by localjoe on 2018-11-20
I have had the exact same problem in the last two or three days or so and [**[COLOR=#000000]cscheppner[/COLOR]**]("https://ubuntuforums.org/member.php?u=2112200")'s solution worked for me. I has to substitute an IP address for the string "pop3.comcast.net" in Thunderbird's Server Settings / Server Name.

I am running Thunderbird 60.2.1 64-bit on Linux Ubuntu 18.04.1 LTS

While searching before finding this thread I saw a thread on another forum (I wish I could remember where :(  ) that postulated that someone's (Thunderbird's) certificates from Symantec were now obsolete. But I don't know enough about it so cannot verify that theory. 

Well at least I have my email now. 

Thank you [**[COLOR=#000000]cscheppner[/COLOR]**]("https://ubuntuforums.org/member.php?u=2112200")

---

### Post by 1clue on 2018-11-20
I had comcast years ago, and used it with Linux. Stopped about 6 or 7 years ago when I moved to a different state.

I had issues with DNS from Comcast servers too, and so did other people I knew.

I came to suspect that they messed with DNS resolution based on what type of customer you were. I had frequent long delays in name resolution of highly trafficked sites, like google.com or yahoo or news sites. Seconds-long.

In my opinion at that time, I suspected that if you had a minimal Internet account they would slow you down so you would upgrade. The speed tests would do a DNS search at the first and then handle a single connection for the entire test, so it was rated speed. A news site or typical commercial website has a bunch of connections from a bunch of different servers with almost every page load. You could mess with TTL and cause the browser to hit the DNS server more often, and delay the response from the DNS to slow down the user experience. 

I also suspected them of "losing" popular sites when your payment was late, and that when they shut off your service they actually just told your DHCP server to assign a different DNS that doesn't exist.

I set up a few scripts to test some of those theories, and one part of it was that I would use google's DNS server, and had a script to copy my version of /etc/resolv.conf over the top of whatever was there. I could bring up a disabled account that way.

---

### Post by rempat on 2018-11-20
I discovered the same problem on November 20, 2018.  Comcast customer service were no help.  The workaround from cscheppner is getting my emails and I am thankful!

---

### Post by QIII on 2018-11-20
You will need to set up an imap account -- in Thunderbird, not with Comcast -- using your current Comcast account.  Then you will have to rename the current account to avoid getting an error and build folders in the new account that match your current account.  Following that, you will have to go through a tedious process of copying emails from each folder in the old account to the corresponding folders in the new account.  Then delete the POP account from Thunderbird.

[This]("https://support.mozilla.org/en-US/kb/switch-pop-imap-account") might help.

And, yes, please be patient.  Don't expect everyone to jump on every new post.  We all have lives outside of the Forum.  None of us works for Canonical and we all volunteer our time as we have it to give. I only just saw this post.  I have Comcast, use Thunderbird, ran into the same issue and fixed it.

Comcast seems to have decided to unilaterally change things without bothering to tell anyone.

---

### Post by walts48 on 2018-11-21
Don't know where I wasn't being patient. More surprised that I wasn't seeing more reports of the problem.

There are over 25 million Thunderbird users. Surely there are  more than the now 5 users reporting the problem using Thunderbird with Comcast POP. Maybe not. 

Not a mention of the problem in the m.support.thunderbird newsgroup, Only one on the mozillaZine forum (tomdkst's post), none on reddit. Didn't check Thunderbird support at SUMO.

I have my Thunderbird betas on Ubuntu and Linux Mint switched over to IMAP. 

May try csheppner's workaround on my Ubuntu supplied 60.2.1.

Undecided about my 60.3.1 and 65.0a1 versions from Thunderbird.

---

### Post by james-warner on 2018-11-21
Allow me to join this growing crowd as I've experienced the same problem since last Sunday.  I am running Thunderbird 60.2.1 64-bit under Ubuntu 18.10.  For what it's worth my experience suggests the root cause is somehow related to Ubuntu, possibly systemd-resolved.

With the same resources (router, ~/.thunderbird directory contents, etc) I experience no problem running Thunderbird 60.3.0 under Fedora-29, openSUSE Tumbleweed or an iMac.  My pop3 email is retrieved from mail.comcast.net without problems.

I, too, wish to thank cscheppner for the work around.

---

### Post by jerry47 on 2018-11-21
I just discovered the above problem yesterday. I just built an Intel NUC7i7 and installed Ubuntu 18.10 on it. Previously I installed 18.04 on an 10 year old laptop. It connected to comcast email via pop3 just fine two weeks ago. The NUC on the other hand did not. I don't believe this is a Thunderbird issue. First, I installed Thunderbird in a virtual environment on my Win 7 machine. Worked just fine connecting to port 995 using pop3. Second, I installed Evolution Mail on the NUC machine and it could not connect to comcast either. The error was "can not resolve mail.comcast.net". Now its looking like a DNS issue only for comcast mail only with Ubuntu. Third, I checked my laptop which has not been running for a couple of weeks and where Thunderbird was working it indeed had the same issue. I had not even updated it. 

I discovered the same thing pinging on my windows machine that mail.comcast.net was redirected to imap.ge.xfinity.com.  I used the host imap.ge.xfinity.com instead and Thunderbird grumbled about security and certificates. Ignored it and pop3 worked. 

Since my Ubuntu install is just for evaluation purposes its not an issue for me. I just configured it IMAP. But I am very curious as to what's going on. We have two Win 7 machines, two iPads, two mobiles all using comcast pop3 without an issue even with the redirection. I was chatting with comcast on twitter for a couple of hours. He checked their archives and it revealed nothing. But he said they have very few customers using pop3 and very few using Linux. He does want me to contact him to log this issue as soon as I can find what the problem is exactly.

---

### Post by 1clue on 2018-11-21
You know, at some point I decided that an ISP's mail server is not necessarily a great thing. 

For one thing it only lasts as long as you have that ISP, so if you move to a place where that ISP does not exist, you lost your email address and probably your mail history.

Another issue is they seem to be more problematic than an independent mail provider.

I've started using several emails each from some third-party provider. At least one is a paid account NOT at a place like gmail or yahoo, and not linked to any of those places with any sort of forwarding.

The thing is, if you have a free account with ANY service on the Internet, you are not the customer. You're the product being sold to customers. If you pay, then you're the customer. Gmail, yahoo and every other free mail service, as well as any forum (including this one) gets significant value translating to money for the host.

That's not always a bad thing. Canonical, in maintaining Ubuntu and hosting this forum, gets customer support for and from the forum members. The good part of that is the members get customer support too. In maintaining Ubuntu, they get a stable Linux platform controlled by them on which software they sell can be hosted.

---

### Post by QIII on 2018-11-21
The "problem", as stated by Comcast, is that they are doing away with POP support and going to IMAP.

Canonical and Mozilla can't do anything about that.

---

### Post by walts48 on 2018-11-21
> **QIII said:**
> The "problem", as stated by Comcast, is that they are doing away with POP support and going to IMAP.

Canonical and Mozilla can't do anything about that.

Where have they stated that, why haven't they sent out emails informing customers, and why does the mail.comcast.net server name still work with Thunderbird on Windows, and older versions of Ubuntu and other Linux operating systems?

I'll agree the Thunderbird developers (no longer paid Mozilla employees, but a separate entity) can't do anything about it.

---

### Post by tomdkat on 2018-11-21
Thanks for the replies and for the discussion.  :)   What is it about Comcast's DNS configuration for "mail.comcast.net" and "pop3.comcast.net" that seem to confuse systemd-resolved?  Thunderbird aside, I can't even ping "mail.comcast.net".   Is Comcast's DNS misconfigured or is this a systemd-resolved problem?

Peace...

---

### Post by jerry47 on 2018-11-22
Comcast is not eliminating support for pop3. At least not in the foreseeable future. They are dropping port 110 supposedly this month. It worked the other day. Yes, I have not been able to ping mail.comcast.net or pop3.comcast.net. According to their online email support page they are moving over to pop3.comcast.net. But both of these host names get redirected to imap.ge.xfinity.com. I can ping both above host names on Windows 7. But I can't however ping either one on my iPad even though the iPad is set up with pop3 email and is working. The iPad, Ubuntu, Win7 ping imap.comcast.net without a problem. But there are no redirects. I've been in touch with comcast techs for the last two days on Twitter. There is no misconfiguration on their side. Several have responded but don't know the reason for the redirect. The only OS having an issue thus far is Ubuntu. So if November 19th is the first day the problem started then its very likely two things are contributing to the issue. One, for whatever reason, Comcast redirected the pop3 host names and Ubuntu systemd-resolved is unable to resolve the redirected names.

---

### Post by jerry47 on 2018-11-22
I ran across this article about DNS issues with Systemd-resolved. Since I have a laptop running Ubuntu 18.04 as a test machine and don't care if I break it, I decided to disable systemd-resolved and replace it with unbound. The pop3 email issue is fixed. Here's the link. [https://blobfolio.com/2017/05/fix-linux-dns-issues-caused-by-systemd-resolved/](https://blobfolio.com/2017/05/fix-linux-dns-issues-caused-by-systemd-resolved/) It proves that two things occurred. Comcast did make the redirection change on or just before November 19th and Systemd-resolved has a problem.

---

### Post by walts48 on 2018-11-22
> **jerry47 said:**
> I ran across this article about DNS issues with Systemd-resolved. Since I have a laptop running Ubuntu 18.04 as a test machine and don't care if I break it, I decided to disable systemd-resolved and replace it with unbound. The pop3 email issue is fixed. Here's the link. [https://blobfolio.com/2017/05/fix-linux-dns-issues-caused-by-systemd-resolved/](https://blobfolio.com/2017/05/fix-linux-dns-issues-caused-by-systemd-resolved/) It proves that two things occurred. Comcast did make the redirection change on or just before November 19th and Systemd-resolved has a problem.

Good to hear POP3 is working for you, and it is a systemd-resolved issue.

I switched my Thunderbird 64.0b2's on Ubuntu 18.04 and Linux Mint over to IMAP.

The 60.2.1, 60.3.1 and 65.0a1 versions are rarely used.

I'm glad we have 10 years of support for Ubutnu 18.04. Maybe the issue will be fixed in 5 years.

---

### Post by tomdkat on 2018-11-24
> **jerry47 said:**
> I ran across this article about DNS issues with Systemd-resolved. Since I have a laptop running Ubuntu 18.04 as a test machine and don't care if I break it, I decided to disable systemd-resolved and replace it with unbound. The pop3 email issue is fixed. Here's the link. [https://blobfolio.com/2017/05/fix-linux-dns-issues-caused-by-systemd-resolved/](https://blobfolio.com/2017/05/fix-linux-dns-issues-caused-by-systemd-resolved/) It proves that two things occurred. Comcast did make the redirection change on or just before November 19th and Systemd-resolved has a problem.
Thanks for the info!

UPDATE:  I just switched to Unbound and everything is working fine for me as well.  Thanks again!

Peace...

---

### Post by tomdkat on 2018-11-25
I submitted a bug report on this issue:

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1805027](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1805027)

Peace...

---

### Post by jnmjr on 2018-11-29
I too switched to IMAP when my POP3 failed about 3 weeks ago, all was working fine until I did my weekly update last night and this morning IMAP failed. I'm so glad I found this article, obviously it's an Ubuntu issue, TBird works fine with my Win10, so I didn't bother to contact Comcast. Unbound resolved my issue. Hope Canonical addresses this problem.

Ubuntu 18.04 64bit
TBird 60.2.1

---

### Post by walts48 on 2018-11-29
> **jnmjr said:**
> I too switched to IMAP when my POP3 failed about 3 weeks ago, all was working fine until I did my weekly update last night and this morning IMAP failed. I'm so glad I found this article, obviously it's an Ubuntu issue, TBird works fine with my Win10, so I didn't bother to contact Comcast. Unbound resolved my issue. Hope Canonical addresses this problem.

Ubuntu 18.04 64bit
TBird 60.2.1

Oh good, I'm not the only one that can't connect using IMAP now.

Fedora 29 works with either type of Comcast account, so...

...to switch or not to switch, use web mail or Thunderbird on Windows 10.

BTW Thunderbird 60.3.2 will be out soon. I tested the release candidate on Ubuntu 18.04, Linux Mint 19, Fedora 29 and Windows 10 today.

---

### Post by trevelyon on 2018-11-29
This is a pain but temporarily you can find the IP of one of the comcast imap servers (use dig imap.comcast.com and pick one of the IP addresses for imap.ge.xfinity.com).  Add this to your /etc/hosts file (as root) with that ip address and then you can connect and use as normal.  This is a lot easier than changing the server name to an ip address or imap.ge.xfinity.com.  Hopefully this gets fixed soon and then we just delete this line from /etc/hosts to get back to normal.  Hope this helps

---

### Post by aehjr1 on 2018-11-29
Thanks all, especially trevelyon.  Not sure I wanted to install the alternative software, though I still look into more.  Best of all for me, digging "mail.comcast.net", though yielding only "imap.ge.xfinity.com", I was still able to get my POP account to work using the /etc/hosts workaround...I still like POP better than IMAP as I **like** storing my emails locally...I don't **want** to access email from multiple devices and see all my saved emails.

---

### Post by dhlocker on 2018-11-30
Rather than using a fixed IP address, I reset the server name to imap.ge.xfinity.com (the canonical name for imap.comcast.net) then had to submit my password for the newly-named server. Works a treat.

---

### Post by walts48 on 2018-11-30
> **dhlocker said:**
> Rather than using a fixed IP address, I reset the server name to imap.ge.xfinity.com (the canonical name for imap.comcast.net) then had to submit my password for the newly-named server. Works a treat.

Well, I can't do that in the beta version of Thunderbird I prefer using for daily use because I switched it over to IMAP.

Now that doesn't connect, and POP3 or IMAP accounts can't be created in a new profile.

I managed to change the server name in the outdated Ubuntu Thunderbird 60.2.1 version that still has a POP3 account for Comcast.

Did the same with my Thunderbird 60.3.1 from Thunderbird and updated it to version 60.3.2 released today.

[https://www.thunderbird.net/en-US/thunderbird/60.3.2/releasenotes/](https://www.thunderbird.net/en-US/thunderbird/60.3.2/releasenotes/)

We'll see how long that works.

---

### Post by tomdkat on 2018-11-30
> **tomdkat said:**
> I submitted a bug report on this issue:

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1805027](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1805027)

Peace...
If anyone else experiencing this issue has a Launchpad account, please update the bug report I filed to let the developers know how widespread the possible underlying issue is.

Thanks!

Peace...

---

### Post by QIII on 2018-11-30
Please don't "update" the bug by posting.  That only confuses things.  Simply use the "Affects me" button.

---

### Post by nef1312 on 2018-11-30
I had (beginning today), until i followed dhlocker[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=1126269")[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=1126269")'s suggestion to change the server name to imap.ge.xfinity.com, the same problem. I was using Thunderbird with imap for 2 comcast accounts and have Ubuntu 18.04.1 (upgraded from 16.04). I had tried using "dig" to get a workable IP addresss but it did not help to add that address to etc/hosts. So, I was really very happy to have found dhlocker[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=1126269")[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=1126269")'s suggestion.

---

### Post by hghopkins on 2018-11-30
I am running Ubuntu 18.04 and using Comcast.  As with others here email was running fine until about a week ago.  Just would like to add that problem occurs with Evolution as well as Thunderbird. POP3 and IMAP both fail.  openssl s_client -showcerts -servername imap.ge.xfinity.com -connect imap.ge.xfinity.com:995 appears to yield proper result. As does using port 993 per IMAP settings. That is, server is found and certificates appear to be there.  Running same command but with imap.comcast.net or pop3.comcast.net results in 'Name or service not known'.  However, 'testssl -p imap.comcast.net' or 'testssl -p pop3.comcast.net' appeared to produce proper results.  nslookup and ping yielded same result as previously reported by others.   The workaround described using imap.ge.xfinity.com as server name works both for Evolution as well as Thunderbird.  For the various programs to fail there must be some common point.  As stated by others, the theory of systemd-resolved seems to fit the data.  Until a more permanent fix is found I, as others, will be using imap.ge.xfinity.com as server name.  This is less than optimal since it is not the recommended settings from Comcast which could change.  From my point of view this problem is not 'solved'.

---

### Post by tomdkat on 2018-11-30
> **QIII said:**
> Please don't "update" the bug by posting.  That only confuses things.  Simply use the "Affects me" button.

Sorry for that.  Thanks for the correction and for the clarification.  :)

Peace...

---

### Post by Electraglider on 2018-12-01
> **jerry47 said:**
> I ran across this article about DNS issues with Systemd-resolved. Since I have a laptop running Ubuntu 18.04 as a test machine and don't care if I break it, I decided to disable systemd-resolved and replace it with unbound. The pop3 email issue is fixed. Here's the link. [https://blobfolio.com/2017/05/fix-linux-dns-issues-caused-by-systemd-resolved/](https://blobfolio.com/2017/05/fix-linux-dns-issues-caused-by-systemd-resolved/) It proves that two things occurred. Comcast did make the redirection change on or just before November 19th and Systemd-resolved has a problem.

Just discovered the same problem yesterday after changing to imap with Comcast and Thunderbird. I can confirm that the solution put forth in the above post has solved the issue for me. Many thanks.:p

---

### Post by hghopkins on 2018-12-01
Something happened, for the moment, email seems to be working again.  Looks like Comast did something . . .

---

### Post by hghopkins on 2018-12-01
One thing further.  Using ../run/systemd/resolve/stub-resolv.conf link to /etc/resolv.conf yields different result than ../run/systemd/resolve/resolv.conf link to /etc/resolv.conf. The ../run/systemd/resolve/resolv.conf link appears to yield expected operation of email clients.  An IPv6 address is used rather than an IPv4.  Does anyone know why different versions of resolv.conf might yield different result?

---

### Post by Kris_M on 2018-12-03
> **dhlocker said:**
> Rather than using a fixed IP address, I reset the server name to imap.ge.xfinity.com (the canonical name for imap.comcast.net) then had to submit my password for the newly-named server. Works a treat.

Yes. in TBird change mail.comcast.net to imap.ge.xfinity.com
it will ask about the certificate.
Say okay to save this exception.
On next read it will ask for password - just give it the same one you used before. 
no renaming of files - easy.
Ubuntu prob. Bypassed

---

### Post by tommylovell on 2018-12-05
I, too, have the same problem. I went to Ubuntu 18.04, thus systemd-resolve, and my Comcast pop mail (evolution) quit. 

I changed mail.comcast.net to imap.ge.xfinity.com and mail works. A precarious work-around.

I just found this and haven’t read all four pages yet, but found that mail.comcast.net is a cname entry with no ipv6 ‘a’ entries. 
‘ping pop3.comcast.net’ and ‘ping mail.comcast.net’ both fail to convert name to ip,
but ‘ping -4 pop3.comcast.net’ will succeed in converting the name to imap.ge.xfinity.com.

I think systemd (systemd-resolve) is the problem, not any of the (non-127.0.0.53) dns clients. 

So so far pop and the work-around work. I’m not confident that the systemd bug will be fixed any time soon.
Or that the work-around will not have to be modified in the future...

---

### Post by pckennedy11 on 2018-12-06
I found additional help here:

[https://forums.xfinity.com/t5/Email-Web-Browsing/imap-comcast-net-not-responding/m-p/3169122/highlight/false#M204051](https://forums.xfinity.com/t5/Email-Web-Browsing/imap-comcast-net-not-responding/m-p/3169122/highlight/false#M204051)

I have Thunderbird configured for IMAP with Comcast. It stopped working on 30 November 2018. As was noted earlier, Thunderbird works as expected in Windows 10, so the issue is with Linux and Thunderbird. As ShellMeister recommends on the Comcast forum, installing libnss-resolve fixed the issue for me. Still, it is not clear to me if this is just another workaround like changing the imap server to imap.ge.xfinity.com. 

Cheers.

---

### Post by kjaspan on 2018-12-07
I found the advice above useful, with some differences.

For the incoming server, I used the IP address found from nslookup, 

 nslookup imap.comcast.net
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
imap.comcast.net	canonical name = imap.ge.xfinity.com.
Name:	imap.ge.xfinity.com
Address: 96.118.148.71

So I plugged in 96.118.148.71 in place of imap.comcast,net. All other settings, like port, authentication method (Normal Password) and Connection security (SSL/TLS) remained as before.

I then, as mentioned above, had to agree to the certificate override. I could now receive incoming mail but outgoing did not work. Here's what I found:
I could ping smtp.comcast.net so there was no need to plug in the IP address or smtp.g.comcast.net. I found I had to change the connection security to STARTTLS, per the Comcast recommendation here:
[https://www.xfinity.com/support/articles/setting-up-thunderbird](https://www.xfinity.com/support/articles/setting-up-thunderbird)

I was then able to send messages.

Thanks for the guidance of all those above.
:D

---

### Post by walts48 on 2018-12-11
> **pckennedy11 said:**
> I found additional help here:

[https://forums.xfinity.com/t5/Email-Web-Browsing/imap-comcast-net-not-responding/m-p/3169122/highlight/false#M204051](https://forums.xfinity.com/t5/Email-Web-Browsing/imap-comcast-net-not-responding/m-p/3169122/highlight/false#M204051)

I have Thunderbird configured for IMAP with Comcast. It stopped working on 30 November 2018. As was noted earlier, Thunderbird works as expected in Windows 10, so the issue is with Linux and Thunderbird. As ShellMeister recommends on the Comcast forum, installing libnss-resolve fixed the issue for me. Still, it is not clear to me if this is just another workaround like changing the imap server to imap.ge.xfinity.com. 

Cheers.

Thank you! Came across this while getting a link to the thread for a Thunderbird bug report.

Just installed libnss-resolve in my Linux Mint 19 and was able to create a new mail.comcast POP3 account using a test profile, and a new imap.comcast.net account in another test profile. Both got emails downloaded.

Now to try changing the server name back in my production profile and add libnss-resolve to my Ubuntu 18.04.

Hope the bug reporter gets Thunderbird working with Comcast on his Fedora 29.

---

### Post by apriest on 2018-12-15
I changed my incoming server to 

imap.ge.xfinity.com 
port 993 
security SS/TLS
normal password 

This has been working perfectly since.

---

### Post by apriest on 2018-12-15
I changed my incoming server to

imap.ge.xfinity.com
port 993
security SS/TLS
normal password

This has been working perfectly since.

---

### Post by srliner on 2019-01-13
I had the exact same problem. It occurred with Thunderbird and also Evolution. I found the solution on a Comcast user group: Install libnss-resolve and reboot.

---

### Post by wildmanne39 on 2019-01-13
Please use the report button in the left bottom corner of the post and ask us to remove the post.

Thanks

---

