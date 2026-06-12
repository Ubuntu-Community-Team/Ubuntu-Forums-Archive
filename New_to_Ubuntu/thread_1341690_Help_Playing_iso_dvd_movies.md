---
title: "Help Playing iso dvd movies"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by TheFuzz4 on 2009-11-30
Ok so I'm not a total beginner I've been running Kubuntu for the last 2 years and just recently made the switch over to Ubuntu.  
Typically with the kubuntu I would make an entry in my fstab to map network drives however with Ubuntu under the places menu I am now able to map to my windows shares quite easily, this I like.  So tonight I discovered that I can right click on a iso file and I can use the archive mouter tool to mount the iso for me.  Very nice feature might I add.  However now that I have the iso mounted what is the easiest way to play the files?  The iso is a dvd movie.  Were in the process right now of converting all of our dvd's to digital backups and my wife just wants an easy way to watch them off of the media center that won't require a whole lot of effort.  Is there some other repositories that I need like in Kubuntu in order to watch dvd movies?  Thanks in advance for your help with this and if it's already been asked and beaten into the ground I apologize I just wasn't sure if my method of going about mounting the iso's and what not was the best method.  Thanks.

---

### Post by s3MA00RRNY on 2009-11-30
In theory mounting the isos SHOULD work, it would be best to mount them to a NEW subfolder in /media (if archive mounter doesn't do that). Also, you will need a few extra packages to decrypt the content. At the terminal type...

$ sudo apt-get install libdvdread4
$ sudo /usr/share/doc/libdvdread4/install-css.sh

All done. You should also install xine if you are using Karmic because Totem acts flaky.

$ sudo apt-get install xine-ui

---

