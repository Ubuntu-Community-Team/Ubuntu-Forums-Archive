---
title: "Network Drives don't show in Nautilus"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by dstjohn on 2010-01-04
When I try to add a profile picture in THIS forum,
the 'browse' access my list of files but the network files do not show.

they show in Open Office and on Places but not on 'browse'.
:confused:

---

### Post by Temposs on 2010-01-04
This is a problem with the file chooser in Firefox and a few other programs. You simply can't see network drives in Firefox in the normal way as of yet.

Here's a workaround:
Make sure your network drives are mounted. That is, you open a regular Nautilus Window and can see them with the Eject button. Then, in Firefox, open the filechooser from somewhere, and go to 

```
~/.gvfs
```

Inside that directory, you should see your mounted network drives. you can choose any file you like on your network drives from this access point. Yeah, it's a bit annoying, but it's the only way to do it right now.

---

### Post by ylucas on 2010-01-13
Thanks, I knew the shares were mounted somewhere, but unable to find this hidden folder in my home folder.

Why this is not mounted in a non hidden folder???

A trick to have a plain visible folder is to create a symlink:

ls -s /home/MyHomeFolder/.gvfs /home/MyHomeFolder/netshares 

Then the "netshares" folder will be visible to all applications
( "netshares" or any name you want, I personally used the windows workgroup's name)

---

### Post by Andy_Dempster on 2010-01-14
> **ylucas said:**
> Thanks, I knew the shares were mounted somewhere, but unable to find this hidden folder in my home folder.

Why this is not mounted in a non hidden folder???

A trick to have a plain visible folder is to create a symlink:

ls -s /home/MyHomeFolder/.gvfs /home/MyHomeFolder/netshares 

Then the "netshares" folder will be visible to all applications
( "netshares" or any name you want, I personally used the windows workgroup's name)

Sorry to be a pain; the actual command is:

ln -s /home/*yourname*/.gvfs /home/*yourname*/netshares - took a newb (*me!) a while to figure this out! Thanks for the tip though; works a treat.

Andy

---

### Post by PJSingh5000 on 2011-10-18
--

---

### Post by oldos2er on 2011-10-19
Closed. If you have a question or problem please start a new thread.

---

