---
title: "Networking with Nautilus"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by gurt on 2009-07-03
I have 2 ubuntu desktops. They are connected to eachother on a dedicated ethernet network. I want to be able to transfer files by dragging and dropping. Can Nautilus do this... (I suspect yes). How?
I see there is vsftpd -- is that the best choice in this situation (private file transfers between devices over dedicated network) or something else?

Ta!

---

### Post by ukripper on 2009-07-03
> **gurt said:**
> I have 2 ubuntu desktops. They are connected to eachother on a dedicated ethernet network. I want to be able to transfer files by dragging and dropping. Can Nautilus do this... (I suspect yes). How?
I see there is vsftpd -- is that the best choice in this situation (private file transfers between devices over dedicated network) or something else?

Ta!
Note: VSFTP is ftp client.

There are many ways you can do that - If it is linux only network then you may use NFS or Samba. if it is mixed network Windows/Ubuntu you have to use Samba. 

Here is some info for NFS - [http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

and for SAMBA - [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by gurt on 2009-07-03
I can't find anything about the Nautilus (drag and drop) part for either NFS or Samba. Samba seems to be primarily for Windows support. But I have 2 Ubuntu desktops. And from what I can gather NFS isn;t supported in Nautilus. Am I missing something?

---

### Post by frunns on 2009-07-03
NFS mounts a remote share in a folder on your computer, and you can navigate that folder just as you would with any other with Nautilus.

Edit: A howto here on the forums [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
Slightly old, but should still be useful.

---

### Post by nothingspecial on 2009-07-03
[COLOR="Red"]Oooops, just read your post again and realised you weren`t connected through a router
[/COLOR]
I`ll leave the post up just incase its usefull to someone else

On both machines ```
sudo apt-get install openssh-client
```

Then in your menu go  places > connect to server.

In the top box change Public FTP to ssh

In the box titled server type

```
username@other.computers.ip.address
```

You can find your ip address by right clicking on the network manager icon and selecting connection information.

Tick add bookmark

Choose a name for your other computer and click connect.

There will now be a entry for your other computer in the places menu for ever more.

Repeat the process on the other one and you can drag and drop all day ;)

It might be an idea to fix the ip addresses in your routers config page[SIZE="3"][/SIZE]

---

### Post by gurt on 2009-07-03
> **frunns said:**
> NFS mounts a remote share in a folder on your computer, and you can navigate that folder just as you would with any other with Nautilus.

Edit: A howto here on the forums [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
Slightly old, but should still be useful.

I think this is way over my head but I'm giving it a try.
Here's what I've done so far....
1. On the server **nfs-kernel-server nfs-common portmap***.* 
I already have the latest.
2. On the server **gksu gedit exports**....
**/home/gurt 8.8.8.0/24(rw,no_root_squash,async)**
I figure I'd just share my home dir. Although this doesn't seem to work as we'll see later.
3. On the client **sudo apt-get install portmap nfs-common**
It seems I already have it.
4. On the client (I assume?) **gksudo gedit /etc/fstab**
**mingus:/home/gurt /home/gurt nfs rsize=8192,wsize=8192,timeo=14,intr**

And now what? How do I access the mount via Nautilus?

---

### Post by frunns on 2009-07-03
I'm not the best on mounts in fstab, but that looks like you mount your remote /home/gurt on your local /home/gurt... Not sure what happens then (conflicts and stuff), I'd mount it in an empty folder, like /home/gurt/serverhome but either you reboot or just run
```
sudo mount -a
```
Should do the trick.

---

### Post by gurt on 2009-07-03
> **frunns said:**
> I'm not the best on mounts in fstab, but that looks like you mount your remote /home/gurt on your local /home/gurt... Not sure what happens then (conflicts and stuff)

You aren't kidding frunns! Everything when grey and I had visions of recovering my crashed desktop. Ugh! 

> **frunns said:**
> I'd mount it in an empty folder, like /home/gurt/serverhome but either you reboot or just run
```
sudo mount -a
```Should do the trick.

I'll give that try. But then once it's mounted how does the client access the mount using Nautilus? nfs://<host_name>? I have no idea.

---

### Post by frunns on 2009-07-03
You just navigate to the folder you've mounted it on. Let's say you use my example with /home/gurt/homeserver, then you just open up Nautilus, which defaults to /home/gurt, then you should have a folder named homeserver where your share is mounted, which just works just like a regular folder. Note that you have to create the folder you mount the share on before mounting it.

---

### Post by gurt on 2009-07-03
I'm obviously doing something wrong. I guess I'm confused about what needs to be done on the server and what needs to be done on the client.

[I've changed some stuff to avoid confusion]

So on the _SERVER_ I do this.....
1. **gksu gedit /etc/exports**
add the dir I want to export and specify the client...
**/opt/Share 8.8.8.0/24(rw,root_squash)**

2. Save and restart NFS...
**sudo /etc/init.d/nfs-kernel-server restart**

3. Export whats in the export file...
[B]sudo exportfs -a


[/B]On the _CLIENT_ I do this....
4. Clear some stuff
[B]sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart

[/B]5.Mount[B]
sudo mount 8.8.8.9:/opt/Share /mingus_Share

[/B]Note: mingus is the server (8.8.8.9)
the client is dali 8.8.8.[B]8

6. [/B]I should see /mingus_Share on dali 8.8.8.8? That can't be right because I don't see it....

---

### Post by frunns on 2009-07-03
No error message? If not I'd think it should work...

---

### Post by gurt on 2009-07-03
First of all I want to say Thank You for helping me on this!

Here's why I think it's not working. Right now the client is shutdown.

On the server [8.8.8.9] we have....
```
gurt@mingus:~$ showmount
Hosts on mingus:
8.8.8.9
```
Isn't that saying that I'm mounting myself (so to speak)?
Shouldn't the output only show something when the client is up?

My exports file seems OK...
```
gurt@mingus:~$ showmount -e
Export list for mingus:
/opt/Share 8.8.8.0/24
```

Is there other output that would be useful?

---

### Post by gurt on 2009-07-03
Oh and here's the error I get on the client...

```
gurt@dali:~$ sudo mount 8.8.8.9:/opt/Share /mingus_Share
mount.nfs: mount point /mingus_Share does not exist
```

---

### Post by gurt on 2009-07-03
AH! It's working!!

```
gurt@dali:~$ mkdir mingus_Share
gurt@dali:~$ sudo mount 8.8.8.9:/opt/Share /mingus_Share
mount.nfs: mount point /mingus_Share does not exist
gurt@dali:~$ pwd
/home/gurt
gurt@dali:~$ sudo mount 8.8.8.9:/opt/Share /home/gurt/mingus_Share
```


Man oh man! frunns, Thanks for help again

---

### Post by gurt on 2009-07-03
Dang! Seems that the client can't save data in the mount though. I tried gksu gedit...

```
Could not save the file /home/gurt/mingus_Share/test
```

So what do I need to do as far as permissions to allow the client to write to the share?
I thought I gave 8.8.8.0/24 rights to rw?

---

### Post by gurt on 2009-07-03
added no_root_squash in the exports file....
works!

---

### Post by frunns on 2009-07-03
Well done! :)

---

