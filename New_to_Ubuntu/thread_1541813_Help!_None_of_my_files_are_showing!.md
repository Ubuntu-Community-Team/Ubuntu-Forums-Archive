---
title: "Help! None of my files are showing!"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by tehweezil on 2010-07-29
I don't know what caused this, I was just in the middle of a regular normal session and had not made any changes in this folder's preferences, but I was downloading an .iso in Deluge and went to open it and when I browsed to my Downloads folder (which is on an external hard drive) it was appearing to be empty, and it's not, so for some reason, Nautilus wasn't showing the contents of just this folder :/

I tried creating a folder and going into it and that worked, but when I browsed up back to the Downloads folder even the new folder wasn't visible.

(for all I know) this is the only folder doing this, and I really really need that folder so please someone help me out :(

---

### Post by -kg- on 2010-07-29
Have you tried marking "Show Hidden Files" under the "View" Menu (or press <ctrl> "h")?  Also, did you pull up a "Properties" dialogue from the right click menu on the "Downloads" folder?

I could maybe understand why the .iso file you were downloading with Deluge wouldn't show up there (somehow, maybe the default download location got changed or something), but if you create a folder in the folder, then browse back and it's gone, I'm not sure at all why that would be.

If a file or folder is named with a dot in front of it, like ".filename", it will make that file or folder invisible.  That's the only thing I can think of as a reason for these files and folders to disappear.  That, or perhaps the name of the default folder is ".downloads" under Deluge.

Another way to (maybe) find your file is to do a search ("Go/Search For Files") for it.  That way, if it exists, the search will (or at least, might) find it.

---

### Post by tehweezil on 2010-07-29
It's not just the .iso it's all the contents of that directory, none of them are hidden files and I didn't delete anything, I thought it was just loading at first until I realized in the status bar it said there were 0 items so it wasn't loading anything.

The .iso was a livecd for Trisquel that I was wanting to try out and I opened VirtualBox and when I browsed to the Downloads folder to open the .iso , the folder's contents were still invisible. BUT I copied the name of the .iso from the Deluge filelist and pasted it with the full directory into the location bar and it worked.

So all my files are still there, just invisible for some reason...

---

