---
title: "Opening a folder issue"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by Uberlame on 2011-01-24
Greetings all,

Just to get the obvious out of the way, I am a complete ubuntu novice :).  This is my first night running ubuntu (10.10) and so far I am really enjoying it. I've been wanting to give ubuntu a try for quite sometime.

Anywho, on to my issue.  I created a new folder on the desktop and saved a few images into said folder. When I double click on the folder to open it, it acts like it's going to open the folder, I see the swirling icon and in the bottom task bar I see a new tab that says "Starting File Manager" but after a few moments the tab goes away and nothing happens. Folder does not open. I get the same reaction if try to open the folder (or any other folder) via "Places-> Home Folder"  or "Places-> Desktop".  However if I right click on the folder and select "Open with other application" and select "File Browser" the folder opens up just fine.

Things I have tried: 
Ran the Update Manager to make sure everything is up to date. This is a fresh, brand new install of ubuntu 10.10 that I just loaded tonight. I ran the updates after install and no more are available for download.

I changed the folder options to open on single click (instead of double click). This made no difference and I changed it back to double click.

When I opened the folder going the "Open with other application" route, I made sure the "Remember this application for 'folder' files" boxed was checked. This produces the same result, folder not opening on double or single click. I unchecked this box and tried again. Same result.

I've not made any other changes to the system, because honestly I don't know how hah ;)

I'd be grateful for any ideas. Thanks and I look forward to a long future with ubuntu! And sorry if this is a complete newb question.

---

### Post by fabricator4 on 2011-01-24
> **Uberlame said:**
> 
I've not made any other changes to the system, because honestly I don't know how hah ;)


Very odd and strange behaviour.  I suspect Nautilus (the file manager in question) is running but not displaying since you get the wait pointer.  Something must have changed to cause the odd behaviour.

Open a terminal windows (in Applications - Accessories) and type:

sudo killall nautilus

It will kill all instances of nautilus running in memory.  Now try again.

If it still doesn't work, run the killal nautilus command again and reinstall nautilus.

To reinstall use synaptic package manager. Go to System -> Adminstration -> Synaptic package manager

type nautilus in the search box, and then tick the box to the left of nautilus and when it asks you select "mark for reinstallation".  I would reboot after the install has finished, but maybe that's just me being paranoid.

See how you go.

I'm sure a complete re-install of Ubuntu would fix the problem and I doubt you'd have it re-occur, but try other means before you resort to that.

Chris.

---

### Post by Uberlame on 2011-01-24
Chris,

Thank you very much for the help. Reinstalling nautilus did the trick! Thanks again for helping a newb out :D


Wes

---

