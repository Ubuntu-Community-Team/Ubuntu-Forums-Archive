---
title: "Can I Bring a Karmic 32 bit /home to Lucid 64 bit /home on fresh install?"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by mikodo on 2010-03-28
Hello everyone,

I intend to do a fresh install with Lucid to a first time 64 bit OS. My present Karmic 32 bit install has my /home on its' own dedicated partition. When it comes to installing from a live CD of Lucid 64, can I use the manual installer to point to my Karmic /home partition to bring the data on that partition to the Lucid 64 bit /home? I am mostly wanting my emails, firefox bookmarks, desktop links and icons, and my documents. I am guessing there may be a little trouble with the firefox bookmarks, because of previous posters' trouble with firefox and 64 bit OS's; and Lucid going to the browsers Yahoo or Google Chrome as default.

Maybe it would be best to have my Karmic /home on an external drive and try to just copy it over to a new dedicated Lucid 64 bit /home partition with an all new partitioning set up for Lucid. I dunno? 

My reason to use Lucid 64 bit is that with Karmic 32 bit with VirtualBox PUEL installed, only allows for 1 of my 4 quad processors to be dedicated to the Windows 7 Ultimate 64 bit I have running in it, and I believe the Lucid 64 bit would allow for more than just one processor being dedicated to it. I am thinking of increasing my ram from 4 gig to 8 gig, along with adding a second HD to run my VM's in.

Anyways, any advice on how I can bring my Karmic 32 bit /home to a clean install (not dist upgrade install), of Lucid 64 bit, would be helpful.

Thank you.

---

### Post by oldos2er on 2010-03-28
> **mikodo said:**
> I intend to do a fresh install with Lucid to a first time 64 bit OS. My present Karmic 32 bit install has my /home on its' own dedicated partition. When it comes to installing from a live CD of Lucid 64, can I use the manual installer to point to my Karmic /home partition to bring the data on that partition to the Lucid 64 bit /home? 

When you install Lucid, set your current /home partition as the new /home, and make sure 'format' is *not* checked.

---

### Post by mikodo on 2010-03-28
> **oldos2er said:**
> When you install Lucid, set your current /home partition as the new /home, and make sure 'format' is *not* checked.

Thanks for the reply. So it will be the same as installing this way from a 32 bit to another 32 bit then. Great! I've done that before...

Thanks.

---

### Post by theozzlives on 2010-03-28
The data and settings aren't what depends on 32 or 64 bit. It's the programs themselves.

---

### Post by mikodo on 2010-03-28
Say Ann, probably I will set up a whole new partitioning schemata; so to bring the data to my new /home partition in Lucid 64, will I be able to copy the the Karmic 32 bit /home data from an external USB HD, to the new Lucid /home partition, when I am ready? Will there be no conflicts that way either?

Presently my one HD is using an EXT3 system with Hardy and an extended partition from there, and I want it all to be Ext4 in Lucid; hence the new schemata.

Mike

---

### Post by mikodo on 2010-03-28
> **theozzlives said:**
> The data and settings aren't what depends on 32 or 64 bit. It's the programs themselves.

Oops;  That might be interesting then. I don't know what to expect. Will most previously used 32 bit apps be able to be run on a 64 bit system? Are there known difficulties, that I should watch out for then?

Mike

---

### Post by oldfred on 2010-03-28
I converted from Jaunty 32 to karmic 64. I did the move /home in jaunty per psychocats instructions and then mounted it in karmic without any issues. I also moved all my data out of home into a /data partition so I could use the data in different systems without any issues. I would not recommend trying to share a /home or going back and forth with old versions and new versions of software.

---

### Post by mikodo on 2010-03-28
> **oldfred said:**
> I converted from Jaunty 32 to karmic 64. I did the move /home in jaunty per psychocats instructions and then mounted it in karmic without any issues. I also moved all my data out of home into a /data partition so I could use the data in different systems without any issues. I would not recommend trying to share a /home or going back and forth with old versions and new versions of software.

Thank you, good to know that you were able to bring 32 bit /home forward to a 64 bit /home. I would like to move all my data also, to a /data partition. I have seen posters speak of this before. Is there a link for a guide that you can post, for me to read and understand how this is done?

I am assuming this means to mount the /data partitions some where under / and then move the data there. Right?

Thank you.

---

### Post by mikodo on 2010-03-28
Hey oldfred; I found this thread that you gave some links about partitioning and making of /data partitions. I'll start with these!


[http://ubuntuforums.org/showthread.php?t=1419072](http://ubuntuforums.org/showthread.php?t=1419072)

Thanks.

---

### Post by asmoore82 on 2010-03-28
You're all good to go, documents and other user data are 32bit/64bit agnostic.

I'm currently using a /home partition from 32bit Jaunty with 64bit Lucid Beta.

---

### Post by mikodo on 2010-03-28
> **asmoore82 said:**
> You're all good to go, documents and other user data are 32bit/64bit agnostic.

I'm currently using a /home partition from 32bit Jaunty with 64bit Lucid Beta.

Great! That answers my original question. I got a little side tracked with other fun things. I'll mark as solved now.

Thank you.

---

