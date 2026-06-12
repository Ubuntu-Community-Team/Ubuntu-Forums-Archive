---
title: "merging old home folder with new, after fresh install + new user name"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by snoopy-2009 on 2011-04-07
wow.. so im extremely sorry for posting such a seemingly simple question, but i just spent the last 20 mins googling, and nothing i found really hit the spot..and 15 before that moving my files back and forth.. mostly running into the result of my old usr folder being INSIDE my new one, along with all the documents, downloads, etc dirs..

what im looking for is the simple cmd line of  'sudo mv -f '  (i believe, would do the best)  to merge my old /home/$USR dir into my new one, replacing all, no prompt (as of now its just the empty 10.04 file structure)

i also saw somthing about rsync? not sure if that has anything to do with this... i think if i could just get the right move cmd  (maybe with or without some dashes ' / ' or maybe adding ' /* ' ? ) i think it would work fine, it seems the files move just fine with terminal...

pre-thanks!


```
[SIG]
The Wrong Channel
twc-tech_support@1337b0x

Ubuntu 10.04 LTS AMD64
```

---

### Post by searchfgold6789 on 2011-04-07
So... Why not just copy all of the files and folders from your old home to your new?
Also I wouldn't use sudo for this particular purpose because then you will be unable to access your freshly copied/moved files and folders unless you are root.
To move recursively (this can move entire folders and the data inside):```
mv -r -f /location1 /location2
```
To copy recursively:```
cp -r /location1 /location2
```

---

### Post by deathadder on 2011-04-07
It's probably easiest to move all of the files using mv and then reset ownership:
```
$ mv -f /home/old_user/* ~/
$ mv -f /home/old_user/.* ~/ 
$ sudo chown -R new_user:new_user *

```
The first mv command moves all files, the second moves all hidden files. The chown command will change it so that your new user is the owner of the files.

Typically rsync is used for backup solutions etc

---

### Post by vanadium on 2011-04-07
If the fresh install is just the same Ubuntu version as before, why not just rename the old home folder to the new username?

Otherwise, it is unwise to just copy the old home folder into the new one. There is no guarantee that config files from older versions will still work with newer versions (usually there won't be a problem, but there is *no* guarantee).

In that case, just move your own user data (e.g. /home/oldusername/Documents, /home/oldusername/Music, )... to the new account. You can do this simply with the file browser (this is the "Absolute Beginner's" section, isn't it?).

---

### Post by snoopy-2009 on 2011-04-08
thanks for all the help... the problem i was running into, was when i did the copy or move commands, it would actually copy/move the ENTIRE folder INTO the destination folder.... instead of staying one dir back, and merging the folders together.. i hope this clarified my first post..

thanks again for the previous help!

---

### Post by snoopy-2009 on 2011-04-08
jeez.. sorry, maybe one more attempt to be sure...lol


when i ran the copy command to move contents from /home/OLD_USR into /home/NEW_USR

i would end up with:
/home/NEW_USR/OLD_USR

this is what i was trying to ask how NOT to do? ..and i imagine it has to do with leaving-off OR adding a slash on the end of the source string, and/or maybe an asterik? or vise-versa with the target string..?

---

### Post by deathadder on 2011-04-08
Ah ok, what you needed to do was add a /* on the end of your command, that'll reference all regular folders / files within OLD_USR instead of OLD_USR itself.

The / on the end tells the shell your looking at the contents of the folder and not the actual folder, while the * is a wildcard to mean everything. 

If you've still got OLD_USR within NEW_USR you can simple move everything up one level like so:
```

~/NEW_USR$ pwd
/home/NEW_USR
~/NEW_USR$ mv -f OLD_USR/* .

```

---

### Post by deathadder on 2011-04-08
> **vanadium said:**
> In that case, just move your own user data (e.g. /home/oldusername/Documents, /home/oldusername/Music, )... to the new account. You can do this simply with the file browser (this is the "Absolute Beginner's" section, isn't it?).
Yeah you can, and for new users a file browser is the better method. However the OP indicated they were using a shell to do it so it made sense to tell them how to use the shell to get it done.

---

