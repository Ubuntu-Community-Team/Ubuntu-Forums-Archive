---
title: "Need help Transferring files from Vista to Ubuntu"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Volume on 2009-08-04
Hey guys,

I'm trying to access some files on my Windows Vista machine to save them before I nuke it for good.  I know that I can use Samba, but I can't seem to find a good Howto that I can follow.  Essentially, I have 2 Ubuntu machines and a Vista machine sharing a common router, and I have already figured out how to share files on the Linux side.

Can anyone point me in the right direction for how to get started using Samba?  What I want to do is browse through the 4 HDs on my Windows box and take the files I want.

Thank you

Steve

---

### Post by PureLoneWolf on 2009-08-04
Presuming you have Gnome and therefore Nautilus..

Load Nautilus.
Choose File then Connect to Server
Change Service type to Windows Share
In the Server box, put the name of the Vista machine (or IP address) without any \\

Press connect

You will probably be prompted for your vista username/password 

Nautilus should then show you all available shares on the Vista machine.

Hope that helps

---

### Post by Volume on 2009-08-04
Hmmm. You presume too much!  I am not sure what Nautilus is!

Also, once I have installed it, how do I run it?

---

### Post by lisati on 2009-08-04
> **Volume said:**
> Hmmm. You presume too much!  I am not sure what Nautilus is!

Also, once I have installed it, how do I run it?

Short answer: Nautilus is the file browser that gets called up when you do something like click on "places->Network", roughly equivalent to Windows Explorer.

Note: at the Vista end, you *might* need to put the files in your "public" folder and/or tinker with Vista's sharing settings.

---

### Post by darkknight85 on 2009-08-04
Well if you can see the Windows machine from the linux one and vice verse then you can just left click on what you want then chose copy. Tada  that should be it. A friend needed to burn a CD using my burner so I found his computer and the file he needed burned and then burned it I had Ubuntu 9.04 he was using Windows XP Home Edition.

---

### Post by Volume on 2009-08-04
Ok, I'm able to see the Windows machine, however, when I try to connect, it says that it was not able to resolve the shares list.  How do I go about allowing Linux to access the files I need on my windows machine?

Steve

---

### Post by dtrot55 on 2009-08-04
I just ran into an issue getting files off my friends Vista computer and my ubuntu computer...he had to go through a couple settings in Vista to allow connections without the need of a password...I would look into your network connections on the vista machine and make sure you give permissions without the need of a password...or if you do have an account put in the login with the "WORKGROUP Name" and the password.  We were able to do it but it took some messing around on the vista computer to do it..all i had to do on ubuntu was install samba...which you already did...hopefully that helps

---

### Post by Volume on 2009-08-04
I have found that my HDs are shared in Vista, through the computer management window, but still when I try to connect, it tells me that it failed to load the shares list.

Any ideas?

Steve

---

### Post by dtrot55 on 2009-08-04
I'm looking for you...though I did find a forum saying they were having issues with the hard drive being shared but the folders worked....so I'll update if I find something

---

### Post by dtrot55 on 2009-08-04
Check out this link .... hopefully it helps [http://ubuntuforums.org/showthread.php?t=373917](http://ubuntuforums.org/showthread.php?t=373917)

---

### Post by Volume on 2009-08-04
> **dtrot55 said:**
> Check out this link .... hopefully it helps [http://ubuntuforums.org/showthread.php?t=373917](http://ubuntuforums.org/showthread.php?t=373917)

Nice!  Thank you, I am reading furiously, and I will let you know if it works!

Really appreciate it.

---

### Post by dtrot55 on 2009-08-04
I know how frustrating it is to find stuff...plus i'm at work...down time needs to be filled some how :)

---

### Post by magh-87 on 2009-08-04
Give this a shot [HTML]
http://ubuntuforums.org/showthread.php?t=202605[/HTML] it could solve that for you.

---

### Post by Volume on 2009-08-11
> **magh-87 said:**
> Give this a shot [HTML]
http://ubuntuforums.org/showthread.php?t=202605[/HTML] it could solve that for you.

Well, I tried following the howto, but I have some questions.  If you are familiar with the howto, can I ask them here?  That thread has grown to cosmic proportions.

I'm a bit confused as to where I input Windows information (passwords, usernames, etc) as opposed to Linux info.  I got to the step where I am supposed to map the network drive in Windows (using WINS) but it says that the network path cannot be found.

Any suggestions on how to fix this?

Steve

---

### Post by juanoleso on 2009-08-11
if you know how to connect the linux machines, I'd pop in the ubuntu live cd, mount the vista drive, connect the computers and copy the files over.

With M$ licensing, who knows if your copy of vista is even allowed to share folders.

---

### Post by dtrot55 on 2009-08-11
I just found this forum for those who are having sound issues with the 9200...i havent tried it yet since im at work but give it a try ... ill update when i get home:

[https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/51592](https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/51592)

---

### Post by kansasnoob on 2009-08-11
I'd give 'ntfsprogs' a whirl, it's in Synaptic.

[http://www.linux-ntfs.org/doku.php?id=ntfsprogs](http://www.linux-ntfs.org/doku.php?id=ntfsprogs)

---

### Post by Volume on 2009-08-12
> **kansasnoob said:**
> I'd give 'ntfsprogs' a whirl, it's in Synaptic.

[http://www.linux-ntfs.org/doku.php?id=ntfsprogs](http://www.linux-ntfs.org/doku.php?id=ntfsprogs)

Ok, what exactly does this program do?  I will install it and see what I can find...

Very confusing

Thanks

Steve

---

### Post by emeraldgirl08 on 2009-08-12
> if you know how to connect the linux machines, I'd pop in the ubuntu live cd, mount the vista drive, connect the computers and copy the files over.

I'd use the live CD in the Vista machine and use a flash drive, ext. burnable CD/DVD, or use an external HD.

I've recovered stuff from an Xp Pro using this method (with an SD card). Only drawback was some thumbnails wouldn't transfer to the SD card. I think it may have had something to do with permissions.

---

