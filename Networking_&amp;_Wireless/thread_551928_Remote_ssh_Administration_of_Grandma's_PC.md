---
title: "Remote ssh Administration of Grandma's PC?"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by jjalocha on 2007-09-15
I'm trying to set up my mother's PC (Ubuntu 6.06) so that I can do the administrative tasks with ssh. I've been reading a lot about it, and I'm getting more and more confused about the very first basic steps to get a connection going. To make things more difficult, we are living in different countries now, and I don't have physical access to her computer. So I have to ask her by phone to do the basic setup. (She has administrative privileges on her machine).

I do have an account on her machine, with administrative privileges.

I don't think she has a static IP, since that's not what you normally get from your provider (?). I've asked her to use give me the information from [http://static-or-dynamic-ip.com/](http://static-or-dynamic-ip.com/), but I don't know if this dynamic IP address is of any use.

On my side, I know for sure, that my IP address is not static. And I read somewhere that this causes problems, too...

She tells me that she is connected to the internet through an Arris 402g device. Googling, it seems to be a cable modem. I've read repeatedly that I had to "forward port 22". Should this be done inside this modem? (I've downloaded the manual, and I will try to do this, if necessary).

'ssh MyName@HerDynamicIp' complains about a refused connection on port 22.

I've read about setting up keys, both on her side and on my side. Is this absolutely necessary for a first connection? I would really love to just get the basics work, and then adjust the finer details.

Is there anything else to set up on her side so that I can get access?

Anyone knows a simple guide for noobs? Where should I start?

---

### Post by chimerical_brio on 2007-09-15
I don't think that you not having a static IP is a problem, and thought it would be nice for her to have one, I don't think that should be a problem either.

A rather...brutish way to figure out if your IP address is static or not is to vist [www.whatismyip.com](www.whatismyip.com) multiple times, and if it's the same, you have a static IP, and if it ever changes, you don't. She can do the same, and if hers isn't static, she'll have to do that every time you want to SSH into her computer.

As far as forwarding port 22, this is only necessary if she's behind a router. If her cable modem connects directly to her computer, you're fine; but if there's a router between her modem and her computer, you'll need to forward port 22. If not, there's no need to do so. You can find instructions on forwarding ports at [www.portforward.com](www.portforward.com).

The most likely reason that you can't SSH into her computer, though, is that she probably doesn't have an SSH server installed. If you have her open Synaptic, have her scroll to openssh, and install both openssh-client and openssh-server (the former just for good measure, though it might already be installed). You should be able to SSH in after that.

---

### Post by kebes on 2007-09-15
> **jjalocha said:**
> I'm trying to set up my mother's PC (Ubuntu 6.06) so that I can do the administrative tasks with ssh.
Good idea. Once you have SSH working, you can also add VNC to it, so that you can get a GUI from her machine, allowing you to do admin tasks via point-and-click if you prefer.

> I don't think she has a static IP, since that's not what you normally get from your provider (?).
It's probably dynamic. But that's no big deal... there are ways of dealing with that. But first you should get to a stage where you can login to her computer via ssh. To start, you'll need to know what her current IP address is, of course. (It seems like you've already done that.)


> On my side, I know for sure, that my IP address is not static. And I read somewhere that this causes problems, too...
That won't cause any problem. Having a dynamic IP on your end isn't a problem.


> I've read repeatedly that I had to "forward port 22". Should this be done inside this modem? (I've downloaded the manual, and I will try to do this, if necessary).

'ssh MyName@HerDynamicIp' complains about a refused connection on port 22.

SSH operates using port 22. So on her end you have to make sure port 22 is not being blocked. Since the connection is refused, this means that it's being blocked somewhere: 
1. It could be her ISP blocking (not usual, but it sometimes happens)
2. It could be her cable modem (some models have built-in firewalls)
3. It could be her router. If she's using a router between the modem and her PC(s), then it will definitely be blocking port 22. You need her to login to the router (usually done by navigating to a "special" webpage from within the local network, like 192.168.0.1 or whatever... it depends on the model) and enable "port forwarding" for port 22.
4. It could be Ubuntu itself. By default, port 22 is not blocked. But if someone has enabled strict firewall rules (e.g. installed "firestarter") then port 22 may be blocked.
5. the SSH server may not be installed on her computer. It has to be installed and running of course. You could also get her to go:
```

sudo /etc/init.d/ssh start

```
And see what happens. (It will either start it, or give an error like "command not found" in which case get her to install an SSH server.)


