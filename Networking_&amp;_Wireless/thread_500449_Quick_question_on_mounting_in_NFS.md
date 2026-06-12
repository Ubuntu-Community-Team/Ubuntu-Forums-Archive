---
title: "Quick question on mounting in NFS"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by timzak on 2007-07-13
I'm following a tutorial on setting up a home network/file sharing and I have a question about mounting.  Here's a copy and paste from the tutorial:
> to mount the share from a terminal type:

sudo mount server.mydomain.com:/files /files


I realize I don't actually type "server.mydomain.com", but what DO I type here?  A real-world example would help.  I'm not too versed on networking, so in my mind, it looks like I'm typing a website address according to the example above, but that doesn't seem right.  I don't have my own website, so what do I type here?

Be kind.  :-)

Thanks!

---

### Post by Mr. C. on 2007-07-13
The command :

```
mount myserver:/path/to/remotedir /mnt/localdir
```

would mount the exported directory **/path/to/remotedir** from the machine **myserver**.  The mount point in the local file system would be **/mnt/localdir**.  This means you would have access on your local machine to the remote files and directories within /path/to/remotedir, directly from within your file system space in **/mnt/localdir**.

Don't confuse this with the web; we're discussing NFS here, and the server:/path syntax was used long before the web was born.

MrC

---

### Post by timzak on 2007-07-14
Thanks.  I'm still trying to understand what I would type in place of "server.mydomain.com" or as in your example, "myserver."  Could I put anything there, or does it have to be my user name, or some other specific-to-my-machine name?

---

### Post by Mr. C. on 2007-07-14
You need an NFS server running.  If you don't have an NFS server, there's no point going further.

If you have setup a system to be an NFS server, that hostname is the hostname you use.

Think:  "I want to act as if the files on **myNFSserver **are present on my current machine".

MrC

---

### Post by timzak on 2007-07-14
I'm following this howto:
[http://doc.gwos.org/index.php/NFS_Easy_Way](http://doc.gwos.org/index.php/NFS_Easy_Way)

I basically have a laptop and desktop that I want to share files back and forth.  In the howto linked above, I've already set up both computers as servers (I have to do that if I want the file transfers going both ways, right?)

So I just use the OTHER computer's hostname?  So let's say we have joe@joe-desktop and joe@joe-laptop.  On the desktop I'd set it to "joe@joe-laptop" and on the laptop I'd set it to "joe@joe-desktop"?

Just to be clear, I've followed the howto step-by-step up to "Mounting Manually" under "Install NFS Client Support".  This is where I got stuck on what to type in place of "server.mydomain.com".

Thanks again for your time.  I do appreciate it.  :-)

---

### Post by Jose Catre-Vandis on 2007-07-14
I assume you have your NFS server set with a fixed IP address (you should have!)
Once this is done and you know what it is, replace

server.mydomain.com

with the IP address.

```
sudo mount 192.168.0.22:/files /files
``` 

You can always associate the Ip address with a name in your hosts file on the client machine, and then use the name instead of the Ip address e.g.

in hosts file:

mynfs         192.168.0.22

and therefore

to mount the share from a terminal type:

```
sudo mynfs:/files /files
```

---

### Post by Mr. C. on 2007-07-14
Spend a few minutes looking at the NFS notes and lab work here:

[http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

MrC

---

### Post by timzak on 2007-07-16
I know for some here this is simple stuff, but something like this (file sharing between two Linux machines) should be easier to set up than file sharing between a Linux and Windows machine.  I had less trouble setting up file sharing with the Windows PC on my home network.  I hope the developers are reading this and making efforts to automate this process in future versions.  

I appreciate the help and the reference material, but unfortunately I don't have the time to study up.  I just want it to work without having to roll up my sleeves and take time away from my family.

Jose, I'm not sure how to determine if I have a fixed IP address or not.  I do have a router with 4 PCs attached (one with Windows, 3 Linux-based), so I'm guessing the standard 192.168.0.X format applies?  I freely admit my ignorance in the realm of networking, so feel free to treat me like a beginner.  :-)

Thanks.

---

### Post by Mr. C. on 2007-07-16
timzak,

Its not that it is simple stuff -its that you are following someone else's cookbook recipe, and are not happy with the results, and ask people here to debug what went wrong with your process.  That's just not possible.

