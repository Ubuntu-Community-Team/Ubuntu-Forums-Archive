---
title: "Open File dialog box in Ubuntu"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by victorhugo289 on 2011-01-09
Hi, I was wondering about the 'Open File' dialog box in Ubuntu which seems a little awkward sometimes:

1. Is it part of Nautilus or it is part of the Gnome desktop...?
2. Why can't you copy, paste, rename files in it?

Is there any setting I can modify to do those things in the Open File dialog box??

Thanks.

---

### Post by mikewhatever on 2011-01-10
Not quite sure I understand, you want to copy/past files into the Open File window? Why? I hate to be so obvious, but tt's for opening file and not copy/pasting.

---

### Post by Frogs Hair on 2011-01-10
To rename files right click the folder/document and a number of options should appear , rename and open in a new window  will appear on the menu.
 
To paste right click and highlight the contents , right click and select copy or right click on the document and select copy , Open the location right click and select paste. 

If the contents are from the file system , you may have to open Nautilus with```
gksudo nautilus
```

---

### Post by victorhugo289 on 2011-01-10
> **mikewhatever said:**
> Not quite sure I understand, you want to copy/past files into the Open File window? Why? I hate to be so obvious, but tt's for opening file and not copy/pasting.

Because you can do it on Windows. You click on File>Open under any application on Windows --say Word-- you get dialog box and it's very functional.

@Frogs Hair, when I right click on it I only get 3 options: "Add to Bookmarks", "Show Hidden Files", and "Show Size Column".

It's one of those times when you want to do things quick and try to modify files while you're opening them, well then I will have to use Nautilus as Frogs Hair says.

Thanks.

---

### Post by victorhugo289 on 2011-01-10
[Had to delete double post here...]

---

### Post by alexjhobbs on 2011-05-31
This is coming up as [solved], but I don't see a solution. Is there anyway to be able to manipulate files in the dialog box. I find particularly useful in Windows when saving files, being able to quickly copy and adjust an existing file name, save over an existing file, create a new folder to save into. It's really a deal breaker for me, Mac OS also doesn't have this ability and is one of the reasons I don't like it. 

Surely in a flexible open source environment like linux someone has created some way of doing this? Or is it back to Windows, which despite it's flaws is excellent for file management.

---

### Post by jeremija on 2011-08-09
I would also be glad to have this feature.

---

### Post by grahammechanical on 2011-08-09
When I was at work (just the other year) and using windows (NT) I had to use the file open dialog in MS Office to delete files. There was no other way as the machines were not set up to have a file manager available to ordinary users. It took me a while to work out this out.

The file open dialog is a function of the application being used. That said the file open dialog in Libreoffice and Bluefish seem closely related to the Nautilus file manager.

If, "because it is done in Windows" is good reason for doing something in Ubuntu, then we should all be paying hundreds of pounds to use Ubuntu. That is how it is done in Windows, after all.

Regards.

---

### Post by jeremija on 2011-08-09
IMHO, the main reason to implement this would be usability, not to copy the windows interface. Imagine the following situation:

- want to save something from a web browser to new folder
- you create a new folder and want to give it a specific name, but accidentally type the wrong name, but you have already pressed the return key
- now there is no way you can rename the wrongly named folder from the save dialog, but you have to do it manually (either from the cli or nautilus)

An alternative would be to be able to copy the folder location and paste it to nautilus to quickly get to the folder, but I have not yet discovered a method to copy the filename (CTRL+L doesn't enable the edit location text box like it does on nautilus).

edit: in some apps you can manually type in a path to get to it, but you can't get the current path from the same box

---

### Post by 3rdalbum on 2011-08-09
I usually treat Nautilus almost as an Open/Save dialog. I use it to find the file or location, and then I drag it to the real Open/Save dialog. It is kind of a "MacOS-y" thing to do, but it's quite effective.

I personally prefer NOT having full file management in an Open/Save dialog; for usability, it makes the dialog less cluttered and less complicated to use.

---

