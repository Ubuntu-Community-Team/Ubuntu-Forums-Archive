---
title: "Shell scripting help"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by mtanner on 2009-06-01
Let me start off by saying sorry if this is not the appropriate forum.  It's the only place I knew to start.  I have more of a shell-scripting question.

I have a dual-boot XP/Ubuntu and a shared partition on which all my music is stored.  I am new to shell scripting and have written a shell script to check the timestamp of a musiclib.date file I created, and copy any new files since the last sync timestamp to my flash drive so I can easily move those files to my desktop at home (this is all on my laptop currently).  That way I don't have to remember or search for which songs I have added since the last time I synced the music on my desktop and laptop.

My question is: it seems to work fine for filenames and directories that don't have spaces (Linux/Unix standard) but since Windows/iTunes works with this shared music library most of the directories and file names do in fact have spaces, and it doesn't work for those because the test for $i being a directory doesn't return true - "for i in `ls /media/SHARE/Music` ... if [ -d "$i" ]..."  If $i is a directory with a space, [ -d $i ] or [ -d "$i" ] don't seem to return true.  I've read the man page for test but I get nowhere with that.  I thought it might be a problem with my quoting, but I tried quoting different ways and no success.  I based the script around the logic that my library is always stored artist/album/song.

I've attached the entire script to the message as well as another short dirtest.sh script that I used to test out the [ -d "$i" ] logic.  Any info/help is appreciated!

[ATTACH]116051[/ATTACH]  musicsync.sh

[ATTACH]116054[/ATTACH]  dirtest.sh

---

### Post by sisco311 on 2009-06-01
[http://www.cyberciti.biz/tips/handling-filenames-with-spaces-in-bash.html]("http://www.cyberciti.biz/tips/handling-filenames-with-spaces-in-bash.html")

But, why don't you use rsync? ;)
[uhelp]community/rsync[/uhelp]

---

### Post by mtanner on 2009-06-01
Thanks for the advice!  I don't guess I know what rsync is... like I said I'm still a bit new to Linux in general.

---

### Post by decoherence on 2009-06-01
you are to be commended for your effort! but sisco311 is right... just use rsync (and maybe write a nice wrapper script around that!)

rsync keeps one directory in sync with another directory, even over different computers. it should be exactly what you need.

---

### Post by Tibuda on 2009-06-01
rsync is so powerful. I suggest you to take a look to the grsync frontend.

---

### Post by mtanner on 2009-06-01
Sweet.  Thanks all!

---

