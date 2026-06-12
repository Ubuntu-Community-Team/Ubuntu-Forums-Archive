---
title: "File sharing"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by Garthhh on 2010-05-23
I have 3 computers on my home network
1- 9.40 unbuntu pc
1-Mint9 notebook
1-Vista notebook

presently I send any files to my self as email & open them on the pc that is connected to the printer
I would like to be able to just directly copy or open the files, maybe even tidy up a bit across the network
I can see any files in the public file on the pinche vista machine
I'm really more interested in the 2 linux boxes
I know I need some server functionalites
which ones?
what stuff am I looking for on synaptic or where ever?

---

### Post by mikewhatever on 2010-05-23
I think you are looking for the Samba server. You can install it from Synaptic and follow a guide on how to configure it, or just right click the folder you want to share, select 'Sharing Options' and create the share. That will install samba too.

---

### Post by Garthhh on 2010-05-23
> **mikewhatever said:**
> I think you are looking for the Samba server. You can install it from Synaptic and follow a guide on how to configure it, or just right click the folder you want to share, select 'Sharing Options' and create the share. That will install samba too.

Thanks Mike,
as usual it's so easy it escapes me:)

---

### Post by Riaku on 2010-05-23
Dropbox is also good [http://www.dropbox.com/](http://www.dropbox.com/) [http://en.wikipedia.org/wiki/Dropbox_%28storage_provider%29](http://en.wikipedia.org/wiki/Dropbox_%28storage_provider%29)

---

### Post by Garthhh on 2010-05-23
> **Riaku said:**
> Dropbox is also good [http://www.dropbox.com/](http://www.dropbox.com/) [http://en.wikipedia.org/wiki/Dropbox_%28storage_provider%29](http://en.wikipedia.org/wiki/Dropbox_%28storage_provider%29)

I use some of the google tools for sharing
my brothers & sisters use a picasa webalbum for family pics
I've been playing with different collaborative tools for a couple of projects I'm working on

---

### Post by Garthhh on 2010-05-23
> **Garthhh said:**
> I use some of the google tools for sharing
my brothers & sisters use a picasa webalbum for family pics
I've been playing with different collaborative tools for a couple of projects I'm working on

I did quite get there right clicking & enabling share for my home folder on both computers
went to synaptic & I have samba already, but don't see the other computer yet

I did find a problem, I have the same user name for both computers
I guess I have to set up a new user & switch around permissions
be back in a few hours

---

### Post by crjackson on 2010-05-23
> **Garthhh said:**
> I did quite get there right clicking & enabling share for my home folder on both computers
went to synaptic & I have samba already, but don't see the other computer yet

I did find a problem, I have the same user name for both computers
I guess I have to set up a new user & switch around permissions
be back in a few hours

I haven't ever done this most basic task before, but I'm watching with interest.  Let me know when / how you get it working.  I'd like to do the same here.

---

### Post by mikewhatever on 2010-05-23
> **Garthhh said:**
> I did quite get there right clicking & enabling share for my home folder on both computers
went to synaptic & I have samba already, but don't see the other computer yet

I did find a problem, I have the same user name for both computers
I guess I have to set up a new user & switch around permissions
be back in a few hours

You could probably still access the shares by typing into Nautilus' address bar, something like smb://192.168.100.20/, or whatever the address is. Once you've accessed the share, add a bookmark to the panel so that you wouldn't have to type again.

---

### Post by Garthhh on 2010-05-23
> **mikewhatever said:**
> You could probably still access the shares by typing into Nautilus' address bar, something like smb://192.168.100.20/, or whatever the address is. Once you've accessed the share, add a bookmark to the panel so that you wouldn't have to type again.

what address am I typing in & how do I find it?

I went here
[https://help.ubuntu.com/10.04/internet/C/networking-share]("https://help.ubuntu.com/10.04/internet/C/networking-shares.html")s.html

still don't get it
so I went here
[http://library.gnome.org/users/shares-admin/stable/tool-introduction.html.en](http://library.gnome.org/users/shares-admin/stable/tool-introduction.html.en)

I'm getting this error
'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.

---

### Post by Garthhh on 2010-05-23
now if I go to network I can see the files for this computer on this computer
& the files for the other computer on the other computer
which I could do before sharing....
am I missing a step or something?

---

### Post by mikewhatever on 2010-05-24
> **Garthhh said:**
> what address am I typing in & how do I find it?

You have to type the address of the computer you want to access. Something internal, I suppose. If that way is used, it's best to assign static ips to all.

> I'm getting this error
'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.

Had the same error here on Karmic. Had to edit /etc/samba/smb.conf, '#security=user' --> 'security=share'.

---

### Post by Garthhh on 2010-05-24
> **mikewhatever said:**
> You have to type the address of the computer you want to access. Something internal, I suppose. If that way is used, it's best to assign static ips to all.



Had the same error here on Karmic. Had to edit /etc/samba/smb.conf, '#security=user' --> 'security=share'.

I'm slow & new:)what do I do to make the change?

---

### Post by mikewhatever on 2010-05-24
> **Garthhh said:**
> I'm slow & new:)what do I do to make the change?

You'll need to open the file for editing with admin privileges:
```
gksudo gedit /etc/samba/smb.conf
```

Find the appropriate line and edit as suggested. When done, run the following to restart samba:
```
sudo /etc/init.d/samba restart
```

---

### Post by Garthhh on 2010-05-24
thanks & I'll probably end up coming back to the code you've so generously provided

But I want to try to show other ex windows users how cool all this unbuntu stuff is
I can't realistically expect newbies to have to go to terminal at the drop of a hat

I went to preferences & clicked on file sharing, got an error, indicating software was missing
I went to synaptic did a search for file sharing, Gshare was suggested, so I installed
gave it a shot, didn't work
did a search on the d[ocumentation for 10.0]("https://help.ubuntu.com/10.04/index.html")4 & found
[this]("http://library.gnome.org/users/gnome-user-share/stable/gnome-user-share-getting-started.html.en#gnome-user-share-enabling-sharing")
I also tried [this]("https://help.ubuntu.com/9.10/internet/C/networking-shares.html")
I'm certainly confused as to why there is at least 2 different ways through the GUI to share & the only computer I can see is running vista:confused:

---

### Post by Sovereign Entity on 2010-05-25
I had the same problem with Ubuntu a few versions back. I switches to Super Ubuntu and everything worked out of the box.Super Ubuntu or Super OS as it is now known is nother more than Ubuntu tweeked

---

### Post by mikewhatever on 2010-05-25
> **Garthhh said:**
> 

But I want to try to show other ex windows users how cool all this unbuntu stuff is
I can't realistically expect newbies to have to go to terminal at the drop of a hat

Who are these ex-windows newbies, and why would they have to use the Terminal? Keep in mind, Ubuntu is cool, but not perfect.

> 
I went to preferences & clicked on file sharing, got an error, indicating software was missing
I went to synaptic did a search for file sharing, Gshare was suggested, so I installed
gave it a shot, didn't work
did a search on the d[ocumentation for 10.0]("https://help.ubuntu.com/10.04/index.html")4 & found
[this]("http://library.gnome.org/users/gnome-user-share/stable/gnome-user-share-getting-started.html.en#gnome-user-share-enabling-sharing")
I also tried [this]("https://help.ubuntu.com/9.10/internet/C/networking-shares.html")
I'm certainly confused as to why there is at least 2 different ways through the GUI to share & the only computer I can see is running vista:confused:

There are usually several way to accomplish the same goal, sometimes with gui tools, and sometimes through cli. There are also several way, apart from Samba to achieve file sharing.:P Ssh is a good alternative I chose after having to troubleshoot samba along the lines posted earlier.

---

### Post by Garthhh on 2010-05-27
> **mikewhatever said:**
> Who are these ex-windows newbies, and why would they have to use the Terminal? Keep in mind, Ubuntu is cool, but not perfect.



There are usually several way to accomplish the same goal, sometimes with gui tools, and sometimes through cli. There are also several way, apart from Samba to achieve file sharing.:P Ssh is a good alternative I chose after having to troubleshoot samba along the lines posted earlier.

I would be that newbie
I haven't had any success when I'm trying to find a line & edit

I can use terminal on a limited basis
I would like to install unbuntu/mint for some friends

I probably am just missing something on the file sharing through the GUI
for now I'll stick with emailing files to myself, because I can make it work & understand the procedure
it would be great to share the printer, not until I can share...

Kind of reminds me of using open office, does everything, but figuring it out is problematic, incomplete help or how tos

still better than yelling at my wife's vista box

---

### Post by mikewhatever on 2010-05-27
Are you saying you couldn't find the 'security=user' line? Let me quote it in the context:
```
####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
**#   security = user**

```

Best of luck, whatever way you use.

---

### Post by Garthhh on 2010-05-27
> **mikewhatever said:**
> Are you saying you couldn't find the 'security=user' line? Let me quote it in the context:
```
####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
**#   security = user**

```Best of luck, whatever way you use.

sorry to be a pain
could you do a step by step for me/us

---

### Post by mikewhatever on 2010-05-27
Open Applications->Accessories->Terminal and copy/paste the following command:
```
gksudo grdit /etc/samba/smb.conf
```
enter your password when asked, then in the text file that opens find the following line - 
**#   security = user** - and change it to **   security = share**
 save and exit.
Again in a Terminal window, restart samba with:

sudo /etc/init.d/samba restart

Now, try creating a share in Ubuntu as suggested above.

---

