---
title: "help home server advice for media share"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by swoskow on 2007-08-17
I have read a lot of the posts on the forum and their are many options for sharing music and video over a network on Ubuntu.  Great - because that is why I switched from Windows (I now only keep Windows for work).  The problem (a good problem) is their are so many choices I am not sure the best way to go.  I have Azurues set up using ASZMRC as a server and client so I can share bittorrent over my network and it is working great.  Now I am ready to tackle the sharing files, playing music and video over the network and wanted some advice on the best options (notice the "s" - I know their is no one "best way to do it).

Some background:
- I have 2 desktops (both running Ubuntu), 
- 3 laptops 
        -One with Windows (though I do use Ubuntu on a usb drive with this box), 
         -1 older laptop with Ubuntu 
        - 1 Mac for the wife (though she actually finds Ubuntu easier to use - please no flamewars it is her personal opinion).

All Ubuntu boxes are using Fiesty.

I use Azureus, Amarok, xmms, K3b and gtkpod, exfalso, SoundKonverter to do all the various handling of my music needs.  Most of the music is stored in files and I have a lot in shn and flac format. For storing on the ipod I convert these to m4a.  I  use smplayer with VLC as a backup for video (I play most of my video from VOB files - some DVD's)

I have been using Samba for file sharing though it appears this is not the best way to do it.  Others on the forum have mentioned NFS as a better way.

I have one desktop set up as a NAS with 2 x RAID 5 devices (1 device - has 4x750 gb SATA drives the other 3x500 gb external drives) so I have plenty of storage for now.  I also have a LAMP server on this box.  I would like to use this box as my main server.

So (finally) the question is what are the best options for:
File sharing
Streaming music and video over the network
Accessing the other programs - k3b, gtkpod, soundkonverter.  Note k3b and soundkonverter are accessible through Amarok.

I realize this is a long post and the answers may be long but I think a lot of people want to use Ubuntu just as I am and though this info is in the forums, it would be nice to have it consolidated so new users can understand their options.  I also don't need all the detail on how to set these up I just want to know what the best options are.

Please note - I have only been using Ubuntu for about 6 months and I have set up all of the above through reading the forums, how to's, guides etc so please understand I am not just being lazy here.

Thanks so much and I look forward to reading everyones advice.

---

### Post by samuraix51 on 2007-08-17
> **swoskow said:**
> 

I have been using Samba for file sharing though it appears this is not the best way to do it.  Others on the forum have mentioned NFS as a better way.


What's wrong with samba sharing?  I've been using it for years on my media server and have not had a problem at all.  Just configure it and samba mount the drives to the machine you want it on and use it.
Mount them using CIFS as a file system, if you're going to be copying large files(>2GB) to them.

Just my thouhts

---

### Post by swoskow on 2007-08-17
I have been using Samba also and have had no problems.  I have read that their may be faster methods for sharing large files (like large video or audio).  I noticed a number of posts on the forum that recommend NFS so I wanted to get others opinion if there is something that may be better than Samba.

---

