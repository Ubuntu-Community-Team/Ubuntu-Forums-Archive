---
title: "Unable to transfer files using FileZilla"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by nuffy on 2008-10-17
I'm new to Ubuntu and most things Linux .... 
This is my first post here so please be gentle with me.....

I've unsuccessfully tried to transfer some .avi files to my TVIX Media Centre from my pc using FileZilla, I can ping the Media Centre but can't transfer files.... 

I get this error...

Error:	Could not connect to server
Status:	Delaying connection due to previously failed connection attempt...
Status:	Connecting to 192.168.1.110:21...
Status:	Connection established, waiting for welcome message...
Error:	Connection timed out
Error:	Could not connect to server

Any clues on the cause?

---

### Post by pytheas22 on 2008-10-17
It sounds like just some kind of generic connection problem either on your end or on your server's end--it's not specific enough to say.  Are you sure that you're connecting on the right port (you specified 21)?

You could also try using gftp instead of filezilla:
```

sudo apt-get install gftp
```

It may work better.  The other option is to install an ssh server on your Media Center and use scp/rsync to upload files to it.

---

### Post by nuffy on 2008-10-17
Cheers pytheas22!

I installed gtfp as suggested and was able to transfer files from my pc to the media centre.  Woo Hoo!!

BTW the media centre is hooked up through my home wired LAN to my home theatre and I use it to view all sorts of media from my pc, stuff stored locally on it's hdd and FTA TV.....so I am not sure if I should be specifying a particular port or not??  I did have to change the file type to Binary for it to work tho. I changed the settings on FileZilla without success..... bummer!

In anycase I can now transfer files using gftp but curiously I cannot work out how to transfer files btwn directories on the media centre, I can using FileZilla.  So btwn the two apps I can do most things I want to....It would be nice to use either one....

---

### Post by pytheas22 on 2008-10-18
I don't know of a way to move files around the remote server using gftp, unfortunately.  A quick Google search makes it sound like that functionality is not there.  But you could always install an ssh server on the Media Center and log in to it that way to move stuff around, provided you're comfortable with basic command-line stuff.

As for FileZilla, I had a lot of bad luck with its Linux version as well.

There's also of course the command-line ftp client, 'ftp', which would probably be the best one to use if you learn it, although I've never tried it.

---

