---
title: "Can't permanently mount samba share"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by bigbadsi on 2006-10-22
I have already posted at the end of this great [Howto]("http://ubuntuforums.org/showthread.php?t=255872&highlight=Permanently+mount+samba+share") but didn't get any bites so I've assumed I should have started a new tread.  Please forgive me if this counts as double-posting or if I've been impatient.

I've only been using Dapper for two weeks and have limtied experience with samba and linux in general so please bear with me...

I am unable to permanently mount a samba share. I have samba running, I can access the share via network:/// and can mount the share manually using:
```
sudo mount -t smbfs //ugly/music /home/bigbadsi/mnt/ -o credentials=/root/.smbcredentials
```
Have have already set up /root/.smbcredentials and this file looks like this:
```
username=uglysamba
password=uglysamba

```
I have set up the user uglysamba on the remote windows box (as a limited user) and set this password to uglysamba.

The share won't mount automatically after a reboot. This is my /etc/fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
#//ugly/music /home/bigbadsi/music smbfs username=uglysamba,password=uglysamba,dmask=777,fmask=777 0 0
//ugly/music /home/bigbadsi/music smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0
#//ugly/music /home/bigbadsi/music smbfs credentials=/root/.smbcredentials 0 0
#//ugly/music /home/bigbadsi/music  smbfs 0 0
#//ugly/music home/bigbadsi/music smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

I have tried using the last four commented lines in /etc/fstab, one at a time, and have read the [Dapper starter guide]("http://ubuntuguide.org/wiki/Dapper#How_to_permanently_mount_a_samba_share") on the subject.

I can mount the share using:
```
sudo mount -a
```