> I've read about setting up keys, both on her side and on my side. Is this absolutely necessary for a first connection? I would really love to just get the basics work, and then adjust the finer details.
Keys are not required. You can just always login with password. It's an "advanced topic" so don't worry about it for now.

Hope that helps. If you need clarification on any step, feel free to ask questions.

---

### Post by jjalocha on 2007-09-15
Thank you very much! All this reading made it look much more difficult. I will try as soon as I can find her on the phone. She'd used Synaptic earlier already, so this shouldn't be a problem.

---

### Post by jjalocha on 2007-09-15
Solved! I didn't realize that I had to install the server first :oops:

On my mother's side:
```

$ sudo aptitude update
$ sudo aptitude install openssh-server

```
Without needing any further setup.

And login from my computer was just trivial:
```

$ ssh MyNameRemote@HerDynamicIP

```

No p&#341;oblems at all.

Thank you very much!

---

### Post by kebes on 2007-09-15
> **jjalocha said:**
> Solved!
Excellent!

> 
$ ssh MyNameRemote@HerDynamicIP

Obviously you'll have to get her new IP each time it changes and you want to login. There is a way to avoid this, by the way. You can configure her computer to use a "domain redirect" and to automatically update it when the IP changes. If you want details on this, you can check out step 5 from this [how-to]("http://ubuntuforums.org/showthread.php?t=268985").

---

### Post by jjalocha on 2007-09-16
Thank you kebes! With your instructions, it was easy to set-up a domain redirect for my mother's computer:

