---
title: "How do I Auto Mount SMB Share at Startup on Wireless?"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by Eddy5 on 2008-02-16
I have a samba share that I want to auto-mount on startup of Xubuntu.
I've added the entries into the fstab e.g. (Real names swapped for generic names here)
//serverip/share /mnt/lan/localshare smbfs credentials=/home/username/.smbcredentials,fmask=0777,dmask=0777 0 0

These commands are correct as when Xubuntu has started 'sudo mount -a' works fine.
I'm pretty sure it's because fstab is running before the PC has connected to my network via the wireless connection.

So my question is what do I need to do to get it to connect to my smb shares after it has connected to the network?
Any help would be very much appreciated.
Thanks

---

### Post by winter7 on 2008-02-22
I'm trying to do the same thing... Have you had any luck?
I can get it to work fine in any number of ways if using the wired connection, but no joy from the wireless.

-Dino

---

### Post by Eddy5 on 2008-02-22
No, nothing yet. There must be a way of doing this. Anyone?

---

### Post by winter7 on 2008-02-25
I found this post:
[http://ubuntuforums.org/showthread.php?t=451976](http://ubuntuforums.org/showthread.php?t=451976)

Basically it says you have to set up a static ip and fstab should work.

I can't try it right now, but I will when I get home. 

Hope this helps
-Dino

---

### Post by Eddy5 on 2008-02-25
I already have a fixed IP address, so that's not it.
Thanks for the reply though.

---

### Post by Eddy5 on 2008-02-28
I'm using WICD for my wireless as I couldn't get a fixed IP address into the standard Xubuntu config. Anyway I've noticed there's the option to run a script after connection in WICD, so when I get 5 mins I'll give that a try and see if it helps.

---

### Post by Linder on 2008-02-28
I had the same problem with my external drive not mounting. Not sure if fstab was run before the USB driver started or something.

I solved it by adding the mount command to the /etc/rc.local script, which is run just before X starts. Try that.

---

### Post by Eddy5 on 2008-02-28
SUCCESS :guitar:

I added this line into rc.local
sudo mount -t smbfs //smbsharepath /localpath -o credentials=/home/username/.smbcredentials,fmask=0777,dmask=0777
worked a treat

---

### Post by bsharitt on 2008-03-02
That's odd, I tried the same thing, but still nothing. I know the mount command works, because copied and pasted it exactly, so the server is there, but I guess it could be taking a while to connect to my wireless. I am also using wicd. Maybe DHCP is taking a long time I would be better off with a quicker static ip.

Actually it looks like the static IP thing didn't work.

---

### Post by Eddy5 on 2008-03-02
Yeah go for a static IP, that's what I'm using.

---

### Post by jocojo on 2008-03-24
Adding the mount-command to /etc/rc.local didn't solve the problem for me. Apparently Wicd is run at the end of the boot-process. To give the DHCP-client a little extratime i changed /etc/rc.local to look like this:
 ```
#!/bin/sh -e
sleep 30
mount /mymountpoint
exit 0
```
All the info mount needs is set in my fstab as described in the other posts.
Work's fine on my system.

---

### Post by Eiríkr on 2008-03-25
> **Eddy5 said:**
> I have a samba share that I want to auto-mount on startup of Xubuntu.
I've added the entries into the fstab e.g. (Real names swapped for generic names here)
```
//serverip/share /mnt/lan/localshare smbfs credentials=/home/username/.smbcredentials,fmask=0777,dmask=0777 0 0
```

You're missing the [font=courier]auto[/font] option.  Without this, I don't think any Samba fstab entry will mount automatically.  Also, you need to replace [font=courier]smbfs[/font] with [font=courier]cifs[/font].  The [font=courier]smbfs[/font] type has been deprecated for a while, and no longer works in Samba v3.026.  

Making these changes, your line should look like this:

```
//serverip/share /mnt/lan/localshare cifs auto,credentials=/home/username/.smbcredentials,fmask=0777,dmask=0777 0 0
```

After making these two changes, do you have any better success?

Cheers,

Eiríkr

---

