---
title: "[SOLVED] Strange cifs issues with Intrepid"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by opus1 on 2008-11-28
I have found this issue reported in a couple other locations, but not with the same details I have to report, so I hope this doesn't bother anyone...

This is basically the same bug that is reported here: [https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-October/006643.html]("https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-October/006643.html")

Basically, since I upgraded from Feisty to Intrepid I have had seemingly random permission issues with a samba server when mounted with cifs.  These issues do not exist with a Hardy computer I have that mounts the samba server using the same fstab.

Originally, I had read only access to the server, but using the "nounix" option in my fstab seemed to solve the problem.  (I used the tutorials here: [http://ubuntuforums.org/showthread.php?t=288534&highlight=cifs+-a+directory]("http://ubuntuforums.org/showthread.php?t=288534&highlight=cifs+-a+directory") and [http://www.marcus-furius.com/index.php?s=cifs&sbutt=Go]("http://www.marcus-furius.com/index.php?s=cifs&sbutt=Go")).

Unfortunately, I still have permission issues that are making Intrepid unusable for me.  In a nut shell, write permission seems to be denied on the samba server for *.html files and to Thunderbird files *only* when compacting or filtering (the filtering issue is similar to one reported here: [http://forums.mozillazine.org/viewtopic.php?f=29&t=538847]("http://forums.mozillazine.org/viewtopic.php?f=29&t=538847")).  Additionally, my mnemosyne file seems to be read only. 

I have checked the permissions and ownership of all the files in question, and they are all correct.  Also, the Hardy computer (which I copied the fstab and home directories from) does not have these issues.  I think it is a bug.

If someone knows of a solution, please let me know.  If not I need to figure out how to report a bug.

Here is a copy of my fstab (//192.168.1.9/server at the bottom is the fileserver giving me trouble):
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5f939b60-2953-4dc6-881e-a201831bc622 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=cda0ca6c-bcf3-45aa-b881-349ae670a3be none            swap    sw              0       0
#/dev/hda5       none  swap  sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2
//192.168.1.9/server /misc/share cifs nounix,credentials=/root/.smbcredentials,uid=bob,gid=bob,file_mode=0777,dir_mode=0777 0 0

```

Please let me know if there is any other information I can provide to help debug this.  Like I mentioned, I've seen other similar postings on the net, but not with the same details I have.

I suspect I may have to take Intrepid off and put Hardy on.  I read somewhere that LTS is considered stable and everything else is not.  Is that true?  does that mean that Intrepid is a testing version?

---

### Post by bab1 on 2008-11-28
> I have checked the permissions and ownership of all the files in question, and they are all correct. Also, the Hardy computer (which I copied the fstab and home directories from) does not have these issues. I think it is a bug.

I'm assuming you are using Nautilus to view and manipulate the files.  I wouldn't call it a bug as much as the way Nautilus has been changing.  The latest version of Ubuntu (8.10) uses a different set of libs (gvfs) from  8.04.  Neither 8.xx are the same as 7.10.  Not all applications are aware of this.  OO has a similar "ownership" problem too.

> ...permission seems to be denied on the samba server for *.html files and to Thunderbird files *only* when compacting or filtering... 

Still another example of the above.

> I suspect I may have to take Intrepid off and put Hardy on. I read somewhere that LTS is considered stable and everything else is not. Is that true? does that mean that Intrepid is a testing version?

Unfortunately the Ubuntu 6 month version cycle does not coincide with Gnome or Samba development.  I use 8.04 on my Samba server for this very reason.  Newer does not always mean better.

---

### Post by opus1 on 2008-11-28
Hey thanks for the quick reply bab1!

> I'm assuming you are using Nautilus to view and manipulate the files. 

Well, I think so.  I open *.html files in Kompozer and my wiki I edit in Firefox.  Not knowing a lot about these things, I guess these programs could be using Nautilus to interface with the share??  With Thunderbird, I  answer "Yes" when it asks to compact folders and then I get the permissions message.   I could see how a library change could be causing this strange behavior.

> I wouldn't call it a bug as much as the way Nautilus has been changing.  
The thought had crossed my mind, but I guess reading some other forums about cifs bug reports colored my thinking.

> Unfortunately the Ubuntu 6 month version cycle does not coincide with Gnome or Samba development. I use 8.04 on my Samba server for this very reason. Newer does not always mean better.

Funny, I've been using Ubuntu since 6.06 and I am just now learning this...:oops:  I just haven't had a need to upgrade that often, and when I have, it wasn't the newest version.

So I think the bottom line is to wait it out, or dropping back to Hardy. Since I have /home on a separate partition, changing to Hardy shouldn't be too bad.

---

### Post by bab1 on 2008-11-28
The short answer is to go back to Hardy.  The apps that you are using (Komposer and Firefox) may not use the latest gvfs libs.  Understand this is a Gnome update in there libs.  

Ubuntu just got cought due to their rigid release schedule.  In another 6 months and lots of whining the developers of the apps will revise their code and then we can update.  I will wait until the next LTS.  I too have hosts running "outdated" (but fully functional) OS's.  I say say use what works.  Let someone else be on the bleeding edge.

[COLOR="Blue"]**If I may ask a question of you;** why do you mount your CIFS shares via fstab?[/COLOR] I never do that.  my clients have shares and they are browsed easily.  I have them mapped (bookmarked).  [COLOR="Blue"]**What advantage do you feel you get from hard mounting the shares?**[/COLOR]

---

### Post by opus1 on 2008-11-28
> Understand this is a Gnome update in there libs. 
I understand.  Thanks for explaining it.

I've learned quite a lot this week!

> If I may ask a question of you; why do you mount your CIFS shares via fstab? I never do that. my clients have shares and they are browsed easily. I have them mapped (bookmarked). What advantage do you feel you get from hard mounting the shares?
Well, I am no expert but basically I wanted to find a way to share thunderbird e-mail boxes and firefox bookmarks between 3 computers using a file server.  I set up the server as a samba server because of the pesky windows 2000 computer I have.  I was using smbfs but read that it is going away and have recently switched to cifs.  I have no problem browsing the shares, but I don't know how to set up the firefox and thunderbird configurations without mounting the share.  If there is a better way, I'm always game to learn it!

Thanks for your help and input.

---

### Post by bab1 on 2008-11-28
It seems that everyone has a different take on what to do.  The doc's at Samba.org do not mention hard mounting the shares to a server.

---

### Post by opus1 on 2008-11-30
Well, I removed Intrepid and went to Hardy and all my remote share mounting issues disappeared.  

The lesson I learned here is to stick with the "LTS" releases.

Thanks to BAB1 for explaining the underlying reasons for the mysterious problems.

I supposed this isn't solved for Intrepid, but my problem was solved, so I'll mark it as such.

---