For every person who has "less trouble" setting up something in another OS, there are dozens who had more trouble.  The bottom line is that interconnecting software between two disparate systems is inherently difficult.

The only thing people here can do is help you question by question, or turn you loose on some tutorial.  People's ability to follow instructions to the letter... is, lets just say, very poor.

There are also conflicting goals between making something easy for users to setup and configure, vs. maintaining the security necessary to prevent ill-willed peopled from easily gaining unintended access.

Sorry its is difficult; that's the way it is today.

MrC

---

### Post by timzak on 2007-07-16
Mr.C, 

I guess part of my frustration is that my questions are being answered with questions.  I think if I could just get an answer to my original question, I could continue following the tutorial I was using (that I referred to in my 3rd post in this thread) and get it up and running, and then look back on what I've done and understand it better.   My questions again:

> Could I put anything there, or does it have to be my user name, or some other specific-to-my-machine name?

> I basically have a laptop and desktop that I want to share files back and forth. In the howto linked above, I've already set up both computers as servers (I have to do that if I want the file transfers going both ways, right?)

> So I just use the OTHER computer's hostname? So let's say we have joe@joe-desktop and joe@joe-laptop. On the desktop I'd set it to "joe@joe-laptop" and on the laptop I'd set it to "joe@joe-desktop"?

I posted the link to the howto I was following and where I got stuck.  I followed the directions to the letter up to the point I got stuck.  But the howto is not very specific at the point I get stuck.  It assumes knowledge beyond the scope of the howto.

When I was single, even when I was married but had no children, I'd relish the opportunity to dive into something like this and learn all about it before getting my hands dirty.  But my time with family is more important than this, so I try my best with the limited time I have.  Sometimes I have to try and get a shortcut, then look back and understand it better after the fact.

Thanks.

---

### Post by Mr. C. on 2007-07-16
I completely hear you, and empathize.

It is, however, the nature of diagnosis that requires asking additional questions.  Consider:

"Doc - my gut is in terrible pain; what should I take?"

Simple question, right?  In your world, you'd get a simple answer, such as "take two aspirin and call me in the morning".  Would you be satisfied with that response, and pay for it!

You and I know the physician must ask you a series of questions to narrow the scope.  You could just take two aspirin, and that might just solve the problem.  Orthogonally, you could just reinstall your OS and start again with a better HowTo.  That's the typical take-two-aspirin equivalent response.

If this was all so easy, a) we wouldn't need HowTos, and b) perfectly clear, easy-to-follow HowTo's would be available.

So, you have to help us outsiders who can't see what you did, or the current state of your system, gain some knowledge about your current environment and problems.  

Otherwise, go find that aspirin and start afresh...

MrC

---

### Post by timzak on 2007-07-16
> **Mr. C. said:**
> So, you have to help us outsiders who can't see what you did, or the current state of your system, gain some knowledge about your current environment and problems.

Let's start over.  I followed this HOWTO:

[http://doc.gwos.org/index.php/NFS_Easy_Way](http://doc.gwos.org/index.php/NFS_Easy_Way)

I followed the HOWTO step-by-step to the letter up to "Mounting Manually" under "Install NFS Client Support".  So up to this point, I have done everything in the HOWTO and **have not experienced any problems or setbacks.**  

At this point, all I want is clarification on what to type in place of "server.mydomain.com" (as it is referred to in the aforementioned HOWTO).  

If it matters, my computers are tim@tim-desktop and tim@tim-laptop.  They are connected to a wired 4-port router and sharing a cable internet connection.  I want these two computers to be able to share files back and forth.  The desktop has Ubuntu 7.04 and and is connected to port 1 on the router.  The laptop has Linux Mint 7.04 and is connected to port 3 on the router.

I hope this is more clear.  I've stated exactly what I've done.

Thanks again.

---

### Post by Mr. C. on 2007-07-16
How can we clarify for you specifically what to enter, when you have not yet told us on which machine you configured an NFS server !  All we know is you have two machines and you've followed some HowTo.

Tell us specifically:

a) which machine you installed the NFS server on
b) which file systems you have exported to be shared
c) where you want the mounted file system to be located on the client

