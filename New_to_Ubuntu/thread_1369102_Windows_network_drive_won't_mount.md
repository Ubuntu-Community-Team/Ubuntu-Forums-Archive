---
title: "Windows network drive won't mount"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by rimshot4 on 2009-12-31
Okay, so I'm totally new to Ubuntu, as of this week. So far I really like it. 

Except. I can't get my Windows network to function. I installed Ubuntu twice, the second time because I screwed up the first installation by installing sub-grade software. The first time I was able to see my Windows drive, and use it, "out of the box." This time no luck. So I installed Samba, and have used multiple "how to" guides to tweak the settings. Still no luck. I can see the "Windows Network" and can see "Home", but "Home" (which is the name of my network, not my Windows computer) won't "Mount". 

I'm using Ubuntu 9.10 and Windows XP. I only have the two computers. The Windows network worked fine when I had both computers on XP.

Any ideas?

---

### Post by rimshot4 on 2009-12-31
To be more specific, it says: "Unable to mount location. Failed to obtain share list from server."

---

### Post by darkeye123 on 2009-12-31
Do you have smbfs installed?
```
sudo apt-get install smbfs
```

If so, make a directory in /mnt/
```
sudo mkdir /mnt/samba
```

Mount the share:

```
sudo mount -t smbfs -o username=user,password=pass //networkaddress/share /mnt/samba
```

Where user and pass are the username and password you need to login, network address is the IP address of the computer with the share, and share is the share name.

If successful, your share will be mounted on /mnt/samba, and you can just browse through it that way. 

Hope this helps!

---

### Post by rimshot4 on 2009-12-31
Hey, thanks a lot!

Now another question. My windows PC has a dynamic IP address. Do I have to plug in a static IP (which seems to make it lose connectivity) or is there a way to keep my window's dynamic IP and still connect to it via my ubuntu PC?

---

### Post by darkeye123 on 2009-12-31
Almost all of my computers on my network have a dynamic IP, and this method still works fine, since my IP addresses rarely change. As long as you are within your network, this should work fine, and you don't need it to be static. However, if your addresses change a lot, there may be a way to reserve a specific IP address for one of your computers using your router, even if it still uses DHCP.

If you use a dlink router, it is under Setup>Network Settings, and then just add DHCP reservation.

Hope this helps.

---

### Post by cgb on 2009-12-31
You can also use the computer name instead of the IP address when mounting the location.  The computer name will be looked up via DNS and if there has been an IP address change it will be reflected.  

```
sudo mount -t smbfs -o username=user,password=pass //ComputerName/share /mnt/samba
```

---

### Post by rimshot4 on 2010-01-01
Hmm. Still no luck. Now I occasionally get another error message, which tells me that the drive cannot be mounted because it has already been mounted (?), yet I still cannot open the drive.

Is there any place I can find a complete conf file set up for a Windows XP/Ubuntu 9.10? I'd like to check mine against it. I've been doing some tweaking and I'm wondering if I screwed something up before I could get things going.

---

### Post by mapes12 on 2010-01-02
I have 2 boxes. One runing Ubu, the other running XP. I found Samba too complicated to configure. So I used PyNeighborhood instead. This is what works for me:

Go into Control panel in XP and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Next, on the Ubu machine go into Synaptic and install pyNeighborhood. Once installed it will be an application you can select from Applications. Click it. First some tweaks:

PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then "Remove mount point after unmount" = tick
- Then "File Manager" tab - add Nautilus

Then in the left hand pain right click the globe and select "Scan"

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.

If your router is providing DHCP services then you shouldn't need to worry about IP addresses. The MS Sharing configuration will sort that out.

BTW - if you're running Vista or whatever, the above should still help you out but the screens in MS may be different. I don't know because MS are not getting any more money from me. XP is the MS end of line from now on..........

---

### Post by rimshot4 on 2010-01-04
New development. I finally got access to selected shared folders by configuring my smb.conf based on this excellent guide: 

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) 

So now I can access those folders by clicking Places--Connect to Server and then typing in //desktop.ip.address/sharedfolder. It mounts without a hitch, I bookmark it--boom, done. I got my printer to share too, so really, I've achieved my goals.

When I try Places--Network, however, I can see "Windows Network" but now when I click on it, that says "Unable to Mount" (if you're following, that's actually a step backward. I used to be able to see my workgroup.)

Mapes, I'm pondering your suggestion, but at this point I'm inclined to just leave it alone. I've got what I want, I just can't brows Windows Style. Which is fine. I'm getting ready to move my Windows box to dual-boot anyway.

Next Q., this one not important: is there a way to remove "Network" from the Places menu?

Thanks everyone for your help.

---

### Post by gmgj on 2010-01-06
I am trying to create a script to mount a bunch of NTFS windows shared directories for my Karmic Dell 600 laptop when I am at home.  I am able to mount these by going through Places - Network and clicking on them.

I do this

$sudo mkdir /mnt/samba

$ sudo mount -t smbfs -o username=myusername,password=mypassword //mycomputername/my\040music  /mnt/samba

I get this message

mount: wrong fs type, bad option, bad superblock on //powerspec/my040music,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubugj@ubugj-DellD600:~/Documents$ dmesg | tail

[ 2946.888208] smbfs is deprecated and will be removed from the 2.6.27 kernel. Please migrate to cifs
[ 2946.888223] smbfs: mount_data version 1919251317 is not supported

I have probably done something wrong above; but, I think it would be more constructive to try and fix with the new stuff.

How do I move to cifs?

---

