---
title: "Big Scary Warning with Rsync"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by Tom_ZeCat on 2008-09-24
I have a simple wired network with 3 PCs, one Windows XP machine and two Ubuntu Linux ones.  The Windows computer is not involved in this file copy attempt.  It's from one Linux machine to another.  

I've been trying to copy files over my network with the Rsync GUI, Grsync, and am still having trouble despite having read previous posts about copying over a network and despite having googled and read info from other boards, namely this one:

[http://ubuntuforums.org/showthread.php?t=795668](http://ubuntuforums.org/showthread.php?t=795668)

Seems to have all the info I need, but I get a big scary warning every time I try to run this profile.  Here's the info:

Source computer: Tom-Fastjuke, Ubuntu Linux 8.04
Destination computer: Toms-jukebox, Ubuntu Linux 7.10
Destination computer's IP: 192.168.0.102

Source folder: 
/home/tom/SyncTest

Destination folder (literal location): 
/home/tom/Pent3/SyncTest

Destination folder (Samba Interpretation): 
smb://toms-jukebox/Pent3/SyncTest/

Destination folder (IP interpretation): 
192.168.0.102:/Pent3/SyncTest/ 
or maybe:
192.168.0.102:/home/tom/Pent3/SyncTest/

Okay, so in Grsync's GUI, I'm putting this in the source box:
/home/tom/SyncTest/

And this in the destination box: 192.168.0.102:/Pent3/SyncTest/ 
Or this: 192.168.0.102:/home/tom/Pent3/SyncTest/

Under Basic Options, I'm checking off these: 
Preserve time
Delete on destination
Verbose
Skip newer
show transfer progress

Under Advanced Options
I'm putting this in the "Additional Options" field:
-e ssh

Whether I run the simulation or the actual execution, I'm getting this warning: 

> @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
3b:f4:db:61:0f:2d:27:e3:c8:51:50:af:fc:4e:fe:d6.
Please contact your system administrator.
Add correct host key in /home/tom/.ssh/known_hosts to get rid of this message.
Offending key in /home/tom/.ssh/known_hosts:1
RSA host key for 192.168.0.102 has changed and you have requested strict checking.
Host key verification failed.
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(454) [sender=2.6.9]


What's going on? How can I make this work?

---

### Post by handaxe on 2008-09-24
On the machine you are working from, delete the first entry in the file /home/tom/.ssh/known_hosts

It appears that you have at some point ssh'd into some other installation / setup with the  IP 192.168.0.102 and "strict checking" dictates that your attention is drawn to this fact as a precaution.
 Cannot be certain this will solve all your problems, but the error comes from ssh that rsync will use as a 'tunnel'.
HA

---

### Post by Tom_ZeCat on 2008-09-26
Thanks for the help.  That's gotten me started and has helped me to understand partially, but I'm still not able to run the rsync.  My known_hosts file looks like this: 

> |1|sVuB/8L8h5+dKZNJ71QyVs4fJKI=|P4yWauJKniptgGC6d6bwKDPRlO Y= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAxmwx9D43hZ9dTgWEmF3bXm X8P0X2vLh/qNYauINXGOd7Q30Wjb02B3mJgF38+Ic0mPJpdQ2WGSlnW15uzY 15BCGZMzoXzNSIKqF2x4TA14Q0plqtOiGr8B0XwVGg2bglUZP/joWEmne/uAe3PZaMP8Ldhx6Lj9fRXmdEDe8t9jNIvKXiqqKu+hMmQSW8qc fwcOknVBqopQd/Sw0eQ5MnahxftHFGJx0h27OlsW8J9mIxqNBxNLOf0gB5WHe3iZ Hs91b6MezvCVBOnDQEwmHqfl7zKYm4io0Mn8Ey2dN9JnoC+tfN 4CxSPVNbiTapaED5ESwSSs0IBi2+o1so+mIlfQ==

I'll be honest.  It looks like gibberish to me.  However, I gave editing it a shot.  I simply tried removing the first line to make it look like this:

> AAAAB3NzaC1yc2EAAAABIwAAAQEAxmwx9D43hZ9dTgWEmF3bXm X8P0X2vLh/qNYauINXGOd7Q30Wjb02B3mJgF38+Ic0mPJpdQ2WGSlnW15uzY 15BCGZMzoXzNSIKqF2x4TA14Q0plqtOiGr8B0XwVGg2bglUZP/joWEmne/uAe3PZaMP8Ldhx6Lj9fRXmdEDe8t9jNIvKXiqqKu+hMmQSW8qc fwcOknVBqopQd/Sw0eQ5MnahxftHFGJx0h27OlsW8J9mIxqNBxNLOf0gB5WHe3iZ Hs91b6MezvCVBOnDQEwmHqfl7zKYm4io0Mn8Ey2dN9JnoC+tfN 4CxSPVNbiTapaED5ESwSSs0IBi2+o1so+mIlfQ==

That didn't work.  All it did was remove my destination PC from the network.  After I restored the backup of my known_hosts file and rebooted both PCs, The network was back up and running.  I need to learn to understand the contents of a known_hosts file and how to edit it to do what I want to do.  I have The Linux Bible.  I'm going to look over the networking chapter.  I'm also willing to read anything online that will help me to understand Linux networking and the known_host file.  Is this file unique to Ubuntu or is it in all distros?

---

### Post by handaxe on 2008-09-26
> 1|sVuB/8L8h5+dKZNJ71QyVs4fJKI=|P4yWauJKniptgGC6d6bwKDPRlO Y= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAxmwx9D43hZ9dTgWEmF3bXm X8P0X2vLh/qNYauINXGOd7Q30Wjb02B3mJgF38+Ic0mPJpdQ2WGSlnW15uzY 15BCGZMzoXzNSIKqF2x4TA14Q0plqtOiGr8B0XwVGg2bglUZP/joWEmne/uAe3PZaMP8Ldhx6Lj9fRXmdEDe8t9jNIvKXiqqKu+hMmQSW8qc fwcOknVBqopQd/Sw0eQ5MnahxftHFGJx0h27OlsW8J9mIxqNBxNLOf0gB5WHe3iZ Hs91b6MezvCVBOnDQEwmHqfl7zKYm4io0Mn8Ey2dN9JnoC+tfN 4CxSPVNbiTapaED5ESwSSs0IBi2+o1so+mIlfQ==Delete all of this.  The file will then be empty and that's ok.  A new piece of gibberish :) will be entered when you next try to connect after you respond with a "yes" to a clear prompt.

SSH and all associated files the .ssh folder are standard to modern *nix systems.  Just  google ssh + linux or search these forums.

Your partial delete could not have taken the target off-line, as the target would know nothing of the contents of the .ssh file (until you connect under certain conditions). If something happened it would be a local effect. 

Anyhow.  Make the edit.  The  try from your Tom-Fastjuke:

ssh tom@192.168.0.102.  That will bring up the prompt for yes I mentioned above.  You can connect by entering the password for tom on the jukebox (provided that ssh is properly setup and so this is a good test).

For your info see [http://justinsomnia.org/2007/09/playing-with-rsync-on-ubuntu/](http://justinsomnia.org/2007/09/playing-with-rsync-on-ubuntu/)  Secure passwordless shared key connection the way to go

Once good, proceed with Grsync.

HA

---

### Post by Tom_ZeCat on 2008-09-26
Thanks, man.  I'm getting closer, but still no cigar.  After that Grsync runs, but doesn't have the file permissions to operate.  I got this: 

> rsync: delete_file: unlink "/home/tom/Pent3/SyncTest/bad_girl_rehab-09-orion.mp3" failed: Permission denied (13)
rsync: failed to set times on "/home/tom/Pent3/SyncTest/.": Operation not permitted (1)
rsync: mkstemp "/home/tom/Pent3/SyncTest/.AlbumArtSmall.jpg.SjXHLb" failed: Permission denied (13)
rsync: mkstemp "/home/tom/Pent3/SyncTest/.Anything Anything.mp3.upfpbb" failed: Permission denied (13)
rsync: mkstemp "/home/tom/Pent3/SyncTest/.bad_girl_rehab-01-time_is_now.mp3.uIyTVa" failed: Permission denied (13)
rsync: mkstemp "/home/tom/Pent3/SyncTest/.bad_girl_rehab-02-boy_too.mp3.Bgd54a" failed: Permission denied (13)
rsync: mkstemp "/home/tom/Pent3/SyncTest/.bad_girl_rehab-03-unsnobby.mp3.S8owJb" failed: Permission denied (13)
rsync: failed to set times on "/home/tom/Pent3/SyncTest/.": Operation not permitted (1)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]


I'm thinking the thing to do must be to set the file permissions in the folder on Toms-jukebox to allow another user to write and delete.  Either that or I should chown over the network to take ownership.  I'm not sure how to chown over a network or if you even can.  Gonna try setting liberal file permissions first.

---

### Post by handaxe on 2008-09-26
Yes, it is about permissions.

But remember, when you rsync over ssh into the remote box, you do so as a user of that box and so the permissions at issue are those for the remote user.

If it was from the command line instead of grsync, the command would look +- like:

```
rsync -avz -e ssh remoteuser@remotehost:/remote/dir /this/dir/ 
```

The permissions focus on remote user for remote directory and for whatever user invokes rsync with /this/dir/.

Be careful of being too liberal with permissions, at least tighten them up once past testing. 

HA

---

### Post by Tom_ZeCat on 2008-09-26
Success!  Thank you very much for your help.  I'm going to post what worked so that this thread might help others in the future who do a search.  

It wasn't what I expected.  I went onto the Toms-jukebox PC and opened Nautilus, then right clicked on SyncTest to allow others to write and delete files.  It was all greyed out because I didn't have ownership of that directory even on that PC.  In fact, for ownership, it said, "nobody."  Weird.  So I went into the terminal, changed to the directory above SyncTest, and tried to chown ownership with:

> sudo chown -R tom SyncTest


It asked for my password and didn't complain about anything.  Now here's where it gets weird.  I exited the terminal, then reopened Nautilus and right clicked on SyncTest to try to change the file permissions.  Still no dice!  The ability to change permissions was still greyed out and it still said "ownership: nobody."  

SyncTest is just a test folder.  It doesn't actually have my music collection.  I'm testing this stuff first before I try it with my real music collection.  So I just deleted SyncTest and then recreated it.  I was surprised it let me delete it!  Why would it allow me to do that, but not let me take ownership and then change the file permissions?  

I don't completely understand it, but it worked.  The Grsync operation worked.  I'm going to do some more tests now to make sure it can properly delete a file from Toms-fastjuke via Grsync.  

I looked at the properties of my real music directory, and it said ownership: tom, so I should be able to do this.  We'll see.  Thank you very much for your help in getting me to where I want to go.  

cheers, Tom

---

### Post by handaxe on 2008-09-26
Many prefer still the command line than the graphic interfaces, as they can lag in reflecting changes.

One way you could have checked the permissions issue straight after the chown was (assuming you were in the directory):

```
ls -la
```

Nautilus file permissions still needs some work, AFAICT.  Bulk changes ala chown are not doable.

Glad you got there.

HA

---

