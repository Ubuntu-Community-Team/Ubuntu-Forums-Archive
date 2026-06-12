---
title: "nfs not working"
date: 2015-02-13
forum: Networking &amp; Wireless
---

### Post by Old Jimma on 2015-02-13
Hi Community:

A few days I set up NFS file sharing using the howto at [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo"). I was able to share the home folder (and everything in it) that is on one of my ubuntu 1.04 machines with my ubuntu 14.04 laptop.

Then yesterday everything stopped working! :( 

I followed the NFS howto to a "T":

After updating my server, I used
> 
# apt-get install nfs-kernel-server
# mkdir -p /export/users 
# mount --bind /home/philipsmith /export/philipsmith


and in the /etc/fstab file I put the line

> 
/home/philipsmith    /export/philipsmith   none    bind  0  0

and in the /etc/exports file I put the lines
> 
/export           192.168.1.74(rw,fsid=0,insecure,no_subtree_check,async)
/export/philipsmith 192.168.1.74(rw,nohide,insecure,no_subtree_check,async)
[QUOTE]

I made sure that  /export and /export/philipsmith had 777 permissions.

Then, after updating my client computer, on the client side, I used
[QUOTE]# apt-get install nfs-common 

and then added 
> 192.168.1.67:/   /mnt   nfs    auto  0  0
to the client's /etc/fstab

I saved copies of the /etc/fstab and /etc/exports on the server and the /etc/fstab on the client in another folder so that I could refer to them another time.... like in an installation.

However, when I trie to access /mnt/philipsmith on the client side now I get the message "access denied."

On the server, I did a 
> # showmount -e 192.168.1.67
and get the response
> 
Export list for 192.168.1.67:
/export/philipsmith 192.168.1.74
/export             192.168.1.74



How do I get nfs to share my home directory? (There are many files there.) :?

Thanks,
Old Jimma from the Old Country

---

### Post by TheFu on 2015-02-13
Didn't look any further ...
s/a sync/async/g

---

### Post by Old Jimma on 2015-02-13
Hi Fu:

What does your email mean?

Thanks!
Jimma

---

### Post by SeijiSensei on 2015-02-13
I'm pretty sure he was pointing to this typo in /etc/exports:
```
/export/philipsmith 192.168.1.74(rw,nohide,insecure,no_subtree_check,a sync)
```
It should read "async" not "a sync".

---

### Post by TheFu on 2015-02-14
> **SeijiSensei said:**
> I'm pretty sure he was pointing to this typo in /etc/exports:
```
/export/philipsmith 192.168.1.74(rw,nohide,insecure,no_subtree_check,a sync)
```
It should read "async" not "a sync".

Correct.

---

### Post by Old Jimma on 2015-02-14
[COLOR="#FF0000"]**[SIZE=7]YES!!![/SIZE]**[/COLOR]

That was exactly the problem! 

While there did not seem to be a space between "a" and "sync" in the /etc/exports file, when I retyped "async" in all locations in that file, and rebooted nfs started working perfectly!

This always has seemed to have been the problem when I had "problems" with nfs.... it always boiled down to mistyped words in the command that I couldn't see, either because I'm an old man, or because of glitches in the file gedit displays.

Many thanks to The Fu and  SeijiSensei's.

One of these days I'm going to retire and figure out how to give back to my wonderful Ubuntu Community. If somebody has suggestions, I'm definately open. Maybe I can work on an "install fest" down at GA Tech.

Many Thanks AGAIN,
Old Jimma from the Old Old Country

---

### Post by TheFu on 2015-02-14
ATL Area LUGs:
* ALE
* ALE-NW - I organize the InstallFest for this annually. Former organizer.
* GA-400 Linux - Co-organizer

I attend most of these.  They also have email lists to help others and answer questions.

You aren't the first person to be bit by a typo.  Seems to me that gedit proportional fonts are the issue. Everyone knows you should be using VIM, right? ;) I joke, but ...

---

### Post by SeijiSensei on 2015-02-14
I use [jed]("http://www.jedsoft.org/jed/") myself coming from an Emacs background.  It's in the repositories.  I would definitely avoid using anything other than a monospace font in a plain text editor.

---

