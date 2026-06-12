---
title: "Ubuntu 15.04 NFS timeout"
date: 2015-04-24
forum: Networking &amp; Wireless
---

### Post by rgammon51 on 2015-04-24
Things have changed in 15.04 and hints that were given for other versions are not working

2 machines, Desktop 15.04 - no server, strictly a peer to peer network

I have updated both machines with latest updates as of April 24 this morning

I have made certain that the exports directory and all files and directories are owned by me, not root.

One machine is nominally server as I have 3 USB thumb drives and two external usb drives that I want to share (not eject, pull plug, put in other machine)

nfs-kernel-server and nfs-common on the 'server', only nfs-common on the 'client'

Here is the except from exports for the 'server' (not running Ubuntu server, only desktop  

/exports                             192.168.124.1*(rw,sync,fsid=0,crossmnt,no_subtree_check)

Here is the except from the 'server' fstab

/media/rgammon51/MyData/Music                           /mnt/Music               none    bind              0       0
/media/rgammon51/MyVideo                                    /mnt/Video               none    bind              0       0   
/media/rgammon51/20A5-A622                                /mnt/Driver1             none    bind              0       0
/media/rgammon51/587C-5D6A                               /mnt/Driver2             none    bind              0       0
/media/rgammon51/D823-048F                                /mnt/Driver3             none    bind              0       0


/exports/Video                                           /home/rgammon51/Videos      none    bind              0       0
/exports/Music                                           /home/rgammon51/Music        none    bind              0       0


every time the 'client' tries to attach, whether thru command line or fstab, I get timeout for 2 minutes and the connection refused.  Also get unknown volume on server.   The usb drives have been formatted ext4.   

These are pure Ubuntu machine and no hint of another other OS around

What's is wrong?      I can move files with FileZilla via ftp without issue.   Both machines have the same user names??  But how do I verify UID/GUID number are the same, and do they really need to be???

No one other than me has access to this machines, at home and no one else here has a clue as to what Linux is all about.  I am the local "expert" but that is a water drop in an ocean compared to the TRUE experts.

I hope for an answer

---

### Post by SeijiSensei on 2015-04-24
> /exports 192.168.124.1*(rw,sync,fsid=0,crossmnt,no_subtree_ check)
Try using a CIDR address specification
```
/exports 192.168.124.0/24(rw,sync,fsid=0,crossmnt,no_subtree_ check)
```
Any better?  

More importantly, though, is there really a space between "subtree_" and "check" in the actual exports file as there is in what you posted here?

---

### Post by rgammon51 on 2015-04-24
no space between _check <--- transpose error to this posting

But BASE address for this domain does NOT start at 0.  100 is the base and I am not sufficiently familiar with the CID numbers to identify what needs to be done.   Addresses range from 100 to around 180 depending on the way the switch sees devices come on and off.

xxx.xxx.xxx.100/200 is not recognized

Does this form REQUIRE a base address of 0? 

No help so far, let keep trying

I don't like it as it opens the entire range from 0..255

I still get timeout errors but the time is fairly short

I will keep playing with mount points as I want to keep things simple

So I will export the subtree elements individually so I will not expose the root of thus tree (as there are other things there that ONLY belong on the server)

Yeah, so I have not gotten far enough into organization to keep it organized as I learn new things.  Gotta learn something new each day or give on life

Thanks for your help

Now not working  

xxx.xxx.xxx.0/24 on server

nfs-common and nfs-kernel-server are installed with apt-get to get the latest version

Old hardware means that I reinstall Ubuntu several times a week, and lots of practice doing

now 'client' says "mount.nfs: Failed to resolve server  servername"

What is wrong now?  any help will be appreciated.   I will keep this tab open to look for answers tomorrow

---

### Post by matt_symes on 2015-04-25
Hi

I'm using 14.04 with NFS and Kerberos authentication on some of the machines on my network (along with SSHFS and Samba for different use cases and test cases).

You upgraded from 14.10 on both machines ? Have you checked the change logs to see what changed between the two versions of the NFS packages ? This is the first thing i would read.

Have you enabled debugging output for NFS on both the server and the client ? That was invaluable when i was trying to get Kerberos working.

Are you sure the problem is with NFS and not with some other package such as bind (if you have set a DNS server up).

Kind regards

---

### Post by rgammon51 on 2015-04-25
Kerberos NO.  No DNS server here, other than the ATT modem that serves the internet connection, and it only feeds the switch.

No sure how to turn on debugging

This is NOT a business, or education, this a  home situation.

No one else is on this network.  Security is NOT an issue

This was not a network upgrade.   Downloaded the iso, burned the image to a CD.   Installed on BOTH machines MULTIPLE times.   There get to be issues with restarting where the dots will blink for 30 minutes or more,  I get tired of waiting so reinstall everything, and it ERASES the image that was there before.

only /var survives, as it is on a LVM separate from the OS.    Get /var loaded when installing (Advanced [two partitions wiped, do you want to change] - spec /, boot, var, swap)  Wish to reduce swap size but haven't the nerve - NEVER touched swap on these machines.  memory use has never been higher than 40%.  Swap is 13G, I could save perhaps as much as 8G if I

---

### Post by matt_symes on 2015-04-25
Hi

Why the capital NO and NOTs ? You'll be less likely to elicit help if your post come across as aggressive.

BTW: My network is also a home network. It should not make any difference that you are running 2 desktop installs to the configuration of NFS itself.

Did you find anything in the change logs ? That really is the first place i would look; that and the man pages to see if there are any updates there.

The mounts in fstab are mounted correctly ?

All NFS services are running on both machines ?

The rpc services are running on both machines ? What does this return on the two machines ?

```
rpcinfo -p
```

You can see exported mounts on both machines ?

```
showmount -e <ip_address>
```

This not a firewall issue ?

You can increase the debug level in syslog with

```

sudo vim /etc/default/nfs-kernel-server

RPCMOUNTDOPTS="--manage-gids --debug all"
```

What does syslog say ?

All the above are only suggestions of things to check as I'm still running 14.04. 

I'll install 15.04 on a spare couple of machines i have when i get the chance and try to reproduce the issue you're having.

Kind regards

---

### Post by rgammon51 on 2015-04-25
Now server and client are talking to each other all exports are mounted.  

Reports the size of the /exports volume not the contents of the link and no files are visible, 

Dolphin and File manager show nothing

---

### Post by SeijiSensei on 2015-04-25
> **rgammon51 said:**
> now 'client' says "mount.nfs: Failed to resolve server  servername"
Just as the error says, the OS cannot resolve the name "servername" to its IP address. You need an entry in /etc/hosts on the client machine that includes the name and IP address of the server.  Or, alternatively, just use IP addresses in /etc/fstab:
```
10.10.10.10:/home   /mnt/home   nfs defaults 0 0
```

As for the client address specification in /etc/exports, please run the command "man exports" to read the documentation for that file.  There are only a few options for address specifications, and none that I see allow for some arbitrary range of addresses.  You could use subnets smaller than a full class-C if you number the hosts correctly.  For instance, the address range 192.168.1.0/25 divides the network into two halves.  The lower subnet contains the host addresses 192.168.1.1-126, with 192.168.1.0 the "network address" and 192.168.1.127 the "broadcast address."  The upper subnet then includes the hosts 129-254 with 128 and 255 as the network and broadcast addresses.  Using a /26 divides the range into four segments, etc.  Whatever scheme you choose would need to be implemented in any DHCP server settings as well.

---

### Post by rgammon51 on 2015-04-26
The network issues appear to be resolved  - there are some timeout issues, but get resolved in a reasonable time

I can get ONE device across.  A 1Tb Toshiba USB external that has only music on it.

But I also want 3 USB Thumb devices and a 4T Toshiba USB external across also.


What comes next is NOT a Networking question so please forgive the venture into different territory

I have checked permissions.  Looks good for the bigger one to look the same on ls -altr

However, fstab WONT bind to the larger device, which has two partitions, 3T and 1T  I do not attempt to mount the !T

here is the example from fstab

/media/rgammon51/MyVideo      /mnt/Video     none  bind  0 0
/media/rgammon51/Music           /mnt/Music    none  bind  0 0

To repeat, NFS mounts will happen, but I can see the contents of only one device not the 5 that I want to see

I am WORRIED that the answer is that a 3T mount (ext4) is not allowed.  ext4 specs allow for very large volumes

---

### Post by rgammon51 on 2015-04-26
I am very pleased with the support that I have received here.  I look for to a response

---

### Post by SeijiSensei on 2015-04-26
Does each export have a different fsid?  
```

/export1    192.168.1.0/24(fsid=0, ...
/export2    192.168.1.0/24(fsid=1, ...

```

---

### Post by rgammon51 on 2015-04-26
No does it need to.   They all stem from root directory

/exports                   *(rw,fsid=0
/exports/Music
/exports/Video

The issue comes before NFS

source is /media/userid/MyVideo  <-an external drive

The is getting a link from the source to /exports/Video

I tried ln -s, but that winds up as complicated.    The only way I could find to create a workable link (and the details are still pending), ln to my home directory, Then another ln to exports (which required another directory to be created and finally a ln to the correct spot in /exports, but retains the name on the source

so the showmount shows

/home/userid/NewVideo

vs 

/export/Video

Is there a better way????

Thanks thanks thanks for your support

---

### Post by rgammon51 on 2015-04-27
The issue is that even with root privileges  ln -s is owned by root and cannot be changed to new ownership

/home/rgammon51/temp is has a bind to /media/rgammon51/MyVideo and files are visible there.

But a bind from there to /exports fails.  ln -s is owned by root and cannot be changed.

I wonder what to do??

THIS IS NOT A NFS TIMEOUT ISSUE.  CAN/WILL YOU HELP??

---

### Post by SeijiSensei on 2015-04-27
What if you just export /media/userid/MyVideo directly?

---

### Post by rgammon51 on 2015-04-27
I tried that.

/home/rgammon51/MyVideo 

 nobody:nogroup 777  

It makes little sense to REQUIRE that the bind has the SAME name.       

accesss denied by server -->   the mount with bind works, but mount fails on client with access denied

added fsid=1 as it was not in the /exports directory

Still not working as a nfs mount for client

---

### Post by rgammon51 on 2015-04-27
You may not notice that I have asked a FAMOUS question, (10,000 page views) and can respond to anyone's question

---

### Post by rgammon51 on 2015-04-27
It will mount on the server, and finding another place to mount, is EXCEEDING difficuilt

And once mounted, cannot export.

The 5th field of ls -altr is 4096 for the one that works,  zero for the rest of the possible mounts

ln -s does not appear to be viable as all the links are owned by root and will not export

---

### Post by SeijiSensei on 2015-04-27
I'm out of suggestions.  I never use bind mounts by the way, and I force my NFS server to use NFSv3.

---

### Post by rgammon51 on 2015-04-27
You do not use --bind

How to force NFSv3????

---

### Post by SeijiSensei on 2015-04-27
Add "vers=3" to the options list in /etc/fstab.  It's a client-side option.

---

### Post by rgammon51 on 2015-05-01
If I wipe the Ubuntu disc and re-install clean from scratch.

mount /media/userid/MyData   /home/userid/Mydata    mounts successfully

But easy on this hardware easy, easy for Ubuntu to get confused and not allow this to happen.

The FIRST challenge is to get the USB device mounted so that it can be shared.

That has been a BIG battle for me.

Now the second system is down and will not come up until I add a Ethernet card to replace the failed on-board Ethernet.

---

