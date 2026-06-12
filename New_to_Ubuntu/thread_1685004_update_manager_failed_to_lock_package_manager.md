---
title: "update manager failed to lock package manager"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by Unguidedone on 2011-02-10
It says only one tool is allowed to make changes at a time.  And in the details it says it was changed by apt-get

](*,)

so confused what have i done to break it :(

---

### Post by nick_goodfate on 2011-02-10
reboot and it should be solved. You may ran apt-get in terminal and sent it to background instead of quit.

---

### Post by Unguidedone on 2011-02-10
it seems to have worked the red ! is gone.  I dont like to keep my computer off because i cant stand not having ubuntu.

---

### Post by Unguidedone on 2011-02-10
the red triangle with the ! is back 
Screenshot = [http://i913.photobucket.com/albums/ac340/Happy_Mask_Salesman/hellohello.png](http://i913.photobucket.com/albums/ac340/Happy_Mask_Salesman/hellohello.png)




i rebooted and it came back has this happened to anyone before?

---

### Post by Unguidedone on 2011-02-11
bump

---

### Post by nick_goodfate on 2011-02-11
Can you remember what you did just before it happen? If the problem appears every time you do something specific(for example, you run any app that asks your password in terminal, then you try to use Synaptic...) describe that something.

---

### Post by Unguidedone on 2011-02-11
yes your are right I had done something in the terminal but have no idea what it was and it did require a password.  Is there a way to view a history or log of system changes?

this guy is having the same problem

[http://ubuntuforums.org/showthread.php?t=1684477](http://ubuntuforums.org/showthread.php?t=1684477)

Screenshot = [http://i913.photobucket.com/albums/ac340/Happy_Mask_Salesman/cannotupdate.png](http://i913.photobucket.com/albums/ac340/Happy_Mask_Salesman/cannotupdate.png)

---

### Post by nick_goodfate on 2011-02-11
> **Unguidedone said:**
> yes your are right I had done something in the terminal but have no idea what it was and it did require a password.  Is there a way to view a history or log of system changes?

this guy is having the same problem

[http://ubuntuforums.org/showthread.php?t=1684477](http://ubuntuforums.org/showthread.php?t=1684477)


Your screenshot shows that two apt processes are running and one of them is using you cpu for 1 day 5 hours and 9 minutes. :?
I'm trying to imagine how can this occur... Anyway, in terminal ```
killall apt-get
``` and make sure you 're using [apt-get]("https://help.ubuntu.com/8.04/serverguide/C/apt-get.html") properly.

---

### Post by Unguidedone on 2011-02-12
thank you so much for the reply it worked : )

---

### Post by Unguidedone on 2011-02-13
:-|

sorry but its back :


[IMG]http://i913.photobucket.com/albums/ac340/Happy_Mask_Salesman/killallaptget.png[/IMG]

---

### Post by nick_goodfate on 2011-02-13
you can ```
killall apt
``` but if we don't figure out why is this happening, it'll just happen back again and again...
If the problem doesn't happening because of your mistake, or if you can't remember want you'r trying to do and causes it, i can't help you, maybe someone else can ...

---

### Post by Unguidedone on 2011-02-14
bump

---

### Post by JKyleOKC on 2011-02-14
> **Unguidedone said:**
> yes your are right I had done something in the terminal but have **no idea what it was** and it did require a password.  Is there a way to view a history or log of system changes?Partially; you can "gedit .bash_history" to view the list of every terminal command you have issued (actually, the last 500 or so depending on how your system is configured, but that should be enough to reconstruct your activity). System changes made through the GUI won't show up in the list, though.

---

### Post by Linyx on 2011-02-14
Try:-

```
sudo apt-get update && apt-get upgrade
```

Did you see any error message in the last lines..??

---

### Post by Unguidedone on 2011-02-17
bump

---

### Post by Unguidedone on 2011-02-17
julio@julio-ThinkCentre-M52:~$ sudo apt-get update && apt-get upgrade
[sudo] password for julio: 
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg [198B]                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]            
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [31.4kB]  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release [31.4kB]         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [27.6kB]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [11.0kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [643B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [93.2kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources [85.5kB]    
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages [49.0kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources [778B] 
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources [31.3kB] 
Media change: please insert the disc labeled                                   
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter

Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources [1,498B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages [234kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages [1,797B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages [98.6kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages [2,834B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages [1,659B]
Media change: please insert the disc labeled                                   
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled                                                                                 
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled                                                                                 
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter

(it will not mount the disk)


julio@julio-ThinkCentre-M52:~$ sudo apt-get update && apt-get upgrade
[sudo] password for julio: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
julio@julio-ThinkCentre-M52:~$

---

### Post by plucky on 2011-02-17
You do not need the Install CD as a repository and you can disable it in **Software Sources**.

Untick the CD rom as a source and run the command again.

Good Luck

---

### Post by stevomanu on 2011-02-17
> **plucky said:**
> You do not need the Install CD as a repository and you can disable it in **Software Sources**.

Untick the CD rom as a source and run the command again.

Good Luck

thank you that worked a treat !! :popcorn:

---

### Post by hansolo4949 on 2011-02-17
It sounds like either one if the apt-get programs is not exiting properly, or you have a 
Program running in the background that is using the package manager. Perhaps it is also the update manager installing updates? Try disabling the update manager temporarily, and see if the problem goes away. Good luck!


Edit: I see that closing apt programs dies not work. Try updating, or fixing all broken packages in synaptic, and see if that helps.

---

### Post by Unguidedone on 2011-02-20
this is odd but the problem "self healed" because its no longer showing up

---

### Post by Foeburner on 2011-04-14
For those having this problem, I was able to fix it by following one of the comments in [this guide]("http://www.ubuntugeek.com/how-to-fix-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error.html") 

"ps -e | grep apt (might show you a number which is essentially a job number. My system was locked due to apt-get and showed me apt-get as job number 1594)

sudo kill 1594 (modify number to your current run)

This works perfect without having to delete the lock and causing unnecessary changes to your system"

use this: 
```
ps -e | grep apt
```

get the ID and kill it.

---

### Post by nspatt on 2011-08-28
Hi Unguidedone,

Did you try 


sudo killall apt-get 

You seemed to have tried just "killall apt-get" .

---

### Post by PcMojo on 2012-05-15
@ Foeburner
Thanks!!! I've been locked up for a week or so trying to update 10.10. When that wasn't working, I tried upgrading to 11.04 and 12.04 and nothing worked. All sorts of weird things have been happening and I thought I had a rare linux virus (wouldn't let me install Avast or AVG). I finally figured out, after reading this thread, that my apt-get was running in the background. The kill all command wasn't working, but finding the job number and doing a "sudo kill job number" worked like a champ!  Thanks a million!

---

### Post by oldos2er on 2012-05-15
Old thread closed.

---

