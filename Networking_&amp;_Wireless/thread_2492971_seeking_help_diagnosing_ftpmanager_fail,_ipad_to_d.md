---
title: "seeking help diagnosing ftpmanager fail, ipad to desktop connection"
date: 2023-11-28
forum: Networking &amp; Wireless
---

### Post by paydaydaddy on 2023-11-28
I have used the app, ftpmanager, for a good while to move files from my desktop computer, Ubuntu 18.04.6 LTS, to my ipad. I just got a new ipad and would like to continue using ftpmanager. I loaded the app on the new ipad and duplicated the settings as near as possible, but so far I have been unable to establish a connection over lan. My results are: ping Host 8 ms, connect port Succeed, Local Network Permission Yes, Operation Timeout. My old ipad still connects flawlessly. Any suggestions?:( After thinking about it, maybe this belongs in general help.

---

### Post by TheFu on 2023-11-29
> **paydaydaddy said:**
> Any suggestions?:( 

I wasn't going to reply, but you wrote "Any suggestions?"   

a) plain FTP should have died in 2002. In 2023, nobody should be using plain ftp.  Use sftp instead.  There are great sftp clients for all networked platforms.  I don't use Apple's iOS (more of a Cisco IOS user), so I cannot list sftp clients.  However, it appears that FTPManager does support sftp, so it shouldn't be a big deal to use it.  On all Linux, if you install the ssh-server package (the exact name changes, sftp-server comes with it.  Or just install "**ssh**", that's a metapackage which includes ssh, scp, sftp, a few helpful utilities for clients and servers.  Wouldn't hurt to install "**fail2ban**" to protect against rogue hacking attempts.  By default, ssh/scp/sftp, are protected from brute force attacks.

b) If you want a non-secure method to transfer files like plain FTP (why?), then I'd just run a 1 line web server from the directory with the files. There are lots and lots of options. Then use the iOS web browser to save the files you want locally.
```
Python 3.x
  $ python3 -m http.server 8000

Twisted (Python)
  $ twistd -n web -p 8000 --path .

Ruby
   $ ruby -rwebrick -e'WEBrick::HTTPServer.new(:Port => 8000,
                        :DocumentRoot => Dir.pwd).start'
Ruby 1.9.2+
   $ ruby -run -ehttpd . -p8000

Perl
   $ cpan HTTP::Server::Brick   # install dependency
   $ perl -MHTTP::Server::Brick -e
           '$s=HTTP::Server::Brick->new(port=>8000);
            $s->mount("/"=>{path=>"."});
            $s->start'

http-server (Node.js)
   $ npm install -g http-server   # install dependency
   $ http-server -p 8000

node-static (Node.js)
   $ npm install -g node-static   # install dependency
   $ static -p 8000

PHP (>= 5.4)
   $ php -S 127.0.0.1:8000    # think using the LAN IP would be needed

busybox httpd
   $ busybox httpd -f -p 8000

```
Pick one. I use the python3 one all the time for read-only sharing. 

There are other methods too. I run a **nextcloud** server on the LAN and have nextcloud clients on my portable devices to make transfers and sync possible.  Installing and running nextcloud on Ubuntu is very easy through the snap package. It isn't as flexible as a manual install, but it is really flexible still.

I can understand why someone may not appreciate the difference between HTTP, sftp, and plain FTP from a security standpoint.  On Android, I use Ghost Commander to connect using sftp, when that is preferred.

With all ssh-based connections, like sftp, we can check the connection by raising the "verbosity"...   
```
$ ssh -vvv user@IP
```
If ssh can connect, then scp and sftp will connect too.  The only firewall port that needs opening, if you have the firewall enabled on Linux will be 22/tcp. All ssh, scp, sftp, and other ssh-based connections will use that same port and authentication.

---

### Post by paydaydaddy on 2023-11-29
Thank you for your reply. Looks like I have some studying to do to get up to date.

---

### Post by TheFu on 2023-11-29
> **paydaydaddy said:**
> Thank you for your reply. Looks like I have some studying to do to get up to date.

Study?

On linux, run this:
```
sudo apt install ssh fail2ban
```

If you have enabled the firewall, open port 22/tcp.  If you haven't specifically enabled the firewall, then nothing is required.  Front-ends to the firewall on Ubuntu are ufw, gufw, iptables. They all provide an interface to the kernel firewall. Just be consistent and use one, not the others.

That's it on the Linux side.

I'll leave the iOS stuff for you, but you'll need to use the Linux userid and either the DNS name or IP address to the Linux system for remote access.

That's it.  Your Linux password would be used for access.  You can setup ssh-keys from any client to the ssh/scp/sftp server and those can be used. It is suggested, but not mandated.  My only caution about this is that you should never use passwords over the internet. Humans are really, really, really, bad at picking passwords, so use ssh-keys only.  ssh-keys are trivial to setup between Unix/Linux and other Unix/Linux systems. On portable Android devices, they are more difficult to setup for some reason. Same on MS-Windows. I've setup ssh-keys from MacOS clients, but I've only used/seen Apple's iOS once in my life - perhaps 2009.  It was too difficult for my needs, but I send a MacOS system back after trying to make it work for 3 weeks.  The paradigm shift didn't add value to me. ;)  I was just frustrated.

---

### Post by paydaydaddy on 2023-11-30
The odd thing is that my old ipad still connects flawlessly. I have copied the settings to the new ipad and everything seems to work except that I get a timeout error. I don't think increasing time allowed will address the problem as plenty of time is allowed. The only difference I see is ip address of the ipads. I only use this to share files between my own devices on my own secure local area network. I have attempted to get support from the app developer but they are very slow to respond and so far have offered nothing of value. I have other ways to move files between the devices, but they are awkward by comparison.

---

