---
title: "Need help using cp to copy to folder with same file"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by holdie on 2008-12-21
So I'm basically trying to use a * to go through a bunch of folders and extract a torrent file from them and place the file in one folder so I can open them all at once...

the problem is, all of the files are simply called "torrent" (damn you ktorrent)...

Naturally, cp returns an error when I try this out, saying it doesn't want to overwrite the file that already exists in my target folder after the first copy has taken place

Is there a way to get cp to append a different number for each file copied or something along those lines?  (ie: copy over torrent1, torrent2, torrent3, etc.)

Thanks

---

### Post by pdtpatrick on 2008-12-21
what tha hell .. haha i think you confused us :) 

lets say you try to copy torrent1 2 and 3 to a folder called freddy.

you would do:

cp torrent* freddy/

does that help?

---

### Post by anim on 2008-12-21
Sorry, I thought I had an idea but it didn't work so hot in practice.

---

### Post by anim on 2008-12-22
Ehh, so I got interested enough in this little problem to screw around with bash scripting and I got a solution for ya.

Move the test.sh file to the directory where all your torrent directories are located. Right click on it and make it executable in the permissions tab. Save the permissions, then click on it again, and choose to run it (you can display it first to prove I'm not being malicious, in fact that's a habit I highly recommend with any file someone tells you to execute).

Anyways after it runs you should have enumerated #.torrent files

If for some reason the extension isn't .torrent on your files, you should be able to edit the script and figure out how to change it :)

---

### Post by anim on 2008-12-22
Oh and a note this script moves the files out of the directories, so if for some reason you wanted to retain the original .torrent files in those directories don't use my script.

---

### Post by holdie on 2008-12-22
So here's the code you sent me (slightly altered to fit the naming of the filesystem...I was wondering if you could explain a bit as to its functions...I've tried to use the find -name tor*/torrent, but it returns an error message saying that "backslashes "/"" are not usually part of the filename aka it thinks the tor*/ is part of the name of the file itself I think

Either way, one other question I had was what the third line of the "for" statement did...I tried looking up =~ on google but couldn't find much...would you mind clearing that up for me?

Thanks

```
#!/bin/bash

j=0

for oldfile in `find -name tor*/torrent`; do
	let j=j+1
	[[ "$oldfile" =~ "(.*)\.torrent" ]]
	newfile="$j.torrent"
	mv $oldfile $newfile
done

```

MODERATOR EDIT: Thread continued here: [http://ubuntuforums.org/showthread.php?p=6438048#post6438048](http://ubuntuforums.org/showthread.php?p=6438048#post6438048)

---

