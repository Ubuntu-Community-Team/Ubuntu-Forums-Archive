---
title: "Home folder and alacarte permissions. What should they be?"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by PatrickZ on 2010-12-30
Hi

Yesterday I was trying to get some folders to appear in the main drop down menu in the "Places" category, I tried to drag and drop in nautilus to no avail - i could move the folders to the left hand pane but they didn't appear in the drop down menu and when i logged out and in again they were gone. I guess this is some kind of permissions issue (because about 99% of my problems have been permissions issues).
So how do I get those folders there?
Also, in all the excitement I went and first changed the /USER/home folder's owner to root:root - that didn't work too well... - so I changed it to user:user. The question here is: is it alright to have it set up that way? If not, how should it be? 
I'm using Ubuntustudio 10.10.

---

### Post by Verbeck on 2010-12-30
> **PatrickZ said:**
> 
So how do I get those folders there?
open the folder you want to add, go to Bookmarks>add bookmark or press ctrl+D
> **PatrickZ said:**
> 
 Also, in all the excitement I went and first changed the /USER/home  folder's owner to root:root - that didn't work too well... - so I  changed it to user:user. The question here is: is it alright to have it  set up that way? If not, how should it be? 
 your home folder should belong to you, not root

---

### Post by PatrickZ on 2010-12-30
I tried the Ctrl+D thing and the folder does appear, but after logging out/turning off it has disappeared.

---

### Post by mcduck on 2010-12-30
perhaps some of the configuration fiels in oyur home are still owned by root?

Try running this:
```
sudo chown -R yourusername:yourusername /home/yourusername
```
(change the user name & directory to correct ones)

You could also check ~/.xsession-errors for any error messages.

---

### Post by Verbeck on 2010-12-30
could you post the output of the following from a terminal
*```
ls -l ~/.gtk-bookmarks
```*

---

### Post by PatrickZ on 2010-12-30
> **mcduck said:**
> perhaps some of the configuration fiels in oyur home are still owned by root?

Try running this:
```
sudo chown -R yourusername:yourusername /home/yourusername
```(change the user name & directory to correct ones)

You could also check ~/.xsession-errors for any error messages.

A-ha!

I checked the ~/.xsession-errors file and found that I only had read permissions for the .gtk-bookmarks file, so I changed that and now it works. Thanks for the help!

---

