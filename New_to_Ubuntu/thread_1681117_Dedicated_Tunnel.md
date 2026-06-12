---
title: "Dedicated Tunnel"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by darkenvy6 on 2011-02-03
Okay so I am a college student who is behind a very restrictive firewall. The firewall doesnt block website or anything (thank god) but when I first got here I had to fill out a complaint form to IT to open the ports required for synaptic package manager. 

Anyways I contantly need to SSH and VNC into my machine. Tunneling VNC through SSH isnt an issue but I cant even SSH locally on this network! That's locked down. So I do have a buzzbox back home that I a able to SSH into.

My idea: SSH into the buzzbox, the buzzbox has a dedicated tunnel between home and my computer behind the firewall. Then I would be able to SSH/VNC to my computer behind the firewall. This would be done through pushing the connection since you wouldnt be able to pull the connection through a firewall. The connection would need to be established by the computer to the buzzbox every time it boots.

Is this possible?

---

### Post by Sef on 2011-02-04
Moved to ABT.

---

### Post by HermanAB on 2011-02-04
Howdy,

Read up on the SSH Socks Proxy - the -D parameter.  Maybe start with this:
[http://www.aeronetworks.ca/howtos/skype-ssh-tunnel-howto.html](http://www.aeronetworks.ca/howtos/skype-ssh-tunnel-howto.html)

---

### Post by Synthetic Sam on 2011-02-04
> **HermanAB said:**
> Howdy,

Read up on the SSH Socks Proxy - the -D parameter.  Maybe start with this:
[http://www.aeronetworks.ca/howtos/skype-ssh-tunnel-howto.html](http://www.aeronetworks.ca/howtos/skype-ssh-tunnel-howto.html)
I'm not sure that D will work in this situation, he's talking about using the tunnel in reverse, leaving an open socket on the remote side, so it's more like

```
ssh -fNR 5002:localhost:5001 user@buzzbox
```

If you want this to run at boot time without interaction from yourself, then you'll need to set up public key authentication using a key with no passcode.

First, on the computer behind the firewall, run:

```
ssh-keygen
```

and leave the password blank when asked, this will give you two files, id_rsa (your private key) and id_rsa.pub (your public key).  Next copy the public key to the home folder of the user on the buzzbox that you log in with:

```
 scp ~/.ssh/id_rsa.pub user@buzzbox:/home/user/id_rsa.pub 
```

Then set that key as an authorized key:

```
 ssh user@buzzbox
cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
logout 
```

Now you should be able to login without a password.  If not, you'll need to edit /etc/ssh/sshd_config on the "buzzbox" and make sure you have the following lines:

```
 PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

```

In terms of running your ssh at boot time, you'll have to create an upstart job, I'm not familiar with that, so someone else will have to explain it, or I'll look it up later if no-one has replied.

---

### Post by Synthetic Sam on 2011-02-04
Ok, after a bit of reading, put a file with something like this in your /etc/init folder as custom_ssh_tunnel.conf and make it executable:

```
#SSH tunnel run as user.

description	"SSH tunnel"

#start when the network comes up
start on network

#stop on any runlevel except 2,3,4 or 5
stop on runlevel [!2345]

#restart if process stops unexpectedly
respawn

#if process restarts more than 10 times in 5 seconds, kill and do not restart
respawn limit 10 5

#run ssh command as user1 (instead of root, as id_rsa can only be read into ssh by the owner (user1) 
exec su -c 'ssh -fNR 5002:localhost:5001 -i /home/user1/.ssh/id_rsa user2@buzzbox' - user1
```

Where user1 is on the local machine, and user2 is on the buzzbox.

---

### Post by Synthetic Sam on 2011-02-04
Also, if this is successful you can check by logging into the remote machine and running ```
ps aux
```

This will list the running processes, there should be 4 for ssh, 2 for the session that you're logged in with running the command, and 2 for the tunnel set up by upstart.

for more info on the options that I suggested for ssh, look at the ssh manpages

---

### Post by darkenvy6 on 2011-02-04
> **Sef said:**
> Moved to ABT.
Really? I have posted several threads in different sections across this forum and you send this topic to ATB? Why sir, I am offended! :o

> you'll have to create an upstart job, I'm not familiar with that
Who is? I mean seriously... I tried looking for information to shed some light on it. I ahte when my runlevel jobs are covnerted to upstart. It makes doing something simple like restarding gdm a pain in my side.


Also guys I'm swamped at work so I'll try this after work. I'll keep you posted.

---

### Post by Synthetic Sam on 2011-02-04
> **darkenvy6 said:**
> It makes doing something simple like restarding gdm a pain in my side.


```
sudo service gdm restart
``` works for me

---

### Post by asmoore82 on 2011-02-04
> **darkenvy6 said:**
> ... I had to fill out a complaint form to IT to open the ports required for synaptic package manager.

This is where your story starts to fall apart.
Synaptic downloads packages over plain HTTP/FTP.

Something else is amiss on campus.

---

### Post by gmargo on 2011-02-04
> **asmoore82 said:**
> Synaptic downloads packages over plain HTTP/FTP.

Perhaps he requested that port 11371 be opened so the [keyserver]("http://keyserver.ubuntu.com:11371/") could be queried, and ppa repositories added.

---

### Post by asmoore82 on 2011-02-04
> **gmargo said:**
> Perhaps he requested that port 11371 be opened so the [keyserver]("http://keyserver.ubuntu.com:11371/") could be queried, and ppa repositories added.
11371 is well above the typical filtered range.
Web servers normally *listen* on port 80.
Web browsers do **not** *connect* from port 80 -
they connect from a randomized port in the higher range -
or else you wouldn't be able to run a browser and server on the same computer.

So, they shouldn't be blocking anything that high or
they risk creating havoc for innocent traffic.

Another possibility is that they could be using some intrusive packet analyzer
to filter by protocol, but even that link to the keyserver is still plain HTTP.

P.S. I was inspired to learn a little more -
It turns out that the higher range that I had heard of *is*
actually somewhat predictable: [http://en.wikipedia.org/wiki/Ephemeral_port](http://en.wikipedia.org/wiki/Ephemeral_port)

I got curious because I starting thinking about the
possibility of filtering based on destination port.

---

