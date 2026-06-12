---
title: "SSH problem"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by russell23 on 2007-07-16
Dear UBUNTU users,

I have just installed ubuntu-7.04 Fiesty on my intel x86_64 inmy desktop. The problem is I could able to connect any other machine from the UBUNTU box without any problem. But I could not able to transfer any file from other machines to  my UBUNTU and I could able to connect my machine from any other machine. I got connection to port 22 refused. I assume this is something to do with firewall I want to disable my firewall. COuld any one help  me to do that. Any hlep would be much appreciated.

---

### Post by Claus7 on 2007-07-16
Hello,

this link about the firewall should help you:

[http://ubuntuforums.org/showthread.php?t=472123](http://ubuntuforums.org/showthread.php?t=472123)

What you have to do in your case is to open the ports you want.

Regards!

---

### Post by jhofmann on 2007-07-16
I'm pretty sure I know what's wrong.

The ssh client is needed to login to another computer.  The client is installed by default.  So with the default installation, you should be able to connect to another, ssh-enabled computer.

In order to connect to a computer using ssh, however, that computer must be running the SSH server.  The SSH server is not installed by default.  Use

# aptitude install ssh

Note that you must be root to do this.  Once installed, you should be able to login from another machine.

Hope this helps.

Jim

---

### Post by williemerwe on 2007-07-16
I accomplished this with
# apt-get install ssh openssh-server
It works 100%, haven't had any problems with access.  Hope this helps

---

### Post by russell23 on 2007-07-17
THnaks for youe kind replies,

My problem is I could not able to run apt-get. I exported the proxy in my apt.conf file. Even then I am encountering problems. Once I give apt-get update, all the repositories were initially saying they are connecting 0%. After a while I am getting connection timed out and it starts trying the other mirror. I could not able to install anything due to this. 

So it would be nice if I could solve this without any further installation. Many thanks in advance.

---

### Post by Claus7 on 2007-07-17
Hello,

I was facing problems with synaptic while I was trying to configure my adsl ethernet connection.This link might help you:

[http://ubuntuforums.org/showthread.php?t=336073](http://ubuntuforums.org/showthread.php?t=336073)

Regards!

---

### Post by russell23 on 2007-07-17
Thank you claus,

But the thing is I am behind my institute's proxy. From other posts I found that I need to add proxy information in the apt.conf file. Since I am using ntlmaps I added the proxy information as for a ntlmaps running system.

proxy=http://proxy.iitm.ac.in:5865

What I am wondering is that in one of our lab machines yum is configured for CentOS-4.4 and it is working fine for updates. I even tried follow the things which has been mentioned in the thread for which you have given me the URL. after I added the "balcklist ipv6" in the /etc/modprobe.d/blacklist I am not getting anything if I type "lsmod | grep ipv6". I don't know how to solve this probelm and where it is going wrong? ANy help to solve this issue would be much appreciated.

NOTE: I tried the ways I found in the thread you have suggested me, even then I am getting the following connection timed out errors.

sanjib@sanjib-desktop:~$ sudo apt-get update
Password:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release.gpg                            
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6), connection timed out [IP: 91.189.89.6 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                     
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out [IP: 82.211.81.138 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Translation-en_IN                 
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (113 No route to host) [IP: 91.189.89.6 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_IN          
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out [IP: 82.211.81.138 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Translation-en_IN           `
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6), connection timed out [IP: 91.189.89.6 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_IN    
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out [IP: 82.211.81.138 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN             
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (113 No route to host) [IP: 91.189.89.6 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_IN      
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (113 No route to host) [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_IN    
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (113 No route to host) [IP: 82.211.81.138 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN           
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (113 No route to host) [IP: 91.189.89.6 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release.gpg
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6). - connect (113 No route to host) [IP: 91.189.89.6 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Translation-en_IN
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.6), connection timed out [IP: 91.189.89.6 80]
0% [Connecting to in.archive.ubuntu.com (91.189.89.8)]

---

### Post by Claus7 on 2007-07-19
Hello,

as far as the ipv6 is concerned is good that you have no output with the command : lsmod | grep ipv6 .  For me at least this was good so I don't think that you should worry.
Now about the proxy things that you mention I didn't have to do anything, so I do not know how you will be able to configure the files you mention. Also I do not know about the configurations of your institute and how these are related to the problem you are facing.
As far as the messages you got I think that it might be a DNS provider problem as in my case. Yet, I tell you this with some reservation. May be a change to the DNS provider might be the solution to your problem.

I hope I could help you more,
Regards!

---