One machine "serves" a directory tree, the others "access" that tree.  Tell us which is which.

MrC

---

### Post by timzak on 2007-07-16
> **Mr. C. said:**
> How can we clarify for you specifically what to enter, when you have not yet told us on which machine you configured an NFS server !  All we know is you have two machines and you've followed some HowTo.

Tell us specifically:

a) which machine you installed the NFS server on
Both machines.  My understanding was that the client can only receive files from the server, not send to the server.  Since I want file transfers to go both ways, I installed NFS server on both.  Is this incorrect?  If I recall correctly, it seems that NFS server was already installed on both machines.  When I entered ```
sudo apt-get install nfs-kernel-server nfs-common portmap
``` it indicated on both machines that it was already installed.  I figured Ubuntu and Linux Mint both had these preinstalled by default.
> b) which file systems you have exported to be shared
I chose this option from the HOWTO:
>     * For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255 


Code:

/files 192.168.1.1/24(rw,no_root_squash,async)

> c) where you want the mounted file system to be located on the client
I think in the HOWTO I'm following this is the next step after the point I'm currently at (did you look at the HOWTO?)  How about a folder called "shared files" in the home directory?  So home/tim/shared files.

> One machine "serves" a directory tree, the others "access" that tree.  Tell us which is which.  Assuming I was wrong in your question a) above, I want tim@tim-desktop to be the server.  Does it matter that I'm using the same home name on both machines?  Will that be confusing for the OSes when trying to communicate?  In other words the laptop is tim@tim-laptop and the desktop is tim@tim-desktop.

Once again, thank you.

---

### Post by Mr. C. on 2007-07-16
Ok, we're making progress.

I'll say up front, I (and many others) will not go off reading someone else's multi-page HowTo to try to figure out what is or isn't working for some given case.  It is up to *you* to translate and reply to diagnosis questions; not us to review other people's documents.

That said, your understanding about the client only receiving files is incorrect.  The client neither sends nor receives.  The client *mounts* an exported file system from the server.  Files and directories can be retrieved, created, deleted, etc. from either the client or the server.  From the application perspective, there is no distinction about where the directories and files actually reside - they simply appear under the root of your file system.

In one of my earlier posts, I indicated how you request the mount.  More specifically given your data, from tim-laptop perform the command:

```
mkdir /home/tim/shared
sudo mount -t nfs tim-desktop:/files  /home/tim/shared
```

If everything is setup correctly, this will work just fine, and from tim-laptop you will have full access to tim-desktop's /files directory.  If the mount command fails, there is something wrong with your configuration.  I could spend the next 10 minutes writing down all the ways that command will fail, but I've already done so in the lab work and notes I've referred to earlier.  If you get an error, post the specific command and its output including error messages for further diagnosis.

MrC

---

### Post by timzak on 2007-07-16
Mr.C:

Thanks for your patience with me.  I'll keep in mind that in the future I should probably copy and paste a HOWTO I am following straight into my post rather than provide a link.  I wanted to give a clear indication of what I had and had not done without making my post too long, hence only posting the link, then saying where I was in the HOWTO.

I will try your suggestion this evening and report back my results.

---

### Post by Mr. C. on 2007-07-16
No problem - we'll get you up and running.

I wouldn't advise your copy/paste suggestion.  The problem is not in following a link, or reading.  Its the missing *output*, diagnostics, and possible clues that are required.

It is generally futile to diagnose without direct access to the current state of the system.

MrC

---

### Post by Jose Catre-Vandis on 2007-07-17
Mr C, you've done a great job so far. Can I point the OP at another howto:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

which I think is more clearly laid out than that of the OP's original choice.
It has worked for me everytime, and helped me to understand what is going on

Also, can see any reason, why it won't work both ways, it does for me

---

### Post by timzak on 2007-07-19
Mr.C

I just now got an opportunity to take another crack.  I obviously have done something incorrectly.  I get the following message when inputting the lines you gave: "can't get address for tim-desktop".

Here's the entirety of what I've done:

On tim-desktop (server):

