---
title: "FTP completely messed up"
date: 2014-02-13
forum: Networking &amp; Wireless
---

### Post by richard30 on 2014-02-13
I'm running Ubuntu Server (Lucid). My FTP server is completely messed up and I don't know how to untangle myself...

Years ago, I originally installed proftpd. This week, I decided to use SFTP (via port 22). It worked for a day, then suddenly Filezilla kept having problems doing file transfers. I stupidly tried installing vsftpd without removing proftpd. Filezilla still wouldn't work.

So I tried removing proftpd, but I got a warning that proftpd wasn't installed--it defaulted to removing proftpd-basic. Then it told me proftpd-basic wasn't installed. I was puzzled.

So I rm'd everything on my filesystem named 'proftpd', including /etc/init.d/proftpd. I figure proftpd was gone for good.

I couldn't connect with Filezilla, so I thought something was wrong with vsftpd. So I removed vsftpd. I figure now I don't have **any** FTP server running. WRONG!

I tried connecting with Filezilla using SFTP (port 22). It connected! I think it's connected to proftpd! WTF.

My system is in a total mess. I have no idea what FTP state it's in. I can't determine for sure which FTP server is running. And I don't know _how to get back to a clean slate_ so that I can install **either** vsftpd **or** proftpd.

I need saving. :-(

---

### Post by richard30 on 2014-02-13
[COLOR=#000000][I]Okay, I think I know where I went wrong. SSH has its own FTP server. It was working until I messed it up with the following, used to limit the number of login attempts:

iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent \[/I][/COLOR]
[COLOR=#000000]*--set*[/COLOR]

[COLOR=#000000]*iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent \*[/COLOR]
[COLOR=#000000][I]--update --seconds 60 --hitcount 4 -j DROP

Can anyone tell why the above would interfere with SFTP file transfers?

Thanks.[/I][/COLOR]

---

### Post by Lars Noodén on 2014-02-14
SFTP is a different protocol from FTP.  It works over SSH so if the rules block SSH, they will block SFTP as well.  If you plan to use SFTP, you can [remove FTP](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely) and the two FTP servers.  SFTP is provided by the package openssh-server, and should work out of the box if you don't have firewall rules otherwise blocking it.

Shouldn't that first line include an ACCEPT target?  Otherwise, the only target is DROP.

```

iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent --set -j ACCEPT

``` 

Speaking of targets, at least while you are debugging your rules, you should use [reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject) so that you get your answer immediately instead of having to wait for a timeout.  Computers should be fast.

---

