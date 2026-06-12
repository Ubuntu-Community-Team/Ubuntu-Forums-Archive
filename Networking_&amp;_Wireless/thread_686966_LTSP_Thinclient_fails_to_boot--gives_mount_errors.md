---
title: "LTSP Thinclient fails to boot--gives mount errors"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by fireworld2406 on 2008-02-03
Hi!
I have been trying to setup LTSP 5 from the Ubuntu repositories. The thinclient boots via PXE, and then takes me to a BusyBox prompt. Pressing Alt-F1 shows a lot of mount errors
> 
mount: Mounting /rofs on /root/rofs failed: Invalid argument
cp: unable to open '/root/etc/': Is a directory
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
I've already rebuilt the ltsp folder with ltsp-build-client and the problem still exists.
I've also tried searching Google but no solution has been found.
Is there a configuration error or some other problem?
Thanks in advance.

---

### Post by calvarymanagua on 2008-02-08
I am not sure if it is the same problem, but I also had a mount problem using ltsp.  The problem was that I was plugging both network cards into the same switch.  I had a router that gave all my computers that were not terminals their IP address, and then my Edubuntu machine was limited to give only IP address to the mac addresses on the terminals.  It worked great for k12ltsp (I did not need a seperate switch for the terminals and normal machines).  However, with edubuntu, it would not work correctly.  It initially seemed to get the correct IP address, run through some configuration.  It would then try and get the IP address again, and my router would give it one and mess the whole thing up.  Anyhow, to fix it, I just bought a seperate switch.

---

### Post by cracker on 2008-05-20
I have this exact same problem. I installed ltsp standalone server on ubuntu server amd64, ran ltsp-build-client --arch=i386, and configured dhcpd according to my ip scheme. The client boots PXE, but never gets anywhere, with a busybox initramfs> prompt. Changing the boot options on the thin client removing "quiet splash" I see the same error as OP,
```
mount: Mounting /rofs on /root/rofs failed: Invalid argument

```

I really don't know what to do, all I can find on Google says to run ltsp-build-client again, but this does not fix the problem.

Everything is Ubuntu 7.10, fresh amd64 server install, and i386 client build.

---

### Post by joehill on 2008-05-25
Same problem here.  I installed it on one AMD64 machine without problems, but I just installed it on a second and I get the same busybox console on console 8 and errors on console 1:

Error: Connect: Connection refused
mount: Mounting /rofs on /root/rofs failed: Invalid argument
mount: Mounting /root/dev/ on /dev/.static/dev failed: No such file or directory
(etc.)
Target filesystem doesn't have /sbin/init

I'd really appreciate if anyone had an idea what's happening.  It's not a router problem--one card is connected directly to the Internet and is 192.168.1.100 and the other is for the LTSP server and is 192.168.0.1

Thanks.

Joe

---

### Post by edenlab on 2008-05-26
Hi,
We are experiencing the same problem after upgrading from Gutsy to Hardy. The system is running on an intel Dell poweredge 830, and has worked for some time. The ltsp-update-keys and ltsp-update-image were run. The thin clients now get stuck with Busybox 1.1.3 prompt 
(initramfs)
ctl-alt-F1 on the client shows the following 

[LIST]
[*]mount: Mounting /nbd0 on /rofs failed: Invalid argument
[*]mount: Mounting /rofs on /root/rofs failed: Invalid argument
[*]cp: unable to open '/root/etc/': Is a directory
[*]mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
[*]mount: Mounting /sys on /root/sys failed: No such file or directory
[*]mount: Mounting /proc on /root/proc failed: No such file or directory
[*]Target filesystem doesn't have /sbin/init
[/LIST][LIST]
[/LIST]

So far I can find no solutions with a google search. Any ideas please?

---

### Post by joehill on 2008-05-28
That's weird, I rebooted the computer and now I'm able to boot the thin client.  (Now, if I could only get the one with the AMD Geode chipset to boot.  Damn, thin clients are complicated.)

---

### Post by edenlab on 2008-05-29
hi this fixed our problem

cd /var/lib/tftpboot/ltsp
sudo mv i386 i386.old
cd /opt
sudo mv ltsp ltsp.old
sudo ltsp-build-client
sudo cp /opt/ltsp.old/i386/etc/lts.conf /opt/ltsp/i386/etc/

After all was working finewe just cleaned up with.

sudo rm -Rf /var/lib/tftpboot/ltsp/i386.old
sudo rm -Rf /opt/ltsp.old

Especially removing the directory under tftpboot seems to be of high importance.

---

### Post by 3rdtechie on 2008-06-13
> **edenlab said:**
> hi this fixed our problem

cd /var/lib/tftpboot/ltsp
sudo mv i386 i386.old
cd /opt
sudo mv ltsp ltsp.old
sudo ltsp-build-client
sudo cp /opt/ltsp.old/i386/etc/lts.conf /opt/ltsp/i386/etc/

After all was working finewe just cleaned up with.

sudo rm -Rf /var/lib/tftpboot/ltsp/i386.old
sudo rm -Rf /opt/ltsp.old

Especially removing the directory under tftpboot seems to be of high importance.

I have the same Busybox problem.
I tried removing the directories and rebuilding with the commands above, but it still didn't work

