---
title: "Can't open .doc (saved as) file on OpenOffice"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Barneyisgamgle on 2009-01-21
Right. A few days ago I saved a text document I wrote in OpenOffice 2.4 as a .doc file. At the time I could open the file and edit it without any problem what so ever. I also had notes in a few other documents which I saved as .doc files (97/2000/XP, I think) as well. Today when I tried to open the first file OpenOffice couldn't select a filter for it and prompted me to do so. I've tried everything on the list more than once, but so far nothing has worked. It either says it's not the format I chose, or I get a general input/output error. I can at best get twenty pages of what looks like squares. And I did try to rename the file extension to .odt and open it as one, but that didn't work. Could it be corrupted? It's quite abit of worked spent on this by now, so it would be a pain to lose it. The converter in OpenOffice doesn't recognize it. I've tried services that converts Word files to OpenOffice-files (like [http://view.samurajdata.se/](http://view.samurajdata.se/) and [http://trial.3bview.com/3BTrial/pages/opendoc.jsp;jsessionid=09F691851B29D778306B1DB0D3ED6A3E](http://trial.3bview.com/3BTrial/pages/opendoc.jsp;jsessionid=09F691851B29D778306B1DB0D3ED6A3E)) but they can't even recognize the file. Tried opening in Microsoft Word in Windows with no luck. And I did try AbiWord. And there isn't a backup of the file in the home directory. I checked. It's now the same for all the files that I saved as .doc files in OpenOffice. I can open .doc files I've not created myself perfectly fine. The files are the same size they were when I saved them, so they look like they still contain information. Does anyone know if there is any hope to recover from this?

Similar issue discussed here: [http://ubuntuforums.org/showthread.php?t=601258](http://ubuntuforums.org/showthread.php?t=601258) - but with no solution.

I've attached two of them (the most important one is the one with Pontus in) here:

---

### Post by SteveDee on 2009-01-21
I downloaded the 2nd of your 2 files and opened it using the Gnome Hex editor.

I'm afraid your file is mostly 00H or FFH. So it looks like its been trashed.

---

### Post by Barneyisgamgle on 2009-01-21
Thank you for the information, Steve. It's as I suspected, then. Why did this happen? It eludes me completely. And makes me completely lose faith in OpenOffice. Well, now I know what I'll be doing for the rest of the night, and tomorrow, and the day after that. Fun as in do it all again. I guess I've learned to always save my documents in an open format, and then save that to another file as a Word document if I happen to need that, which I happen to do from time to time. Frustrating, to say the least.

---

### Post by SteveDee on 2009-01-21
I guess I've been using OpenOffice for about 2 years now in the PortableApps (USB stick) version, and about 9 months on 'buntu.

I can't remember any real problems, and certainly nothing like the problem you describe.

I think you need to invest some time in experimenting with a dummy document, to see if you can repeat the problem, or work out what happened. Its worse than useless to use an unreliable application/configuration for a task that is important to you.

---

### Post by Barneyisgamgle on 2009-01-21
True. I will try as best I can to reproduce the scenario. It's hard to do something in the way of a bug report in this case. If I would succeed, all I would get is a file I can't open. Right now I can save to .doc and open without any problem. My guess is some part of the save progress messed up the format, the formula, the magic reference frame of a WinWord file, or something, I don't know much about document type files, and I don't know why it would do that or what happened in-between the time that I saved it and could access it, and now. Far as I know, I haven't changed a thing.

---