Is this a permissions issue at startup, do I need to include other options in /etc/fstab or am I missing something else? Also, is there a log I should have checked (I looked in /var/log/samba but didn't know what I was looking at)?

I don't necessarily need the security of using the credentials file but I suspect this isn't the issue.

Thanks.

---

### Post by featherking on 2006-10-22
Dont know if this will help you but this is the line from my fstab file

```
//RON/iTunes\040Music /mnt/iTunes smbfs username=chris,password=chris,umask=022 0 0
```

I dont even have a credentials file but the username/password should be your user name and password. I always thought the credentials file was just to prevent somebody from looking at you fstab to see you username/pass. Also the  "\040" in that line is a space.

Ive been using it this way forever and its worked fine. As long as you have a place created to mount your share it should work fine i think

---

### Post by bigbadsi on 2006-10-22
Thanks for your quick reply featherking, it's appreciated.

I tried the line from your /etc/fstab, i.e.: 
```
//ugly/music /home/bigbadsi/music smbfs username=uglysamba,password=uglysamba,umask=022 0 0
```
and can mount the share using:
```
sudo mount -a
```
However when I reboot my PC, the share isn't automatically remounted.

I briefly thought the problem was a samba password issue so I mirrored the remote userid and password locally, and created a samba password for new userid.  This also failed to automatically mount the share on reboot.

Should the local mount point simply be a directory without any special attributes?

Confused.

---

### Post by featherking on 2006-10-22
The local mount point doesnt have to be anything fancy. Mine is /mnt/iTunes with the permissions set as drwxr-xr-x so only root can write to the directory. I used to have that directory mount automatically as you are trying to do because i have all of my music on a windows pc in another room.

I set that up to mount automatically every time i booted up. It works great. I have been traveling a lot lately and havent needed it as much so ive just recently commented that line out of my fstab but i dont think anything else is required for it to work.

I even looked through my /etc/samba/samba.conf to see if i changed anything there but it didnt look as though i had (it was some time ago i set this up)

Your username and password should be set up on the pc you are trying to connect to and not your local pc, is this how you have it set? However, you said you were able to connect so this must not be an issue. Hmm

---

### Post by featherking on 2006-10-22
Looking again at what youve posted so far, i wonder if another issue could be that the folder you are trying to mount to is in your home folder.

```
/home/bigbadsi/music
```

Or look at the permissions on that folder, maybe because fstab is accessed way before you ever log in maybe thats why it cant mount it, and you are able to once you log in.

If you could change the permissions on that mount folder to 755 and the owner to root maybe that would make a difference. To do this run

```
sudo chown root /home/bigbadsi/music
```

That will change the owner to root and not your username. Then run

```
sudo chmod 755 /home/bigbadsi/music
```

That will change the permissions on the directory so that only root has read,write,exec on that directory. Since fstab is accessed as root maybe this is your problem? Hope you figure it out. I am interested if that fixes the problem

---

### Post by dmizer on 2006-10-22
you're better off creating a folder in the /media directory, eg: /media/music

this way, your mounted drive will automatically appear on your desktop.  also the masking will work correctly (which i think might be your problem here).

just make a directory in /mount for your share:
```
sudo mkdir /media/music
```
then change your fstab to read:
```
//ugly/music /media/music smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0
```
this should work correctly on reboot.

---

### Post by bigbadsi on 2006-10-23
Thanks featherking and dmizer, I tried the following scenarios:

1.
sudo mkdir /media/music
fstab:
//ugly/music /media/music smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

This didn't remount after reboot.

2.
sudo chown root /media/music
sudo chmod 755 /media/music
fstab:
//ugly/music /home/bigbadsi/music smbfs username=uglysamba,password=uglysamba,umask=022 0 0

This didn't remount after reboot.

3.
sudo chown root /home/bigbadsi/music
sudo chmod 755 /home/bigbadsi/music
fstab:
//ugly/music /home/bigbadsi/music smbfs username=uglysamba,password=uglysamba,umask=022 0 0

After reboot the share didn't automatically remount but I did notice that Nautilus shows "music" under Places with a samba symbol on it but the remote share isn't mounted, the music directory under /home now as a padlock symbol on it, presumably because of the change of ownership and permissions in 2., and has nothing in it. Scenario 2. also shows the samba symbol.

4.
sudo rmdir /media/music
sudo mkdir /media/music
fstab:
//ugly/music /media/music smbfs username=uglysamba,password=uglysamba,umask=022 0 0

After reboot I saw the same symbol in Nautilus as in scenario 3. although /media/music doesn't have a padlock on it.

5.
fstab:
//ugly/music /media/music smbfs username=uglysamba,password=uglysamba,dmask=777,fm ask=777 0 0

After reboot I saw the same symbols in Nautilus as in scenario 3., except /media/music doesn't have a padlock on it.

My noob guess is that a permissions issue is in effect here but I don't understand enough to see patterns of behaviour. It seems that Nautilus recognises the share, at least to some degree, as a samba share, i.e. I see a samba symbol on "music" under Places.

Still confused.

---

### Post by techstop on 2006-10-23
I am having *exactly* the same problem. I have 2 ubuntu boxes on my network, 1 ubuntu and 1 xubuntu. They both connect to a samba share on a Clarkconnect box. The ubuntu box mounts the share perfectly. The xubuntu box will mount from the command line with the command found in this howto;

[http://www.ubuntuforums.org/showthread.php?t=280473](http://www.ubuntuforums.org/showthread.php?t=280473)

```
sudo smbmount //Clarkconnect/shared /media/clark -o username=user,password=mysecretpassword,uid=1000,mask=000
```

However, when I add the line to fstab as per the same guide;

```
//Clarkconnect/shared  /media/clark   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
```

...and reboot, thunar takes about 2 mins to open the mounted folder, and then there is nothing there. I'm going batty.

FWIW, here is the fstab from my working ubuntu box;

```
//Clarkconnect/shared       	/media/clark  	smbfs   credentials=/root/.smbcredentials,uid=barney,dmask=777,fmask=777 0 0
```

I have tried using the same format on the xubuntu box with no luck. I don't understand the dmask, fmask, umask etc, or why there is uid in the working fstab. Every howto I read about samba seems to be telling a different story.

---

### Post by dmizer on 2006-10-23
what happens when you do this ...
```
ping ugly
```

i bet both of your problems are related to netbios name resolution.

---

### Post by featherking on 2006-10-23
You can enable netbios in windows by going to All Programs>Accessories>Communications>Network Connections. Then right click on the network connection you use and hit properties. The scroll down to TCP/IP and hit properties. Then at the bottom hit advanced. Go to the WINS tab and at the bottom check "Enable NetBIOS over TCP/IP"

Another thing - If you go to the places tab in gnome and then to network places, are you able to find you windows box through that window? After you click network under the places tab on the menu (sorry im not at my ubuntu machine, cant remember exact menu names) it will ask you to select a workgroup and then it will show you the machines in that workgroup and then the shares on individual machines. Perhaps you arent on the same workgroup as the windows computers?

Also, maybe you could post the [global] section of your smb.conf file (found in /etc/samba/smb.conf) the global section is where you declare your machine name and workgroup. Check and make sure you are on the same workgroup as the windows machine

Im just spinning trying to think up scenarios, i really dont remember having this much trouble configuring it on my laptop..

---

### Post by dmizer on 2006-10-23
no ... to simply mount samba shares, you don't need to do anything to smb.conf ... smb.conf is only for serving samba, not for reading samba.

i think this will be your answer:
edit nsswitch as follows:
```
gksudo gedit /etc/nsswitch.conf
```
edit the line that says:
> hosts: files dns
and add "wins" so it looks like this:
> hosts: files dns wins
save the file and exit.

now you'll need winbind:
```
sudo aptitude install winbind
```
reboot, and see if the shares are mounted.

---

### Post by bigbadsi on 2006-10-24
dmizer, I tried:
```
ping ugly
```
and just as you predicted, the name would not resolve.

I made the change to /etc/nsswitch.conf, as per your instructions and installed winbind also following your instructions, then...
```
ping ugly
```
did resolve!

Unfortunately when I rebooted, the share still failed to automatically remount.

I did notice that IP addresses were generally take a long time to resolve.  This was very noticable in Firefox.  I have the Fasterfox plug installed and this reported that Firefox took many seconds to look up a new page, sometimes as many as nine (seconds, not milliseconds)!  Also, when I pinged a site by name there was often a delay of several seconds before seeing the results, even though PING returned sub-second times.  The local machine duals boots Windows and I didn't see this behaviour in that OS; pings were quick and so were new DNS lookups in Firefox, even after a DNS cache flush.  I'm using the past tense because on a whim I powered-down every machine on the local network including the smoothwall firewall, a networked printer, the modem and the network switch.  After restarting everything, I didn't get the long IP resolve and ping delays.  The change was dramatic and websurfing seems several orders of magnitude faster.

But the the share still doesn't mount after reboot.

I get the distinct impression that samba is perhaps suffering from a wider networking issue, although at least one troubling problem seems resolved.

Thanks for everyone's time and I welcome suggestions.

---

### Post by dmizer on 2006-10-24
you might also get better surfing results if you turn off ipv6 (search for ipv6 in the wiki for how to resolve this pesky little issue if you haven't already).  also, check your dns servers and make sure your router isn't listed as the primary dns server.

glad to see you've resolved at least one of your issues ... lol, but that hasn't fixed your auto mount problem.

take a look through your system messages in /var/log/ ... see if you can find anything related to samba or fstab.

also might try cleaning out your fstab and removing all the lines you have commented out, and just use this:
```
//ugly/music /media/music smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0
```
humm ... might try replacing "ugly" with the target computer's lan ip address.

i know the above line will work because i use it myself.

tell me about your network.  wired? wireless? if wireless: wpa/wep? ndiswrapper?

how about your router? you said you're using smoothwall firewall, but your router should have a firewall as well ... they could be interfering with eachother.  and the more i think about this, the more i'm thinking that it probably is firewall related.

do you have another method of connecting to your network?  if so, try using it instead and see if you can get it to auto mount then.

if it's wired ... try a different port in your router.

this is not a configuration issue on the part of your fstab.  if you can get it to work with 'sudo mount -a', then fstab is working as it should.

---

### Post by MetalMusicAddict on 2006-10-24
bigbadsi, did you add the user your trying to connect to the other machine on that machine?

Say your 2 PC are Frick and Frack. A user (Jeff) on Frack wants to connect to Frick. Jeff would have to be a user on Frick also.

Is this a all Linux network or a win and linux setup?

---

### Post by The-J on 2006-10-24
bigbadsi,

The problem is most likely that you are trying to mount the samba share on non root drive. I had the exact same problem mounting on my hdb1 drive. Try making a mount directory on your root drive and mount the samba share there. To be completely sure you can always specify the IP address of the samba machine in fstab.

(Yes I did make an account for this answer (; )

---

### Post by The-J on 2006-10-24
FYI This is my fstab:

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /mnt/hdb1       ext3    defaults        0       0
#music and movie shares
//192.168.3.2/misc   /mnt/server/misc smbfs username=shared,password= 0 0
//192.168.3.2/data   /mnt/server/data smbfs username=shared,password= 0 0

---

### Post by dmizer on 2006-10-24
MetalMusicAddict ... the first post indicates that the user was added on the remote windows machine.

The-J ... welcome!  unfortunately i don't think this is the problem either becuase the remote machine is not a linux box.  but i'm interested to see what happens when fstab is set up to use the lan ip instead of the netbios name.

---

### Post by The-J on 2006-10-25
Dmizer, 

My answer was not related to the remote machine. 
I used to first mount my hdb1 drive to /mnt/hdb1. The next line in fstab was to mount my server to /mnt/hdb1/server/. This works, but when I rebooted the share was not automatically remounted. (mount -a then did the trick). Mounting the share to /mnt/server instead of /mnt/hdb1/server does get the shares automatically mounted on reboot.

---

### Post by bigbadsi on 2006-10-25
dmizer, my network is wired: a D-Link DSL-302G ADSL modem, a smoothwall box with a red and green interfaces, a 10/100Mbps network QoS switch, three Windows PCs (including local dual boot), an Ubuntu box, a printer, and my local Ubuntu install.  All network cards are either onboard or PCI.

The-J, I have on two partitions used by Ubuntu locally: a swap partition and root.  There's also FAT32 and NTFS partitions.

I tried removing the extra lines from fstab, leaving only:
```
//10.1.1.27/music /media/music smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

```

When I reboot and log on I get the following in a dialog box:
> Internal error
filed to initialize HAL!


And the share doesn't automatically remount.

I bypassed the smoothwall box entirely and used my ADSL modem as the default gateway and saw the same "failed to initialize HAL" error, and no auto remount.  When I tried:
```
sudo mount -a
```
I saw: 
> Could not resolve mount point /media/music

I could ping ping 10.1.1.27 without problems.  I could ping ugly but this was slow, sometimes takes several seconds to return each line, even though reported times are similar to ping 10.1.1.27

I can change fstab to:
```
//ugly/music /media/music smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

```
...and while the share doesn't automount...
```
sudo mount -a
```
...mounts the share.

I reread the documentation I made when setting up the smoothwall box and I now remember I had to disable the NAT server on the modem, forming some sort of semi-bridge with the smoothwall box.  To check this setting I had to use IE and Windows to access the modem's web-based GUI tool and I found the NAT server was enabled but also found I couldn't reboot the modem without this setting  resetting.  This might be because the smoothwall box wasn't in the chain on reboot.  I'm still in Windows even though I can't access the modem's web-based GUI with smoothwall as the gateway.

I think I'm onto something here.  I'll have a look at the smoothwall forums shortly and also spend some time trying to understand why I can't seem to disable the NAT server on the modem.

At moment I'm downloading Xubuntu for another machine so I can't test anymore tonight.  Dumb!  Thanks for everyone's help though.

Hey, Firefox 2.0 has spellcheck, although "spellcheck" is apparently spelled wrong - at least I had some fun/wins tonight!

Si

---

### Post by dmizer on 2006-10-25
edit: see my next post for your answer ;)

> **bigbadsi said:**
> dmizer, my network is wired: a D-Link DSL-302G ADSL modem, a smoothwall box with a red and green interfaces, a 10/100Mbps network QoS switch, three Windows PCs (including local dual boot), an Ubuntu box, a printer, and my local Ubuntu install.  All network cards are either onboard or PCI.
nice hardware.  at least we can rule out wireless and encryption as a cause.

> The-J, I have on two partitions used by Ubuntu locally: a swap partition and root.  There's also FAT32 and NTFS partitions.

I tried removing the extra lines from fstab, leaving only:
```
//10.1.1.27/music /media/music smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

```

When I reboot and log on I get the following in a dialog box
[quote]Internal error
filed to initialize HAL!

And the share doesn't automatically remount.[/quote]
try mounting the share in mnt as The-J suggested.  i never had to resort to this, but there's no reason to not try it.  also, you're going to want to keep an eye on this bug: [https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874](https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874) ... i didn't read through it carefully, but there doesn't seem to be any resolution yet.  but there are links to other bug reports, so you might find something.

> I could ping ugly but this was slow, sometimes takes several seconds to return each line, even though reported times are similar to ping 10.1.1.27
definitely check your network configuration to make sure that your router is not listed as your primary dns server.  it could be that you're simply timing out on the mount during your boot process.

> I can change fstab to:
```
//ugly/music /media/music smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

```
...and while the share doesn't automount...
```
sudo mount -a
```
...mounts the share.
if you did this with your smoothwall bypassed, and still failed to auto mount, then you can be fairly sure that your smoothwall is not the problem.

> I reread the documentation I made when setting up the smoothwall box and I now remember I had to disable the NAT server on the modem, forming some sort of semi-bridge with the smoothwall box.  To check this setting I had to use IE and Windows to access the modem's web-based GUI tool and I found the NAT server was enabled but also found I couldn't reboot the modem without this setting  resetting.  This might be because the smoothwall box wasn't in the chain on reboot.  I'm still in Windows even though I can't access the modem's web-based GUI with smoothwall as the gateway.
not sure what you mean about semi-bridge.  were you ever only able to view the modem admin gui with windows?

> I think I'm onto something here.  I'll have a look at the smoothwall forums shortly and also spend some time trying to understand why I can't seem to disable the NAT server on the modem.

Hey, Firefox 2.0 has spellcheck, although "spellcheck" is apparently spelled wrong - at least I had some fun/wins tonight!
i've been using aspellfox plugin for some time.  works great.  happy hunting, and enjoy xubuntu ... it's awesome!

---

### Post by dmizer on 2006-10-25
looks like this is the answer:
[https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874/comments/48](https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874/comments/48)

let me know if you need help deciphering that.

---

### Post by The-J on 2006-10-25
> **dmizer said:**
> looks like this is the answer:
[https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874/comments/48](https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874/comments/48)

let me know if you need help deciphering that.

Think Dmizer nailed that one for you. 

The directory where I mount (/mnt/server) is owned by the user who is going to use it, not root. In my case the user mythtv (chown -R mythtv:mythtv /mnt/server)

---

### Post by techstop on 2006-10-25
/kisses dmizer

Great work! This workaround fixed my problems, thanks very much! I owe you one. :mrgreen: 

Lots of other comments here too (same bug);

[https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874](https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874)

---

### Post by dmizer on 2006-10-25
> **techstop said:**
> /kisses dmizer

Great work! This workaround fixed my problems, thanks very much! I owe you one. :mrgreen: 

glad to know it helped, but thanks need to go to bigbadsi for having the fortitude to stick this out.  without all the troubleshooting bigbadsi's done, we wouldn't have found the hal error. all i had to do was google the bug report ... lol.

all the same ... i've always wanted to go to australia. ;)

---

### Post by bigbadsi on 2006-10-26
> [https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874/comments/48](https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874/comments/48)

Success! This is so sweet.

Thanks dmizer, and everyone else who helped, I really appreciate all the work.

And finally, how should I record the thread as being solved?

---

### Post by dmizer on 2006-10-26
fantastic!

i remember seeing thread titles edited to reflect solutions had been found, but they have since changed forum software, and i haven't been able to figure out how to do that since.

if you feel like it, you could always write up a nifty howto and post it in the howto section ;)

---

### Post by techstop on 2006-10-26
I was a little hasty with my celebrations..... :( 

In dmesg, I get this after booting;
```

smbfs: Unrecognized mount option noauto
```

And in thunar, I can see the folders of the share, but no files!

If I run /etc/rc.local, the share mounts fine and I can see all the files etc....

Strange. :confused: 

Here is my /etc/fstab;

```
//Clarkconnect/shared /media/clark  smbfs    noauto,credentials=/root/.credentials,uid=josh,dmask=777,fmask=777 0 0
```

And here is my /etc/rc.local;

```
#!/bin/sh -e
mount /media/clark
exit 0
```

Any tips?

EDIT: after a bit of clicking around, the files seem to reappear, and they are visible from the terminal as well. Might be a thunar issue?

---

### Post by dmizer on 2006-10-26
what's the output of uname -r ? (ie, what kernel are you using)

i'm reading about issues with some kernels having this problem and others not. (2.6.16)

try removing the "noauto" option from fstab. noauto appears to not be a real option for smbfs, and doesn't know what to do with it when mount passes the option to smbfs.

from man mount:
> Mount options for smbfs
Just like nfs, the smbfs implementation expects a  binary  argument  (a struct  smb_mount_data) to the mount system call. This argument is constructed by smbmount(8) and the current version of  mount  (2.12)  does not know anything about smbfs.

just today, i started to look into cifs which is suppose to be a replacement for smbfs, but i haven't had much luck yet.  but eventually, we are not going to have a choice and will have to use cifs.  that's where fedora core sits now.

edit:
here's something else, you don't happen to have non-latin characters in your shared folder names, or file names do you?

---

### Post by techstop on 2006-10-26
I'm using 2.6.15-23-386...

On reflection, I think the issue is something to do with thunar. I just booted then and went straight to the console, all the files were there as expected, it might be something I'm doing wrong with thunar. I'll just leave it for a while, if I'm still having problems, I'll post back here. Thanks for your help anyway!

Cheers.

---

### Post by dmizer on 2006-10-30
linked to this thread in my howto for cifs mounting here: [http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)

thanks bigbadsi!

---

### Post by armalite on 2006-11-15
I have same problem as above, I'm using Edgy and a Gentoo server.

Automounting (in fstab) a CIFS partition in Edgy doesn't work when mount point is in different partition than root.
I have 2 mounts in /mnt and 2 in /home/user. The ones in /mnt do mount automatically at boot, the others in /home/user don't. 

A subsequent command line "mount /home/user/remote" works with no errors.

This is strange anyway... I come from Gentoo with equal setup and nothing wrong there.

Problem is surely the mount point not in root partition, I don't know why anyway... workaround works but a workaround shouldn't ever be needed, in my opinion.

---

### Post by dmizer on 2006-11-15
> **armalite said:**
> Problem is surely the mount point not in root partition, I don't know why anyway... workaround works but a workaround shouldn't ever be needed, in my opinion.
which is why the bug is still open and marked with a "medium" importance.

---

### Post by gekkothelizard on 2007-06-21
I have the same problem, I even tried adding the _netdev option, becouse the only solution that I can think of is that at the point when linux tries to mount stuff from fstab somethink that is needed to mount a samba share isn't loaded yet. But even _netdev didn't help (should signal linux to mount the share after every networking driver is loaded). It's very strange that mount -a fixes the problem if called after the os has booted. I think this could be a bug in xubuntu, becouse I have been using this in kubuntu without problems.

---

### Post by applezip on 2008-01-07
I was having the same problem.

I found that amarok was still running something even after I closed it, and it screwed something up. I killed amarok and I was able to umount the share. 

I have everything up and running again, but the mount doesn't show up on the desktop like it used to. It's not a big deal, everything else is working as it used to.

edit: It's also not in the Places menu like it used to be.

```
//192.168.1.111/160 /home/drax/music   smbfs  username=remote,password=XX,uid=drax,gid=users 0 0
```

---

### Post by dmizer on 2009-01-25
> **applezip said:**
> I have everything up and running again, but the mount doesn't show up on the desktop like it used to. It's not a big deal, everything else is working as it used to.

edit: It's also not in the Places menu like it used to be.

```
//192.168.1.111/160 /home/drax/music   smbfs  username=remote,password=XX,uid=drax,gid=users 0 0
```

If you move your moutpoint from /home/drax/music to /media/music, the share will show up on the desktop and in Places. 

Alternatively, you can also create a symbolic link to the desktop, and create a bookmark in Nautilus by dragging the /home/drax/music folder from the left pane to the right pane (I believe this creates a link in Places as well).

---

