---
title: "Making a standalone home fileserver, best options?"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by ovid9 on 2010-01-31
Ok, please bear with me.  I had a system set up with FreeNAS, but I did something wrong and broke it losing the data I was getting ready to put back on my main machine.  Since I know more linux, and ubuntu than I do freebsd(yeah, i know none) I was wondering if I could accomplish the same thing using Ubuntu.

I have an old Dell desktop.  It has 2 harddrives in it, an 80 gig and a 40gig.  I want to use it as a general file backup system.  Back up my /home there, back up my data and music files, as well as access data & music from the laptop.

Here's what I was thinking and if any of you have better ideas, I'm open.  I am slightly above a *complete* novice in Ubuntu and a complete novice when it comes to networking.

1.  Install Ubuntu on the old desktop.  Get it set up, partitioned correctly etc.

2.  Create folders for my various shares: music_share, data_share, backup_share, etc.

3.  Change permissions of the share folders to be "shared" which would allow the other computers on my home network to access them.  

4.  Copy files to the shared folders and go along my merry way.

5.  Every so often hook the monitor & keyboard back up to the desktop to update Ubuntu and make any necessary changes.


So, my 2 questions are:  Would this work?  And would there be a simpler way to turn my old desktop into a remote storage device without learning an entirely new system?

---

### Post by llamakc on 2010-01-31
If you install openssh-server on it, you can just ssh into it and update it from the CLI.

---

### Post by ovid9 on 2010-01-31
> **llamakc said:**
> If you install openssh-server on it, you can just ssh into it and update it from the CLI.


I know what SSH is and thanks to google I know what CLI is.  Cool.

Obviously doing this is going to require me learning new things.  I don't have a problem with that, I love doing that.  However, its nice to have a base to go off of already.

Thanks.

---

### Post by mrtomservo on 2010-01-31
I have 3 headless Ubuntu servers in my house.  I too recommend ssh for logging in to maintain it.  For the serving part, it depends on how you will be accessing your files.  If from windows, you'll probably want Samba or FTP, if linux, then you should be able to just use ssh with nautilus (default Gnome file manager) to access the files in your file manager like you would local files.  On some Ubuntu's you can find this under "Places->Connect to server" then enter the ip and ssh as the protocol, username and there ya go!

---

### Post by ovid9 on 2010-01-31
And thanks for additional info.  The headless system is exactly what I'm trying to do.  I'm still using 8.04 and probably will be until a month or so after the next LTS comes out.  

At my rate of getting my computing needs taken care of around here, I'll either get it set up with 8.04 and then update or, wait til the next LTS is released and start then.   

Thanks again!

---

### Post by mrtomservo on 2010-01-31
Oh yeah, sounds silly, but don't forget before you pull the monitor and keyboard that you change stop boot on errors in your bios.  Otherwise if it doesn't detect a keyboard, it might not boot. And 8.04 should work perfectly.  I have one 8.04, one 9.04, and one 9.10.  Really, all are outrageously stable. :)

---

