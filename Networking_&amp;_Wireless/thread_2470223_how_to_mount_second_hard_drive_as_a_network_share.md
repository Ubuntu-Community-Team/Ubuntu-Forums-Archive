---
title: "how to mount second hard drive as a network share"
date: 2021-12-22
forum: Networking &amp; Wireless
---

### Post by mike430 on 2021-12-22
Happy Holidays! and please bring joy to my Linux world!

Cannot for the life of me get a network share mount working. 

Have a desktop/server that has the following hard drives.
sda - windows 10
sdb - Ubuntu 20.04
sdc - 2 Tb drive

Nothing special per the sda - windows/sdb - ubuntu install, use grub for os selection at boot. The sdc drive currently has 2 partitions, one of which is sdc1 ~500gb that runs a pxe server. I have this mounted at /var/www/html/pxe_srv which serves a couple different versions of Linux and it works even for UEFI believe it or not. Sdc2 ~700gb is an ext4 formatted partition that contains no data and the remaining space is unformatted. 

I mount the sdc2 700gb partition successfully through the fstab file or conversely, I do it manually through the mount command on my server. Per my fstab entry I have uuid=partitionUUID /mnt ext4 defaults 0 0.

What I am attempting to do is mount this 700gb partition as a network share on a laptop running the same version of Ubuntu with same sudo user and password. My entry in fstab per this laptop to access the share is //192.168.1.120/mnt /mnt cifs defaults 0 0. 

When I do this, depending on what options in my fstab entry I am using on the client laptop I get either a permissions issue error 13 or Bad_Network error 2. 

I have thrown everything at this, testing different options in my fstab entry. I have changed directory ownership to the main sudo user, me, with 777 permissions on both the server and laptop to no avail and have also tried keeping these as root ownership as well for testing. I have cifs installed on both machines as well as Samba. In addition, I do run samba for network access to sdb drive which works fine and have configured my samba config for this access.

Any help or pointers in getting this working would be greatly appreciated. 

Thank you my fellow Linux users, -Mike

---

### Post by TheFu on 2021-12-22
First, Unix systems prefer to use NFS, not CIFS. There are many reasons, but mainly for performance and full support of Unix permissions.  We can have both CIFS and NFS shares from Linux - the NFS would be for other Unix-like OSes and CIFS would be only for Windows.

NFS is server-to-server, not user-to-server like CIFS.  Normal Unix permissions are used for NFS storage controls, not user authentication from the client to the server. End-users shouldn't need to know anything about non-local storage. It should behave the same as local storage, IMHO.

On the system with the partition/file system you want to share, please run
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
and post those results - we only need to see the line for the specific file system. It is about the file system used.  Both CIFS and NFS need a native Linux file system to work best.  Not NTFS nor exFAT. Something native.

On the system with the actual partition, you'll need to setup either the NFS-server or the Samba Server.  NFS is much easier to setup, so I would encourage that first. [https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs) has instructions for 20.04, but they should work for any supported Ubuntu. NFS hasn't changed much and they succeed to keep backwards compatibility over the last 15-25 yrs.  The NFS-client instructions are in there too.

On the system that will mount the remote storage, you'll need to setup either the NFS-client or the Samba-Client.  Again, NFS is much easier.

BTW, you probably don't want to actually mount any storage directly to the /mnt directory.  It would be best to either create a sub-directory under /mnt/ or under /media/ and mount the storage there instead.  There are too many reason to list them all.

The fstab line for NFS - after the nfs-server /etc/exports is configured (by you, manually), looks like this:
```
istar:/d/D1     /d/D1    nfs  nconnect=2,proto=tcp,rw,async  0 0
```
istar is the hostname of the nfs-server. That can be an IP address, if you prefer.  Another example:
```
istar:/media/TV     /media/TV    nfs  nconnect=2,proto=tcp,rw,async  0 0
```

Don't use DHCP for either CIFS or NFS servers.  Ensure those have static IPs on your LAN.

You'll note that I keep the storage location the same on the server as on the clients. This is for my sanity.  My mount location does cause some issues with snap packages, but I'm stubborn about following standards and don't care about snaps which do not follow standards.

