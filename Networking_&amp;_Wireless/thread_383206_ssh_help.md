---
title: "ssh help"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by fjr0122 on 2007-03-13
I had a [previous thread]("http://ubuntuforums.org/showthread.php?t=378486") about ssh and other methods of big file transfer. 

I have essentially the same problem but with a bigger scope.

Here's my situation, I want my friends or myself to be able to login to my machine through SSH, so that it is as if the far away computers are on my home network (and can share files and such).  I operate through a dsl modem and a router/firewall/switch (from netgear). 

I've recently read several articles on this but none cover my situation exactly, each time they are focused on SSH'ing into a server on the internet and then into the target box. Where as I want to serve the SSH myself....

The problems I have are 
1-what's the ip/address/port I should give my friend 
2-how can I test if a port has actually opened on my router (a problem I've had before)
3-how do I open/link the ports in linux 
4-is there anything I should do to setup SSH
5-What does the command look like if I want to connect to the network of the computer that is serving the SSH (my friends box-->his router--->internet-->my router-->my box (SSH server and target network))....
6-how do I configure and ftp or file sharing setup to allow my friend to read/write
7-What's the proper terminology for what I'm trying to say?
8-What to tell my windows using friend to make this work
9-When I type in SSH in the terminal, does it run here or there? And does there have to be an SHH program on the client computer to make this work? (say for example, if someone was a windows user...
My networking knowledge is honestly still rudimentary. 

Btw, my target friend needs to be able to simply launch filezilla (in windows) and use the info I give him to connect right up.

---

### Post by Mr. C. on 2007-03-13
With all due respect, this is far too much to ask at once.  You need to do the bulk of the work and research; others will pitch in and help when you are stuck.  But we can't do it for you.

Here's a nut shell of what you will get via SSH.

* Your friends will get a secure connection to your system.
* Your friends can all tunnels via SSH to various services your system provides.
* For those ports that are forwarded, services will appear as if they come from the server machine itself (from the services point of view).

If you want your friends to appear on your net, you need to setup a VPN connection.  The extends your network to your remote friends, and they will appear as if they are on your network.  This is far more complex to setup on both ends.

Do you have your SSH server setup and configured yet ?  If not, set it up, and get some experience using it and becoming familiar with the terms and how it works.

MrC

---

### Post by dmizer on 2007-03-13
first of all, you will have to configure your netgear router to forward port 22 do your ubuntu machine.  port 22 is the communications port for ssh.  you should be able to refer to your routers documentation for that, as it's not a complicated setup.

then, you should set up your router to bind an ip to your ubuntu machine's mac address so that every time you reboot, you don't pick up a different ip.  (again, this is relatively easy to accomplish if you take a look at your router documentation).

next, you should register yourself for a free dynamic domain here: [http://www.dyndns.com/](http://www.dyndns.com/) (there are others as well, but this is the most common.  but with a dyndns domain, your friends can ssh into a url (for example: fjr0122.dyndns.com) instead of having to remember your ip address.

once you install openssh-server (sudo aptitude install openssh-server) your ssh server will be online and accepting connections as long as your computer is turned on.

your friends (if they have windows) will be able to use putty: [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/) to get a command line connection to your ubuntu machine.  this will be a gui interface, so no "command" to type in.  just fill in the appropriate blanks and off you go.  but they WILL have command line access to your entire machine.  and if they are knowledgeable, or if they just make a few mistakes ... they could wax your entire setup.

that all said, you're probablly better off using something intended for transferring files across the internet, rather than ssh.  ssh is more powerful than you really need if you just want to swap music.  it's also a huge security risk because port 22 is a well known port, and worms are constantly looking for it.  i suggest taking a close look at seting up an ftp server instead (third link in my sig).  as mr. c. says, it's probably better to create a vpn tunnel for your friends connection ... but it is complicated and i've yet to accomplish this.

---

### Post by alamba on 2007-03-13
This is how I have it set up at home since I travel a fair bit:
1. Dynamic IP mapped to a dyndns.org account
2. SSH setup incase I need to do any remote admin
3. Firewall to block everything else except SSH and a port for OpenVPN
4. In order to be on the "same network" at home when I want to access some network resources (storage, printer & a win box for the folks), I also have OpenVPN setup on the same box.

dmizer's advice is good, however, I'd suggest using SCP instead of FTP. If you have ssh installed you all ready have SCP. Google for WinSCP for a client for windows. 

A

---

### Post by DoorGunner on 2007-03-13
Hi Fjr0122

When it comes to hackers they look for pre-existing ports to go too. I moved my ssh ports to another  location to make it more difficult. When i first set it up I was hacked from some guy from Korea. in one of the urls below there is a awk code so you can check if this has happened.

As far as your router is concerned you should be able to change a port and direct it to the spacific ip of your personal computer. You will find this in your port forwarding section of the netgear router.

You will also need to change your sshd.conf to reflect that port change. Also you will need to register the change in /etc/services. IE change ssh  tcp/22 and ssh upd/22 into tcp/3333 and upd/333 if that port is available in the list.

It would also not be a bad idea to set up a certificate so that your passwords etc dont float around the internet unencrypted.

I found some good sites here.
[https://help.ubuntu.com/community/GPGsigningforSSHHowTo](https://help.ubuntu.com/community/GPGsigningforSSHHowTo)
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[http://ubuntuforums.org/showthread.php?t=30709&highlight=ssh+RSA+key+user+password](http://ubuntuforums.org/showthread.php?t=30709&highlight=ssh+RSA+key+user+password)

Once you make the certificate you can copy it to your friends machine and no one should be able to hack in.

---

### Post by fjr0122 on 2007-03-13
I should have said at the start of this thread that I have all these questions and I'm sure I'm not the first one to wonder about them. I would like to tap the knowledge of those on this forum on how to do this not just so I will know but so every person who wonders in the future can find this thread and know exactly how to setup SSH. 

Here's some of the pages I've been to so far....I've read some and skimmed most, none of them start at step one, knowing my ip address and getting my computer to connect past my router (which is as I said something I've had trouble with (maybe its my router)), or setting up dyndns.

[http://www.rzg.mpg.de/networking/tunnelling.html](http://www.rzg.mpg.de/networking/tunnelling.html)

[http://www.cyberciti.biz/tips/howot-install-ubuntu-linux-ssh-server.htm](http://www.cyberciti.biz/tips/howot-install-ubuntu-linux-ssh-server.htm) <--useful info on changing the ssh port

[http://www.linuxjournal.com/article/4413](http://www.linuxjournal.com/article/4413) <-- mostly about advanced key issues but also includes "TCP Port-Forwarding with SSH: VPN for the Masses!'

[http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/](http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/) <--A few basic FAQ about ssh (not including any of my questions)

[http://www-128.ibm.com/developerworks/aix/library/au-satopenssh.html?ca=dgr-lnxw16OpenSSh](http://www-128.ibm.com/developerworks/aix/library/au-satopenssh.html?ca=dgr-lnxw16OpenSSh) <--Excellent IBM article that will be useful once I have things working

[http://www.ssh.com/support/documentation/online/ssh/winhelp/32/Tunneling_Explained.html](http://www.ssh.com/support/documentation/online/ssh/winhelp/32/Tunneling_Explained.html)

[http://www.ssh.com/support/documentation/online/ssh/winhelp/32/Forwarding_FTP.html](http://www.ssh.com/support/documentation/online/ssh/winhelp/32/Forwarding_FTP.html)

[http://www.ssh.com/support/documentation/online/ssh/winhelp/32/file_transfer-3.html](http://www.ssh.com/support/documentation/online/ssh/winhelp/32/file_transfer-3.html)

[http://www.ssh.com/support/documentation/online/ssh/winhelp/32/command_line_options.html](http://www.ssh.com/support/documentation/online/ssh/winhelp/32/command_line_options.html) <--these four dont apply to OpenSSH but do have generic info about how SSH works 

[http://www.unixwiz.net/techtips/putty-openssh.html](http://www.unixwiz.net/techtips/putty-openssh.html) <--one of the best... an explanation of everything in putty (windows client)

[http://www.oreillynet.com/pub/a/wireless/2001/02/23/wep.html](http://www.oreillynet.com/pub/a/wireless/2001/02/23/wep.html) <--this one is really great too, about tunnelling in both linux and windows...

[http://www.openssh.org/faq.html](http://www.openssh.org/faq.html) <--the Openssh faq 

[http://www.openssh.com/windows.html](http://www.openssh.com/windows.html)  <--windows SSH clients

[http://www.openssh.com/](http://www.openssh.com/) <--official OpenSSH site 

[http://www.openssh.com/manual.html](http://www.openssh.com/manual.html) <--OpenSSH manual, in depth info 

[http://www.debianadmin.com/manage-ssh-tunnels-with-gnome-ssh-tunnel-manager.html](http://www.debianadmin.com/manage-ssh-tunnels-with-gnome-ssh-tunnel-manager.html) <--this would be my preferred way to setup (i installed this already)

[http://www.vdomck.org/blog/2005/11/21/reversing-an-ssh-connection/](http://www.vdomck.org/blog/2005/11/21/reversing-an-ssh-connection/) <--I don't understand this article...

[http://gstm.sourceforge.net/](http://gstm.sourceforge.net/) <--Gnome SSH Tunnel Manager

[http://kimmo.suominen.com/docs/ssh/](http://kimmo.suominen.com/docs/ssh/) <--A good article covering SSH 

[http://www.linuxjournal.com/article/6602](http://www.linuxjournal.com/article/6602) <--Eleven SSH tricks 

[http://linuxhelp.blogspot.com/2005/11/secure-linuxunix-access-with-putty-and.html](http://linuxhelp.blogspot.com/2005/11/secure-linuxunix-access-with-putty-and.html) <--Another good article 

[http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html](http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html) <--Excellent No-ip setup article...

Doorgunner your link led me to  [https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN) , that's a good start :)

[http://www.revsys.com/writings/quicktips/ssh-tunnel.html](http://www.revsys.com/writings/quicktips/ssh-tunnel.html) <--Simple

[http://www.ccs.neu.edu/howto/howto-sshtunnel.html](http://www.ccs.neu.edu/howto/howto-sshtunnel.html) <--Good Explanation

Well, that's certainly enough links...

So to really it break down, every page I find assumes you are the client and not the server. And if it does talk about the server it assumes that you know how to  set up the server and the network to work with SSH. :P

---

### Post by Mr. C. on 2007-03-13
fjr0122,

I'm sure everyone here would enjoy helping you configure your server.  But it has to be taken one step at a time.  This is like drinking from a fire hose.

How about one step at a time.

What do you have setup now, and what _one_ problem or question can we help resolve for you?

MrC

---

### Post by dmizer on 2007-03-13
> **fjr0122 said:**
> So to really it break down, every page I find assumes you are the client and not the server. And if it does talk about the server it assumes that you know how to  set up the server and the network to work with SSH. :P

because configuring the server is easy.
```
sudo aptitude install openssh-server
```
your server can now accept ssh connections.

that's it.  nothing else to do.  you're done.

configuring your local network is a simple matter of configuring your router correctly to forward the ssh port to your ubuntu server.  as i said before, your BEST bet for getting this accomplished is to crack open that router manual.  there's really no other way to go about it.  none of the documentation can talk about this in detail because every router manufacture and even different models within one brand all do this differently.

---

### Post by fjr0122 on 2007-03-13
> How about one step at a time.

What do you have setup now, and what one problem or question can we help resolve for you?

I have openSSH installed, I have setup the port on my router. 

I dont think the port is open on my box (aka, server) nor do I know if that is necessary.

My router doesnt change the IP(lan) it connects me with (unless I unplug and plug into a different jack). And my internet ip rarely changes (daily ..maybe) 

How can I test if the port is open? (locally and to the net)... 
Is there some way for my machine to know what my internet ip is? (aside from whatismyip.com)

My friend is probably gonna try and help me experiment with this tommorow night (he's gonna try to connect to me). He will be using windows.

Before this we tried to do Filezilla server in windows and my friend (different friend) couldnt connect.

We will also need to be able to get through my friends' networks (apparently not a big deal).

Anyways, Sorry if that link list is overwhelming...there is alot of info out there, just, seemingly not what I'm looking for.

---

### Post by dmizer on 2007-03-14
to test ssh ...
```
ssh localhost
```

this will allow you to test ssh on your local machine.

AGAIN i REALLY think you need to look at something OTHER than ssh here.  you will really be hanging your tail out on the net with an ssh connection.

ftp or sftp is what you really need.  ssh is _way_ beyond a file sharing application.  it is 100% full command line access to your ubuntu computer.  whoever gains access to your machine via ssh will be able to do ANYTHING ... including, but not limited to:

changing and deleting critical system files
viewing and browsing to other computers on your network.
hyjacking your computer and making it a part of a bot network.
dropping automatic executables in your shared folders to execute when a windows machine accesses it.
preventing you from logging into your own computer.

---

### Post by fjr0122 on 2007-03-14
dmizer, I am familiar with the procedures for my router, I've used them several times.  I need a way to test the open port on my router. There have been times (like my recent unsuccessful attempts with hamachi and ftp) where I opened the ports, but then the connections still didnt work. 

Your warnings of the risk of this activity are noted.  But beg the question, how does everyone else keep those nasty things from happening? How would I know if they did? I thought SSH was used so those things wouldnt happen...

I tried the ssh localhost...it gave me...
->ssh localhost
ssh: connect to host localhost port 22: Connection refused
->$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server...                             [ ok ] 
->ssh localhost
ssh: connect to host localhost port 22: Connection refused

---

### Post by Mr. C. on 2007-03-14
This indicates your ssh daemon is not running, or the packet was refused by a firewall.  Do not believe the OK in the startup script.  Evaluate the messages in /var/log/auth.log .  The ssh program attempted to open a connection to port 22, and the connection was immediately refused.

What does it say regarding the sshd server ?

MrC

---

### Post by fjr0122 on 2007-03-14
> Mar 14 00:49:15 username sudo: username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/etc/init.d/ssh restart
Mar 14 00:49:15 username sshd[4694]: Received signal 15; terminating.
Mar 14 00:49:16 username sshd[7737]: Server listening on :: port 512.
Mar 14 00:49:56 username sudo: username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/usr/bin/ssh localhost
Mar 14 00:51:15 username sudo: username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/usr/bin/ssh localhost
Mar 14 00:51:18 username sudo: username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/etc/init.d/ssh restart
Mar 14 00:51:18 username sshd[7737]: Received signal 15; terminating.
Mar 14 00:51:18 username sshd[7812]: Server listening on :: port 512.
Mar 14 00:51:54 username sudo: username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/usr/bin/ssh localhost:512
Mar 14 00:52:10 username sudo: username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/usr/bin/ssh 512:localhost
Mar 14 00:53:18 username sudo: username : TTY=unknown ; PWD=/home/username ; USER=root ; COMMAND=/usr/sbin/firestarter
Mar 14 01:08:20 username sudo: username : TTY=pts/0 ; PWD=/home/username ; USER=root ; COMMAND=/usr/bin/gedit /var/log/auth.log

(my username is not username)
I think I changed the port to 512....
> 
username@username:~$ sudo ssh localhost -p512
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 9e:e2:e4:13:c9:c1:69:d9:ad:45:c3:32:f7:4e:30:35.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
root@localhost's password: 
Permission denied, please try again.
root@localhost's password: 
Permission denied, please try again.
root@localhost's password: 
Permission denied (publickey,password).
 
Yep I changed it. :P

---

### Post by Mr. C. on 2007-03-14
You're wastin' some peoples time here...

So, where are we.  Are you good now?

MrC

---

### Post by dmizer on 2007-03-14
ssh is a tool used for remote system administration and is usually implemented in tandem with a secure vpn network or vpn tunnel.  that, or it is reserved for use from within a secure local network.  this is how the big boys keep their tails from getting nailed.  keeping in mind of course that they're working with equipment that makes your puny retail router's firewall look like a piece of trace paper.  and ... lest we forget ... they STILL get nailed.

ask yourself how much access you want exposed to the internet.  the answer to that SHOULD be ... as absolutely little as possible.  so, if you want to share files ... pick a server app that's designed to share files only.

you're having authentication problems because you'll need to log in with an actual account on your ubuntu machine.

from your error messages, it appears that you're trying to test this from a root prompt.  you shouldn't be trying to test ssh from the root account because unless you've enabled the root user, there will be no authentication for your ssh server to authenticate against.

try something like:
```
ssh username@localhost -p 512
```
where "username" is an actual valid account on your ubuntu server.

you should end up with something like this:
```
dmizer@tokkyu:~$ ssh localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
[COLOR="Red"]dmizer@localhost's password:[/COLOR]
Linux tokkyu 2.6.15-28-686 #1 SMP PREEMPT Thu Feb 1 16:14:07 UTC 2007 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Wed Mar 14 17:36:19 2007
dmizer@tokkyu:~$
```

---

### Post by fjr0122 on 2007-03-14
> ssh is a tool used for remote system administration and is usually implemented in tandem with a secure vpn network or vpn tunnel.

See this is what I dont understand, I thought SSH was on the outside and the VPN was run from within SSH. Such as this [https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

Serving files isnt my only interest, we play games as well. Some games wont allow us to play over the internet, but when it looks like they are local that problem goes away. We used to use hamachi but it is a. hard to install in linux b. doesnt seem to work lately. 


> So, where are we. Are you good now?


No, my friend and I are gonna test it tonight (he's gonna connect from his house). I would like to be able to test if the router is forwarding the ports like its supposed to without having to resort to someone else having to connect to me. I'm expecting problems with it. 

Sorry if I wasted anyone's time, my problem was never with installing SSH it was making it work beyond "localhost".

I do appreciate the help I've received so far.

---

### Post by Mr. C. on 2007-03-14
fjr0122,

You are correct.  There are two commonly used mechanisms today for creating a secure connection to a remote host over the internet: VPN or SSH.  There is little advantage to SSH over the VPN other than an extra layer of encryption.  Configured appropriately, either offers the best security known today.

dmizer's point about constant attack is valid.  Once a port is open on the firewall, attacks come in by the hundreds or thousands daily.  For a properly configured server, these are nothing more than annoyances; but pay attention to them.

The point about opening the smallest holes possible is right on target.  Every opening creates an opportunity for attack.

You will find that your gaming experience over SSH is suboptimal, simply because every packet must be encrypted, and this is both CPU intensive, and latency causing.  Try it to find out, and disable compression in sshd if this is a primary issue.

You can configure SSH so that your friends can make the connection, but their access is restricted or limited.  There's more risk involved with allowing your friends a login connection, so beware.

First, get your remote ssh connections working.  Step 2 is configuring a tunnel.  

MrC

---

### Post by fjr0122 on 2007-03-15
Thanks Mr. C.,
The answer to this or that in *nix and the internet is usually, Both!

My work extended into tonight so me and my friend didnt get to test (i think he forgot :P)....

---

