---
title: "mount network attached storage drive in kubuntu"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by GrantShoe on 2007-11-11
I have a Buffalo Link Station Network Attached Storage Drive.  I store my music, videos, and any documents that I have on it.  with kubuntu 7.10, I can now browse the network and just play the files in amarok no problems (in the past this was hell...) but I want to set this up as a collection in Amarok and do a few other things with the drive.  To do this, I have to do more than just browse the network for it and read the samba share.  I have to mount the drive.  I'm having a HELL of a time trying to figure this out.  Can anyone help me out?

a couple things 
- this isn't the normal winNT mount because there's no name/pw for it.
- I alway prefer the GUI way but I have a feeling I'll have to jump back into my good friend fstab
- My computer and the NAS connect to the router through DHCP so I guess there's the possibility that the IP addresses may change.

any help would be greatly appreciated!

---

### Post by Peter09 on 2007-11-12
I have a buffalo nas drive.my way is to mount through fstab. Due to problems with DHCP I have to mount by IP address. Once mounted then its easy enough to access.

---

### Post by abubin on 2007-11-12
i have a d-link nas but cannot mount through fstab. I had to add the mounting command in rc.local for it to mount during bootup.

---

### Post by Peter09 on 2007-11-12
Here is my mount command from fstab. Note that I had to use cifs because I could not get samba to mount it reliably. That was in Fiesty, 


//192.168.0.8/nas1share		/mnt/nas1/nas1share	cifs	rw,defaults,errors=remount-rw

Also try using the 'places' menu top left. Select 'Connect to Server',
Then field options: 

drop down menu -> Windows Share
Server -> IP address
Share -> Share name

Does this work?

---

