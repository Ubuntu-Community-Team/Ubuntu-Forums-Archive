---
title: "Best Backup Method for Re-Install?"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2011-08-08
I have Ubuntu 10.10 64 bit.  I want to do a new install of 11.04 on the same system, without doing an upgrade.

Is there a quick/easy backup method to re-install my programs and settings that I want?  For example, I use Thunderbird as my mail client, and have about 8 e-mail addresses.  It would be nice to be able to install Thunderbird again and copy whatever files are needed so I don't lose my settings.

I want to do a re-install because my system has become quite cluttered and there is a lot I want to get rid of, so I want to be able to selectively choose what I want to restore in terms of programs.

Any thoughts/ideas/questions welcome. 

Thanks

---

### Post by x C0MMAND0 x on 2011-08-08
Additionally, all of my custom settings for Compiz in terms of my desktops and hotkeys etc I don't want to lose.

---

### Post by jimwill on 2011-08-08
I'm basically trying to do the same thing. Only I'm going from Hardy all the way up and I know there have been a lot of changes. Plus I want to go to the Trinity release since it uses the KDE3.5 desktop (I don't like KDE4). 
Presently the only option I can see is to use a 40 gig partition that I have some virtual machines on. Really don't want to loose the vm's but it wouldn't be so bad as loosing my settings for thunderbird and other programs I have in Hardy.

So, about the only thing I could suggest is that if you have another partition you could install kubuntu 11.0 to and the transfer things over as needed then you would have the option of booting either 10 or 11.

I'll keep watching this thread and hope someone can help both of us!

---

### Post by Paqman on 2011-08-08
Check out [apt-clone](apt:apt-clone). It'll make a full backup of all your installed programs. Take a full backup of /home as well and that should be everything.

It's not in the repos for 10.10, but you could try installing it from [here]("http://packages.ubuntu.com/natty/apt-clone") and giving it a go. It'll be available in the repos when you install with 11.04

---

### Post by kaloasd on 2011-08-08
You can export your compiz profile from the ccsm preferences.

---

### Post by dwasifar on 2011-08-08
One warning about apt-clone - it does not save the config files for the applications it restores.  So for instance if you had Apache installed, you'll get Apache back, but you'll still need to restore (or recreate) your httpd.conf file.  At least this is how I understand it.

I'm not sure apt-clone is the right tool for you anyway, since your goal is to get rid of clutter, and I think apt-clone would reinstall everything, clutter included.

In your situation I would install to a blank drive, install what apps I wanted, connect my old drive and mount it somewhere in the filesystem, then copy over whatever I needed.

---

### Post by x C0MMAND0 x on 2011-08-08
I guess I'm more concerned with all my settings for a given program and where those are located.

I can re-install the programs I use fairly easily, but say once I install a program, what do I need to copy for the settings to be the same as the were?  Is it the /home/user/.programname?  Or don't some settings reside it /etc?

And what about all of my wireless networks that are saved?  I guess I may be asking for more than is able to be easily accomplished...

---

### Post by oldfred on 2011-08-08
All your user settings are in /home in hidden files & folders unless you have redirected else where. If you have manually made system settings for video or networking the will be in /etc.

You can just back up /home and restore. But now might to be good time to migrate to a separte /home so when you reinstall you can just reuse it and specify NOT TO FORMAT it. If it is in your / (root) it will be overwritten so you have to back it up.

I always do clean installs but cheat and just install to a new 25GB / partition. I have all data in separate data partition including many of the hidden folders that include larger amounts of data like my Firefox & Thunderbird profiles. I then only copy some settings from my old home to my new one.

If you have room make the new /home.
These three are all the same except using different copy commands. If immediately reinstalling you only need the part that copies to a new partition.
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Since I do clean reinstalls and do not have a lot of critical data in my home computer this is my backup which would let me do a clean install in a new drive if my old one died.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

I modified the above script to include this:
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by Basher101 on 2011-08-08
Another good method would be using Remastersys. It will backup all your programs, settings, files, and about everything you have there, into a bootable Live CD. Then you can simply boot it and reinstall it with the command ```
sudo ubiquity --desktop %k gtk_ui
```and the normal isntaller will pop up. Good luck

---

### Post by 1clue on 2011-08-08
Depends on how dirty your system is.

I'm always pretty careful about where I put things, meaning I don't just go editing files all over the system.

Before any backup or upgrade I always do this:
[LIST=1]
[*]Stick in an external drive like a USB drive, or another partition that will not be known to the new installer.
[*]tar -czf /my/backup/etc.tgz /etc
[*]Export all my email addresses into an external form into my home directory somewhere.
[*]Export my firefox bookmarks just in case.
[*]Same with anything else that has a funky configuration that might have problems with an upgrade.
[*]cp -prd /home /my/backup/home
[*]copy anything related to configuration or data in /var, like /var/www if you have a web server.
[*]copy anything in /opt that you put there yourself.
[/LIST]

For /etc I zip it so I have a mostly non-corruptible copy of what was there.  For /home and others I don't zip because I will be taking things out of there piecemeal and just want everything backed up, and sometimes my home directory gets too big to zip.

I generally do NOT pull settings over into my new directory.  It often causes more trouble than it's worth.  Firefox and evolution are usually pretty good but they aren't always entirely trouble-free.

You can always try direct replacement of configuration files, but it may not work well.

---

### Post by magic8ball on 2011-08-08
I just did some updates on my own system.  I wanted to change my 10.04 from 32-bit to 64-bit.  Since I was doing this, I also took the opportunity to re-size my partitions (Windows dual-boot) and format my / as ext4.  I already had a separate / and /home.

Anyhow, I used the commands from the post below to backup and restore my packages...

[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

I think that the package list was just a text file, so I guess that a person could edit out packages that they didn't want to reinstall.  Not sure if that helps, but thought that I'd throw it out there.


P.S.  I was very impressed by how smoothly my update process went.  Thanks Ubuntu!

---