Create an account on No-IP.com for my hosts/redirects:
[http://www.no-ip.com/newUser.php](http://www.no-ip.com/newUser.php)

After email confirmation and login, I did Add a Host/Redirect with the default settings (DNS Host A).

Since I don't have physical access to my mother's computer, I used 'wget' for downloading the noip2 software on her PC. (I'm using my "old" ssh connection with dynamic IP here.) Installation on an i686 was easy following your instructions:

```

$ wget http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz
$ tar -xvzf noip-duc-linux.tar.gz
$ cd noip-2.1.7
$ cp binaries/noip2-Linux-32bit noip2
$ sudo make install

```

After answering the questions with the same information I used at No-IP.com, I could run the application for first time:

```

$ sudo noip2

```

And to make sure the service gets started after each reboot, add the following line to the '/etc/rc.local' file before [FONT="System"]exit 0[/FONT]:

```

/usr/local/bin/noip2 &

```

After this, I could 'exit' from my "old" shh connection, and log-in using the new domain name.

Now, I will try to:
[LIST]
[*]disable ssh login for all user accounts on her PC but mine.
[*]set an ssh port other that 22.
[*]set-up 'iptables' on my mother's PC so that ssh is only allowed from my PC.
[*]set-up keys for both PCs.
[/LIST]

---

### Post by jjalocha on 2007-09-16
OK, I found out that I can set most of the ssh connection settings on the '/etc/ssh/sshd_config' file. In my case, I would change the following lines:

```

AllowUsers MyName   # I only want to allow myself.
Port 12345          # Set to some large number.

```

But in order to apply the changes, I have to restart the service. I would think, that this is done with:
```

$ /etc/init.d/sshd restart

```

But on my mother's system, there is no '/etc/init.d/sshd' script. So how can I apply the changes without restarting the computer?

---

### Post by kebes on 2007-09-16
Try:
```

sudo /etc/init.d/ssh reload

```
(I don't know why it's called "ssh" instead of "sshd", since the binary is actually called "sshd")

---

### Post by kebes on 2007-09-16
> [list]
[*]set-up keys for both PCs.
[/LIST]

By the way, this is the procedure I've used for key-pair creation, assuming you want to allow key-based login from usera@clientcomputer to userb@remotecomputer:
```

1. On client (clientcomputer):
$ cd ~/.ssh/
$ ssh-keygen -t rsa

2. Put key onto server (remotecomputer):
$ ssh userb@remotecomputer
$ mkdir /home/userb/.ssh/
$ chmod 700 /home/userb/.ssh/
$ cd /home/userb/.ssh/
$ exit

$ sftp userb@remotecomputer
sftp> cd .ssh
sftp> put id_rsa.pub
sftp> bye

3. Add key to server's trusted keys:
$ ssh userb@remotecomputer
$ cd /home/userb/.ssh/
$ cat id_rsa.pub >> authorized_keys2
$ ln -s authorized_keys2 authorized_keys
$ chmod 600 *
$ exit

```
There are many online guides that give further details about generating ssh key-pairs (e.g. [this one]("http://www.bscb.cornell.edu/computing/sshkey.php")).

---

### Post by jjalocha on 2007-09-16
Thanks again, kebes you were right, in this case, 'ssh' is needed:

```

$ sudo /etc/init.d/ssh reload
 * Reloading OpenBSD Secure Shell server's configuration               [ ok ] 

```

After logging-out, I was able to log-in again through the new port:

```

$ ssh -p 12345 userb@remotecomputer

```

Next, I will have a look at your keys setup.

---

### Post by magicjo83 on 2007-11-03
Hey everybody,

I finally convinced my mother to change from Windows to Linux when she buys a new Laptop. As I live not too close I told her I can take care of her Laptop and solve problems via remote ssh. 
Now, some guy told her, that her local ISP inhibits remote control. 
Can that be? And how do I access her Laptop if that is the case??

Thx a lot!

---

### Post by stroyan on 2007-11-04
It is possible for an ISP to block inbound connections to their client's computers.  It might be that they do that along with forbidding clients to provide services to outside computers.  That might be motivated by a shortage of upstream bandwidth.  Or at least some inbound connections could be blocked as a security feature.  Blocking port 139 for windows file sharing could help to keep many customers out of trouble.  But blocking all inbound connections would be very unfriendly.  I have seen reports that some ISPs do that.  They NAT all outbound connections.  The customer has no unique IP address.
If you are dealing with an ISP that blocks all inbound connections, then you might still get around the limitation by making the system connect outbound to a VPN.  That is just one more outbound connection that even a NATing ISP should let through.  You could do that with OpenVPN if you can set up a server somewhere that is always available at a fixed IP.  Or you could use hamachi, [http://hamachi.cc/](http://hamachi.cc/) .  Then LogMeIn provides the stable server that your system and the other system both rendevous at to set up a peer to peer VPN.

---

### Post by jjalocha on 2008-01-03
@magicjo83: An other alternative to the ones mentioned by stroyan is SSH tunnelling. By this, you set up a permanent "tunnel" through a firewall (or NAT) from your blocked host to a machine with a permanent IP. It's also referred to as "poor man's VPN", but should be quite simple to set up, and very effective. Try googling for that.

---

### Post by jjalocha on 2008-01-03
After many months, I finally could work on the remote-administration again, and I finally was able to set-up the key-pairs for SSH, thanks to kebes' help.


The key-pair is created for one user at the client host:
```

localhost$ ssh-keygen -t rsa

```
You can use the default options, and choose whether you want to use a passphrase or not. (This can be changed later if necessary with 'ssh-keygen -p'). This creates the following files (one key, with its public key):
```

~/.ssh/id_rsa
~/.ssh/id_rsa.pub

```


Copy the public key to the server using the "Secure Copy Program":
```

localhost$ scp ~/.ssh/id_rsa.pub RemoteHostIP:/home/username/id_rsa.pub

```


Now that the public key is on the remote host, log into the remote host:
```

localhost$ ssh remoteuser@RemoteHostIP

```

Add the key to the list of authorized keys:
```

remotehost$ cat ~/id_rsa.pub >> .ssh/authorized_keys
remotehost$ rm ~/id_rsa.pub

```
And remove the public key that is no longer used.


Now we can log into the remote host again, and we won't be asked for a password:
```

remotehost$ exit
localhost$ ssh remoteuser@RemoteHostIP

```


Alternatives
==========

Instead of adding the key to one user's personal '.ssh/authorized_keys' file, it is also possible to save it globally on '/etc/ssh/authorized_keys', although this might have some security implications.


It is also possible to restrict the use of keys with the from=""' comand in authorized_keys. You can read more about this in [this tutorial]("http://ezine.daemonnews.org/200411/openssh.html").

---

