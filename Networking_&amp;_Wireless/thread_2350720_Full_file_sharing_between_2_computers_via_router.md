---
title: "Full file sharing between 2 computers via router"
date: 2017-01-27
forum: Networking &amp; Wireless
---

### Post by oygle on 2017-01-27
I have 2 Kubuntu (vers 16.04.1) computers that can access the internet via an ethernet cable connected to a router.

Have looked at various posts and docs in regards to this, but can't seem to find how to have SSH across these 2 computers, and then enable full file sharing. I'd prefer SSH, as I use beyond Compare a lot for file copying and comparing. It can connect via SSH. Failing that, just Samba or similar, so I can use Dolphin to navigate and copy.  :)

---

### Post by ian-weisser on 2017-01-27
Look at [sshfs]("https://help.ubuntu.com/community/SSHFS") or nfs for secure 'file sharing' (access to each file by one system at a time).

Or do you mean same-time access by both systems to the same file? (collaboration)

---

### Post by The Cog on 2017-01-27
If you can already coinnect with SSH, then probably the easiest way is to enter the URL into the address bar of dolphin.
I have been using thunar for this, but I'm pretty sure that dolphin would be the same.

The simplest form of the address would be something like **sftp://192.168.0.103** which will try to connect using your username. 
You can of course specify a different username, like this: **sftp://pi@192.168.0.103**
I use passwordless login, but I think it will prompt you for a password if one is needed.

---

### Post by Dennis N on 2017-01-27
**gigolo** - to manage connections btw. 2 or more computers at the same time. Has gui; remembers connection details. Access each computer in a file manager window.

---

### Post by TheFu on 2017-01-27
To make life easier, long-term, 

a) setup static IPs for all systems that run "servers" - like ssh, nfs, samba
b) setup name resolution for all systems that need to be contacted. This is either DNS, /etc/hosts entries, or a working avahi (hostname.local) setup.
c) On a secure LAN, NFS is by far the best solution for remote storage between Unix-like systems. That includes Linux, Ubuntu, OSX.
d) Over the internet or other untrusted network, secure file transfers are best left to scp, sftp, rsync (using ssh), and either encrypted NFS with Kerberos or sshfs.

All of the ssh-based methods work best with a and b configured. Also, passwords shouldn't be used with ssh-based stuff after the first 5 minutes on a new system. After that, ssh-keys should be used because they are 1) more secure, and 2) much more convenient. How often does being MORE secure actually make things MORE convenient?  I know of 1 instance - ssh, scp, sftp, rsync (which used with ssh).

All of these things do not require a GUI to setup or use.  ssh keys are automatically used after they are setup (use **ssh-copy-id** for that) for all ssh-based connections.  Much more convenient.  sshfs storage shows up in all the GUI file managers (and every other tool) like local storage.  However, sshfs is slow and doesn't always work as expected with every file system capability - like symbolic links and hard links. Just beware that some implementations are flakey with this stuff.  Besides being slow and those issues, pretty much everything else works as expected.  ```
mkdir ~/remote-stuff; sshfs me@remote-stuff:~/path/to/my/stuff ~/remote-stuff
``` simple.  Just replace the local and remote directory names to make sense for your needs and the remote userid@server for your needs.  Same credentials as ssh.

---

### Post by SeijiSensei on 2017-01-27
In Kubuntu, use URLs like **fish://server/share** in the Dolphin address bar.  That sets up an on-the-fly SSH connection to the other machine.  I use this all the time to move files to and from my remote servers hosted in the "cloud."

Of course, you need to install openssh-server on both machines to make this work.  If you use [shared keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys"), then you won't even need to authenticate when making the connections.

---

### Post by oygle on 2017-01-28
Thanks everyone for your detailed replies. My head was spinning with so much information.  :)

Desktop  192.168.1.102
Laptop    192.168.1.103

Trying to connect from Desktop to laptop. Both running Kubuntu 16.04.1

It is Beyond Compare that I use for copying/comparing, as it has a great interface for comparing files/folders.
[ATTACH=CONFIG]273420[/ATTACH]

But when I try that, BC gives me these error messages ..

> 
28/01/17 03:52:24 PM  Connecting to 192.168.1.103
28/01/17 03:52:24 PM  Connection failed: Connection lost (error code is 111)
28/01/17 03:52:24 PM  Unable to load sftp://192.168.1.103/: Connection lost (error code is 111)
28/01/17 03:52:24 PM  Load comparison:  <-> 


and if I try sftp://192.168.1.103 in Dolphin, I get a 'connection refused"

[ATTACH=CONFIG]273419[/ATTACH]

I did look at [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS) ; for some reason sshfs was already installed, but when I tried

```
sudo gpasswd -a $USER fuse
```

a msg

> gpasswd: group 'fuse' does not exist in /etc/group

and I notice that document is 5 years old. UFW on the laptop says the firewall is disabled. It's probably as simple as opening up port 22 on both computers to the other computers IP address ??

---

### Post by oygle on 2017-01-28
On the laptop, is this all I would need ?

```

