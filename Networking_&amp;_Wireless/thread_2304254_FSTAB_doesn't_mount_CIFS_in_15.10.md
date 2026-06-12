---
title: "FSTAB doesn't mount CIFS in 15.10"
date: 2015-11-25
forum: Networking &amp; Wireless
---

### Post by bobblex on 2015-11-25
I loaded up Lubuntu 15.10 a few days ago and I'm having trouble getting my NAS auto-mounted.  In Lubuntu 14.04 LTS and earlier the NAS mounts using a CIFS entry in FSTAB:

//NAS IP address/NAS directory/TB-Mail  /mnt/TB cifs rw,guest,nounix,noserverino,uid=1000,_netdev 0 0

Using this same line in FSTAB for Lubuntu 15.10 I have to mount the NAS after login by running sudo mount -a.

In reviewing the forum I've found there was a similar problem in Ubuntu 14.10 for people trying to mount NFS and other file systems. I've tried the workarounds posted in those threads, but haven't found any that work yet.

Any suggestions?

Thanks

---

### Post by bab1 on 2015-11-25
> **bobblex said:**
> I loaded up Lubuntu 15.10 a few days ago and I'm having trouble getting my NAS auto-mounted.  In Lubuntu 14.04 LTS and earlier the NAS mounts using a CIFS entry in FSTAB:

//NAS IP address/NAS directory/TB-Mail  /mnt/TB cifs rw,guest,nounix,noserverino,uid=1000,_netdev 0 0

Using this same line in FSTAB for Lubuntu 15.10 I have to mount the NAS after login by running sudo mount -a.

In reviewing the forum I've found there was a similar problem in Ubuntu 14.10 for people trying to mount NFS and other file systems. I've tried the workarounds posted in those threads, but haven't found any that work yet.

Any suggestions?

Thanks
The first thing I would try is using the correct SMB (cifs) term for the share.  The SMB resource (share name) is always //NAS IP Address/NAS-Share-Name.

---

### Post by bobblex on 2015-11-25
> **bab1 said:**
> The first thing I would try is using the correct SMB (cifs) term for the share.  The SMB resource (share name) is always //NAS IP Address/NAS-Share-Name.

Thanks for your input.

What I have listed in my example are just fillers for the actual share names. I do use the correct IP address and do use the actual same share name as the SMB share name, which happens to be a directory and it's sub-directory on the NAS.

The line is currently working in Lubuntu 14.04.2 and Linux Mint 17.1 Xfce.  The line appears to correctly read, but the mount fails as the network isn't loaded at the time it is called.  In Lubuntu 14.04.2 and Mint and earlier versions of Lubuntu, I typically saw from three to six failed to connect messages, but the system kept trying to mount until successful.  In 15.10 I don't see any warning/errors about not being able to mount due to the network not being ready.

As you can see from the first post "_netdev" is used which is supposed make fstab wait until the network is ready, but it apparently doesn't work and it makes no difference where I put it after the "cifs".

After I log in, I'm able to run sudo mount -a and the NAS is mounted correctly.

---

### Post by bab1 on 2015-11-25
> **bobblex said:**
> Thanks for your input.

What I have listed in my example are just fillers for the actual share names. I do use the correct IP address and do use the actual same share name as the SMB share name, which happens to be a directory and it's sub-directory on the NAS.

I'm not sure what you are really saying here exactly.  The share name (e.g movies) can have a path of something like this:  /srv/share/movies.  The SMB resource is always //Server IP/movies.  We may be talking of the same thing here.
> 
The line is currently working in Lubuntu 14.04.2 and Linux Mint 17.1 Xfce.  The line appears to correctly read, but the mount fails as the network isn't loaded at the time it is called.  In Lubuntu 14.04.2 and Mint and earlier versions of Lubuntu, I typically saw from three to six failed to connect messages, but the system kept trying to mount until successful.  In 15.10 I don't see any warning/errors about not being able to mount due to the network not being ready.

It sounds like you already know what is not working.  Ubuntu 15.10 uses a different init system (systemd vs the earlier Upstart) so the workarounds will be different.
> 
As you can see from the first post "_netdev" is used which is supposed make fstab wait until the network is ready, but it apparently doesn't work and it makes no difference where I put it after the "cifs".

That's not my take on what _netdev does.  I see it as preventing a failure of the host to complete booting up if there is no network connectivity for one of the lines in the fstab file.  In this case it is working as I would expect it to.  From the man page for **mount**
```
  _netdev
              The filesystem resides on a device that requires network access (used to  pre&#8208;
              vent  the  system from attempting to mount these filesystems until the network
              has been enabled on the system).
```
> 
After I log in, I'm able to run sudo mount -a and the NAS is mounted correctly.
By this time the network is up and the **mount -a** command works.  The command also uses the *fstab* file, but this time it works.  See below from the same mount man page```
 -a, --all
              Mount all filesystems (of the given types) mentioned in fstab.

```

In the end the problem is the network connectivity not the line in the fstab file.

---

### Post by bobblex on 2015-11-26
BAB1,
Once again, thanks for your comments and input.  I agree it is the network connectivity that is the problem.  I did a very short Bash script to run mount -a. It did work from the command line, and I tried placing it in systemd and a few other places with no success. I did, however, come up with another work-around I found on the forums that seems to work.

I edited crontab (crontab -e) by adding a line to run mount -a at reboot.

```
 bob@Gracie-3:~$ sudo crontab -e
[sudo] password for bob: 
[code/end]

Which opens up crontab in an editing session, the added a line at the end.

[code]
@reboot sleep 20 && mount -a

```

The sleep 20 && tells the mount command to wait 20 seconds after reboot before executing and may need to be shortened or lengthened to meet the needs of individual systems.

---

### Post by bab1 on 2015-11-26
> **bobblex said:**
> BAB1,
Once again, thanks for your comments and input.  I agree it is the network connectivity that is the problem.  I did a very short Bash script to run mount -a. It did work from the command line, and I tried placing it in systemd and a few other places with no success. I did, however, come up with another work-around I found on the forums that seems to work.

I edited crontab (crontab -e) by adding a line to run mount -a at reboot.

```
 bob@Gracie-3:~$ sudo crontab -e
[sudo] password for bob: 

```

Which opens up crontab in an editing session, the added a line at the end.

```

@reboot sleep 20 && mount -a

```

The sleep 20 && tells the mount command to wait 20 seconds after reboot before executing and may need to be shortened or lengthened to meet the needs of individual systems.
I don't know that it really matters how you get the share mounted, as long as it works for you.  The **.system ** file for systemd should just point to a script you have.  Since the task is simple cron works just as well.  I think I would have tried the autofs package,  Autofs after configuration mounts the share only after first demand.

---

### Post by bobblex on 2015-11-27
> **bab1 said:**
> I don't know that it really matters how you get the share mounted, as long as it works for you.  The **.system ** file for systemd should just point to a script you have.  Since the task is simple cron works just as well.  I think I would have tried the autofs package,  Autofs after configuration mounts the share only after first demand.

I'm not sure the autofs would have worked for what I'm doing.  I keep my Thunderbird mail files on my network drive. I needed some way for Thunderbird to be able to able to access the NAS share in some way that Thunderbird could see and use them when setting up the account and configuration. 

Even though I could access the NAS and it's files through PCMANFM without configuring anything, T-Bird couldn't see them that way. After install cifs-utils, I could set up fstab to mount the share and could point T-Bird to the share. Seemed to be the only way that T-bird could see the NAS shared files.  I'm not really that familiar with Autofs, so will do some investigation into it.

Thanks for sharing your ideas.

---

