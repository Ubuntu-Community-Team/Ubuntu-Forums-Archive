---
title: "how to change computer owner name"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by mystmaiden on 2011-03-30
I've found how to change the name of the computer and how to change the owner of individual files, but what I need to do is change the owner name - without setting up another user, etc so that instead of mystmaiden@hal it'll say xyz@hal. Everything else can stay the same, just need to change that. Is there a command line that will do that?

thanks 


mystmaiden

---

### Post by 5149.5 on 2011-03-30
Huh? My computer doesn't have an owner name that I know of. Who told you to change your owner name?

---

### Post by Frogs Hair on 2011-03-30
I also have computer and user name . You can change permissions from System > Administration > Users and Groups > Advanced Settings

---

### Post by mystmaiden on 2011-03-30
Thanks for the replies. No one 'told' me to change the owner name. The hd is a clone of another machine on my network and I just want it to have a different computer and owner name for clarity.

I'll have a look at that Frogs Hair and see if I find what I need. 

Edit - If I just rename home/mystmaiden to home/somethingelse will everything on the computer then be owned by 'somethingelse'? (this is what I'm after)

---

### Post by 5149.5 on 2011-03-30
> **mystmaiden said:**
> Thanks for the replies. No one 'told' me to change the owner name. The hd is a clone of another machine on my network and I just want it to have a different computer and owner name for clarity.

I'll have a look at that Frogs Hair and see if I find what I need.

So change  the computer name using the hostname command. There is no such thing as owner name.

---

### Post by crispy_420 on 2011-03-30
My guess would be that changing the user's home folder to another name would be a bad idea. Why not create a new user and move what you want over to the new profile?

Owner name? Never heard of that until right now but will check it out when I get on my Ubuntu system.

---

### Post by Ghost_Mazal on 2011-03-31
I think what he is actually asking is how to rename his username.

---

### Post by deathadder on 2011-03-31
If you want to rename your user you can do so with the usermod command:
```
usermod -l new_name old_name
```
However, the user needs to be logged out, so you'll need to boot into single user mod. I'm not sure what this will do with the permission etc on the home directory, so you may need to reset permissions anyway (see below). A simpler (IMHO) solution would be to create a new user via the "System->Administration->Users and Groups" menu option and then copy all the files across and change permissions.

Lets say I (username adam) have just created a new user (bob). You'll need to open a terminal and cd into the new home directory:
```

adam@adamj-VB:~$ cd /home/bob/
adam@adamj-VB:/home/bob$ ls -la
total 8
drwxr-xr-x 2 bob  bob  4096 2011-03-31 10:54 .
drwxr-xr-x 4 root root 4096 2011-03-31 10:52 ..
adam@adamj-VB:/home/bob$
```
Here you can see the newly created users directory is empty (you may have some default folders / files). Now you'll need to copy the files across like so.
```
adam@adamj-VB:/home/bob$ sudo cp -r /home/adam/* .
cp: cannot stat `/home/adam/.gvfs': Permission denied
adam@adamj-VB:/home/bob$ sudo cp -r /home/adam/.* .
cp: cannot stat `/home/adam/./.gvfs': Permission denied
cp: will not create hard link `./adam' to directory `./.'
cp: cannot copy a directory, `/home/adam/..', into itself, `.'
cp: cannot stat `/home/adam/.gvfs': Permission denied

```
Now if you list the directory you will see a number of files:
```

adam@adamj-VB:/home/bob$ ls -a
.              .config           .fontconfig      .ICEauthority  .profile                   Templates                 .wireshark
..             .dbus             .gconf           .icons         programming_challenges     test.sh                   .xsession-errors
.bash_history  Desktop           .gconfd          .local         Public                     .themes                   .xsession-errors.old
.bash_logout   Documents         .gksu.lock       .mozilla       .pulse                     .thumbnails
.bashrc        Downloads         .gnome2          Music          .pulse-cookie              .vboxclient-display.pid
.cache         .esd_auth         .gnome2_private  .nautilus      .recently-used.xbel        .vboxclient-seamless.pid
.compiz        examples.desktop  .gtk-bookmarks   Pictures       .sudo_as_admin_successful  Videos
```
However, all of those files will be owned by the root user. So we'll need to reset the permission:
```

dam@adamj-VB:/home/bob$ sudo find ./ -type f -exec chown bob:bob {} \;
adam@adamj-VB:/home/bob$ sudo find ./ -type d -exec chown bob:bob {} \;
adam@adamj-VB:/home/bob$ ls -l programming_challenges/
total 4
drwxr-xr-x 2 bob bob 4096 2011-03-31 10:56 chang_1
adam@adamj-VB:/home/bob$
```
Now the new user, bob, owns all of the files and directories in /home/bob.

Simply log out, and login as the new user.

---

### Post by Ghost_Mazal on 2011-03-31
Can I ask something , at the last step why not simply use the chown command:

```
sudo chown -R usernam:username /home/username
```

This worked for me when I shifted to new pc.

---

### Post by deathadder on 2011-03-31
Simply because I've always done it that way :) 

I tend to use find with chmod, not chown, to change file and directory permissions to different values. I guess I'm just stuck in the habit of doing it that way, but you're right a single chown makes more sense.

---

### Post by mystmaiden on 2011-03-31
Thanks everyone for the replies, very helpful!! I'll give it a whirl this evening.

---

