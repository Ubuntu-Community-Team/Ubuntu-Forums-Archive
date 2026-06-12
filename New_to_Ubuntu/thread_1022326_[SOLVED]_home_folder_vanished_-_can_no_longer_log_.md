---
title: "[SOLVED] home folder vanished - can no longer log in"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by al.adab on 2008-12-26
hello,

I was in the process of installing "sunbird" on Ubuntu 8.04 (in terminal) - the command I was giving began with "sudo mv..." - and all of a sudden my home directory disappeared.

Is it somehow possible to do an emergency log in and recover my files? Or have they been wiped out my HD? When I attemp a log in a get the following message:

"your home directory is listed as: '/home/tutuanddani' but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely (...)". 

If I click on "yes", I get a message "User's $HOME/.dmrc file is being ignored (...)". A second message informs that "/etc/gdm/Xsession: Beginning session setup...can't create directory...".

Can anyone PLEASE help. Thanks!

---

### Post by mkvnmtr on 2008-12-26
Boy I have seen a lot of requests for help and made a few but I have never seen one as bad as yours. I don't Know what to do but I will be watching son that when I do it I will have a place to start. If you remember the exact command you should put it in a post so someone can help you. If you dont see if you can find it in a log. Good luck.

---

### Post by OutOfReach on 2008-12-26
Looks like you moved your homefolder somewhere, hopefully you didn't delete it.
Can you give us the instructions that you used to install Sunbird?

---

### Post by unutbu on 2008-12-26
Check /tmp for your home directory first. Note that rebooting can erase files/dirs in /tmp, so be sure your home dir is not there before rebooting. If you find your home dir in /tmp, then **do not reboot**, post back and we can work from there.

If it isn't there, then keep reading...

Open a terminal (Accessories>Applications>Terminal) and type
```

find / -user tutuanddani -print 
```

If you do not have a gnome panel, then press Ctrl-Alt-F2. This will give you a text console. Login there. Then type the above command.

This will search your root filesystem for any file owned by tutuanddani. 
This command may take a while to run.

Hopefully, after a bit, a whole slew of files will be printed.
If you recognize them as your home directory files, you can press Ctrl-C to quit the find command. 

Copy down the path to one of the files listed in the output and post it here.
We can then supply you with the right command to move your home directory back to 
/home/tutuanddani.

---

### Post by ercferret18 on 2008-12-26
wow, that is really weird...

---

### Post by melojo on 2008-12-26
Shouldn't he or she still be able to login even if the home directory has been moved.  If so can you do a search for the folder and move it back.

---

### Post by al.adab on 2008-12-26
Thanks so much for your support!
Here's what I got (hope I picked up the righ path):

/opt/tutuanddani/.openoffice.org2/user/uno_packages/cache/uno_packages/86CTHV_/wiki-publisher.oxt/licence/LICENSE_sv

The print goes on so fast I can hardly make out my home directory files, but I seem to remember that OpenOffice is one of them...

Thanks again!

---

### Post by jerome1232 on 2008-12-26
so it sounds like you just moved your home folder to /opt you can do a ls /opt/tutuanddani to list the folders there and see if it really is your home folder, if it is you can move it back like this

```
sudo mv /opt/tutanddani /home
```

Then ensure it's still owned by you (I think mv preserves permissions but I don't remember, so this may be unnecessary)

--edit--- forgot -R flag on chown, I'm pretty sure chown isn't necessary though
```
sudo chown -R tutanddani:tutanddani /home/tutandddani
```

---

### Post by al.adab on 2008-12-26
Thanks Jerome1232 I'll be eternally grateful :)

I can now log in, except that:

a) all the icons from my desktop have disappeared - no response if I right-click on the desktop;
b) all the applications seem to work fine - if I go to start>places>home, I get the following message: 

"Error - could not open the location 'file///home/tutuanddani' - there is no default action associated with this location"

c) if I try to open my home folder from an icon I've got on the panel on the desktop, I get a different message:

"Could not launch application - failed to execute child process 'nautilus' (no such file or directory)"

Can you help further?...thanks!

---

### Post by al.adab on 2008-12-26
well, I re-installed Nautilus from Synaptics and now things are back in place. Thanks again for all your support!

---

