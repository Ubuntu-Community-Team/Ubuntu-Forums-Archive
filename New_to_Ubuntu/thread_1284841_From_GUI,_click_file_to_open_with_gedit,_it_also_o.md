---
title: "From GUI, click file to open with gedit, it also opens a second file automatically"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by anewguy on 2009-10-07
Okay, I know this sounds stupid, and I'm sure there is something going on I just don't understand.  The problem:

- if I use gedit from the command line, it works normally

- if I am using the gui file browser and right click and ask to open a file with gedit, it opens another file first, then opens the file I clicked on in another tab in the editor.  The file it opens first is a file that doesn't even exist anymore.  I have tried recreating the file just to see if it would stop opening it, but it doesn't.  What to me is really strange is this:[LIST]
[*]if I right-click and the top option says "open with text editor", and I click on that, it opens only the file I clicked in gedit
[*]if I right-click and select "open with" and then go to "gedit", that's when the second file is automatically opened as well
[/LIST]

Any help would be greatly appreciated!

Thanks in advance!

Dave :)

---

### Post by oldfred on 2009-10-07
At the bottom of right click, open with, open with other applications custom command, then opens another blank line to input a command. I used gksudo gedit several times to open system files that I had browsed to and then decided to edit. I then noticed a lot of gksudo in the open with list but when it click it executes both gksudo and gedit as I had typed in on the custom command. It never shows the gedit as the second part perhaps because of the space?

Did you use a custom command and then that has been memorized, and added to the list, but it does not show the full command.

---

### Post by oldfred on 2009-10-07
You got my curiosity up. I found it here.

If you right click on applications, edit menus, other,  then look at all the commands with gedit. If you check properties you may find the actual command does not match the displayed name.

I just edited the item name to gksudo gedit as that is the command it saved and deleted the duplicates of gksudo that have the gedit in the actual command.

---

### Post by anewguy on 2009-10-07
I have no idea how it happened, because I never *purposefully* changed it, but indeed even though gedit was not checked on the "other" menu, it's definition had the extra file name before the %f for the file I really want to edit.  Removed the extra file name and it works great!  I don't actually have gksudo gedit defined anywhere - I just type in sudo gedit and haven't had a problem even when editing system files.

Thanks!
Dave :)

---

