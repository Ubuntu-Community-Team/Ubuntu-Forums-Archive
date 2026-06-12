---
title: "nfs kicking my butt"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by rm06 on 2009-12-28
I've been trying to share some folders on my server (8.04 server) with the other computers on my small network so far without success. I've scoured the internet, followed every tutorial to the T and even own the 2009 edition of the "Linux Bible" on which I've followed all the given examples and still no joy.

I've configured the /etc/exports file, installed nfs-common, portmap and nfs-kernel-server, I've run dpkg-reconfigure portmap and chosen no to the loopback address. I've even individually shared out the specific folders on the server. I'm running Firestarter which I've disabled on both machines though I have configured the ports to allow for NFS.

I haven't yet configured the /etc/fstab on any clients yet as I cannot even mount the folder manually.

When I try: "mount 192.168.0.100:/etc/servername/Share /mnt/server" 
I get "mount.nfs: mount system call failed". I've created the /mnt/server directory already using the mkdir command.

I've failed trying to get this to work in too many ways to list here and I'm unsure of where to look to next.

---

### Post by falconindy on 2009-12-28
You should be mounting the root of the share, not the full path on the server. It would be helpful to see your /etc/exports.

I also notice you're sharing out of /etc? While it's not going to hurt anything, it's a little on the awkward side. You should keep your data mounted in a place like /mnt or /media and use 'mount -o bind' to "map" the shares to a place like /srv.

---

### Post by rm06 on 2009-12-28
I've changed the mount point to the /mnt and created a directory named Shared within it and reflected the change in the /etc/exports:

```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)

/mnt/Shared	192.168.0.0/24(rw,no_root_squash,async,no_subtree_check)

```

I then restarted the nfs service and tried again to connect with the same error as before. I did just notice that I have two events on my Firestarter gui from my client workstation on ports 53903 and 34851? I don't know if they're related or not.

---

