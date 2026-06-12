---
title: "Downloading files directly to my file server"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by jm8254og on 2008-07-02
Hey I guess this is the best place to post this.  I just finished setting up my file server.  It is running Ubuntu 8.04 and it works fine.  The whole idea behind having it was to have a central computer to download music, iso, and just other files I don't want to always have locally.  Of course you can't select the file server from the browsers in the applications I am using (amarok, frostwire, ect) so am I doing something wrong?  I tried to manually type the path to the server and folder in the options under frostwire but it just created a folder 

/usr/lib/frostwire/smb:/server1/music/Joey
I have no idea in amarok what to do

So is there a good solution to be able to effectively do this?  I mean I could download the files locally and copy them to the server but if I can't configure amarok to default the server share as my collection that no fun.
Any help would be much appreciated.  If nothing else it was a fun project.

I am using Kubuntu 8.04 on my desktop and Ubuntu 8.04 (desktop not server) on my server.

Thanks

---

### Post by coolaj86 on 2008-07-02
Use the Places menu in Gnome and then use the Connect to... applet.

Once you mount your share it will be in ~/.gvfs/PATH_TO_SERVER/PATH_TO_SHARE/

You can then access it from any application just as if it were local and without having to mount anything as root.


Is that what you're looking for?


[edit]
Oops, didn't notice that you had said Kubuntu there. I'm supposing that KDE has something like gnome-vfs... if not, well, switch to Gnome! Not that I'm biased but *cough* it's better anyway!!!

---

### Post by jm8254og on 2008-07-02
Thank you for your reply.  You connect to applet on the client side I assume? I am using KDE on my client (Kubuntu) so how do you do that there?  Or do you do connect to applet on the server end?

---

### Post by jm8254og on 2008-07-02
OK so thats where that whole mounting shares comes into play I see.  I guess it like mapping a network drive.  I saw some tutorials but I am still confused.  My server is named server1 my share is music and I don't have any password protection on it so what would the mount -t smbfs command parameters be?  Also is there a GUI way of doing this?

---

### Post by jm8254og on 2008-07-02
well i searched a lot and kept trying but no luck I got the options menu in mount -t smbfs.  I have a computer named server1 with a shared folder named music.  It has a static IP so I could enter that as well.  Is there a good break down on what I need to enter as smbfs parameters?  would it be 

mount -t smbfs //server1/music -o (this does not work for me)

Whats missing? 

I don't have password protection. Well anyways I am just happy to see my server on the network and I got remote desktop working I just hope this last step can happen for me.

---

### Post by coolaj86 on 2008-07-03
Sorry, I'm not that familiar with KDE, but KDE's version of gnome-vfs is called KIO and FISH. You should have some sort of "Connect to Server" menu somewhere I suppose.


I'll try to ask someone who uses KDE or maybe open up KDE at school (I think both are installed).

As far as samba goes, just do a few searches for 'smbmount' or 'samba examples'
```
sudo smbmount //server/share /localdir -o username=user,password=pass
```

I hope that helps. Remember CaPS MAttEr.

---

### Post by Iowan on 2008-07-03
Try mounting via CIFS. More info [here.]("http://ubuntuforums.org/showthread.php?t=288534")

---

### Post by jm8254og on 2008-07-03
I finally got it!  I used this [site]("http://ubuntuforums.org/showthread.php?t=288534"). It work really well.  Thanks for responding you both were a big help.

---

