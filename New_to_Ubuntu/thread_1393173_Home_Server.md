---
title: "Home Server"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by chriscms on 2010-01-29
Ok so I am completely new to Ubuntu and linux for that matter. I am trying to use an old computer I had laying around to share files between the computers I have on my network. I have a macbook and a couple windows pcs. I also would like to use the linux computer for back-ups. So basicly I would like to have a very simple server. I have the newest version of Ubuntu desktop already installed on the machine. What is the easiest way to set up this? Would samba work or would I need something else. Any help is greatly appreciated.

---

### Post by danking12 on 2010-01-29
Here are some links for the file server, I haven't used them but most seem to get good comments.

[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)
[http://ubuntuforums.org/showthread.php?t=679805](http://ubuntuforums.org/showthread.php?t=679805)
[http://www.overclockingwiki.org/joomla/blogs/hot_new_products/how_to_make_a_ubuntu_file_server_and_more_part_1..html](http://www.overclockingwiki.org/joomla/blogs/hot_new_products/how_to_make_a_ubuntu_file_server_and_more_part_1..html)

As for backup I am attempting to do something with that for myself right now. I am goind to have a file server as you and then you rsync on the clients to backup on to the file server.

For this I have the advantage that most of my files, ie music, videos and all that are already on a file server, code is source controlled and it is just small personal documents that I tend to backup.

Hope this helps.

---

### Post by jd65pl on 2010-01-29
If you want to back up your mac [this guide]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/") is great for setting up a time machine server on ubuntu.

---

### Post by Morbius1 on 2010-01-29
Open Nautilus
Right click on a directory you own, say /home/your_user_name/Documents
Select "Sharing Options"
Click on all three boxes at first just to test the system
Select "Create Share".

If I remember correctly, if you don't have samba installed, when you try to use "Sharing Options" it will give you an error and prompt you to install it.

---

### Post by 3rdalbum on 2010-01-29
Samba might end off being the best way of doing it, as it's cross-platform.

Samba is quite easy to set up. Install the "system-config-samba" package from Synaptic. Go to System > Administration > Samba and use it to create a share, that anyone can access (or enable "guest" account). It's very easy really.

If you want to add extra security you can use System > Administration > Users And Groups to set up some user accounts for your computers, and then create those same users in System > Administration > Samba, and limit access for your shares to those particular users. However this then leads to each user only being able to access their own files.

Make sure you don't set your share as being "hidden". Macintoshes can't access hidden shares.

---

### Post by Morbius1 on 2010-01-29
I feel obligated to mention that there are two completely different ways to share folders in Ubuntu - Gnome.

The method that 3rdalbum described is now called "Classic Sharing". It's shares are defined in /etc/samba/smb.conf.

The method I described is called "Simple Sharing" ( aka, Nautilus-share or Usershare). It's shares are defined in /var/lib/samba/usershares.

I don't have a religious affiliation with either method but I would recommend that you use only one method at a time. It's not that using both methods together won't work, it's just that you need to keep track of what method is being used to share what folder - using overlapping methods on the same folder, for example.

---

### Post by chriscms on 2010-01-29
So would it be better to follow one of the guides or just manually install the server aspects (ie. samba). I would like to have the gui just because I like that. Or would the better way just to share the files over my network? 

> **jd65pl said:**
> If you want to back up your mac [this guide]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/") is great for setting up a time machine server on ubuntu.

I tried that guide and the nealtalk failed to install. it says there was no location.... does that work on all versions of ubuntu and what should my system be set up as before I do the time machine server?

---

### Post by BitJunkie on 2010-01-29
If all you need is a file server, you might want to look at FreeNAS ([www.freenas.org]("http://www.freenas.org")). It can be booted from a live cd so you can check it out without installing anything. I'm not familiar with macs, so I don't know how well it will work with them.

---

### Post by jd65pl on 2010-01-30
> **chriscms said:**
> 
I tried that guide and the nealtalk failed to install. it says there was no location.... does that work on all versions of ubuntu and what should my system be set up as before I do the time machine server?

I would suggest you haven't followed the instructions correctly, what point are you getting stuck at?

---

### Post by chriscms on 2010-01-30
I got to the very first terminal command and that one i get 2 errors. It is the very first thing so i am not sure what i should have set up before I run the first command

---

### Post by jd65pl on 2010-01-31
> **chriscms said:**
> I got to the very first terminal command and that one i get 2 errors. It is the very first thing so i am not sure what i should have set up before I run the first command

Any chance you can post the errors, its pretty difficult to help without them

---

