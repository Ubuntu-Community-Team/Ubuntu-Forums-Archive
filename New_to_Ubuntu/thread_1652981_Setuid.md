---
title: "Setuid"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by joey711 on 2010-12-26
Ok, so I'm new to Linux. I am dual booting Win7 and Ubuntu 10.10. When I first installed Ubuntu, I set up my files and chat and the next thing I tried to do was edit the unsightly boot screen. I followed some directions online, which involved editing some files and changing permissions. I ended up having to change my permissions on /usr so I could put a picture in there somewhere to use as the background for the boot screen. I got it all set the way I wanted and everything seemed to be working. Now, whenever I try to use the software center to install or uninstall anything, I get a popup that says "To install or remove software, you need to authenticate." Sometimes this box pops up and shakes violently for about a second and then vanishes, other times it stays there and the only way to get rid of it is to close it (clicking the authenticate or cancel button does nothing). When I went to the terminal to try some fix I found for this, I got "sudo: must be setuid root" and can't do anything. I have seen fixes for this that involved booting into the recovery console, however when I was formatting my boot screen the way I wanted, I removed every option but those for Ubuntu and Windows 7, so I can't get into recovery mode that way. This is frustrating me, as I am normally pretty good with computers, and making me want to just not mess with Linux if it is really this hard to get working. I would rather not reinstall Ubuntu. In fact, if I uninstall it I think I will just leave it like that. It would be a shame because I spent so much time trying to get my harddrive to defrag correctly so that I could partition it. If anyone has seen this before or has any ideas please let me know.

---

### Post by Gone fishing on 2010-12-26
Mmm be careful when you use chown if you changed the ownership of the whole /usr directory you will have done some damage. I suggest that you set the ownership of the directory back to root

as you've broken sudo you will need to do this from a live cd. So boot from a live CD

and then run the following

```
sudo mkdir /media/sillyme
sudo mount /dev/hda1 /media/sillyme
sudo chown -r root /media/sillyme/usr
sudo umount /media/sillyme
```

Assuming the ubuntu / (root directory) is on /dev/hda1 if not adjust as needed

I don't know that this will work I am guessing yes as I am guessing the entire contents of /usr should be owned by root (I think that's a good guess).

What you should have done is become root using sudo and then changed the files you wanted to change in /usr

---

### Post by joey711 on 2010-12-26
> **Gone fishing said:**
> Mmm be careful when you use chown if you changed the ownership of the whole /usr directory you will have done some damage. I suggest that you set the ownership of the directory back to root

as you've broken sudo you will need to do this from a live cd. So boot from a live CD

and then run the following

```
sudo mkdir /media/sillyme
sudo mount /dev/hda1 /media/sillyme
sudo chown -r root /media/sillyme/usr
sudo umount /media/sillyme
```Assuming the ubuntu / (root directory) is on /dev/hda1 if not adjust as needed

I don't know that this will work I am guessing yes as I am guessing the entire contents of /usr should be owned by root (I think that's a good guess).

What you should have done is become root using sudo and then changed the files you wanted to change in /usr

I have already done this and changed ownership of everything in /usr to root.

---

### Post by Gone fishing on 2010-12-26
Did you use the -r switch when you used chmod command? What is the permission of /usr/bin/sudo?

Post edit also remember if you use a live CD the live CD has its own /usr as well as the mounted /media/sillyme/usr 

Sorry if you've not made any mistakes but I'm just checking

---

### Post by joey711 on 2010-12-26
I did use the -r switch, and /usr/bin/sudo is owned by root

---

### Post by Gone fishing on 2010-12-26
Also if you changed the permissions of the /usr directory graphically - I've found this usually doesn't change the permissions of the sub folders.

---

### Post by joey711 on 2010-12-26
> **Gone fishing said:**
> Also if you changed the permissions of the /usr directory graphically - I've found this usually doesn't change the permissions of the sub folders.

what do you mean by graphically? I'm pretty sure I changed everything back to being owned by root that should have been. And the -r switch takes care of subfolders, right?

---

### Post by mcduck on 2010-12-26
Sad to tell you, but recovering the correct permissions will not be as simple as chowning the ownership to root.

While most of the files in /usr are owned by root and have pretty standard permissions, there's plenty of stuff that requires other ownership or different permissions.

While in theory it would be possible to get a list of the correct permissions and ownership for all the files, and then manually change them back while running from a Live-CD, it would actually be a lot less work to just backup all your personal files and reinstall Ubuntu.

..and next time you need permissions to do something, don't change the ownership/permissions of system files and directories. Change your *own* permissions. That's what the sudo command is for. [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Edit:
So, instead of running a command as root to change the ownership of some directory so that you can write there as your normal user, you should just leave the ownerships alone and do the *writing* as root.

Instead of this:
```

sudo chown youruser:youruser /some/system/directory
mv somefile /some/system/directory/somefile
```

just do this:
```

sudo mv somefile /some/system/directory/somefile
```

(..or just run "gksudo nautilus" to open the file manager as root, giving you a graphical tool for moving files anywhere you want. Be very careful with that, though. :D)

---

### Post by Gone fishing on 2010-12-26
When I said graphically I meant using nautilus you didn't do that - sorry.

I'm afraid mcduck is probably right as changing /usr to root hasn't fixed it.

I was wondering about trying one last time in single user mode with a root prompt. At the grub screen press escape edit the entry (click e) and change the ro to rw init=/bin/bash then boot with contro x when it boots chmod -r root /usr

---

