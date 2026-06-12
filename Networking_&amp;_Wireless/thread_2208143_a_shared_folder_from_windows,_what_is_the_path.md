---
title: "a shared folder from windows, what is the path?"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2014-02-26
smb://lr-pc/users/Public/ is the smb folder location.

'Recorded Tv' is the folder

I tried that in mythtv, but it said path did not exist.

Any ideas?

---

### Post by bab1 on 2014-02-26
> **sdowney717 said:**
> smb://lr-pc/users/Public/ is the smb folder location.

'Recorded Tv' is the folder

I tried that in mythtv, but it said path did not exist.

Any ideas?

Samba shares are always located by this:  //SERVERNAME/share_name

An example of this might help.  If I create a share named FORD on a Samba server named CARS  you would locate that share with this in Nautilus: *smb://cars/ford*.  

If the share mount point was /srv/cars/ford on the local host.  That would also make the local path *[FONT=Courier New]/srv/cars/ford[/FONT]*.  But this is not a "share path"

Mythtv is right in your case.  Maybe the NETBIOS resource (the share) can be located with //lr-pc/Public/

---

### Post by Rsxhawk on 2014-02-27
It should be able to use netbios but my experience is that Linux won't find the windows computer name on the network that way.  Not unless you edit your host file and add an entry with its name-to-ip mapping.  Try using the remote computers IP address instead of the name in the file path.  //ipaddress/sharename

Just a suggestion.

---

