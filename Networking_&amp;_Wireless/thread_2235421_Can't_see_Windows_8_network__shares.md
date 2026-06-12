---
title: "Can't see Windows 8 network / shares"
date: 2014-07-21
forum: Networking &amp; Wireless
---

### Post by cris6 on 2014-07-21
Hello there

I am using Ubuntu Studio 14.04 x64 here and its impossible to see my Windows 8 machine here

And I can see my Ubuntu machine from Windows with no problem at all, and I can copy files to my home folder with no problem since I shared it and logged in with my linux user from my windows machine.

In Thunar when I click on Browse Network it shows nothing at all but if I type smb:// the ip address of my windows machine it shows the shares, but does not access them because of the password
But if I type the netbios name of my machine smb://mywindowsmachine it does not connect

In my smb.conf I added
name resolve order = bcast host lmhosts wins
and removed the # from    wins support = yes so it can support wins

my nsswitch.conf I added
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

my hosts file
127.0.0.1    localhost
127.0.1.1    crisubs

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


And when I use smbtree it shows nothing at all

My Windows 8 machine is fine because I can connect my Android smartphone to my IP address but it does not show the netbios name inside ES File Explorer, but my settings inside Win8 wireless adapter is configured to activate netbios over TCPIP

Any idea of what I am doing wrong ?

BTW: My android phone access (rw) everything fine in the windows machine but it does not acess my 2TB and my 4TB external hdd
Do you know if there is a limit of hdd size to share thru SMB ?


Tks

---

### Post by bab1 on 2014-07-21
> **cris6 said:**
> Hello there

I am using Ubuntu Studio 14.04 x64 here and its impossible to see my Windows 8 machine here

And I can see my Ubuntu machine from Windows with no problem at all, and I can copy files to my home folder with no problem since I shared it and logged in with my linux user from my windows machine.

In Thunar when I click on Browse Network it shows nothing at all but if I type smb:// the ip address of my windows machine it shows the shares, but does not access them because of the password
But if I type the netbios name of my machine smb://mywindowsmachine it does not connect

From what you describe it sounds like Samba file sharing is working but the NETBIOS name services are not.
> 
In my smb.conf I added
```
name resolve order = bcast host lmhosts wins
```
and removed the # from   ```
 wins support = yes so it can support wins

```

When you use bcast first in the "name resolve order there is really no need to specify anything else.  Since bcast ALWAYS works in a single segment network (a single network range) the other methods are never used by Samba (smbd/nmbd).
> 
my nsswitch.conf I added
```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```

This however affects the kernel operations for things other than Samba.  You should revert this back to the default.
> 
my hosts file
```
127.0.0.1    localhost
127.0.1.1    crisubs

