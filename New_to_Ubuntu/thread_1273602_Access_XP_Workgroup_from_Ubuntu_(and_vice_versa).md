---
title: "Access XP Workgroup from Ubuntu (and vice versa)"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by hnarwan on 2009-09-23
Hi All,

This question i'm sure has been asked a million times, i've even asked it myself but after a fresh Ubuntu install on my laptop i cant get my Ubuntu laptop to access files on any XP computer in my workgroup.

I wanted to figure out a step by step method for doing this (assuming Ubuntu has just been installed) - if this has been documented somewhere i cant find it very easily.

So the basic requirement is to add my ubuntu laptop to my XP workgroup (named workgroup) - i then want to be able to copy files to and from any computer.

Here's what i was hoping would work but didnt:

1. Right click a folder and share - this installs Samba
2. Modify the smb.config file in etc\samba with the workgroup name i want to join:

 #======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

3. sudo smbpasswd -e hardeep

Where 'hardeep' is my username on my Ubuntu laptop. I also give my password when prompted here.

I thought these 3 steps would help me out but although i can see my ubuntu laptop on my xp computer (under 'workgroup') i cant access it - i get a permissions error. 

I also dont see any computer apart from my ubuntu laptop when i go under places\network\windows network\workgroup

Please someone put me out of my misery. This is such a common thing but i dont know why i cant get it to work.

thanks
Hardeeep

---

### Post by lwvmobile on 2009-09-23
I've been though a similar situation before.

[https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html]("https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html")

This can help you a bit, I think.

If you are on a home/private network, you can probably just use the guest=ok option in the smb.conf file.

```
[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

```

But if you want to set it up for a user and not a guest, I think that the user you create on your Ubuntu machine has to either be a member of the samba user group or given precise permission to the share. Its been a while so I can't remember. 

Check this link, it I think will help you with creating samba users with permissions.

[http://samba.netfirms.com/addusers.htm]("http://samba.netfirms.com/addusers.htm")

Hope this helps!

---

### Post by lwvmobile on 2009-09-23
Also, if you need to browse from Ubuntu to the Windows shares, then try opening nautilus, Home will suffice, then type in the address bar smb:\\{computername}\{Sharename}

and see if you get anything.

Also, if you need to supply username and password to get into windows share, this might work:

```
smb://domain-name;username:password@machinename/mountpoint
```

Try that out.

---

### Post by hnarwan on 2009-09-24
Thanks for those suggestions, i seem to be having trouble firing up ALT F2, nothing happens so i cant check.

I've also played around with my smb.config file as suggested but the same problem continues.

I cant believe i havent found a step by step on this yet, i'm sure there is one out there, anybody?

---

### Post by mapes12 on 2009-09-24
If all you need is access from your Ubu box to your windoze box then this is what works for me:

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

BTW - if you're running Vista or whatever the above should still help you out but the screens in MS may be different. I don't know because MS are not getting any more money from me. XP is the MS end of line from now on..........

---

