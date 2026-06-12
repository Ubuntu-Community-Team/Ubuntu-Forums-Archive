---
title: "Can't Get Rid of akirad Respository"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by Roger Allott on 2011-03-09
The akirad repository hosts the packages for an app named 'Cinelerra'. I've tried it and decided I don't like it.

So, I've uninstalled the app and I've tried everything I can think of to get rid of the repository from my sources list.

But each time I think I've blitzed it, the next time I run Update Manager I get a response like this:

```
W:Failed to fetch http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/akirad/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

I've tried purging them from Uvuntu-Tweak. It tells me that my cleanup was successful, but they return a few hours later.

I've tried double-clicking on the sources.list file in etc/app and got the old familiar Software Sources dialog thing that for some reason isn't on my System>Administration menu in maverick. But even after blitzing them there, they again return after a few hours.

Any other ideas on how to blitz a no longer needed repository?

---

### Post by plucky on 2011-03-09
Post output from a terminal of ```
ls -l /etc/apt/sources.list.d/
cat /etc/apt/sources.list
```

so we can see where the ppa source list is located.

---

### Post by Zeno Izen on 2011-03-09
> **Roger Allott said:**
> 
I've tried double-clicking on the sources.list file in etc/app and got the old familiar Software Sources dialog thing

Any other ideas on how to blitz a no longer needed repository?

Perhaps edit the sources.list file through a text editor?

---

### Post by kc1di on 2011-03-09
go to a terminal and enter the following:
sudo gedit <hit enter>

when gedit come up hit open file 
find /etc/apt/sources.list and open it in gedit.

scroll down the list of repositories and find the one you want disable. 
at this point you can do 1 of 2 things simply place a # sign in front of the repository line you no longer want to use or you can manually delete the line. But be careful make sure you only delete line you want to get rid of.  

Place a # sign infront of each line with the repository you want to disable. 
save the file and exit gedit.

in the terminal now type sudo apt-get update

That's it it should now be gone.

---

### Post by Roger Allott on 2011-03-09
> **plucky said:**
> Post output from a terminal of ```
ls -l /etc/apt/sources.list.d/
cat /etc/apt/sources.list
```

so we can see where the ppa source list is located.

```
me@me-laptop:~$ ls -l /etc/apt/sources.list.d/
total 108
-rw-r--r-- 1 root root   0 2011-03-07 22:28 akirad-akirad-lucid.list
-rw-r--r-- 1 root root 561 2011-03-05 20:55 akirad-akirad-lucid.list.distUpgrade
-rw-r--r-- 1 root root 100 2011-03-07 22:28 akirad-akirad-lucid.list.save
-rw-r--r-- 1 root root 471 2011-03-09 02:04 akirad.list
-rw-r--r-- 1 root root 459 2011-03-05 20:55 akirad.list.distUpgrade
-rw-r--r-- 1 root root  93 2011-03-07 22:30 akirad.list.save
-rw-r--r-- 1 root root   0 2011-03-07 22:28 akirad-ppa-lucid.list
-rw-r--r-- 1 root root 543 2011-03-05 20:55 akirad-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root  97 2011-03-07 22:28 akirad-ppa-lucid.list.save
-rw-r--r-- 1 root root 105 2011-03-05 20:55 chromium-daily-beta-lucid.list.distUpgrade
-rw-r--r-- 1 root root   0 2011-03-07 22:28 chromium-daily-beta-maverick.list
-rw-r--r-- 1 root root 108 2011-03-07 22:28 chromium-daily-beta-maverick.list.save
-rw-r--r-- 1 root root  67 2010-10-19 14:07 chromium-daily-ppa-karmic.list.distUpgrade
-rw-r--r-- 1 root root  97 2010-10-25 16:12 chromium-daily-ppa-karmic.list.save
-rw-r--r-- 1 root root  99 2011-03-05 20:55 chromium-daily-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root 207 2011-03-05 20:55 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 207 2010-10-25 16:12 google-chrome.list.save
-rw-r--r-- 1 root root 287 2011-03-08 00:36 medibuntu.list
-rw-r--r-- 1 root root 301 2011-03-05 20:55 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root 287 2011-03-07 22:30 medibuntu.list.save
-rw-r--r-- 1 root root  62 2010-10-19 14:07 team-xbmc-ppa-karmic.list.distUpgrade
-rw-r--r-- 1 root root  92 2010-10-25 16:12 team-xbmc-ppa-karmic.list.save
-rw-r--r-- 1 root root  92 2011-03-05 20:55 team-xbmc-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root  64 2011-03-08 00:36 team-xbmc-ppa-maverick.list
-rw-r--r-- 1 root root  64 2011-03-07 22:30 team-xbmc-ppa-maverick.list.save
-rw-r--r-- 1 root root  62 2010-10-19 14:07 tualatrix-ppa-karmic.list.distUpgrade
-rw-r--r-- 1 root root  92 2010-10-25 16:12 tualatrix-ppa-karmic.list.save
-rw-r--r-- 1 root root  92 2011-03-05 20:55 tualatrix-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root  64 2011-03-08 00:36 tualatrix-ppa-maverick.list
-rw-r--r-- 1 root root  64 2011-03-07 22:30 tualatrix-ppa-maverick.list.save
```

```
me@me-laptop:~$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu maverick main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ maverick-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu maverick-updates universe main multiverse restricted
```

---

### Post by yeats on 2011-03-09
> **Roger Allott said:**
> ```
me@me-laptop:~$ ls -l /etc/apt/sources.list.d/
total 108
-rw-r--r-- 1 root root   0 2011-03-07 22:28 akirad-akirad-lucid.list
-rw-r--r-- 1 root root 561 2011-03-05 20:55 akirad-akirad-lucid.list.distUpgrade
-rw-r--r-- 1 root root 100 2011-03-07 22:28 akirad-akirad-lucid.list.save
-rw-r--r-- 1 root root 471 2011-03-09 02:04 akirad.list
-rw-r--r-- 1 root root 459 2011-03-05 20:55 akirad.list.distUpgrade
-rw-r--r-- 1 root root  93 2011-03-07 22:30 akirad.list.save
-rw-r--r-- 1 root root   0 2011-03-07 22:28 akirad-ppa-lucid.list
-rw-r--r-- 1 root root 543 2011-03-05 20:55 akirad-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root  97 2011-03-07 22:28 akirad-ppa-lucid.list.save