I'd post a CIFS mount, but I don't use CIFS between Unix systems.  I have 1 CIFS mount from an old Windows box and the required options to get it working fill 2 lines. It is very ugly and not nearly so flexible. It also requires per-userid credentials - because that's the way the CIFS protocol works. Yuck.  

If you get stuck, please post the server-side and client-side config files. Less description, more ASCII text from the files. Please.

---

### Post by Morbius1 on 2021-12-23
[1] I wish you hadn't mounted this partition at /mnt ( both as the partition on the server and as the cifs mount point ). That's a system directory. Mounting it *under* /mnt like /mnt/data would be more appropriate.

[2] What is missing is how the samba server is set up and how the share is configured. Providing the output of this command would tell us that:
```
testparm -s
```

[3] This will not work on the client:
> //192.168.1.120/mnt /mnt cifs defaults 0 0

*** The client has to tell the server who is calling and this goes back to item [2].

If the share is allowing guest access specify that in the mount directive:
```
//192.168.1.120/mnt /mnt cifs defaults,guest 0 0
```
If the share requires credentials pass those credentials - For example:
```
//192.168.1.120/mnt /mnt cifs defaults,username=morbius,password=morbiuspw 0 0
```

*** In both cases above the share will mount on the client with owner = root with r/w access and read access to everyone else.

*** If you want it to mount with the client user as owner you need to specify that as well:

For example for a share that requires credentials and mounted with the user morbius as owner it would look something like this:
```
//192.168.1.120/mnt /mnt cifs defaults,username=morbius,password=morbiuspw,uid=morbius 0 0
```

---

### Post by mike430 on 2021-12-24
Hello Morbius. 

testparm -s on my server

```
testparm -sLoad smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed
Server role: ROLE_STANDALONE


# Global parameters
[global]
    bind interfaces only = Yes
    interfaces = lo enp3s0
    server min protocol = NT1
    server role = standalone server
    server string = xmas_samba
    idmap config * : backend = tdb




[movies]
    force create mode = 0754
    force directory mode = 0754
    path = /home/santa/Videos
    valid users = santa
    write list = santa


[music.study]
    force create mode = 0754
    force directory mode = 0754
    force group = music_study
    path = /home/santa/music_study
    valid users = @music_study
    write list = santa







```

As you can see what I am attempting to mount is not in samba config. I take it, that the share needs to be in my samba configure as the others. I also changed my mount points 1 more deep. 

So on the server - 
> UUID=1234 /mnt/data ext4 rw 0 0

and on the laptop -
> //192.168.1.120/mnt/data /mnt/data cifs defaults,guest 0 0

Ownership for both server and client directories are currently root with 755 rights.

That should be it, right? Confirm and I'll test. Thank you for your time. -Mike

---

### Post by mike430 on 2021-12-24
Thanks Fu for your time. I am interested in NFS. My situation however is that I have kids that are back and forth with Windows and Linux. This will be the arrangement for the foreseeable future. They are enjoying apps on both os's and will continue, therefor need that compatibility for hard drive space.

---

### Post by Morbius1 on 2021-12-24
I have noticed lately many users have a smb.conf that has been totally ripped apart like yous. I don't know if there is a HowTo out there that suggest this sort of thing but it is not helpful.
> //192.168.1.120/mnt/data /mnt/data cifs defaults,guest 0 0

Nope, That is not how Samba or CIFS works. You don't define a path to the internal path of the server. You specify the network path to the share.

[1] Guest access is not possible with the way you are set up since you disabled it be removing too much from the [global] section so add - at a minimum - one thing back:

Add the following line under the server min protocol = NT1 line:
```
map to guest = Bad User
```

[2] Create a share definition at the end on smb.conf that looks like this:

```
[data]
path = /mnt/data
read only = no
guest ok = yes

```
[3] The restart smbd:
```
sudo service smbd restart
```
[4] Then the cifs line on the client looks like this:
```
//192.168.1.120/data /mnt/data cifs defaults,guest 0 0
```

[COLOR="#0000FF"]Note: I am still confused about your use case with this share.[/COLOR]
> Ownership for both server and client directories are currently root with 755 rights. 