---

### Post by scubasteve657 on 2008-06-27
I had the same problem on my machine (Error: Connection Refused, cannot mount, etc.).  I finally fixed it by re-installing Ubuntu, but after trying to get vmware setup the problem started again.

Turns out that the problem was with xinetd.  Removing xinetd auto-removes ltsp-server ltsp-server-standalone tftpd-hpa, so i had to reinstall ltsp-server-standalone & it works again.

Hope this helps someone!

---

### Post by Putu Wiramaswara Widya on 2008-07-01
I have same problem too....
But i could fix it by removing /opt/ltsp/i386 directory and install again using _ltsp-build-client_ command.

---

### Post by haz2a on 2008-07-04
Steve - how do you know it was xinetd?  Do you think it might be possible to fix without reinstalling LTSP?  Also, were you running the LTSP server in a VM, or just running VMware on the same host? - and which VMware product?  Thanks Haz

---

### Post by wirelessben on 2008-07-10
> **3rdtechie said:**
> I have the same Busybox problem.
I tried removing the directories and rebuilding with the commands above, but it still didn't work

I tried this and got the same results. I had upgraded from Dapper to Hardy 8.04.1 and installed ltsp-server and openssl-, and I just wanted to add LTSP to this already working PXE boot server. Following the Filesystem Hierarchy Standard, I had my tftp root at /srv/tftp. So I wanted to add the ltsp/i386 directory to it as /srv/tftp/ltsp/i386. For insurance, I added a symlink for /var/lib/tftpboot to point to /srv/tftp, in case any scripts referenced the old location.

So now I still get:
Error: Connect: Connection refused.
mount: Mounting /rofs on /root/rofs failed: Invalid argument
...

I have tried sudo apt-get clean and sudo apt-get update and have run ltsp-build-client 3 times.

apt-get update  does return a GPG error for an invalid signature from security.ubuntu.com

---

### Post by bobwdn on 2008-07-14
I am also having the same problem.  After following edenlab suggestion, I have rebuilt my ltsp-client image and it still gives me a BusyBox mount error the same as fireworld2406 listed in first thread.

I will follow this thread with my fingers crossed.

---

### Post by wirelessben on 2008-07-15
The server reboot solution worked! I made it to the GUI login screen. Thanks to joehill.

I'm not sure what it fixed. It may have been the GPG error I mentioned above that went away after I waited a day and did a "sudo apt-get update".

Server: Ubuntu 8.04 upgraded from 6.06.
Packages added: ltsp-server openssh-server

---

### Post by bobwdn on 2008-07-15
Well, what I have discovered (so far) is that installing VMware includes the installation of xinetd.  Ubuntu (and Debian) use inetd by default.  As both inetd and xinetd do similar (and most likely the same) jobs, could not one be "fighting" the other?  Both configuration files (for inetd and xinetd) have entries that reference identical services (time and discard.)  

I am to newbie to understand this depth of programing. Nor am I sure what I am talking about specifically and therefore I could be wrong.  But, I see posts that are guessing answers and users who are not sure what they did to "fix it."  I would like to find a solution that allows running both LTSP and VMware.  

I need to review a default inetd.conf file from a computer that has not had VMware installed.  And therefore xinetd has not been installed, yet.  To compare to my existing inetd.conf file.

Could someone post their default inetd.conf file?

---

### Post by bobwdn on 2008-07-18
Thanks to JAM at LTSP forum and Oliver Grawert at Ubuntu. Their posts to my thread at ltsp-discuss forum helped me solve my problem. That being the BusyBox prompt our clients were receiving.

Now, let's be clear here, this worked for me in my situation. I did NOT know if this is a true fix, yet.

What happened to me was my installation of VMware onto our LTSP server. Following the install instructions I found at howtoforge.com, I installed xinetd as instructed. Vmware install went okay and worked. (That was on a Friday.) The following Monday, LTSP thinclients would not boot complaining of mount errors and resulted in a BusyBox prompt command line.

I did not know (until now) that installing xinetd (on Ubuntu) will un-install openbsd-inetd (the version of inetd Debian/Ubuntu distros uses as it's default.) That un-install "breaks" the mount sequence used by LTSP clients.

My "fix" was to install openbsd-inetd which un-installs xinetd. Then, I was pleased to find that my thin clients booted properly AND my VMware still worked. Apparently VMware is not all that dependent on xinetd. But, I could be wrong and later find I may have a different problem.

I did consider (briefly) configuring xinetd to replace my default inetd service but, it was immediately apparent (to me) that that was over my head of knowledge. Better left to the professionals who understand all the programing.

I want to close with this fact. This fixed my LTSP thinclient boot problem and it was easier than re-installing LTSP.

Hope this helps.

---

### Post by richvers on 2008-07-19
I tried all mentioned still gives me a busybox screen.
Reinstalling ubuntu ltsp gave back ltsp, after installing virtualbox (1.6-2 Sun), all ended in busybox. No xinetd was installed, but even after reinstalling openbsd-inetd as suggested nothing more.
Does somebody has a clue?, otherwise I am putting LTSP behind me as the kids do not like it anymore (although they were thrilled when it was working OK)

Thanks

---

