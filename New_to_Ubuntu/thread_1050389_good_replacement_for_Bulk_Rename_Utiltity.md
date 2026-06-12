---
title: "good replacement for Bulk Rename Utiltity"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by jimmy the saint on 2009-01-25
I haven't used windows in a very long time, but every once in a while I come across a project that I had a tool for, but can't seem to find a good one in Linux.  For example, I used to use Bulk Rename Utility (the best renamer I have ever used) to bring order to a mess of poorly named files.  The most useful feature is an incredibly simple one: you can manually change the order of the files by dragging one up.  This is extremely useful files that show up out of order because of the way they are numbered. id
1,11,12,13.....4,5,6   as opposed to 1,2,3,4,5........23,24,25

Anyway, I went through a bunch in the repos and none of them can do this.  Does anyone know of a better one that I may have missed because it isn't in add/remove?  I am really tired of loading up windows in a vm to rename these files!

---

### Post by blueridgedog on 2009-01-25
Are you willing to run something in wine?

---

### Post by jimmy the saint on 2009-01-25
I hadn't seriously considered it.  Last time I tried wine I found it to be pretty buggy.  I suppose this would be a situation where trying it again would make sense though.  I would still prefer to find a good linux program though.

---

### Post by Piraja on 2009-01-25
Thunar has a tool named Bulk Rename. I use it often to remove messy characters from audio files, etc.

PS. Sorry, I suppose that's not what you had in mind.

---

### Post by jimmy the saint on 2009-01-25
Yeah, I tried that one as well.  They are all good for what they do.  I tried, the Thunar app, Bulk Rename, pyrename, gprename and even prefixsuffix.  They all have the key limitation of listing the files in the order they see them and not allowing the user to modify it.  That makes fixing the numerical order very difficult.

---

### Post by llamabr on 2009-01-25
Running wine is almost never the answer.

I'm not exactly clear on what you want to do.  Where do you want these files relocated?  You want to actually change their name?  Or just have them show up in a different order?  If the latter, where?

If the former, it sounds like it's about time for you to learn your way around some regular expressions, particularly, using awk and sed.

---

### Post by blueridgedog on 2009-01-25
I used rename-it! in windows and I use it now in wine with ease.  You will need a dll you can get on the net easily, placing it in the program directory.  It is pretty functional.

---

### Post by 73ckn797 on 2009-01-26
> **jimmy the saint said:**
> I haven't used windows in a very long time, but every once in a while I come across a project that I had a tool for, but can't seem to find a good one in Linux.  For example, I used to use Bulk Rename Utility (the best renamer I have ever used) to bring order to a mess of poorly named files.  The most useful feature is an incredibly simple one: you can manually change the order of the files by dragging one up.  This is extremely useful files that show up out of order because of the way they are numbered. id
1,11,12,13.....4,5,6   as opposed to 1,2,3,4,5........23,24,25

Anyway, I went through a bunch in the repos and none of them can do this.  Does anyone know of a better one that I may have missed because it isn't in add/remove?  I am really tired of loading up windows in a vm to rename these files!

I use Thunar several times daily to rename multiple files. I can designate the numbering order to begin with 01. All resulting file names are 02, 03....etc. That keeps them in their original order. If I need to add more files to that batch I designate beginning number to pick up where original renaming left off, ie........ 11, 12 and so on.

Don't know if that is what you really are intending to do according to your post but figured I would throw it into the discussion.


See attached screenshot.

---

### Post by jimmy the saint on 2009-01-28
> **73ckn797 said:**
> I use Thunar several times daily to rename multiple files. I can designate the numbering order to begin with 01. All resulting file names are 02, 03....etc. That keeps them in their original order. If I need to add more files to that batch I designate beginning number to pick up where original renaming left off, ie........ 11, 12 and so on.

Don't know if that is what you really are intending to do according to your post but figured I would throw it into the discussion.


See attached screenshot.

Yeah, the problem is more with not having the files start in the intended order though.  It would be really nice to find a utility in which I can manually change the order in which the files appear, then apply a numbering scheme to them.  Otherwise I have to manually rename them to adjust their order, just to be able to use the batch renamer.  Kind of defeats the purpose for my needs!  I will keep looking!

---

### Post by blueridgedog on 2009-01-30
Another thread mentioned KRename.

---

### Post by yther on 2009-01-30
I'll second KRename.  Once you have the files selected, you can use the GUI to change their order, in case the original sort order is not what you want.  You can also replace parts of the names, extract info from the file using plugins, etc.

Sorry I don't know of any GNOME equivalent.  I either use KRename or a Bash script, but KRename is friendlier for doing random stuff on the fly like if I'm organizing my music or something.  :)

---

### Post by jrusso2 on 2009-01-30
Its already built into the terminal unless I don't understand what your trying to do?

[http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

---

### Post by vin100vin on 2012-08-08
I just let the information for people looking for same problem : 
KRename is perfect and replace all Bulk Name Utility I was use to have
Terminal functions are unfortunately useless for newbies

---