```
tim@tim-desktop:~$ sudo apt-get install nfs-kernel-server nfs-common portmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nfs-kernel-server is already the newest version.
nfs-common is already the newest version.
portmap is already the newest version.
The following packages were automatically installed and are no longer required:
  gnome-bin rrootage-data nethack-common libexchange-storage1.2-3 libgnome32
  gnome-libs-data libart2 libgnorbagtk0 libedata-cal1.2-6 libwv-1.2-3
  libegroupwise1.2-13 libgii1 libgnomeui32 libdb3 libgii1-target-x sox
  libedata-book1.2-2 imlib-base liborbit0 gdk-imlib11 libgnomesupport0
  libgsf0.0-cil liballegro4.2 libgnorba27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```
tim@tim-desktop:~$ sudo dpkg-reconfigure portmap
 * Stopping portmap daemon...                                            [ OK ] 
 * Starting portmap daemon...                                            [ OK ] 
 * Restoring old RPC service information...                              [ OK ] 
There are RPC services which registered with the portmapper
before the configuration was changed.
You need to manually restart them in order for the changes to take effect.
Current registered services:
------------------------------------------------
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  32770  nlockmgr
    100021    3   udp  32770  nlockmgr
    100021    4   udp  32770  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  50895  nlockmgr
    100021    3   tcp  50895  nlockmgr
    100021    4   tcp  50895  nlockmgr
    100024    1   udp  32771  status
    100024    1   tcp  37061  status
    100005    1   udp    840  mountd
    100005    1   tcp    843  mountd
    100005    2   udp    840  mountd
    100005    2   tcp    843  mountd
    100005    3   udp    840  mountd
    100005    3   tcp    843  mountd
------------------------------------------------
```
I selected "No" when it asked me if I wanted to bind loopback.

```
tim@tim-desktop:~$ sudo /etc/init.d/portmap restart
 * Stopping portmap daemon...                                            [ OK ] 
 * Starting portmap daemon...                                            [ OK ]
```

I edited /etc/exports and added this line to the end of the file and saved it:
```
/files 192.168.1.1/24(rw,no_root_squash,async)
```

```
tim@tim-desktop:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.1/24:/files".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ]
```

```
tim@tim-desktop:~$ sudo exportfs -a
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.1/24:/files".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0
```

Next, on the client (tim-laptop): (to be continued)

---

### Post by timzak on 2007-07-19
From tim-laptop:

```
tim@tim-laptop:~$ sudo apt-get install portmap nfs-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
portmap is already the newest version.
nfs-common is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.20-15-generic libavahi-compat-howl0 module-assistant
  xserver-xorg-dev libsilc-1.0-2 libdecoration0 libwv-1.2-3
  libmono-sqlite2.0-cil linux-headers-2.6.20-15 libemeraldengine0
  libgsf0.0-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tim@tim-laptop:~$ 


```

```
tim@tim-laptop:~$ mkdir /home/tim/shared
tim@tim-laptop:~$ sudo mount -t nfs tim-desktop:/files /home/tim/shared
mount: can't get address for tim-desktop

```

So that's where I'm at.  I'm sure I've done something incorrectly, I'm just not sure what.  Any ideas?

Thank you.

---

### Post by Mr. C. on 2007-07-19
> $ sudo mount -t nfs tim-desktop:/files /home/tim/shared
mount: can't get address for tim-desktop

This error indicates that the function called gethostbyname failed to translate tim-desktop into an IP address.  The gethostbyname call will add your domain name (as in /etc/resolv.conf) to attempt hostname trasnlation.  It will look in /etc/hosts and DNS by default configuration, but is depends on the hosts entry in /etc/nsswitch.conf to determine which files/services are queried for hostname translation.

So, what's you hosts entry look like in  /etc/nsswitch.conf ?

Is tim-desktop in /etc/hosts, and what does the entry look like?

hostname translation of course is avoided if you use an IP address.

MrC

---

### Post by timzak on 2007-07-19
Here's the hosts entry in /etc/nsswitch.conf:

> hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

Here's the contents of /etc/hosts:

```
127.0.0.1 localhost
127.0.1.1 tim-desktop.Linux

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Thanks.

---

### Post by Mr. C. on 2007-07-19
There's your problem.

The hostname tim-desktop is not known on the host tim-laptop.  Add:

```
*Tim-desktop_IP_here*  tim-desktop
```

to tim-laptop's /etc/hosts file.

MrC

---

