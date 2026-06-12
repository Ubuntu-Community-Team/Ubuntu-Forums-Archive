---
title: "Backup to ftp"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by rucker222 on 2011-06-07
Hi,

I am quite new to Linux and am running Ubuntu 10.10 Maverick Meerkat and recently managed to mistype [PHP]rm -rf[/PHP] while trying to delete some folders Leaving me no other option than to do a complete reinstall.  

Long story short I lost years of pictures & Documents etc... as I have never bothered to do a backup.  

Well I have learned the hard way now and plan to never have that happen again so I went out at the weekend and picked up an external HDD and have plugged it into my home Router.  I have a Netgear EVG2000 wireless router and it allows access the USB Drive via FTP.  

The problem I am having now is that I'm not sure what the best way to backup to it would be.  

Before I realised that I could plug the HDD into & access it via the router I found rsync (I am very impressed with this) and have found the below command does exactly what I want as far as creating backups.

[php]rsync -avb --suffix=\ `date '+%y-%m-%d\%H:%M:%S'` /home/lee/Documents /home/lee/Recovery/[/php]This does a quick check of everything in my documents folder, compares it to the destination folder and then only backs up things that have been modified or added since my last backup with a backup date suffix added to each file.

The problem is that everything I have managed to find on the net tells me that I wont be able to use rsync to backup to my HDD via ftp as I need to have rsync running at the receiving end also.  
I have had a go at backing up with rsync by mounting the HDD with Places > Connect to Server and then set the HDD as the backup destination via .gvfs but get the below errors (though im not even sure if i'm doing things correctly).

[php]lee@lee:~$ rsync -avb --suffix=\ `date '+%y-%m-%d\%H:%M:%S'` /home/lee/Documents /home/lee/.gvfs/ftp\ as\ homehdd\ on\ my.dyndns-home.com/Recovery
sending incremental file list
rsync: mkdir "/home/lee/.gvfs/ftp as homehdd on my.dyndns-home.com/Recovery" failed: Input/output error (5)
rsync error: error in file IO (code 11) at main.c(595) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
[/php]Can anyone tell me if there is actually a way I can get this to work and if so how I can do it. Or if it's not an option then tell me how to use an alternative method?

I have seen mirrordir mentioned on different websites but cant get my head around it and therefore not overly excited about the prospect of using that.  (unless of course someone is able to tell me exactly how create backups just like I have managed to create with rsync)

Any help would be greatly appreciated.

Cheers
 Lee.

---

### Post by lordadi on 2011-06-07
Is there any particular reason you are accessing the drive from the WAN? Why don't you use the internal IP assigned to your target?

---

### Post by rucker222 on 2011-06-07
> **lordadi said:**
> Is there any particular reason you are accessing the drive from the WAN? Why don't you use the internal IP assigned to your target?

I must admit that I had not really thought about it, though that is mainly because I'm not sure if it's possible to access the HDD any way other than via ftp if its plugged into the router. The internal IP would have to be the routers IP hey?  as the HDD itself does not have an IP for me to target...

There is a section where I have had to enter a host name workgroup and ftp port which I assume may have something to do with windows share though I'm not sure again.

If I try to mount as a windows share though I must be doing something wrong because all I get is an error saying failed to retrieve share list from server.

---

### Post by rucker222 on 2011-06-08
Can anyone offer me some help or advise on this one? 

I really want to get it working properly so I don't ever manage to lose everything again. 
Trust me when I say the fiancée was not happy to hear all pictures we had from over the last few years are now lost for ever.

Any help would be greatly appreciated.

Thanks.

---

### Post by lordadi on 2011-06-27
Have you tried this - [http://freshmeat.net/projects/deja-dup](http://freshmeat.net/projects/deja-dup) ?

---

### Post by HermanAB on 2011-06-27
Uhmm... Move the external drive and plug it into the machine that you want to back up, then use rsync the way you intended to.

---

