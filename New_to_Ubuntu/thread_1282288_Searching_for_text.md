---
title: "Searching for text"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by ltwinner on 2009-10-04
Everytime I have to search for a string in some file I have to open a terminal and type grep "my string" -R *

While it gets the job done I would prefer to do it more efficiently with a gui. As in just type the string into a text box and press enter. So are there any applications out there that have this functionality?

---

### Post by crolanx on 2009-10-04
You could open the file in **gedit** or a similar editor and then press <CTRL> + <F>. 

Then a box appears in which you can enter you search term.

If you need an application to use in a terminal, take a look at **nano** and search with <CTRL> + <W> oder use **vim**, use */Searchterm* and press return.

EDIT: Sorry, read your post too fast. 

To search in all files in a directory, use **gnome-search-tool**

---

### Post by ankspo71 on 2009-10-04
Hi,

I have a little advice for searching using the default search tool for gnome (in Ubuntu at least). It works great if you follow these steps... 

This example is for text search:
1 Open Places > "Search for Files" or in a terminal run gnome-search-tool (like mentioned above).
2 Choose your desired folder to search.
3 Click on "select more options".
4 Make sure "Contains the Text" and "Owned by User" is added.
5 Enter the search term and appropriate username
6 Click "Find"
Note: It should remember line 4 the next time you need to perform a search again. 
James

---

### Post by andyba on 2009-10-05
Thank you ankspo71.
That's exactly what I was looking for.
But is there such a tool in nautilus?
Or may be some add on for nautilus?

---

### Post by ankspo71 on 2009-10-05
Hi,

It is already installed with the gnome desktop. All you have to do is go to your places menu (part of the start menu) and click on "Search for Files"

Remember, to search for system files, use the "owned by user" = Root
I'll provide a screenshot of how I search for files, using the instructions I mentionend.

James

---

### Post by ankspo71 on 2009-10-05
Hi again,
Nautilus has it's own search tool but I think it is for searching by filenames only. To access that one, all you have to do is open a nautilus window (your home folder is fine) and type the shortcut keys Ctrl+f. It opens as a toolbar in the nautilus window. It also can be found in the Go menu in the top of the nautilus window (our folder windows). So far the search tool in the places menu is the one I prefer the most. There are other search utilities listed in Synaptic Package Manager though.
James

---

