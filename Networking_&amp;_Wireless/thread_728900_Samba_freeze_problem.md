---
title: "Samba freeze problem"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by pablo.mrg on 2008-03-19
Hi all,

  I'm running Kubuntu Feisty, with some Samba shares in my fstab. Shares are not mounted automatically at startup do to a known problem, I mount them with a script once system is up and running.

  Shares are on a NAS, and in fstab are specified as:
```
//192.168.1.3/ingegneria /home/paolo/nas/ingegneria smbfs defaults,username=paolo,password=xxxxxxx,uid=paolo,gid=paolo,dmask=770,fmask=770 0 0
```

  Browsing or copying files with Konqueror happens that it freezes... 

  In that condition, once killed Konqueror, trying to unmont the smb file system come to an error: 
```
umount: /home/paolo/nas/ingegneria: device is busy
```

Trying to check who is engaging the share, no processes show explicit share usage, lsof and fuser commands fail:

```
sudo lsof /home/paolo/nas/ingegneria:
lsof: WARNING: can't stat() smbfs file system /home/paolo/nas/ingegneria
      Output information may be incomplete.
lsof: status error on /home/paolo/nas/ingegneria:: No such file or directory

paolo@picasso:~$ fuser -mv /home/paolo/nas/ingegneria
Cannot stat /home/paolo/nas/ingegneria: Input/output error

```

Trying to connect to NAS from another machine shows no problem.

Just waiting about 5 minutes, the problem fixes by itself... 

Any idea on how to avoid the problem or fix it once occurred withoit waiting that long delay?

---

### Post by Eiríkr on 2008-03-19
Not sure what Ubuntu version you've got, but the old [font=courier]smbfs[/font] filesystem type was deprecated for a while and has finally been phased out a bit ago.  You must use the [font=courier]cifs[/font] type now, which sometimes requires an IP address instead of hostname for the mount command (no problem for you since that's already what you're using). 

Try switching that out in your fstab and see if that doesn' work better for you.

Cheers,

Eiríkr

---

### Post by pablo.mrg on 2008-03-19
Thank you Eiríkr, i didn't know smbfs was deprecated...

I'll try cifs!

Bye,

Paolo

---

