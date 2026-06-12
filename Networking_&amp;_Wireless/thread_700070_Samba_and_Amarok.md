---
title: "Samba and Amarok"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by rabid9797 on 2008-02-18
Ok guys, so i recently moved my external hardrive over to another computer, and want to serve up music to my laptop from it. Exaile can't do this, but I know amarok can.

I have been trying the guide i found here: [http://amarok.kde.org/wiki/Samba](http://amarok.kde.org/wiki/Samba)
and it should work for me, but it doesn't.

for some reason i can't use //192.168.x.x to find my computer, i have **have** to use smb://192.168.x.x

So, how can i still mount the shared folder while using smb://

or, 

how else can i setup this shared folder so i can use // instead?

thanks

---

### Post by njparton on 2008-02-18
Mount it using **CIFS** in your **fstab** file.  Search the forum using these 2 keywords and you'll find your solution.

---

### Post by rabid9797 on 2008-02-18
that still doesn't help me, i get this when i try to use cifs with the smb: protocol
```

rabid9797@rabid9797-laptop:~$ sudo mount -t cifs smb://MSHOME%3Brabid9797@rabid9797-desktop/The%20Goods -o username=*******,password=******* /home/rabid9797/Desktop/thingy
[sudo] password for rabid9797:

Mounting cifs URL not implemented yet. Attempt to mount MSHOME%3Brabid9797@rabid9797-desktop/The%20Goods
No ip address specified and hostname not found

```

so how can i re-setup my remote computer so that i don't use smb: ?
(i guess thats what i should really be asking)

also: ive included a screenshot of what i actually did to get my folder shared.(thats all ive done)

is there something else i should of done?

---

### Post by njparton on 2008-02-18
My fstab file for a cifs mount looks like this:

```
//192.168.1.10/folder_to_be_shared   /mnt/mount_point   cifs   defaults
```

Try that sort of thing in "/etc/fstab" then reboot or "sudo mount -a".

Where "192.168.1.10" is the IP address of the remote computer.

---

### Post by rabid9797 on 2008-02-18
doesnt work :/

(because doing //192.168.1.138 doesn;t do anything, i just get a "couldn't fine /192.168.1.138" error)

---

### Post by jhetrick62 on 2008-02-19
What OS is your "other computer" running?

Jeff

---

### Post by njparton on 2008-02-19
Are you connecting via a router or switch? If the former you may need to set up some port forwarding so you can see the ip address.

---

### Post by jhetrick62 on 2008-02-19
You should not need forwarding if you are on the same subnet with matching first 3 octets.

Jeff

---

### Post by rabid9797 on 2008-02-21
@ jeff
its ubuntu too.

i managed to get it all working(the mounting) by messing around with fstab, im using this line:

```
\\192.168.1.138\floyd /media/remote smbfs user,password=******,username=rabid9797 0 0
```

this seemed to work, the first time i used it it worked right off the bat, full read and write access. but now for some reason i only have read access(after a restart).

so what should/can i add to that line in order to gain write access again?

---

### Post by jhetrick62 on 2008-02-22
I always place rw at the beginning of the options, so it should be, 
\\192.168.1.138\floyd /media/remote smbfs rw,user,password=******,username=rabid9797 0 0

Give that a try.  As long as all folder permissions are correct, this should work.

Jeff

---

### Post by rabid9797 on 2008-02-23
> **jhetrick62 said:**
> I always place rw at the beginning of the options, so it should be, 
\\192.168.1.138\floyd /media/remote smbfs rw,user,password=******,username=rabid9797 0 0

Give that a try.  As long as all folder permissions are correct, this should work.

Jeff

thanks for the help, but still no luck :(

---

### Post by jhetrick62 on 2008-02-24
What are the errors that you are getting if you mount the above with the following command line statement:

mount //192.168.1.138/floyd /media/remote -t smbfs -o rw,username=rabid9797,password=*****

List the error messages in the terminal back here.  Also if that doesn't work try it again with the only change being -t cifs.  List those errors messages also.

I don't use the smbfs mounts myself, but they should work.  I access all of my samba mounts using cifs as Fedora went to that a couple of years ago so I got used to it. 

Also, you may need to place sudo in front of these, it depends on how /media permissions are set up.  I use user mounts inside of the users's home directory and these don't require sudo.  I also use general system mounts inside of my /mnt directory and those do require sudo usually the way I have them set up.

That exact statement above with cifs works on my system with of course my own share and permission settings.

Jeff

---

### Post by rabid9797 on 2008-02-24
sambfs got this error:

```

rabid9797@rabid9797-laptop:~$ sudo mount //192.168.1.138/floyd /home/rabid9797/Desktop/remote -t smbfs -o rw,username=rabid9797,password=*******
[sudo] password for rabid9797: 
mount: wrong fs type, bad option, bad superblock on //192.168.1.138/floyd,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

but cifs worked perfectly!

so now, how can i use that line to mount it with fstab?

---

### Post by jhetrick62 on 2008-02-24
Good!  CIFS works pretty well with most file systems as it stands for Common Internet File Systems.

I would change the line in fstab to:
//192.168.1.138/floyd /media/remote cifs  rw,username=rabid9797,password=*****,auto  0 0

Add auto if you want it to auto mount.  If not, use noauto.

Jeff

---

### Post by rabid9797 on 2008-02-25
thanks,it worked flawlessly. you are my hero! :)

---

