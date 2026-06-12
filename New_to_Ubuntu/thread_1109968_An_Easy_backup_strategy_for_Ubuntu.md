---
title: "An Easy backup strategy for Ubuntu"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by nobodysbusiness on 2009-03-29
Over the years, I've tried many different backup solutions, but nothing was ever as simple or convenient as I thought it should be, until now. I've discovered a free service called "Dropbox", and if you don't feel that your current backup strategy gives you enough protection, you might want to check it out.

I wrote a blog post on the service, including a step-by-step guide:
[Protect Your Important Data with Dropbox -- An Easy Backup Solution for Ubuntu]("http://pragmattica.wordpress.com/2009/03/29/protect-your-important-data-with-dropbox/"). I'd appreciate any feedback you might have, particularly with regards to the instructions; are they clear, easy to follow and accurate?.

Thanks everyone!

---

### Post by binbash on 2009-03-29
drop box  is good but it has some serious bugs.And 2gb is not enough if you call that backup

---

### Post by nobodysbusiness on 2009-03-29
What are the serious bugs that it has? I've been using it for a while, and the latest version seems pretty stable and predictable to me.

You're right about the 2 GB though. It's basically enough space to keep important documents that I edit frequently, but definitely not enough to store all of my pictures, music, etc... It is possible to upgrade to 50 GB now, if you're willing to pay.

---

### Post by beercz on 2009-03-29
[http://rsnaphot.org]("http://rsnaphot.org/")

---

### Post by hyper_ch on 2009-03-29
Just get a NAS and make backups over your lan use ssh, rsync, cron and hardlinks... and I even have an old computer at my parents' place to which I also make backups (documents but not videos and music)

---

### Post by nobodysbusiness on 2009-03-29
I definitely think that rsnapshot and the ssh-and-rsync solution would eliminate the 2 GB limit, but they're also harder to set up and potentially cost money (to get the NAS device, or whatever you will store the backups on).

If there's a beginner who doesn't really have a backup solution in place, Dropbox would be a good starting point. It's free, quick to get going, and, although it isn't perfect, it's almost certainly better than no backups at all.

---

### Post by binbash on 2009-03-29
> **nobodysbusiness said:**
> What are the serious bugs that it has? I've been using it for a while, and the latest version seems pretty stable and predictable to me.

You're right about the 2 GB though. It's basically enough space to keep important documents that I edit frequently, but definitely not enough to store all of my pictures, music, etc... It is possible to upgrade to 50 GB now, if you're willing to pay.

gksudo nautilus will give you %60 cpu usage ( with intrepid and jaunty = gnome 2.24 and 2.26)  and after that nautilus crashes

I am using ssh + rsync + my web server's space : )

---

### Post by hyper_ch on 2009-03-29
ssh, rsync, cron, hardlinks --> not difficult to setup... and for the costs...how much is a nas? not much... or a small computer with a harddisk in it for backup... it's worth to know you have backups... my data is more valuable to me than the few bucks I spend for backup equipment.

---

### Post by malfindin on 2009-03-29
Take a look at Remastersys it has about a 5-gig limit (the size of an ISO) but--and this is no lie--it creates a bootable, installable backup of your sys, updates, programs, files and all. Then if you are feeling lucky transfer the ISO to an 8-gig thumb-drive with Unetbootin AND YOU CAN TAKE YOUR SYS WITH YOU ON YOUR KEYCHAIN.

Optionally you can install it to the thumb-drive from the DVD you create with the ISO from Remastersys, synchronize the home directories on your computer and USB device and have a truly portable computer, that live boots on your friends computers.

malfindin

P.S. The USB drive will boot faster than a HD. Isn't Linux wonderful???

---

### Post by nobodysbusiness on 2009-03-30
@binbash: I just gave a shot at running "gksu nautilus" in a terminal. As soon as I did, the CPU did spike for a while, and a second instance of the Dropbox applet popped up. However, both applets seemed to go into a state where they were disconnected from any Dropbox account, ie. the one didn't operate separately from the other. Nautilus itself didn't crash for me, but that is a pretty significant bug. I'll have to keep an eye on that. Hopefully it gets fixed in the next version.

@hyper_ch: I agree that setting up ssh, rsync and cron isn't too hard to set up, for me at least, but I'm pretty knowledgable about Linux. But we're in the "Absolute Beginner" forum, and it would probably take a while for someone who doesn't know anything about the command-line to get up to speed. Now that I think about it, this would be a good project for a newbie to start with, if they wanted to start learning about the command-line and the powerful tools that *nix-like operating systems make available.

@malfindin: Remastersys is pretty neat! In the context of this discussion, I have only one question: is there an automated "watcher" that looks for changes in your personal files and copies them over to the USB drive? That way, as long as your USB drive is plugged in, you could edit a document, save it, and be sure that within a few seconds the file would be backed up on the USB key. You wouldn't even have to think about it; if your hard-drive crashes right before a big deadline, just boot from the USB key and resume working on the file you were using before the crash.

> Isn't Linux wonderful???

You're darn right it is!!! :)

---

### Post by hyper_ch on 2009-03-30
> **nobodysbusiness said:**
> But we're in the "Absolute Beginner" forum, and it would probably take a while for someone who doesn't know anything about the command-line to get up to speed.

If they didn't want to learn anything then they wouldn't have started linux (ok, some maybe forced due to changes in the company but there they will get already setup computers to work on). So I think even if it requires learning and some time it's not inappropriate here.

If you're not prepared to invest some time of learning that OS then you should not have switched to it - IMHO.

---

### Post by MrWES on 2009-03-30
> **hyper_ch said:**
> If they didn't want to learn anything then they wouldn't have started linux (ok, some maybe forced due to changes in the company but there they will get already setup computers to work on). So I think even if it requires learning and some time it's not inappropriate here.

If you're not prepared to invest some time of learning that OS then you should not have switched to it - IMHO.

Running rsync from a cron is NOT that difficult; with a 'few' commands you can have it running, and there are plenty of HOWTO's out there on cron and rsync. Running a server is just that -- command line only, and I believe I've learned more in the last three weeks setting up my server than I have in the last year running the desktop version. I am not an IT professional either. 

1. ```
sudo crontab -e
```

2. Add this line:
```
# Weekly backup of Documents on external drive to /data/backup
30 3 * * 0 rsync -av --delete --progress  /media/external/Documents /data/backup
```
 - edit the paths to fit your needs.
3. Exit the editor
:q for vi and Ctrl + x for nano.

It's that easy!

Bill

---

### Post by tchalvakspam on 2009-03-30
There's a big difference between learning "an OS", e.g. the default collection of apps that come with an OS, and an app.  If an app is hella complicated, then a simpler solution -should- win out.

So, dropbox is a sometimes useful secondary backup location if you do it manually.  Unfortunately, it has a 200MB limit on uploads, so that's a major downfall when we're talking about backing up information.  If you create a giant file (e.g. a zipped backup), chances are that that file -needs- to be backed up, but it will be ignored by the dropbox system.  So that pretty much takes it out of the running as an automatic backup solution, as far as I'm concerned.

Which makes flash drives still pretty much the cheapest and easiest solution, though not necessarily the most automatic.

---

### Post by malfindin on 2009-03-30
@nobodysbusiness I love your way of responding to particular posters and will use it from now on.

No it does not sync without additional software. However!!! Once you have used Remastersys once it gives you the ability to install TO thumb-drive and it is possible to mirror folders in your  home directory on both your PC and USB Drive in real-time. This gives you essentially a RAID 1 computer that can be split-up (at will), one stays home and the other travels with you to be live-booted to, or installed on other peoples systems. The mind boggles.

I have a beta-test of this up a running (too cool for words), but only in Kubuntu 8.04. My reason for 8.04 KDE--you get desktop effects and multiple wallpapers on multiple desktops even when live booting and no video drivers enabled. I have not yet tested it with my Normal Ubuntu 8.10 sys and will be sure and keep you all posted as to my success (if you want me to).

There is far too much to tell about Remastersys in this thread. It's touchy, but when it works you keep waking up in the morning and thinking to yourself, "that must have been a dream". Then you plug your keychain USB-drive into an old sys (other than the one you backed-up on--with no hard-drive in it) and 1 min later you have a perfectly usable sys with all your programs, updates and even desktops themes on and then you realise--it wasn't a dream, Windows is just that lame. 

Tomorrow I will start a new thread and invite all you folks and we can knock it around a bit. This is only my 6th thread hope my info was helpful. I don't know much about the programs you are using.

sincerely,


malfindin

---

### Post by malfindin on 2009-03-30
Confused my threads sorry.

---

### Post by MrWES on 2009-03-30
> **malfindin said:**
> Confused my threads sorry.


Heheh...you had us all confused!:lolflag::lolflag:

---

### Post by MedianMajik on 2009-03-30
I'm using Dropbox to backup my documents, firefox profiles/add-ons, and personal data.  You can use Truecrypt to encrypt your data within dropbox.  I'm planning on putting a couple virtual distros such as DSL into dropbox for use on various computers (I read on another forum it works with VM and Virtualbox).

---

### Post by nobodysbusiness on 2009-03-31
@hyper_ch: I'm somewhat conflicted about insisting that new Linux users being required to invest time in learning the command-line. On one hand, yes, users should know more about their computers. Even Windows users usually haven't invested enough time in knowing how to run their Windows boxes, thus leading to the botnet problem being worse than it would otherwise be (yes, I realize that Windows is just plain less secure, but I think the problem is made worse by many users not even knowing that there are things called "security updates" that should be installed). On the other hand, I've been helping to teach some computers to my mother for a while, and she just recently learned the amazing skill of *resizing windows*. If she had to learn the command-line to use her computer, then computers would be essentially off-limits. I like Dropbox because it can provide a backup strategy for someone who's not just new to Linux, but new to computers in general.

@MrWES: You make it look so easy. :)
A little more setup along those lines and it would be possible to do, say, hourly backups to a remote machine using a mounted NFS folder. That would be pretty much equivalent to Dropbox.