```
These listings are not use for bcast either but you do need them to other operations that are not Samba related.  You should add a NETBIOS NAME to the smb.conf file in the [global] section like this```
netbios name = <SOME_NAME>
```...where <SOME_NAME> is the name of the Samba server.> 
And when I use smbtree it shows nothing at all

Add some debug to the command and past the output back here.  The command would be```
smbtree -d3
```
...when you post the information **please place the text inside the [code] brackets to preserver the formatting**.  You can do this by first clicking on the [SIZE=5]**# **[/SIZE] icon located at the top of the editor and the placing the info inside the brackets. > 

My Windows 8 machine is fine because I can connect my Android smartphone to my IP address but it does not show the netbios name inside ES File Explorer, but my settings inside Win8 wireless adapter is configured to activate netbios over TCPIP

Any idea of what I am doing wrong ?

NETBIOS NAME services not correctly configured.  This is very common but easily fixed.   ;-)
> 

BTW: My android phone access (rw) everything fine in the windows machine but it does not acess my 2TB and my 4TB external hdd
Do you know if there is a limit of hdd size to share thru SMB ?
As far as I know there is no practical limit to the size of a SMB/CIFS share.  The file system where the HDD is mounted may have a limit that is lower than 2TB.  Where do you have these HDD's mounted (in the file system) and what format are the partitions?.

---

### Post by cris6 on 2014-07-22
Hello there :)

Tks for the help

I searched for some more questions and changed nsswitch.conf
 > hosts:        files dns wins

And now it can connect to my Windows shares with no problem 



But the devices I told you about they do not connect at all really do not work on network, and I have no idea why

All other HDDs are showing with no problem and connecting here but those 2 units

Both are NTFS on a Windows 8.1 x64 machine and they are mounted at my windows 8.1 machine with no problem, and are really the ones that do not work thru my network

Gigolo says:
Failed to mount Windows share: Invalid argument

Do you have any idea why this happens ?

Tks!

---

### Post by bab1 on 2014-07-22
> **cris6 said:**
> ...

But the devices I told you about they do not connect at all really do not work on network, and I have no idea why

All other HDDs are showing with no problem and connecting here but those 2 units

Both are NTFS on a Windows 8.1 x64 machine and they are mounted at my windows 8.1 machine with no problem, and are really the ones that do not work thru my network

Gigolo says:
Failed to mount Windows share: Invalid argument

Do you have any idea why this happens ?

Tks!
Are we just talking about the 2 HDDs?  Are they shared properly?  Gigolo is onl interested in SMB/CIFS shares so it only looks for SMB resources in the form of //NETBIOS_NAME/SHARE_NAME.

SMB/CIFS shares are by directory not block devices (HDD).  This means that if you want to share an entire HDD you need to share the root directory of the partition that spans the drive.  This is the directory at the mount point of the partition in question.  Drives are hardware, partitions are the formatting on the drive and the file system the data.  The file system on the partition is what you really are mounting to the existing file system.

---

### Post by cris6 on 2014-07-23
Hi

Yep, they are shared correctly since I see the shares in Gigolo when I create a new bookmark, and they do not mount and give this error message
> Failed to mount Windows share: Invalid argument

If a drive is not connected to my Windows machine, Gigolo says, as expected:
> Failed to mount Windows share: No such file or directory

But, still did not find any reason it does not mount those 2 drives that are working fine inside Windows

I even tried to make a new share, specific to one folder inside the F drive (windows letter), assign a different sharename, check all user permissions just like the other shares, and mount it to see if the specific shared folder would mount here, and Gigolo sees the new share name, but fails to mount it in the same way it failed to mount the whole drive as above.

Any idea why its failing this ?

Those drives are connected to a external powered USB 3.0 HUB and I made Windows to not power off USB devices or hubs, and they are working fine 24/7 on the machine, but they do not mount at all here

Tks

---

### Post by bab1 on 2014-07-25
> **cris6 said:**
> Hi

Yep, they are shared correctly since I see the shares in Gigolo when I create a new bookmark, and they do not mount and give this error message

If a drive is not connected to my Windows machine, Gigolo says, as expected:


But, still did not find any reason it does not mount those 2 drives that are working fine inside Windows

I think we should clean up the little errors you have in your configuration.  The may not help;  on the other hand it may not help at all.  We won't know until you try it and we see what happens  You do not need any WINS for a single segment LAN. In my opinion should never use WINS in such a configuration.  In addition you have configured it to access only 127.0.1.1 which is only accessible from the Ubuntu host.  The network 127.0.0.0/8 is for the localhost only.  This can cause name service problems. 

My suggestion is to add a NETBIOS name to the smb.conf and delete *wins* from the name resolve order line so it looks like this```

netbios name = <SOME_NAME>

name resolve order = bcast
```

Then you need to comment out this line like this```

#      wins support = yes so it can support wins
``` 

Then you need to reboot the samba server with this command```
sudo service smbd restart
```
Now allow about 15 minute for the settings to be accepted by the Master Browser of the LAN before you check to see if you can access the shares via Gigolo.
> 

I even tried to make a new share, specific to one folder inside the F drive (windows letter), assign a different sharename, check all user permissions just like the other shares, and mount it to see if the specific shared folder would mount here, and Gigolo sees the new share name, but fails to mount it in the same way it failed to mount the whole drive as above.

Any idea why its failing this ?

I hate guessing. diagnosing the problem is much more rewarding.  If I had to guess I would say you have a misconfiguration of the smb.conf.  You have not really followed my suggestions completely.  In a sense I'm telling you to revert everything back to the default other than the NETBIOS name and bcast settings so we have a solid starting point.  I would also return the nsswitch.conf file to it's default.  I doesn't directly affect SMB/CIFS sharing, but it can affect other things down the line.

Gigolo is really just the gvfs libs (gnome nautlius) packaged for use by other file managers.  It does not need to have book marks set for you to mount the share.  If you click on the specific share icon that share will be mounted.  All the available shares should show up under the specific servers NETBIOS name.

---

### Post by cris6 on 2014-07-31
Hello there

Sorry for the delay, had some problems with my ISP those days, but I tried to change the things you told me to and they did not work as expected

So I decided to keep my hosts files with

> 
127.0.0.1    localhost
127.0.1.1     crisubs

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


and my smb.conf
> 
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = WORKGROUP
    name resolve order = bcast host lmhosts wins

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
    wins support = yes



So, that made things work as they were at first, but the hard drives I told you (the ones with more than 2TB) did not mount

I even bought a new HDD (2,5') 2TB to install games from Steam and the same hapenned, did not mount, since it could mount only smaller drives

I tested mounting those units with Android, ES File Explorer, since it has SMB and cloud options, and the same problem happens, what makes me think it is a Windows issue

I even installed a SMB client on my Windows Phone (Lumia 520) to test if it was something related to *nix SMB clients issue since Android has linux kernel, and the same problem happens, since the WP app gives an error msg when mounting those units, since it also mounts the smaller ones

Do you have any idea about what may be possibly happening here ?

All things I have done makes a evidence that this is a server side/ windows related problem...

Would you have any idea about what is happening here ?

But tks anyway for your help

---