The cifs line above will result in a read only mount since the Linux permissions on the folder being shared on the server will not allow guest write access. If that is what you want that is what that line on the client will do. If you want something else you are going to have to provide far more detail about how you want this share to work.

---

### Post by mike430 on 2021-12-27
Hey Morbius. Thanks for your help on this, it totally works. But I think it brings up more questions then answers for me. I'm not going to pepper you with a bunch of questions, but perhaps you have a minute to answer a few then point me to a resource that can deepen my understanding.

There are really just 2 questions I have. First, mount scripts in etc/fstab and samba.conf can have similar or even conflicting options, which one of these takes precedence?

The next question is permissions. Take the case of mnt/data which are currently owned by root and in root group. If for example I want to make a Samba user or non-sudo user have complete access one way I could do this is make them owner of the 'data' directory as well as a group they are part of, would that be correct. 

Any good resources per these topics you suggest? 

Thanks brother for your help.  -Mike

---

### Post by rsteinmetz70112 on 2021-12-27
At the risk of butting in and and confusing everyone. I think there may be a disconnect here. 

/etc/fstab - mounts filesystems on a Linux filesystem. These can be either local or network filesystems usually either cifs or NFS
/etc/samba/smb.conf - shares filesystems using SAMBA from a Linux computer to (usually) Windows users.
/etc/exports - exports filesystems using NFS and is generally used between Linux or Unix computers.

---

### Post by Morbius1 on 2021-12-27
>  First, mount scripts in etc/fstab and samba.conf can have similar or even conflicting options, which one of these takes precedence?
They both do:

**SERVER**

The samba server is in charge of everything that happens on the server itself - dependent only on the underlying Linux permissions of the item being shared.

For example:

Let's say I have a folder on the server at /mnt/data - it is owned by root and has permissions of 755. Only root on the server can write to the folder.

I then create a share of the folder in samba that looks like this:
```
[data]
path = /mnt/data
read only = no
guest ok = yes
```
Samba will **[COLOR="#FF0000"]allow[/COLOR]** anyone the ability to access the share and will also [COLOR="#FF0000"]allow[/COLOR] them to write to that share. But the underlying Linux permissions will not **[COLOR="#FF0000"]permit[/COLOR]** it. The end result is that the client user will be read only.

The only way to allow a write to the folder being shared is to set Linux permissions permitting it. One way is to set the Linux permissions of /mnt/data to 777. There are other ways.

**CLIENT**

The situation and control is similar - but only on the client.

CIFS is a virtual filesystem. It cannot see or change or dictate the permissions of anything on the server. This is by design.

So let's say the mount declaration in fstab is this.
```
//192.168.1.120/data /mnt/data cifs defaults,guest 0 0
```

To the samba server you are the "guest" user ( normally mapped to the user "nobody" on the server ).
Samba will let you in and it will not stop a write.
But the Linux permissions on the folder on the server will stop it unless permissions are set to 777 on the server.

But there's more: By default cifs will mount with owner = root and permissions of 755 on the client. 
So even if permissions are set to 777 on the server and samba will allow a write to everyone only root will be able to write to the share - on the client.

If I morbius want to be able to write to that share from the client I must take ownership of the cifs mount replacing root as the owner. I do that by adding **uid=morbius** to the list of options:
```
//192.168.1.120/data /mnt/data cifs defaults,guest,uid=morbius 0 0
```

If I am in the unfortunate situation of having many users on this one client I can open this mount up to all users on the client:
```
//192.168.1.120/data /mnt/data cifs defaults,guest,dir_mode=0777,file_mode=0777,nounix 0 0
```
I can also limit access to a group of users on the client if I wish.

Once mounted at /mnt/data on the client it's permissions will be 777 allowing everyone to write - as long as Samba on the server **[COLOR="#FF0000"]allows[/COLOR]** it and the Linux permissions of the shared folder **[COLOR="#FF0000"]permit[/COLOR]** it.

Even though morbius, sally, and my Aunt Tilly can now write to the share on the client to the server they are all viewed as "guest".

---