```

do Alt-F2 and type 'gksu nautilus'.  Then navigate to Filesystem -> etc -> apt -> sources.list.d and delete any files that say 'akirad'.  Then run update manager again.

---

### Post by Roger Allott on 2011-03-09
> **kc1di said:**
> go to a terminal and enter the following:
sudo gedit <hit enter>

when gedit come up hit open file 
find /etc/apt/sources.list and open it in gedit.

scroll down the list of repositories and find the one you want disable. 
at this point you can do 1 of 2 things simply place a # sign in front of the repository line you no longer want to use or you can manually delete the line. But be careful make sure you only delete line you want to get rid of.  

Place a # sign infront of each line with the repository you want to disable. 
save the file and exit gedit.

in the terminal now type sudo apt-get update

That's it it should now be gone.

That certainly used to be the way to do it, but it seems that the structure of sources (repositories) information has changed in maverick.

I'd be interested to know what these changes actually are, and why they've been implemented.

---

### Post by tgm4883 on 2011-03-09
> **Roger Allott said:**
> That certainly used to be the way to do it, but it seems that the structure of sources (repositories) information has changed in maverick.

I'd be interested to know what these changes actually are, and why they've been implemented.

It's a lot easier/cleaner to deal with repositories now. It's actually been like that for more than just maverick. The main Ubuntu repositories are still in /etc/apt/sources.list, but any additional repos now have their own files in /etc/apt/sources.list.d/

---

### Post by Roger Allott on 2011-03-10
> **yeats said:**
> do Alt-F2 and type 'gksu nautilus'.  Then navigate to Filesystem -> etc -> apt -> sources.list.d and delete any files that say 'akirad'.  Then run update manager again.

Thanks for that. It seems to have done the trick, but then again as I mentioned before, the other things I did seemed to do the trick but then the issue re-occurred.

Something very bizarre though was that as soon as I hit enter after entering 'gksu nautilus' my desktop background reverted to the default metallic purple maverick one!

And when I looked at System>Preferences>Appearance in the Visual Effects tab, my setting had gone from 'Custom' to 'None'.

Any ideas as to what caused that to happen?

---

### Post by Roger Allott on 2011-03-12
Well, after one reboot and upon another Update Manager, I've got the same error message again!

And when I look at my etc/apt/sources.list.d folder, I find that a file has miraculously resurrected itself - "akirad.list".

How?? It reminds me of Windows viruses that recreate themselves after you've deleted them. This sort of thing shouldn't happen with linux systems, should it?

---

### Post by plucky on 2011-03-12
Please repost the output of ```
ls -l /etc/apt/sources.list.d/
```

How did you delete the previous lists?

Did you use the GUI or through the terminal.

---

### Post by Roger Allott on 2011-03-12
> **plucky said:**
> Please repost the output of ```
ls -l /etc/apt/sources.list.d/
```

```
me@me-laptop:~$ ls -l /etc/apt/sources.list.d/
total 64
-rw-r--r-- 1 root root 471 2011-03-11 21:29 akirad.list
-rw-r--r-- 1 root root 207 2011-03-05 20:55 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 207 2010-10-25 16:12 google-chrome.list.save
-rw-r--r-- 1 root root 287 2011-03-10 18:08 medibuntu.list
-rw-r--r-- 1 root root 301 2011-03-05 20:55 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root 287 2011-03-07 22:30 medibuntu.list.save
-rw-r--r-- 1 root root  62 2010-10-19 14:07 team-xbmc-ppa-karmic.list.distUpgrade
-rw-r--r-- 1 root root  92 2010-10-25 16:12 team-xbmc-ppa-karmic.list.save
-rw-r--r-- 1 root root  92 2011-03-05 20:55 team-xbmc-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root  64 2011-03-10 18:08 team-xbmc-ppa-maverick.list
-rw-r--r-- 1 root root  64 2011-03-07 22:30 team-xbmc-ppa-maverick.list.save
-rw-r--r-- 1 root root  62 2010-10-19 14:07 tualatrix-ppa-karmic.list.distUpgrade
-rw-r--r-- 1 root root  92 2010-10-25 16:12 tualatrix-ppa-karmic.list.save
-rw-r--r-- 1 root root  92 2011-03-05 20:55 tualatrix-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root  64 2011-03-10 18:08 tualatrix-ppa-maverick.list
-rw-r--r-- 1 root root  64 2011-03-07 22:30 tualatrix-ppa-maverick.list.save
```


> **plucky said:**
> How did you delete the previous lists?

Did you use the GUI or through the terminal.

The instruction was to do it through gksu nautilus, so GUI. Why would there be any difference between deleting files via nautilus and via the terminal?

---

### Post by bapoumba on 2011-03-12
Remove the repository, either the way you did, or in the terminal, or using the -r param with apt-add-repository.
```
sudo apt-add-repository -r ppa:user/repository
```
Then run an update:
```
sudo apt-get update
```
for the removal been taken into account.

---

### Post by yeats on 2011-03-12
> **Roger Allott said:**
> Well, after one reboot and upon another Update Manager, I've got the same error message again!

And when I look at my etc/apt/sources.list.d folder, I find that a file has miraculously resurrected itself - "akirad.list".

How?? It reminds me of Windows viruses that recreate themselves after you've deleted them. This sort of thing shouldn't happen with linux systems, should it?

You might have one APT tool fighting against another here.  Can you go to Administration -> Update Manager and click Settings...?  Then go to the Other Software tab and check for any reference to Akirad.  If you see one, select it and click Remove.  If there are references to Akirad there, then you'd need to go back through your /etc/apt/sources.list and any files in /etc/apt/sources.list.d/ and remove them manually.  You should be able to find out quickly where the reference is by doing

```
grep akirad /etc/apt/sources.list
grep -R akirad /etc/apt/sources.list.d/
```

EDIT: sorry - didn't see the other responses before posting - please ignore if I've duplicated or contradicted what others have said ;-)

---

### Post by Roger Allott on 2011-03-13
I thought I'd do a combination of things suggested by yeats and bapoumba.

So, System>Administration>Update Manager>Settings>Other Software

I removed the 4 instances of akirad in that list.

gksu nautilus - deleted the two files in sources.list.d that mentioned akirad

ran 'sudo apt-get update'. Message returned was:

```
me@me-laptop:~$ sudo apt-get update
[sudo] password for me: 
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg                   
Ign http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://archive.ubuntu.com maverick Release.gpg                   
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en   
Hit http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg                    
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Hit http://ppa.launchpad.net maverick Release                        
Hit http://packages.medibuntu.org maverick Release.gpg               
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en       
Hit http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB    
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
Hit http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB    
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en         
Hit http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB      
Hit http://archive.ubuntu.com maverick-updates Release.gpg                     
Hit http://security.ubuntu.com maverick-security Release                       
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://archive.ubuntu.com maverick Release                       
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://archive.ubuntu.com maverick-updates Release                         
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Ign http://packages.medibuntu.org/ maverick/free Translation-en_GB             
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_GB         
Hit http://packages.medibuntu.org maverick Release                             
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages                
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages          
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://packages.medibuntu.org maverick/free i386 Packages
Hit http://packages.medibuntu.org maverick/non-free i386 Packages
Reading package lists... Done
```

All seemed great! So I rebooted.

Before doing anything at all, I look at sources.list.d folder and find ......... a file named "akirad.list"!!!

AAAARRRGGGGHHHHH!! How the heck did that get re-created yet again??????

Here's the output from those two 'grep' commands that yeats suggested:

```
me@me-laptop:~$ grep akirad /etc/apt/sources.list
me@me-laptop:~$ grep -R akirad /etc/apt/sources.list.d/
/etc/apt/sources.list.d/akirad.list:deb http://ppa.launchpad.net/akirad/akirad/ubuntu maverick main #Akirad Repository - Main
/etc/apt/sources.list.d/akirad.list:deb http://ppa.launchpad.net/akirad/ppa/ubuntu maverick main #Akirad Repository - Main
/etc/apt/sources.list.d/akirad.list:#deb-src http://ppa.launchpad.net/akirad/akirad/ubuntu maverick main #Akirad Repository Sources- Main
/etc/apt/sources.list.d/akirad.list:#deb-src http://ppa.launchpad.net/akirad/ppa/ubuntu maverick main #Akirad Repository Sources- Main
```

---

### Post by plucky on 2011-03-13
If something is re-creating the repository,you need to find out when it is being created.

Is it the "sudo apt-get update"? Or is it the reboot?

After you delete the file,run "sudo apt-get update" and see if the file is re-created.

If it is, then you should look in all the list files (including sources.list) for a command that starts with "sudo wget" or "sudo apt-add" or "sudo add-apt-repository ppa:user/ppa-name".

Also remove all the non-maverick repositories in the sources.list.d directory given by the ls -l command.i.e ```
-rw-r--r-- 1 root root  62 2010-10-19 14:07 team-xbmc-ppa-karmic.list.distUpgrade
-rw-r--r-- 1 root root  92 2010-10-25 16:12 team-xbmc-ppa-karmic.list.save
-rw-r--r-- 1 root root  92 2011-03-05 20:55 team-xbmc-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root  62 2010-10-19 14:07 tualatrix-ppa-karmic.list.distUpgrade
-rw-r--r-- 1 root root  92 2010-10-25 16:12 tualatrix-ppa-karmic.list.save
-rw-r--r-- 1 root root  92 2011-03-05 20:55 tualatrix-ppa-lucid.list.distUpgrade