@tchalvakspam: I did a bit of looking around, and I don't think that the limit is 200 MB. From Wikipedia:
> There is no limit to file size for files added via the Dropbox application, but files transferred through the web interface are capped at 350 MB.

@malfindin: I didn't actually invent this way of replying; I just saw someone else do it and thought it was a good idea. I'll be watching your other thread on remastersys.

@MedianMajik: I also like Truecrypt. I'm thinking of writing a follow-up blog post about using it together with Dropbox.

---

### Post by hyper_ch on 2009-03-31
learning cli is not more difficult than learning how to resize windows partition.

---

### Post by MrWES on 2009-03-31
> **nobodysbusiness said:**
> 
@MrWES: You make it look so easy. :)
A little more setup along those lines and it would be possible to do, say, hourly backups to a remote machine using a mounted NFS folder. That would be pretty much equivalent to Dropbox.



It is :D -- setting up a backup cron is no more than entering one command to get into the crontab and one line of text to enter the back information. Why recommend an outside solution to backing up, when it already resides in the OS? Depending on how much data were talking about here; you could back up to a thumb drive.

I'm done...

Bill

---

### Post by nobodysbusiness on 2009-03-31
@hyper_ch: Oh, I actually didn't mean resizing a Windows partition. I meant resizing a singe application window. As in, moving the mouse to the corner of the window, clicking and dragging it to make it larger. :)

---

