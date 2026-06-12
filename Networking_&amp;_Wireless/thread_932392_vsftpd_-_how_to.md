---
title: "vsftpd - how to"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by skozzy on 2008-09-28
Just after some starter tips setting up vsftpd

I don't want anon access, I want to share files and folders on other drives (not the ubuntu install drive) and have some user accounts for mates (without having to add users to my ubuntu desktop.

I normaly have a old computer with win xp running filezilla server, being used to point and click software I find it hard to get the inital grasp on playing with configs, but not saying I can't learn though.

I just need something to get me started. After installing vsftpd I see only one file to edit in /etc/vsftpd.conf but inside that I don't see how to setup  usernames and shares.

Will someone spare the time to give me starter.

---

### Post by fwre01 on 2008-09-28
When i set up my VSFTP server i used local usernames, and assigned them a false shell so they couldnt log in via ssh. Then set up the file permissions accordingly.

Are you looking for a common dir to share for all users? or for each user to have access to his/her home dir?

EDIT: I found this useful when writting my vsftp.conf to see what all the options mean

[http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)

---

### Post by skozzy on 2008-09-28
Here is an example:
Friends names I want to have access: Brett, James, Colin and Skozzy (myself), each user a different password

Folders to share:
/media/750gig/sci-fi/ (read only)
/media/500gig/mp3/ (read only)
/media/200gig/uploads/ (read/write/mkdir/deldir etc...)

So all my mates can access/share same folders and upload to a common folder

If this were windows I would have no problem using IIS or Filezilla Server adding groups and users and virtual folders. I find many programs on linux lacking the "fresh from windows OS" kind of instruction documentation. I learn quick but need a hand up on something new.

Just so you know, I have port 20,21 on the router setup and working when I boot to Windows XP to run FTP. If I need to I will install firestarter (I tinkled witht he gui on it and it wasn't too bad). But if I don't need to install it then I won't.

I looked over what docs I could find for vsftpd and can't see any mention about a seperate config for users or for virtual folders. But I'd guessing there would need to be somewhere.

---

### Post by fwre01 on 2008-09-28
Users are handled by the operating system, you dont (or at least i didn't) create users with VSFTP.

Here's an example of how i built mine, say I had 3 Users, Aaron, Matt and John. I created these users on my server, and placed them all into a group called FTPUSERS. 

Then i configured my share(s) /fileserver/Documents. The files in the dir were Owned by Me, and the Group was FTPUSERS which had read-only access. (read up on linux file permissions if you are unsure of how to do this). 

So, then, in my vsftp.conf file i defined the folder which they were able to access, and chrooted them to that folder (meaning they cant leave that folder)

....and thats kind of it! the main thing is that you set up your file permissions properly on your server. remember file permissions look like this <owner><group><public>. The other basic thing i did was deny them an SSH shell (i cant remember off the top of my head how i did that)

Does your server sit behind a firewall/NAT box already?

---

