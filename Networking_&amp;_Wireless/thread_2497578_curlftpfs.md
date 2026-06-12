---
title: "curlftpfs"
date: 2024-05-10
forum: Networking &amp; Wireless
---

### Post by demonenero84 on 2024-05-10
Hi there:o
I set up a ftp server, I can access it without problems using dolphin, all I need to do is specify protocol, ip address and port ([ftp://192.168.178.37:4663](ftp://192.168.178.37:4663))
I try to mount with curlftpfs with this command:
```
curlftpfs 192.168.178.37 /home/user/test/ -o ftp_port=4663
```
and I get
```
Error connecting to ftp: Failed to connect to 192.168.178.37 port 21 after 5 ms: Connection refused
```
Obviously my syntax is wrong since it tries to use the standard port 21 instead of 4663, I tried to put "-o ftp_port=4663" before my ip address and got the same error message
any suggestions?
thanks a lot in advance

---

### Post by TheFu on 2024-05-10
Nobody should be using plain FTP since 2002.  Use a better protocol.

Heck, use **sshfs** instead.  Combined with ssh-keys, it is seamless, assuming you won't use NFS.

```
mkdir ~/mount-point
sshfs     username@192.168.178.37:~username/      ~/mount-point

```
Now you can use any file manager to access  ~/mount-point/  and use it like it is local storage.  This is secure enough to use over the internet, if you must, though network performance and latency will be felt.  

Of course, there is a dependency on ssh-server, but that would be installed on any Linux/Unix system anyway.

Stop using plain FTP.  [https://www.howtogeek.com/886945/ftp-is-dangerous-heres-why-you-should-use-sftp-instead/](https://www.howtogeek.com/886945/ftp-is-dangerous-heres-why-you-should-use-sftp-instead/)   There are many, many, more articles which explain why plain FTP should be killed everywhere.

---

### Post by demonenero84 on 2024-05-10
> **TheFu said:**
> Nobody should be using plain FTP since 2002.  Use a better protocol.

Heck, use **sshfs** instead.  Combined with ssh-keys, it is seamless, assuming you won't use NFS.

You are absolutely right, setting up an ssh server is easy, fast and secure (I copy my keys and then disable password access), after that all you have to do is mount the remote file system with sshfs. Samba share is also quite easy to set up and very useful for android devices or VMs with old operating systems (like windows xp)
My question was a personal curiosity, I am running a few tests on my lan so it is not really a problem.

Just an off topic question. Is it safe to access my ftp server outside my lan if I use a vpn installed on my modem/router (wireguard) ?
thanks a lot for the reply

---

### Post by currentshaft on 2024-05-10
3>4

---

### Post by TheFu on 2024-05-10
> **demonenero84 said:**
> You are absolutely right, setting up an ssh server is easy, fast and secure (I copy my keys and then disable password access), after that all you have to do is mount the remote file system with sshfs. Samba share is also quite easy to set up and very useful for android devices or VMs with old operating systems (like windows xp)
My question was a personal curiosity, I am running a few tests on my lan so it is not really a problem.

Plain FTP can be fast, but with any CPU made the last 15 yrs, sftp, sshfs, NFS, are very fast.  The only time I use Samba is for MS-Windows.  Ghost Commander on Android supports sftp or there are tools like nextcloud, wormhole, rsync to move files to-from android.
For testing network performance, I start with iperf3, then move to scp, NFS, sshfs, and if I really want the fastest, then I'll use **netcat**.  It is also possible to run a 1-line web server using almost any scripting language if you want to provide short-term access to all the files below a directory level. Some examples.

```
Python 3.x
  $ python3 -m http.server 8000 

Ruby 1.9.2+
   $ ruby -run -ehttpd . -p8000

PHP (>= 5.4)
   $ php -S 127.0.0.1:8000

busybox httpd
   $ busybox httpd -f -p 8000

```
I tend to use the python one, even though I'm a perl guy.  But 
```
   $ plackup -MPlack::App::Directory -e
               'Plack::App::Directory->new(root=>".");' -p 8000

```
just doesn't feel as easy.  I already use plack for those stuff, so it is already installed on my perl dev systems.

> **demonenero84 said:**
> 
Just an off topic question. Is it safe to access my ftp server outside my lan if I use a vpn installed on my modem/router (wireguard) ?
thanks a lot for the reply

If you are using wireguard, then almost any protocol is fine, thought plain FTP wouldn't be the way I did it.  I'd just use sftp:// URLs and come in over ssh outside the wireguard tunnel, if I were on a Linux laptop.  Pretty much all Linux file managers support sftp:// URLs (or some weird replacement that does the same thing using sftp).

In short, getting out of the plain FTP mindset will simplify your life and keep you from accidentally doing something with poor security.

---

### Post by demonenero84 on 2024-05-10
> **currentshaft said:**
> That being said, what are you trying to do? Just access your  files from other hosts? There are much simpler, more elegant solutions  than FTP.
I was looking for a practical way to share files between my linux desktop and android devices. Right now I installed a samba server on my pc and I use an app on my phone that acts as a samba client, it works quite well, I am able to upload files from android to linux and access files shared folders from android. Since the android app that I use (File manager plus) can act as an FTP server I was curious to learn a bit about FTP and curlftpfs. It would be nice to have a quick and easy way to mount my android filesystem on my desktop, KDE connect can do that but it seams to slow down transfer speed.

thanks for the reply

> **TheFu said:**
> 
```
Python 3.x
  $ python3 -m http.server 8000 

Ruby 1.9.2+
   $ ruby -run -ehttpd . -p8000

PHP (>= 5.4)
   $ php -S 127.0.0.1:8000

busybox httpd
   $ busybox httpd -f -p 8000

```
I tend to use the python one, even though I'm a perl guy.  But 

Thanks I am a python guy myself
> **TheFu said:**
> In short, getting out of the plain FTP mindset  will simplify your life and keep you from accidentally doing something  with poor security.
I see, I like to play with old windows VMs, FTP works fine with Windows 98, qemu-nbd is a rather cumbersome way to move files around, any suggestions for VMs with old operating systems?
thanks a lot for the reply

---

### Post by Morbius1 on 2024-05-10
I don't want to get in the middle of a religious debate about ftp but just so you know there is no curlftpfs in Ubuntu 24.04 or any other disto derived from Debian 12. Too buggy apparently.

---

### Post by TheFu on 2024-05-10
> **demonenero84 said:**
>  
I see, I like to play with old windows VMs, FTP works fine with Windows 98, qemu-nbd is a rather cumbersome way to move files around, any suggestions for VMs with old operating systems?
thanks a lot for the reply

Any standard network protocol works inside VMs, assuming you choose normal, bridged, networking.  If you choose host-only or NAT, then the guest can access outbound, but not the opposite.  That's a "feature" in those other choices, right?

If you want bi-directional connections, then you'll need to run a server of some sort on both sides and use bridged networking. Probably want to use a firewall to limit access to unsupported OSes. They really shouldn't be setup to allow inbound connections of any type.

Win98 was a the worst OS I've ever had. MS-DOS v5 was better, even with the limitations. I had a Win98 system that would boot and even if I didn't touch it, within 2 hrs it would BSOD on it's own.  Win95 was stable (not really), in comparison.  Win95 was stable when compared to Win3.11.  Win98 was a huge step backwards.  Of course, during those years, I was an OS/2 Warp user on my desktop and ran Linux on my home server.  OS/2 never crashed. Uptime was measured in months, not hours.  

NT4 was almost as stable.  It did some funky things to my NT4 workstation and it would stay up for 3+ weeks, which was about the time I needed to reboot for some new library.  I was doing C/C++ cross-platform development in that decade, so we had 1 of every OS in our lab for porting software.

Sometimes I do get religious about plain FTP. There are just so many better protocols to be used that are much more firewall friendly and don't put credentials in the open.

---

### Post by demonenero84 on 2024-05-11
> **Morbius1 said:**
> I don't want to get in the middle of a  religious debate about ftp but just so you know there is no curlftpfs in  Ubuntu 24.04 or any other disto derived from Debian 12. Too buggy  apparently.

Ok thanks, I am still on 22.04, I will update soon

> **TheFu said:**
> Any standard network protocol works inside VMs, assuming you choose normal, bridged, networking.  If you choose host-only or NAT, then the guest can access outbound, but not the opposite.  That's a "feature" in those other choices, right?

If you want bi-directional connections, then you'll need to run a server of some sort on both sides and use bridged networking. Probably want to use a firewall to limit access to unsupported OSes. They really shouldn't be setup to allow inbound connections of any type.

Thanks a lot

---

### Post by Morbius1 on 2024-05-11
> **demonenero84 said:**
> Ok thanks, I am still on 22.04, I will update soon

When you do move to 24.04 and Dolphin still posses an issue you will be forced to use something else ... like filezilla for example.

---

### Post by morovan on 2024-06-26
> Nobody should be using plain FTP since 2002.  Use a better protocol.
Agreed. However curlftps supports SSL with option -o ssl.

> there is no curlftpfs in Ubuntu 24.04 or any other disto derived from Debian 12. Too buggy apparently.
It is possible to download deb file from [http://archive.ubuntu.com/ubuntu/pool/universe/c/curlftpfs/](http://archive.ubuntu.com/ubuntu/pool/universe/c/curlftpfs/) and install manually

And now to the original question, to set curlftps to connect to specific port syntax is as follows:
> curlftpfs 192.168.178.37:4663 /home/user/test/

Option ftp_port is used only in active move and tells server what port on client's side to connect to.

---

### Post by currentshaft on 2024-06-26
> **demonenero84 said:**
> I was looking for a practical way to share files between my linux desktop and android devices. Right now I installed a samba server on my pc and I use an app on my phone that acts as a samba client, it works quite well, I am able to upload files from android to linux and access files shared folders from android. Since the android app that I use (File manager plus) can act as an FTP server I was curious to learn a bit about FTP and curlftpfs. It would be nice to have a quick and easy way to mount my android filesystem on my desktop, KDE connect can do that but it seams to slow down transfer speed.

Run a webserver on your router (apache, nginx, lighttpd, hell ask AI to write you one in golang) which serves a simple page with a POST form and enable directory listing. Now everyone on your network can upload and download files over a flexible, modern and potentially secure protocol.

---

### Post by TheFu on 2024-06-26
I'd never suggest that a router be used for anything except routing and simple firewall stuff.  WAN routers are our first line of defense and running complex code on them just provides more chances for buggy code to sit in a place that nasty people can access.

I'd never put a WAN router inside a VM either.  WAN routers need to be on real hardware that when it fails, it failed broken and closed.
Of course, if you want a more complex router inside your network, using a VM-based router can be a nice compromise over more hardware.

This same sort of recommendation goes for using a router as a storage device.  There have been so many bugs in that code that I'd never trust it.  Best case seems to be that all the connected storage is made available to the world.  Almost every router vendor that had a storage capability in their routers had at least 1 if not 2 or 3 failures.  Just because the router software claims to be able to do X, Y, Z and A, B, C, that doesn't make it a good idea.

---

### Post by currentshaft on 2024-06-26
> **TheFu said:**
> I'd never suggest that a router be used for anything except routing and simple firewall stuff.  WAN routers are our first line of defense and running complex code on them just provides more chances for buggy code to sit in a place that nasty people can access.

I'd never put a WAN router inside a VM either.  WAN routers need to be on real hardware that when it fails, it failed broken and closed.
Of course, if you want a more complex router inside your network, using a VM-based router can be a nice compromise over more hardware.

This same sort of recommendation goes for using a router as a storage device.  There have been so many bugs in that code that I'd never trust it.  Best case seems to be that all the connected storage is made available to the world.  Almost every router vendor that had a storage capability in their routers had at least 1 if not 2 or 3 failures.  Just because the router software claims to be able to do X, Y, Z and A, B, C, that doesn't make it a good idea.

I've got some bad news for you: almost every commercial router available at the store already runs a web server, usually it's 10-15 years out of date and full of bugs.

I should have been more clear, when I said "router" I meant a Linux/BSD host forwarding packets and providing dhcp/dns/etc and not the former COTS.

---

### Post by TheFu on 2024-06-27
> **currentshaft said:**
> I've got some bad news for you: almost every commercial router available at the store already runs a web server, usually it's 10-15 years out of date and full of bugs.

Which is why adding more stuff to them is foolish.

For most people, the best they can do is to expect to spend $100 every 3-5 yrs on a newer home router.  For networking nerds, they can step off the router HW upgrade treadmill and use systems that are supported by constantly maintained router projects which do get patched every few weeks.  

I'm not sure that commercial routers are any better, regardless of cost. Same for specific commercial firewall products. Both equipment types have had some massive attack vectors that impact companies of all sizes.  Don't forget about misconfiguration or using trivial credentials, which still happens.  

At security conferences some of the presenters show how to take advantage of misconfigured router settings, misconfigured firewall rules, and bonehead credentials.  These were in fairly large corporations - with LIVE demonstrations.  If you are a security professional, you know what I'm talking about.

If hacking Linux systems were so trivial, why isn't every linux system on the internet pwn'd today?

---

### Post by currentshaft on 2024-06-27
> **TheFu said:**
> If hacking Linux systems were so trivial, why isn't every linux system on the internet pwn'd today?

Two reasons: most hosts are behind NAT and almost all attackers are not very skilled, nor very smart.

Given a dichotomy of using FTP or trusting the router already trusted to send and receive all packets, I going to choose the latter for sharing files on my local network.

---

### Post by demonenero84 on 2024-09-29
Thanks a lot, I marked this thread as solved

---

