---
title: "if its so common how come theres no solution?"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by linux000019 on 2009-05-25
im having the same exact problem these guys are having, in xubuntu 9.04, and also a error popping up saying "input/output error when trying to write"

_______possible solution?____ im using a 8GB; so how big should i make the sizes?_________

::::quote from thread:::::::

fdisk is used to create partitions. Press 'n' to create new partitions, then simply follow the prompts. I greated a 1 GB on /dev/sda1, another 1 GB on /dev/sda2, and gave the rest of the space (~1.6 TB in my case) to /dev/sda3.

Next I had to use mkfs to make the file systems.  I chose ext3:

$ sudo mkfs -t ext3 /dev/sda1
$ sudo mkfs -t ext3 /dev/sda3

I then used mkswap to make the second partition a swap partition:

$ sudo mkswap /dev/sda2

Finally I ran the installer, and chose "manually partition" when I came to the appropriate window. Ubuntu's partitioner saw my partitions, and allowed me to assign /boot to /dev/sda1, swap to /dev/sda2, and / to /dev/sda3.





                   BZRK                   [View Public Profile]("http://ubuntuforums.org/member.php?u=7366")                   [Send a private message to BZRK]("http://ubuntuforums.org/private.php?do=newpm&u=7366")                   [Send email to BZRK]("http://ubuntuforums.org/sendmessage.php?do=mailmember&u=7366")                        [Find More Posts by BZRK]("http://ubuntuforums.org/search.php?do=finduser&u=7366")               [Add BZRK to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=7366")                
                                                            [CENTER]     [LEFT]         [LEFT]                                                                                        [IMG]http://ubuntuforums.org/images/statusicon/post_old.gif[/IMG]             October 11th, 2006                                                                       #[**2**]("http://ubuntuforums.org/showpost.php?p=1607301&postcount=2")                                                                                  [newmonkey]("http://ubuntuforums.org/member.php?u=178279")                                               
              First Cup of Ubuntu
             
                                                           
                Join Date: Oct 2006
                                                             Beans: 6                 
                                                                                                        
             
                                                                                                   **Re: Stuck on 'detecting file systems'**             
                                                                I'm actually having a very similar problem, the only difference being that it hangs at 15% instead of 75%.

Now here's the weird thing--it's not freezing. I can move the mouse, click elsewhere. I even see the CD-ROM light glow every few moments. Any thoughts?

I'm installing on a Compaq Presario M2105US laptop. 256MB Ram, 40 gig hard drive. AMD Sempron 1.4 GHz, I believe.

I'd really appreciate any feedback or thoughts about how to get around this. I have experience with Red Hat/Fedora and Gentoo but I am new to Ubuntu.

Many thanks in advance,
Robby
                                                                                                            newmonkey                   [View Public Profile]("http://ubuntuforums.org/member.php?u=178279")                   [Send a private message to newmonkey]("http://ubuntuforums.org/private.php?do=newpm&u=178279")                             [Find More Posts by newmonkey]("http://ubuntuforums.org/search.php?do=finduser&u=178279")               [Add newmonkey to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=178279")                
      
    
   
     
         
              [/LEFT]
     [/LEFT]
 [/CENTER]
             [CENTER]     [LEFT]         [LEFT]                                             
                    newmonkey                   [View Public Profile]("http://ubuntuforums.org/member.php?u=178279")                   [Send a private message to newmonkey]("http://ubuntuforums.org/private.php?do=newpm&u=178279")                             [Find More Posts by newmonkey]("http://ubuntuforums.org/search.php?do=finduser&u=178279")               [Add newmonkey to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=178279")                
      
    
   
     
         
              [/LEFT]
     [/LEFT]
 [/CENTER]
             [CENTER]     [LEFT]         [LEFT]                                             
                    newmonkey                   [View Public Profile]("http://ubuntuforums.org/member.php?u=178279")                   [Send a private message to newmonkey]("http://ubuntuforums.org/private.php?do=newpm&u=178279")                             [Find More Posts by newmonkey]("http://ubuntuforums.org/search.php?do=finduser&u=178279")               [Add newmonkey to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=178279")                
      
    
   
     
         
              [/LEFT]
     [/LEFT]
 [/CENTER]
             [CENTER]     [LEFT]         [LEFT]                                                                                        [IMG]http://ubuntuforums.org/images/statusicon/post_old.gif[/IMG]             October 13th, 2006                                                                       #[**5**]("http://ubuntuforums.org/showpost.php?p=1614142&postcount=5")                                                                                  [mpeppers]("http://ubuntuforums.org/member.php?u=179011")                                               
              First Cup of Ubuntu
             
                                                           
                Join Date: Oct 2006
                                                             Beans: 3                 
                                                                                                        
             
                                                                                                   **Re: Stuck on 'detecting file systems'**             
                                                                I just ran into this problem today, same as newmonkey's problem. Thanks for the tip newmonkey, but it didn't work for me. I'm still stuck at 15% "Detecting file systems..."

Anyone have any ideas? I'm trying to install on top of a hardware SCSI RAID 5 array of 8 250-GB hard drives (so 1.7 TB usable). I choose to format the whole 1.7 TB, and the installer first gives an "Error: no root directory" or something like that, then continues to 15%, and hangs.
                                                                                                  [IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]                             [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=1614142")                                                                                         [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=1614142")                               [[IMG]http://ubuntuforums.org/images/buttons/multiquote_off.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=1614142")                                                                                                                            mpeppers                   [View Public Profile]("http://ubuntuforums.org/member.php?u=179011")                   [Send a private message to mpeppers]("http://ubuntuforums.org/private.php?do=newpm&u=179011")                             [Find More Posts by mpeppers]("http://ubuntuforums.org/search.php?do=finduser&u=179011")               [Add mpeppers to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=179011")                
      
    
   
     
         
              [/LEFT]
     [/LEFT]
 [/CENTER]
                                 [CENTER]     [LEFT]         [LEFT]                                                                                        [IMG]http://ubuntuforums.org/images/statusicon/post_old.gif[/IMG]             July 31st, 2007                                                                       #[**8**]("http://ubuntuforums.org/showpost.php?p=3109882&postcount=8")                                                                                  [paris-unmatch]("http://ubuntuforums.org/member.php?u=328219")                                               
              5 Cups of Ubuntu
             
                                                           
                Join Date: Jun 2007
                                                             Beans: 37                 
                                                                                                        
             
                                                                                                   **Re: Stuck on 'detecting file systems'**             
                                                                I got the same problem (15% stuck - detecting file systems).
After a reboot and analysis of the situation it seems there is a bug in the installer: it makes a kind of mix between the previous partition table and the new one - probably trying to detect older file systems to save any data (?).

Suggestion: maybe a complete deletion of the partition table first (using either Ubuntu commands or even Windows (reboot after the partition table is written)), then installing Ubuntu from the unpartitioned disk may work.


What I did: use the Alternate version of the installer (same download page as desktop) - installation is text-based but Ubuntu will still be windowed 
                                                                                                                                                                                                                                 paris-unmatch                   [View Public Profile]("http://ubuntuforums.org/member.php?u=328219")                   [Send a private message to paris-unmatch]("http://ubuntuforums.org/private.php?do=newpm&u=328219")                             [Find More Posts by paris-unmatch]("http://ubuntuforums.org/search.php?do=finduser&u=328219")               [Add paris-unmatch to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=328219")                
      
    
   
     
         
              [/LEFT]
     [/LEFT]
 [/CENTER]
             [CENTER]     [LEFT]         [LEFT]                                             
                    waratah                   [View Public Profile]("http://ubuntuforums.org/member.php?u=8658")                   [Send a private message to waratah]("http://ubuntuforums.org/private.php?do=newpm&u=8658")                             [Find More Posts by waratah]("http://ubuntuforums.org/search.php?do=finduser&u=8658")               [Add waratah to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=8658")                
      
    
   
     
         
              [/LEFT]
     [/LEFT]
 [/CENTER]

---

