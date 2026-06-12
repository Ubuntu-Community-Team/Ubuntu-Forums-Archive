---
title: "Security Conscious Internet Server for File Syncing/Backups &amp; Remote Desktop/Shell."
date: 2009-10-07
forum: New to Ubuntu
---

### Post by Remagen on 2009-10-07
Well, the title basically says it all.

I recently built a computer from scratch, and I intend to use it as a server to keep files synced between my computers as well as backed up.  

Also, this server will basically be sitting in a corner with only power and Ethernet plugged in, so I'll need some sort of remote capability with it. (I'd prefer having both remote desktop and CLI, but just CLI will do).

Now, I'd go and set up everything myself, right now, but all this will have to go through the Internet.  This means I can't just wantonly set up my backup server, so I'd like some recommendations as to what packages etc you guys think are the best and some security tips. 

Also, I was thinking about installing Fedora on the server (if only to give me some experience with a non-ubuntu distro) but it's cutting edge nature may be a double edged sword as far as security is concerned...

---

### Post by XCan on 2009-10-07
I would have done as I do with my workstation and home computer, setup SSH, change port to a high number to avoid bots/hammering and run rsync. Optionally, if you are concerned about security and is on the move a lot, you could enable your ssh server to only use keyfiles (although if you want to use rsync through ssh you will have to use keyfiles unless you enjoy typing in your password every time you sync). There are also scripts like fail2ban or denyhosts that will automatically block off brute forcers.

---

### Post by Remagen on 2009-10-07
I was figuring on doing something in SSH, like duplicity, but rsync is alright too.

What are key files?

---

### Post by unutbu on 2009-10-07
You can read about "Key-Based SSH Logins" (key files) here:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[http://ubuntuforums.org/showpost.php?p=6532505&postcount=6](http://ubuntuforums.org/showpost.php?p=6532505&postcount=6)

---

