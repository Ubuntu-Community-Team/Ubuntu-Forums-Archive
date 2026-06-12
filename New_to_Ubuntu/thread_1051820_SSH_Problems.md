---
title: "SSH Problems"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by BlakeM on 2009-01-27
I'm having difficulty using SSH. I've used it before but I'm obviously not doing something right this time. I want to create a shortcut to a folder on a local server on the client pc's desktop. I eventually want to be able to do this using a remote server but I want to get it working locally first. So here's what I've done:

I've installed the openssh server package on the server.

On a client PC on the same network as the server, I've gone to Places>Connect to Server. Here are the settings I've put into the fields:

Protocol: SSH
Server: I've put in the internal IP address of the local server I want to connect to. 
Port: I've put in port 22 in the port field 
Folder: I've put /home in the Folder field. 
Username: I'm using the same user name as the user on the local server.

The error I get is:

> "Can't display location "sftp://username@internalip/home. Time out when logging in"

I can think of a few things that might be going wrong:

1) Firewall. I've disabled both on the client and server until I can get this working...
2) Do I need to specify port on an internal network...?
3) Do I need to open the port on my router even though I'm trying to connect to a server on the same network... (I think this might be it).
3) Perhaps I need to specify a "keepalive" value?

Where am I going wrong here? TIA

---

### Post by Temposs on 2009-01-27
On the local server, do you have ssh daemon running? You need this running in order to connnect to it using ssh.

The command would be:

```
/usr/sbin/sshd
```

You can add this to your startup programs using the System->Preferences->Sessions

---

### Post by BlakeM on 2009-01-27
Thanks for your reply :).

Yes, I believe the SSH daemon is running. Out put of > ps -A shows "sshd" in the list.

---

### Post by BlakeM on 2009-01-27
I should add that I can ssh into the server using CLI. I.e. ssh <internalipaddress>. Can I use this in anyway to create a shortcut to a folder on the server?

---

### Post by Temposs on 2009-01-27
Can you open nautilus(file browser) and in the URL bar put something like:

```
sftp://username@internalip/home
```

Tell me if that works or not.

---

### Post by albinootje on 2009-01-27
> **BlakeM said:**
> 
On a client PC on the same network as the server, I've gone to Places>Connect to Server. Here are the settings I've put into the fields:


Nautilus uses sftp, does that work ? You can also try sshfs.

---

### Post by BlakeM on 2009-01-27
> **albinootje said:**
> Nautilus uses sftp, does that work ? You can also try sshfs.

Thanks for your reply :).

Hmm, I read about sshfs. What's the difference between sshfs, sftp and scp? From what I know, sshfs is more for entire file systems whereas scp and sftp are more for single files...is that correct?

---

### Post by BlakeM on 2009-01-27
> **Temposs said:**
> Can you open nautilus(file browser) and in the URL bar put something like:

```
sftp://username@internalip/home
```

Tell me if that works or not.

Done. No luck. Comes back with same error: Error: Timed out when logging in
Please select another viewer and try again.

I should also add that I can use sftp from the command line. I.e:

```
sudo sftp username@internalipaddress
```

Allows me sftp CLI access to the server. Perhaps it's a problem with nautilus...

...I'm also running denyhosts....completely forgot.

Just tried after disabling deny hosts...still no good. But even when I had denyhosts running I had no trouble using CLI to sftp into server...so lost at the moment.

---

### Post by BlakeM on 2009-01-28
Ok, totally don't understand what I did. But I've got it working. Here's how I fixed it for anyone else having the same issue:

On the server I checked the /var/log/auth.log file to check ssh login attempts. By the looks of it, every time I tried to ssh into the server I got the following error message:

> reverse mapping checking getaddrinfo for <ipaddress of client> failed - POSSIBLE BREAK-IN ATTEMPT!

Don't really understand what it means. The gist of it is that reverse mapping the ip address does not match the nameserver? Or something like that.

I fixed this problem by editing /etc/hosts file and adding an entry to the bottom of the file. Eg.

127.0.0.1 localhost
127.0.1.1 <nameserver>

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
<ipaddress of client> <nameserver>

Hopefully someone wiser than I can come and explain what went wrong for everyone.

Thanks to all those who took the time to read and post! :).

---

### Post by albinootje on 2009-01-28
> **BlakeM said:**
>  Hmm, I read about sshfs. What's the difference between sshfs, sftp and scp? From what I know, sshfs is more for entire file systems whereas scp and sftp are more for single files...is that correct?

Good that you have it working! :)

Sftp and scp are both commands provided by openssh client.
With sftp and scp you can copy files and directories.

Sshfs is for mounting a remote directory via ssh, to have it appear as a local directory (both in GUI and CLI).

Nautilus + sftp looks almost the same as you would use sshfs, but in my experience sshfs is really "seamless".

---

### Post by BlakeM on 2009-01-29
> **albinootje said:**
> Good that you have it working! :)

Sftp and scp are both commands provided by openssh client.
With sftp and scp you can copy files and directories.

Sshfs is for mounting a remote directory via ssh, to have it appear as a local directory (both in GUI and CLI).

Nautilus + sftp looks almost the same as you would use sshfs, but in my experience sshfs is really "seamless".

Yeah, that was the definition of SSHFS that I read but then I thought: "Isn't that the same as sftp with nautilus?" Bit confusing but I suppose it's not unusual to have two programs that overlap and do the same thing.

You've persuaded me to to have a go at SSHFS. I might leave it a while because I've just got sftp + nautilus working (and loving it!)

---

### Post by albinootje on 2009-01-29
> **BlakeM said:**
> Yeah, that was the definition of SSHFS that I read but then I thought: "Isn't that the same as sftp with nautilus?" Bit confusing but I suppose it's not unusual to have to programs that overlap and do the same thing.

Yes, indeed.
> 
You've persuaded me to to have a go at SSHFS. I might leave it a while because I've just got sftp + nautilus working (and loving it!)

Well, I'm not trying to promote sshfs to everyone out there, because sshfs has a few little quirks, and doesn't come with a GUI for mounting and unmounting.
But for me Nautilus+sftp doesn't work with OpenOffice for example, while sshfs does.
Also sshfs can be used on the CLI, which makes it useful for servers too.

---

### Post by BlakeM on 2009-01-29
> But for me Nautilus+sftp doesn't work with OpenOffice for example, while sshfs does.

Yeah, I had that same issue. It came as a bit of a surprise. I suppose copying it locally for editing is the preferred workaround? That was my idea anyway.

I'll also read a lot about SSHFS before trying it.

---

### Post by albinootje on 2009-01-29
> **BlakeM said:**
> Yeah, I had that same issue. It came as a bit of a surprise. I suppose copying it locally for editing is the preferred workaround? That was my idea anyway.

Yes.
I seem to remember that Konqueror with fish://username@ssh-server-ip/ has the same problem with OpenOffice.
But with sshfs it's no problem.
> 

I'll also read a lot about SSHFS before trying it.

Recommended reading :
[http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq](http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq)

---

### Post by BlakeM on 2009-01-30
> **albinootje said:**
> Recommended reading :
[http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq](http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq)

Hey, thanks for taking the time to read and reply. I'll read that link about SSHFS.

---