sudo ufw allow proto tcp from 192.168.1.102 to any port 22

```

---

### Post by TheFu on 2017-01-28
If you didn't enable the firewall, then it isn't on.  **sudo ufw status** will show the status.
I doubt that beyondCompare can use sftp directly. You probably need to use sshfs or NFS to remotely mount storage. I've never heard of beyondcompare before. Always use diff, sdiff, or meld. No matter.

The fuse group doesn't seem to be part of 16.04, so don't get stuck on that. Make an empty directory and use **sshfs** modeled after what I've shown above to mount the remote storage where you want it.  If you need more options, take a look at the **man sshfs** page. I like to use the reconnect and compression options when I'm outside the LAN.

```
SSHFS(1)                         User Commands                        SSHFS(1)

NAME
       SSHFS - filesystem client based on ssh

SYNOPSIS
   mounting
       sshfs [user@]host:[dir] mountpoint [options]

   unmounting
       fusermount -u mountpoint
.... 
```

---

### Post by SeijiSensei on 2017-01-28
OK, lets start from scratch.  Did you install openssh-server on both machines?  If not run
```
sudo apt-get install openssh-server
```
It will automatically set itself up to run at boot.  You can confirm it is running with
```
ps ax | grep sshd | grep -v grep
```
You should get a result like
```
 1262 ?        Ss     0:00 /usr/sbin/sshd -D