### Post by timzak on 2007-07-19
Clarification, when you asked me the previous questions, you didn't specify for which system (tim-desktop (host) or tim-laptop (client)).

My answers were based on tim-desktop.  I didn't even look at the contents of those files on tim-laptop.

I'll check back this evening.

Thanks.

---

### Post by Jose Catre-Vandis on 2007-07-19
Yep, I agree about the hosts setup from what is posted. Try using the Ip address first, then move onto the hosts file issue.

Also, you are running on the 192.168.1.1 sub net ? For both machines?

And you do have a directory called /files on your server (tim-desktop) available to share (put some files in it so you can see things are working)

And also, do you need to run:
```
sudo mount -t nfs tim-desktop:/files /home/tim/shared
```
as opposed to simply:
```
sudo mount tim-desktop:/files /home/tim/shared
```
?? I don't.

These may be all basic stuff you have done, but just checking :)

---

### Post by Mr. C. on 2007-07-19
timzak,

Here's the rule - if you want to use hostnames instead of IP addresses, you need an entry in any one of /etc/hosts or a local DNS server.  The system has no idea how to figure out the IP address of some machine on your LAN without that.  There must be a name translation somewhere.  /etc/hosts is easiest, but is required on every machine.

Jose Catre-Vandis - one can use an abbreviated mount command when an /etc/fstab entry exists for that mount, as in :

/etc/fstab:
```
remote:/remote/fs                /mountpoint   nfs ...
```

Either of the mountpoint or remote file system can be used:
```
mount remote:/remote/fs
mount /mountpoint
```

Otherwise, both the device (eg. remote fs) and mountpoint must be specified, along with all desired mount options.

MrC

---

### Post by timzak on 2007-07-21
Okay, I added

```
Tim-desktop_IP_here  tim-desktop
``` using my DHCP IP for tim-desktop.

to /etc/hosts on tim-laptop.  Now when I type
```
$ sudo mount -t nfs tim-desktop:/files /home/tim/shared
```

into the terminal I get
```
mount: tim-desktop:/files failed, reason given by server:  Permission denied
```

By the way, is this discussion we're having in any way compromising my system security?  I'm not well-versed in networking, so I'm not sure if someone could take any of this info we've been discussing to access my system?

Thanks.

---

### Post by Mr. C. on 2007-07-21
Ok, you are getting closer.

There are a number of reasons why you get permission denied when trying to mount.  Show your server's /etc/exports file, and the error message you see in the server's log.

There is no security issue in what you've been sharing in the forums here.

Have you read and studied my week 4 NFS notes and lab : [http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)  ?

MrC

---

### Post by LunatikOwl on 2007-07-21
> **timzak said:**
> 
By the way, is this discussion we're having in any way compromising my system security?  I'm not well-versed in networking, so I'm not sure if someone could take any of this info we've been discussing to access my system?
Thanks.

Have you read [http://www.unhandledexceptions.com/tutorials/tut_11.html](http://www.unhandledexceptions.com/tutorials/tut_11.html) ?
you need to edit /etc/hosts\.(allow|deny) to completely block nfs from outside the subnet.

p.s.

does any of you experts know if theres a possibility to "bounce" tcp/ip packets from within the  subnet so the the server will think it came from within?

if so, isn't in a security compromise(a MAJOR one)?

---

### Post by Mr. C. on 2007-07-21
Spoofing packets to look like they came from the LAN is difficult with a firewall.  It requires a compromised system or application or other attack vector.  Typically firewalls are not setup to allow remote connections to inside services, including portmap.

Using tcpwrappers is another layer of security, but is less important for a simple firewall-protected LAN.  It should **not** be used when trying to bring a service up for first time, as the extra layer of protection is also an extra layer that must be diagnosed when the service does not work as expected.  Only after services are working should the additional layers of security be added.

Many "HowTo" guides teach nothing, and almost never *explain* how the system works, or how to resolve unexpected problems.  Following them blindly is for lemmings.

MrC

---

### Post by timzak on 2007-07-21
Here's /etc/exports:

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
#
/files 192.168.1.1/24(rw,no_root_squash,async)
```

Where do I find the server's log?

I'll check out your notes when I get a chance.  I'll check back later this evening.

Thanks.

---

