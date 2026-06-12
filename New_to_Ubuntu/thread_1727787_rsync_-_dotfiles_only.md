---
title: "rsync - dotfiles only"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by earthpigg on 2011-04-12
so, decided to learn to back up the proper way instead of weekly drag-and-drop.

not yet at the phase of automating using a shell script, still trying to do it command-by-command and learn nuances.

can't back up my entire ~ because my external hard drive is much smaller than my ~. so, selective folders and files.

how would i go about including dotfiles only?

so, the file .bashrc and the folder .gconf for example, but not "Documents" and the rest?

what i've been using for other files/folders...

```
rsync -av --size-only --delete /home/chris/Music/. /media/C734-BCF8/Music/.
```

and it is working fine. deleting stuff that needs to be deleted, leaving stuff alone that is already there, and copying new stuff over. great!

for the dotfiles and dotfolders, though, here is what i tried...

```
rsync -av --size-only --delete /home/chris/.* /media/C734-BCF8/dotfiles/.
```

and it did copy dotfiles and folders, but it also started copying ***everything*** over.

i think the confusion is because . indicates 'in here' and .* is being interpreted as 'in here, anything' whereas i want .* to be interpreted as "any files or folders that start with a dot". i obviously cannot sternly lecture rsync into seeing things my way, so i must alter the command i issue. suggestions?

---

### Post by earthpigg on 2011-04-13
off the first page, so i feel justified in bumping this. :)

if a mod comes across this, would you mind moving it to "general help"?

---

### Post by entropy1 on 2011-04-13
cd to your home directory and try

```
rsync -av --log-file=log.txt --include=".**" --exclude="*" . /media/flashdrive/backup
```

But be warned: this will backup not just .files but .directories AND their contents.  In particular, thousands of files in my .thumbnails directory were backed up.  It might be better to specify which .directories you want to back up.  See post #5 in [http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---

### Post by earthpigg on 2011-04-13
is no full path needed? could you explain what --include is, and why .** works with it?

---

### Post by entropy1 on 2011-04-13
Oops.  I forgot to say that you need to cd to your home directory before issuing the command.  The ** matches anything, including "/" --- in other words, if you only used ".*" instead of ".**" then rsync would copy the file .bashrc but not the directory .gconf.  I should also mention that you need to put --include before --exclude or rsync won't back up anything.  The --include tells rsync what patterns of filenames and directory names to back up.

---

### Post by earthpigg on 2011-04-14
looks to be working perfectly, thank you!

EDIT: unmarking. .wine....

lets see if this works.

```
rsync -av --log-file=log.txt --include=".**" --exclude="*" --exclude=".wine" . /media/C734-BCF8/dotfiles
```

edit2:

version 3...

```
rsync -av --log-file=log.txt --include=".**" --exclude="*" --exclude=".wine" --exclude=".PlayOnLinux" . /media/C734-BCF8/dotfiles
```

---

### Post by earthpigg on 2011-04-14
Nope. the command in the post above is still copying .PlayOnLinux over.

---

### Post by entropy1 on 2011-04-14
Try putting the ```
--exclude=".wine" --exclude=".PlayOnLinux"
``` before the ```
--include=".**"
```

---

### Post by earthpigg on 2011-04-14
thanks again for the help, entropy. i didn't try your latest suggestion because i'd already more-or-less worked it out on my own by the time i saw your post. 

my solution was to rename .wine, .PlayOnLinux, and .VirtualBox to aa.wine, aa.PlayonLinux, and aa.VirtualBox and then rename them back after.

that'll do fine for me, as i can easily create a script to replicate that.

re-marking as solved.

---

