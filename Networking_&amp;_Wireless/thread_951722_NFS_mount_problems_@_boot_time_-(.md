---
title: "NFS mount problems @ boot time :-("
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by rflook on 2008-10-18
I have two machines on my home network, the backend which has all my films etc etc on it and a seperate frontend in my bedroom. In fstab i have the following

192.168.0.4://media/HD2/Videos /var/lib/mythtv/video nfs rsize=8192,wsize=8192,timeo=14,intr

Now the following command 

mount -a

mounts the network directory absolutely fine. However when i reboot the machine i get the following error 

starting nfs common utilities 
mount.nfs: internal error

It sits like this for a looooong time before moving on to the rest of the boot process. Then when the system is all booted up the shares are accessable. Can anyone help me with what is going wrong here?

---

### Post by rflook on 2008-10-19
Slight update

As i was using 7.10 on my backend and 8.04 on my frontend machine i installed 7.10 on the frontend so both systems were running the same version of the OS. Now rather than giving the original error it gives the following message 

starting nfs common utilities 
waiting for "/var/lib/mythtv/videos"       [fail]

Any ideas as to why it might be failing. As before once the boot sequence is completed the mount has been made sucessfully. But the boot sequence takes sooooooo long still. Any help appreciated

---

### Post by MTHarden on 2008-12-18
I just installed Mythbuntu 8.10 and have this same ... problem? The shares are mounted when the system has finished booting, it just adds... maybe 3 minutes to the boot time while it is "waiting" on the nfs share, and then failing. Any suggestions?

---

### Post by rflook on 2008-12-21
I might have something which may help you. I only sorted this recently. Drop out of mythtv and into the desktop. Then under system select network. In the network manager have a look in the properties of the wired connection. See if roaming mode is enabled (it wasnt on mine). This fixed my problem. However i cant remember if i did this on the backend or frontend machine and i cant check the frontend right now cos my missus is asleep. Sorry :-(

---

### Post by mdifabio on 2009-01-25
Did anyone have a solution to this problem?

Thanks in advance!

---

### Post by dmizer on 2009-01-25
Recently there are a number of threads with this issue. Oddly I couldn't find them quickly.

So, if this is your current /etc/fstab line for NFS mounts:
```
server.mydomain.com:/files /files nfs rsize=8192,wsize=8192,timeo=14,intr
```

Just add the "[COLOR="Red"]noauto[/COLOR]" to the fstab line like so:
```
server.mydomain.com:/shared/files [COLOR="Purple"]**/mount/point**[/COLOR] nfs [COLOR="Red"]noauto[/COLOR],rsize=8192,wsize=8192,timeo=14,intr
```

Then edit your /etc/rc.local to include the words mount [COLOR="Purple"]**/mount/point**[/COLOR] like so:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
mount [COLOR="Purple"]**/mount/point**[/COLOR]
exit 0
```

---

### Post by gier on 2009-02-01
The *mountnfs.sh* script in */etc/init.d* is the root cause of the behaviour you're seeing. The comment in the script says:

```

# Short-Description: Wait for network file systems to be mounted
# Description:       Network file systems are mounted by
#                    /etc/network/if-up.d/mountnfs in the background
#                    when interfaces are brought up; this script waits
#                    for them to be mounted before carrying on.

```

Essentially, the script puts in a 900 seconds wait to mount the NFS mounts in fstab, regardless of the options you put in, except NOAUTO.

What I've done is two things. First, I add in the *bg* option to my nfs mounts in */etc/fstab* as so:

```

192.168.xxx.xxx:/opt/Videos /var/lib/mythtv/videos/server nfs bg,async,proto=tcp,rw,ac 0 0

```

Secondly, I edited the */etc/init.d/mountnfs.sh* script as so:

Change

```

                case "$OPTS" in
                  noauto|*,noauto|noauto,*|*,noauto,*)
                        continue
                        ;;
                esac

```

To

```

                case "$OPTS" in
                  noauto|*,noauto|noauto,*|*,noauto,*|bg,*|*,bg,*|bg|*,bg)
                        continue
                        ;;
                esac

```

This bypasses the TIMEOUT=900 and your box should boot normally. The *bg* flag simply instructs the nfs mount client to put the mounting in the background.

HTH

---

### Post by mdifabio on 2009-02-23
Wow!  Excellent first post gier!

That solved my problem with NFS getting stuck while trying to mount my videos folder.

Thank you very much!  I hope others see this as I came across very few other posts out there regarding this issue.

---

### Post by dmizer on 2009-02-23
> **mdifabio said:**
> Wow!  Excellent first post gier!

Agreed. Good find.

---

### Post by gier on 2009-03-07
Heh ... Thanks. I was trawling looking for a solution for another problem, and I saw this thread and the OPs were sounding pretty frustrated. And the solution given in the post above mine, while working, sounded like a long way round. So, I decided to pitch in.

Am currently on another mindfrakking problem trying to get hdmi audio working on a DG45FC motherboard ... :(

---

