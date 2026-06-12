---
title: "Sound themes and default filenames"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by kage52124 on 2009-10-20
Hi all, I've been working on setting up filenames to what would be considered default here: >  [http://0pointer.de/public/sound-naming-spec.html#background](http://0pointer.de/public/sound-naming-spec.html#background)
Using sudo mv -r commands, I've been able to move sound files into the proper directory of /usr/share/sounds/ and putting folders in there, as well as using the index.theme file from the Ubuntu sound theme as a template (sudo cp to the other directory), and changing anything inside of it to reflect the name of the new theme, which works.
Here's my problem: when I use sudo mv to rename the file to something that would be considered 'default', sometimes it works and sometimes it doesn't.  For example, renaming one file to 'dialog-warning.wav' from another name will work, but the exact same process for 'dialog-error.wav' will not work; the default will still be the default Ubuntu sound, even though I've picked a new sound theme.
I know that this is a new feature here in Ubuntu, but does anyone have any other thoughts besides, "It's buggy." ?

---

### Post by martrn on 2009-10-20
if you are using the command : 

```
sudo mv /usr/location/file1a.ext   /usr/location/file3b.ext
``` and fail then it should give you a proper error message as to why it did not work and usually these are very good error messages as to why it failed.

The sound themes have to be placed into /usr/share/sounds/ with the correct permissions (try 0775 just in case), and the sounds in a sub directory with an index.theme file inside that folder.

The theme or sounds should not be changed until this is selected from the gnome (or kde menu) by selecting **System > Preferences > Sound** and then applying by closing the sound preferences menu.

---

### Post by kage52124 on 2009-10-20
The renaming didn't fail, but even though it has the same filename as the Ubuntu sound theme, it seems selective as to which it wants to use, whether it be what I put in or the Ubuntu default.

The files seem to have the same permissions (root only) and they are placed in the proper folder with a working index.theme (as far as I can tell since it works at least sometimes).

I am also changing it where you suggest in the Preferences -> Sounds -> Theme tab and selecting the said theme (say "Personal" for example), and that's how I know that some work and some don't.

---

### Post by kage52124 on 2009-10-22
*bump*

Anyone else have a thought?  Also, thank you to Martrn for bringing those items up; I wasn't detailed enough originally.

---

### Post by martrn on 2009-10-22
> **kage52124 said:**
> Anyone else have a thought?  Also, thank you to Martrn for bringing those items up; I wasn't detailed enough originally.

You were detailed enough originally in that you wanted to change your theme or was asking about themes.

Have you read the tutorial about themes....
[http://ubuntuforums.org/showthread.php?t=203093]("http://ubuntuforums.org/showthread.php?t=203093").

The gnome themes and such change specification from time to time and some themes that worked with a previous version of gnome do not fully work the correct way with the next version of gnome.

---