```

If it is the reboot then I am at a loss.

---

### Post by Roger Allott on 2011-03-13
Would I be doing any damage if I were to delete all of the files in apt/ folder that include 'distUpgrade' in the title? The common theme for all of them is that they refer to pre-maverick versions of ubuntu.

Why do they exist?

---

### Post by Roger Allott on 2011-03-13
> **plucky said:**
> If something is re-creating the repository,you need to find out when it is being created.

Is it the "sudo apt-get update"? Or is it the reboot?

After you delete the file,run "sudo apt-get update" and see if the file is re-created.
Nope, it's not being recreated then. I've just deleted the files, run "sudo apt-get update", and then run System>Administration>Update Manager as well, and the files have not been recreated.

So they must be being recreated when I boot up. But how? And why???

> **plucky said:**
> If it is the reboot then I am at a loss.

Ah. That's a problem!

---

### Post by CharlesA on 2011-03-13
Any entries in cron?

```
sudo crontab -l
```

```
crontab -l
```

---

### Post by Roger Allott on 2011-03-13
> **CharlesA said:**
> Any entries in cron?

```
sudo crontab -l
```

```
crontab -l
```

I haven't got the faintest idea what cron is, but:

```
me@me-laptop:~$ sudo crontab -l
[sudo] password for me: 
no crontab for root
me@me-laptop:~$ crontab -l
no crontab for me
```

---

### Post by CharlesA on 2011-03-13
cron runs automated tasks. So there's nothing there to run.

You could try this to see if this finds anything:

```
locate akirad
```

---

### Post by bapoumba on 2011-03-13
In addition, have your completely purged cinerella ?

---

### Post by Roger Allott on 2011-03-13
> **CharlesA said:**
> 
You could try this to see if this finds anything:

```
locate akirad
```

```
me@me-laptop:~$ locate akirad
/etc/apt/source.list.akiradbackup
/etc/apt/sources.list.d/akirad.list
/etc/init.d/akiradrelease
/etc/rc0.d/K20akiradrelease
/etc/rc1.d/K20akiradrelease
/etc/rc2.d/S20akiradrelease
/etc/rc3.d/S20akiradrelease
/etc/rc4.d/S20akiradrelease
/etc/rc5.d/S20akiradrelease
/etc/rc6.d/K20akiradrelease
/usr/share/aptlists/mirror-akirad.list
/usr/share/doc/akirad-keyring
/usr/share/doc/akirad-keyring/changelog
/usr/share/doc/akirad-keyring/copyright
/usr/share/keyrings/akirad-keyring.gpg
/var/lib/dpkg/info/akirad-keyring-and-mirrors.list
/var/lib/dpkg/info/akirad-keyring-and-mirrors.postinst
/var/lib/dpkg/info/akirad-keyring-and-mirrors.prerm
/var/lib/update-rc.d/akiradrelease
```

Blimey! Well, that looks like there's something!

Should I simply delete all of these files? Or is there an approach that's less brutal?

---

### Post by Roger Allott on 2011-03-13
> **bapoumba said:**
> In addition, have your completely purged cinerella ?

I'm pretty sure that I 'Completely Removed' it via Synaptic. Isn't that the same as purging (presumably via Terminal?

---

### Post by CharlesA on 2011-03-13
> **Roger Allott said:**
> ```
me@me-laptop:~$ locate akirad
/etc/apt/source.list.akiradbackup
/etc/apt/sources.list.d/akirad.list
/etc/init.d/akiradrelease
/etc/rc0.d/K20akiradrelease
/etc/rc1.d/K20akiradrelease
/etc/rc2.d/S20akiradrelease
/etc/rc3.d/S20akiradrelease
/etc/rc4.d/S20akiradrelease
/etc/rc5.d/S20akiradrelease
/etc/rc6.d/K20akiradrelease
/usr/share/aptlists/mirror-akirad.list
/usr/share/doc/akirad-keyring
/usr/share/doc/akirad-keyring/changelog
/usr/share/doc/akirad-keyring/copyright
/usr/share/keyrings/akirad-keyring.gpg
/var/lib/dpkg/info/akirad-keyring-and-mirrors.list
/var/lib/dpkg/info/akirad-keyring-and-mirrors.postinst
/var/lib/dpkg/info/akirad-keyring-and-mirrors.prerm
/var/lib/update-rc.d/akiradrelease
```

Blimey! Well, that looks like there's something!

Should I simply delete all of these files? Or is there an approach that's less brutal?

I don't know. That's a ton of stuff and the akirad site was totally messed up when I looked at it.

I'd remove/rename the stuff in /etc/rc* and the stuff in /etc/apt and see what happens after a reboot.

---

### Post by Roger Allott on 2011-03-13
> **CharlesA said:**
> 
I'd remove/rename the stuff in /etc/rc* and the stuff in /etc/apt and see what happens after a reboot.

Sorry to be dumb, by why wouldn't I also delete the stuff in usr/share/..... and/or var/lib/..... ?

---

### Post by CharlesA on 2011-03-13
Well, there's no reason to keep the other files around, but I was trying to play it safe :)

---

### Post by Roger Allott on 2011-03-13
> **CharlesA said:**
> Well, there's no reason to keep the other files around, but I was trying to play it safe :)

Right. To hell with safety - I deleted all of them that were on that list!

Now going to reboot .....

---

### Post by Roger Allott on 2011-03-13
Done the reboot. Checked various folders in File System. None of the files that I've just zapped have been re-created.

That's a cautious relief - I'm going no further than that at this stage!

Shall I run update or should I do another 'locate akirad' first?

---

### Post by Roger Allott on 2011-03-13
Bah, I ran update anyway. Doesn't seem to have given me any errors or nasty stuff:

```
me@me-laptop:~$ sudo apt-get update
[sudo] password for me: 
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release.gpg                   
Ign http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://packages.medibuntu.org maverick Release.gpg               
Hit http://archive.ubuntu.com maverick Release.gpg                   
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_GB
Hit http://ppa.launchpad.net maverick Release                                  
Get:1 http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB [94.5kB]
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Hit http://security.ubuntu.com maverick-security Release                       
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en       
Get:2 http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB [91.2kB]
Hit http://ppa.launchpad.net maverick/main i386 Packages             
Ign http://packages.medibuntu.org/ maverick/free Translation-en_GB             
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
Get:3 http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB [2,332B]
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en         
Get:4 http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB [32.0kB]
Hit http://archive.ubuntu.com maverick-updates Release.gpg                     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Hit http://packages.medibuntu.org maverick Release                             
Hit http://packages.medibuntu.org maverick/free i386 Packages                  
Hit http://packages.medibuntu.org maverick/non-free i386 Packages
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://archive.ubuntu.com maverick Release
Hit http://archive.ubuntu.com maverick-updates Release
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Fetched 220kB in 1s (216kB/s)
Reading package lists... Done
```

---

### Post by Roger Allott on 2011-03-13
So I then did a 'locate akirad', thinking it would return with something like "what the fugg is akirad?", but:


```
me@me-laptop:~$ locate akirad
/etc/apt/source.list.akiradbackup
/etc/apt/sources.list.d/akirad.list
/etc/init.d/akiradrelease
/etc/rc0.d/K20akiradrelease
/etc/rc1.d/K20akiradrelease
/etc/rc2.d/S20akiradrelease
/etc/rc3.d/S20akiradrelease
/etc/rc4.d/S20akiradrelease
/etc/rc5.d/S20akiradrelease
/etc/rc6.d/K20akiradrelease
/usr/share/aptlists/mirror-akirad.list
/usr/share/doc/akirad-keyring
/usr/share/keyrings/akirad-keyring.gpg
/var/lib/dpkg/info/akirad-keyring-and-mirrors.list
/var/lib/dpkg/info/akirad-keyring-and-mirrors.postinst
/var/lib/dpkg/info/akirad-keyring-and-mirrors.prerm
/var/lib/update-rc.d/akiradrelease
```

That is exactly what that command gave me before I deleted those files. And I've just checked and those files definitely don't exist, or at least, not in those locations.

This tells me that there's some gremlin still lingering in my system somewhere.

---

### Post by CharlesA on 2011-03-13
Ah ok.

Do this:

```
sudo updatedb
```

Then try using locate again.

---

### Post by Roger Allott on 2011-03-13
> **CharlesA said:**
> Ah ok.

Do this:

```
sudo updatedb
```

Then try using locate again.

Ah. That seems to have done the trick. No output at all from the locate command.

I thought something like 'updatedb' was the first stage of the apt-get update procedure, but it seems it's not.

---

### Post by Roger Allott on 2011-03-13
That's now 2 reboots and updates done without errors, so I'm going to mark the thread solved.

Thanks for all your help.

---

### Post by CharlesA on 2011-03-13
> **Roger Allott said:**
> Ah. That seems to have done the trick. No output at all from the locate command.

I thought something like 'updatedb' was the first stage of the apt-get update procedure, but it seems it's not.

I think it's a separate thing from apt-get, as it's just a database of the files in the file system, but I can't be sure.

Glad you got it fixed. :)

---

### Post by dfreer on 2011-03-13
> **Roger Allott said:**
> 
```
me@me-laptop:~$ locate akirad
/etc/apt/source.list.akiradbackup
/etc/apt/sources.list.d/akirad.list
/etc/init.d/akiradrelease
/etc/rc0.d/K20akiradrelease
/etc/rc1.d/K20akiradrelease
/etc/rc2.d/S20akiradrelease
/etc/rc3.d/S20akiradrelease
/etc/rc4.d/S20akiradrelease
/etc/rc5.d/S20akiradrelease
/etc/rc6.d/K20akiradrelease
/usr/share/aptlists/mirror-akirad.list
/usr/share/doc/akirad-keyring
/usr/share/keyrings/akirad-keyring.gpg
/var/lib/dpkg/info/akirad-keyring-and-mirrors.list
/var/lib/dpkg/info/akirad-keyring-and-mirrors.postinst
/var/lib/dpkg/info/akirad-keyring-and-mirrors.prerm
/var/lib/update-rc.d/akiradrelease
```


So this is interesting. It appears that akiradrelease is being run as a system service, and it starts upon bootup. My guess is that this daemon is what kept adding it's repository info back into your folder. 

My question is why would any legitimate repository need to go to these lengths, to install a service just to make sure you keep it's repository installed? 

I would **really** like to take a look at these files and find out exactly what it does, but unfortunately their website appears to have a massive MySQL problem at the moment.

---

### Post by CharlesA on 2011-03-13
> **dfreer said:**
> So this is interesting. It appears that akiradrelease is being run as a system service, and it starts upon bootup. My guess is that this daemon is what kept adding it's repository info back into your folder. 

It's definitely suspicious. I don't add ppas that often, but I've not seen one do that sort of thing before.

It's really strange.

---

### Post by alphacrucis2 on 2011-03-14
> **CharlesA said:**
> It's definitely suspicious. I don't add ppas that often, but I've not seen one do that sort of thing before.

It's really strange.


There is a launchpad ppa for cinelerra which seems to not do anything weird like this.

---

### Post by CharlesA on 2011-03-14
> **alphacrucis2 said:**
> There is a launchpad ppa for cinelerra which seems to not do anything weird like this.
It sorta looked like the OP was using the PPA (judging from the error message), but I don't know for sure.

---

### Post by Roger Allott on 2011-03-14
> **CharlesA said:**
> It sorta looked like the OP was using the PPA (judging from the error message), but I don't know for sure.

Yes, it was the PPA via launchpad, which I know isn't guaranteed kosher stuff, but the behaviour of this one raises a few flags as well as the obvious question - why? What benefit derives from forcing users to have to go through these loops to remove a repository?

I suppose it could have just been badly written, but I think that's unlikely. It seems far more like a designed behaviour that really is quite similar to a virus (although it doesn't seem to actually do any damage as such - just a pointless irritant).

---

### Post by CharlesA on 2011-03-14
> **Roger Allott said:**
> 
I suppose it could have just been badly written, but I think that's unlikely. It seems far more like a designed behaviour that really is quite similar to a virus (although it doesn't seem to actually do any damage as such - just a pointless irritant).

I don't know if it's due to the program that was installed, or not, but yeah, it definitely seemed like designed behavior.

---

### Post by tgm4883 on 2011-03-14
> **Roger Allott said:**
> Yes, it was the PPA via launchpad, which I know isn't guaranteed kosher stuff, but the behaviour of this one raises a few flags as well as the obvious question - why? What benefit derives from forcing users to have to go through these loops to remove a repository?

I suppose it could have just been badly written, but I think that's unlikely. It seems far more like a designed behaviour that really is quite similar to a virus (although it doesn't seem to actually do any damage as such - just a pointless irritant).

It's likely just a mistake from the developer. They were probably trying to ensure that the repository was reactivated after a distribution upgrade. Google does something similar with Picasa, and I'm looking at doing something similar with one of my packages.

It's a bug though since it should have been removed if you removed the packages. What I think happened (and this is just a guess based on the errors you were getting) is that they changed repos and fixed their packages to remove the new repos, but didn't account for people that had the old repos active. So when you removed the packages, there was no way for it to remove the old repos.

---

### Post by Roger Allott on 2011-03-15
Oh well, it seems my system hasn't been completely purged of akirad after all. I've just reinstalled a package to try sort out a completely separate issue, and I saw this as part of the script generated in Terminal:

```
dpkg: warning: files list file for package `akirad-keyring-and-mirrors' missing, assuming package has no files currently installed.
```

So, it seems that dpkg has some sort of reference table somewhere that it uses to check which repositories to check out. Anyone know how I can adjust that table?

---