### Post by louieb on 2009-12-28
Looks like your close: I use nfs to share folders on my desktop with my laptop. Had no problems after using this guide [HOWTO: NFS Server/Client - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs")

example /etc/exports on my desktop

```

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/media/utility  10.0.0.0/255.255.255.0(rw) 
/media/stuff    10.0.0.0/255.255.255.0(rw) 

```

and the script on my laptop to mount

```

#!/bin/bash
sudo mount whitebox:/media/stuff /media/wbstuff
sudo mount whitebox:/media/utility /media/wbutility

```

---

### Post by falconindy on 2009-12-28
What version of NFS are you trying to setup? I wasn't aware 8.04 was able to run nfs4 so I didn't ask.

Did you run exportfs after making the changes in /etc/exports?

edit: If you have the option to run nfs4, i highly recommend it. You have the ability to do the following:

```
/srv/nfs	192.168.2.0/24(ro,sync,fsid=0,no_subtree_check)
/srv/nfs/iso	192.168.2.0/24(ro,async,no_subtree_check,nohide)
/srv/nfs/video	192.168.2.0/24(ro,async,no_subtree_check,nohide)
/srv/nfs/music	192.168.2.0/24(ro,async,no_subtree_check,nohide)
```

And then mounting is as easy as:

```
mount -t nfs4 quake:/ /quake
```
Where 'quake' is the name of my server and the mount point. By having an nfs root declared, you're allowed access to iso, video, and music with a single mount. the 'fsid=0' declaration is the key.

---

### Post by rm06 on 2009-12-28
I don't know which version is supported in 8.04 though I still am apparently doing something wrong. I've changed the /etc/exports file to any number of simpler configurations still without success and always using exportfs and restarting services.

I've completely uninstalled Firestarter on both machines on the off chance it is blocking the traffic. 

I still cannot connect to the share - or any others I've created to test with.

---

### Post by falconindy on 2009-12-28
Silly question -- is the nfs module installed?

lsmod | grep nfs

---

### Post by Jose Catre-Vandis on 2009-12-28
Don't get confused by trying nfs4 just yet :)

Not sure if you are exporting your exports?

Suggest you completely drop your firewalls to start off with, and do as louieb suggests and follow the [tut]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs")

FWIW

**_On server_**
Install **portmap, nfs-common, nfs-kernel-server**.
Create mount point, e.g. **/media/share**
Put something in it to share
Create /etc/exports file with a line like this:
**/media/share 192.168.1.0/24(rw,no_root_squash,async)**
Restart server: **sudo /etc/init.d/nfs-kernel-server restart**
Export your exports: **sudo exportfs -a**
Maybe restart server again: **sudo /etc/init.d/nfs-kernel-server restart**
[B][U]
On client[/U][/B]
Install **portmap, nfs-common**
You may need to do a couple of restarts on the client:
[B]sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart[/B]
Create a mount point e.g. **/media/my-nfs-share**
Mount it! **sudo mount 192.168.1.100:/media/share /media/my-nfs-share**

Once you are up and running, get to work on security if needs be.

---

### Post by Cuco3 on 2009-12-28
I remember firestarter giving me problems when I installed it. Like I would have it disabled, but it would still block packets.

I switched to the Ubuntu recommended method for graphically configuring the built in firewall --- gufw (can be installed through repositories).

Anyways, I remember I even got so mad with firestarter that I reinstalled Ubuntu all together. Luckily I was still figuring out what the problem with my Suspend was, so it didn't hurt to try a reinstall at that time.

Good luck.

---

### Post by rm06 on 2009-12-29
@ falconindy - here's the output of the grep command on the server:

```
nfsd                  228720  13 
auth_rpcgss            43424  1 nfsd
exportfs                6016  1 nfsd
nfs                   262156  0 
lockd                  67720  3 nfsd,nfs
nfs_acl                 4608  2 nfsd,nfs
sunrpc                185500  11 nfsd,auth_rpcgss,nfs,lockd,nfs_acl
```

and on my workstation:

```
nfs                   271912  0 
lockd                  67724  1 nfs
nfs_acl                 2844  1 nfs
auth_rpcgss            36576  1 nfs
sunrpc                191712  4 nfs,lockd,nfs_acl,auth_rpcgss
```

@ Jose Catre-Vandis - I followed your instructions to a "T" with the same error message as previous: "mount.nfs: mount system call failed" One caveat, however, I was not able to stop or restart the nfs-common and received the following when attempting to do so: "bash: /etc/init.d/nfs-common: No such file or directory". I verified it is installed and rebooted my workstation which should effectively accomplish the same thing, right?

@ Cuco3 - I uninstalled Firstarter via command line and marked for complete removal through Synaptic on both machines.

---

### Post by Jose Catre-Vandis on 2009-12-29
Please check and confirm the IP address of your server, this should be the same as the one in your mount command. (Sorry in my example I used 192.168.1.100 instead of 192.168.0.100) Am now assuming your server is 192.168.0.100.

Try mounting this way:

sudo mount -t nfs 192.168.0.100:/media/share /media/my-nfs-share

or

sudo mount -t nfs -o nolock 192.168.0.100:/media/share /media/my-nfs-share

Try

# /etc/init.d/portmap status
# /etc/init.d/nfs-common status

to check these are up and running on your client

Try mounting the share on the server (you'll need to create a separate mount point on the server) If that works then we know the issue is beyond the server and lies with the network or the client.

Try rebooting both machines (and sometimes a cold boot, i.e. switching the buggers off for at least ten seconds) can help to resolve configuration changes - don't ask me why :)

Are you running either machine as root, as opposed to a normal user? I try to keep things simple by running both client and server with the same username and UID. That said the nfs server should be up regardless of whether you are logged in or not.

Check your hosts.allow/deny for multiple instances of statd and make sure you have nothing in there that can cause a problem

What Ubuntus versions are you running? are they uptodate? There was a bug in Hardy and Jaunty that caused problems.

---

### Post by rm06 on 2009-12-29
I'll check all of the suggestions and report back - I am sure about the IP of the server, however:)

I was planning on upgrading the server box at some point as it has been beat on and experimented on six ways from Sunday and it could stand some freshening up anyway. I'll still see if I can get it to work as learning point before proceeding with an upgrade.

---

### Post by rm06 on 2009-12-29
Okay, I've installed and configured my new server and I apparently am making the same mistakes or the problem is on my workstation and not the server. I don't know how to create another mount point or if it is a simple enough operation for me to undertake at this point.

whenever I do a "mount -t" I get this:

```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

@Jose Catre-Vandis - what do you get when you try "/etc/init.d/portmap status" or "/etc/init.d/nfs-common status"? When I do the portmap status I receive an error stating it is an upstart job and to use the "status( 8 ) utility" - if I try "service portmap status" it tells me it is running. If on the other hand I try as you suggested the /etc/init.d/nfs-common status (or start or restart) I receive "bash: /etc/init.d/nfs-common: No such file or directory" I can see it is installed via synaptic.

I've tried running as root and using sudo, both with identical results. Both machines are now running 9.10 and are updated daily (or whenever updates are applicable and available).

The hosts.allow/deny are both stock standard and are completely commented out.

I hope that helps? Glad to provide anything else anyone can think of - hopefully it is something minor and stupid which I've simply missed.

---

### Post by falconindy on 2009-12-29
the -t option of mount requires an argument to specify the mount type -- in this case it would be '-t nfs'.

---

### Post by rm06 on 2009-12-29
> **falconindy said:**
> the -t option of mount requires an argument to specify the mount type -- in this case it would be '-t nfs'.

Got it, that part makes sense now.

---

### Post by Jose Catre-Vandis on 2009-12-30
```
:~$ /etc/init.d/portmap status
 * portmap is running
:~$ /etc/init.d/nfs-common status
all daemons running
:~$ service nfs-common status
all daemons running
:~$ service portmap status
 * portmap is running
```

Is what you should be seeing. If you are not getting the all clear for both, something ain't right.

Did you try mounting your share actually on the server?

---

### Post by rm06 on 2009-12-30
Here's what I get:

```
:~# /etc/init.d/portmap status
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service portmap status

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the status(8) utility, e.g. status portmap
portmap start/running, process 1115
:~# service portmap status
portmap start/running, process 1115
:~# /etc/init.d/nfs-common status
bash: /etc/init.d/nfs-common: No such file or directory
:~# service nfs-common status
nfs-common: unrecognized service
```

I am also trying this on my laptop which is running 9.04 and the services respond as yours do.

I am seeing this in the /var/log/messages after the mount fails: "Dec 29 21:47:56 MyWorkstation kernel: [  390.320284] rpcbind: server 192.168.0.100 not responding, timed out"

---

### Post by Jose Catre-Vandis on 2009-12-30
Hmmmm

Getting the same results as you with nfs-common on Karmic, but mounts are working fine both from command line and through fstab. How frustrating in not being able to pin this down for you. It's guru time !

---

### Post by rm06 on 2009-12-30
Jose Catre-Vandis and everyone else who replied - thanks for your persistence. Pardon my ignorance, what/who is "it's guru time"?

---

### Post by Jose Catre-Vandis on 2009-12-30
Hoping it might prompt someone who understands the inner workings of nfs to come up with a solution :)

---

### Post by rm06 on 2009-12-30
Well, I think it is working now. 

It just so happens that I fried a hard disk after my upgrade yesterday and after replacing it and reinstalling Karmic server and configuring my exports file and installing nfs services, it seems to be functioning. At least I am able to mount the share using "mount -t nfs 192.168.0.100:/mnt/Share /mnt/server" and it shows as mounted when I run "mount".

I didn't do anything different this time around either, so I don't know what the original problem is/was.

The reason I say I *think* it is working, is that after all that gnashing of teeth, I am embarrassed to say I'm unsure how to go about exactly using it. I cannot find any graphical representation of the mounted share in anyplace I'd expect to find one, nor do I know if one is even supposed to show up. I guess all the tutorials I've read presume that one will know how to use it once it's been set up.

That said, my master plan is to have most of my music files, pictures and important files and backups residing on various shares which I would theoretically connect seamlessly to from any workstation.

---

### Post by falconindy on 2009-12-30
Well, grats I suppose.

The share is now accessible at /mnt/server. It'll behave like any other mounted drive -- an extension of the base filesystem. It can be treated exactly the same, even though the underlying workings of it are certainly different. You can browse to it with a graphical filesystem browser like Nautilus, Thunar, or Dolphin, or just 'cd /mnt/server'

---

### Post by rm06 on 2009-12-30
Hey - *cool* - :)

Appreciate all the help, thanks again!

---

### Post by Jose Catre-Vandis on 2009-12-31
Great news. Now you need to put it in your fstab so it mounts on boot.

---

### Post by rm06 on 2009-12-31
I've configured my fstab with a couple of more shares that I created and it all seems to work very well.

Thanks again to all.

---

