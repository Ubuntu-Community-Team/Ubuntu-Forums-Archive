---
title: "Basic network drive concepts"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Andy_Dempster on 2010-01-12
I have moved exclusively to Ubuntu 9.04 on my Toshiba Satellite A30-303 and so far all is running well, having fixed graphics issues and even the ACPI problem thanks to excellent guides on here I am stumped when it comes to network drives.

I have a Freecom Network Drive with the usual share of PUBLIC under which I have folders for Music, Video, Photos etc. I can see it, mount it, even set up a bookmark and have even imported the music library into Rhythmbox but I cannot see the bookmarks in other applications like EasyTag or VLC or RawTherapee.

I have looked at Samba (SMB) mount points and editing the fstab but I would like to understand it more fully before I dive in! While I am happy with shell commands I am frustrated that this is not more obvious in the GUI! I saw a forum post a while back that showed you how to set the Workgroup name without editing the SMB config but stupidly did not bookmark it!

Any help gratefully received!

Andy

---

### Post by ikt on 2010-01-13
> **Andy_Dempster said:**
> I have a Freecom Network Drive with the usual share of PUBLIC under which I have folders for Music, Video, Photos etc. I can see it, mount it, even set up a bookmark and have even imported the music library into Rhythmbox but I cannot see the bookmarks in other applications like EasyTag or VLC or RawTherapee.

I'm sure someone knows the answer, I'm thinking it has to do with those programs specifically using samba.

> I have looked at Samba (SMB) mount points and editing the fstab but I would like to understand it more fully before I dive in! While I am happy with shell commands I am frustrated that this is not more obvious in the GUI! I saw a forum post a while back that showed you how to set the Workgroup name without editing the SMB config but stupidly did not bookmark it!

There is a gui option for editing the fstab, but it's fairly easy, as a starting point:

[http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/)

---

### Post by Morbius1 on 2010-01-13
> I have a Freecom Network Drive with the usual share of PUBLIC under which I have folders for Music, Video, Photos etc. I can see it, mount it, even set up a bookmark and have even imported the music library into Rhythmbox but I cannot see the bookmarks in other applications like EasyTag or VLC or RawTherapee.Adding an actual mount point in fstab may be your only way out but if you're mounting the desired share in Nautilus there already is a mount point. The problem is it's hidden.

The location of the mount point is in your home directory at:
[B]/home/user_name/.gvfs
[/B]The "." in front of gvfs indicated it's a hidden directory. To see it in Nautilus you need to enable it:

Nautilus > Edit > Preferences > Views > Show hidden and backup files

The problem is some applications can see this hidden directory natively, some will have to be configured to see them, and some will never see them. I don't know enough about your specific applications to know if they can.

I suppose you could create a symbolic link from the hidden directory to a "real" directory but I'm real bad at symbolic links.

Why the nautilus developers decided to create a hidden mount point still puzzles me.

[COLOR=Blue]EDIT: Saw another post about this just now where someone suggested the "symbolic link" approach: [/COLOR]
[http://ubuntuforums.org/showpost.php?p=8658401&postcount=3](http://ubuntuforums.org/showpost.php?p=8658401&postcount=3)

---

### Post by Andy_Dempster on 2010-01-14
Thanks for the info - the user forgot you need to mkdir before symlinking! I will give that a go.

Andy

Edit:

Got it working - helps when the right commands are listed

ln -s /home/*yourname*/.gvfs /home/*yourname*/*yourfoldername*

---