```
though the number at the beginning (the id of the process) will be different.  

Now, try again using fish.  If you need to log in as a different user on the remote machine you can use "fish://user@192.168.1.103/" in the Dolphin address bar.  You'll be prompted for the password for "user."

---

### Post by oygle on 2017-01-28
> **SeijiSensei said:**
> OK, lets start from scratch.  Did you install openssh-server on both machines?  If not run
```
sudo apt-get install openssh-server
```


Installed that on the desktop and also on the laptop. Ran Dolphin on the desktop and used the fish protocol, it prompted for username/pwd, and it connected just fine. very slow to navigate folders/files though.

Then ran Beyond Compare on the desktop and used sftp://192.168.1.103 , it asked for username/pwd and connected okay. Navigation was very quick; was able to copy/delete a files on either computer.

It preserves time/datestamps and permissions, you can touch files, compare any sort of file. It will show where folders or files have differences. Here is a screenshot of the interface - [http://www.scootersoftware.com/features.php](http://www.scootersoftware.com/features.php)

Firewall - I didn't have to add port 22 to ufw. It's inactive anyway.  :)

Now, as the desktop is the computer where all data files are located and backed up from, I would consider that to be the local system. So, in the process of sharing/copying files, the desktop is the client and the laptop is the server. Therefore I can probably remove the package openssh-server from the desktop. The use of sharing/copying will always be done from 192.168.1.102 (desktop) and connect to 192.168.1.103 (laptop).

Note: Considering both computers have ufw disabled, can access be granted via port 22 now, to anyone attempting to gain access from outside the LAN ? (I realise they would need username and password though).

---

### Post by ian-weisser on 2017-01-28
> **oygle said:**
> Considering both computers have ufw disabled, can access be granted via port 22 now, to anyone attempting to gain access from outside the LAN ?

Yes. Wide open if they can get past your router. And some attacks can.
Dictionary attacks are fairly easy, and human-created test/initial-setup passwords are generally quick to crack.

Take 15 minutes and set up proper key-based authentication. Then disable password-based access.

Sometime next week, when you get pwned, you will wish you had.

---

### Post by oygle on 2017-01-28
> **ian-weisser said:**
> Yes. Wide open if they can get past your router. And some attacks can.
Dictionary attacks are fairly easy, and human-created test/initial-setup passwords are generally quick to crack.


Thanks for your reply. I doubt they would get past the router, and even if they did, would still need to crack the username and password.

> **ian-weisser said:**
> 
Take 15 minutes and set up proper key-based authentication. Then disable password-based access.


Thanks, I will ask in the security forum how to do that. :)

---

### Post by ian-weisser on 2017-01-28
> **oygle said:**
> I doubt they would get past the router, and even if they did, would still need to crack the username and password.
My first test server, with password protection and behind a firewall, was penetrated by a randomly-passing white-hat within 24 hours of going online. I learned the lesson cheap.
Unless your username is L"[_<Y7Gh;,M75Hbs&#'/ , and a similarly easy-to-remember password, their scripts *will* find it. Soon.
Lots of enormous botnets out there made up of tens of thousand of password-protected systems...behind firewalls...with users who still don't know they were compromised long ago.

> **oygle said:**
> I will ask in the security forum how to do that.
Start here: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
The Ubuntu Wiki is your friend. Stop by and say hello to it.

---

### Post by oygle on 2017-01-28
> **ian-weisser said:**
> The Ubuntu Wiki is your friend. Learn to use it: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Great thanks. I enabled the firewall on both computers, then of course Beyond Compare or Dolphin couldn't access 19.168.1.103 , so I added this rule ..

```

sudo ufw allow proto tcp from 192.168.1.102 to any port 22

```

then access was granted. Is that the correct rule to only allow access to port 22 from 192.168.1.102 ?  I don't know what the "to any" is ?

---

### Post by oygle on 2017-01-28
> **ian-weisser said:**
> My first test server, with password protection and behind a firewall, was penetrated by a randomly-passing white-hat within 24 hours of going online. I learned the lesson cheap.
Unless your username is L"[_<Y7Gh;,M75Hbs&#'/ , and a similarly easy-to-remember password, their scripts *will* find it. Soon.
Lots of enormous botnets out there made up of tens of thousand of password-protected systems...behind firewalls...with users who still don't know they were compromised long ago.


The only server I run is openssh-server, and that is all local, nothing outside the LAN.

---

### Post by ian-weisser on 2017-01-28
The firewall on each system is less important than the upstream firewall on your router, and less important than key-based authentication. Do those first.

Firewalls are a big deal for Windows because Windows runs services that can be compromised listen for connections...and the service cannot be turned off by the user. Other services call home without your permission. Firewalls are a way to control what goes in and out.

In Linux, you control all the applications and ports directly. If you don't want a certain listening or call-home service, you can uninstall it, or prevent it from binding to a port..
That's an oversimplification - internet-facing servers do need firewalls. But the rules and strategies are different from Windows firewalls for Windows services.

---

### Post by TheFu on 2017-01-29
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) explains the what and why for securing ssh/sftp/scp.

# For setting up ssh-keys, 
$ ssh-keygen

# For transfering and configuring the public keys on the other machines
$ ssh-copy-id

That's all there is to setting up ssh-keys from A to B.  BTW, I put ssh-server on every machine because you never know when the GUI will lock up and being able to get in from another machine would be handy to determine the root-cause.

You'll want to read the manpages for each of those tools. There are some interesting options and security related tips.

BTW, that ufw rule is only correct (enough) on 1 of the machines.  Most of the time, firewall rules are setup for a subnet, not an exact machine.

---

