---
title: "Renaming multiple files"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Motorhead Kaze on 2009-08-30
Odd! I have been using Ubuntu for a couple years but still have never figured out how to do this. I need a way to rename hundreds of photos and videos that I take (.jpgs and mpegs)to one name. For example "summerbeach(1).jpg" or whatever.

I have seen some options for renaming file extensions, but I just want to rename the file name. If you know how to do this within the Gnome GUI, I prefer it. I have done ctrl+A, rename and that did nothing. If there is no way to rename multiple files in Gnome, then a terminal option is OK.

Thank you for the help

---

### Post by x33a on 2009-08-31
try these:

[http://www.krename.net/Home.4.0.html](http://www.krename.net/Home.4.0.html)

[http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)

---

### Post by tgeer43 on 2009-08-31
There are numerous apps to do exactly what you want, both GUI and command line.

Just do a Google search for 'ubuntu batch rename'.

tgeer

---

### Post by natravis on 2009-08-31
Hopefully this helps! I googled "rename many files ubuntu", one of my favorite methods of finding info on how to do something in Ubuntu, since Google will turn up answers on this forum as well as the many other websites out there that have useful stuff for us. Anyways, the website I found was [http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

And he had the following to say about the default renaming utility built in to Ubuntu. I would read through the top part of the website to understand what that long string does, 


```
Tip: Before trying more complicated renaming like in the example below, do a test run with the -n option as described at the beginning of this tutorial.

rename -v 's/(\d{8})\.JPG$/BeachPics_$1\.jpg/' *.JPG

That will change filenames that have the pattern ########.JPG (8 numbers and capital .JPG) to something like BeachPics_########.jpg (the same 8 numbers and changing the extension to lowercase .jpg). Here is a test run with the -n option:

$ rename -n 's/(\d{8})\.JPG$/BeachPics_$1\.jpg/' *.JPG
00001111.JPG renamed as BeachPics_00001111.jpg
00001112.JPG renamed as BeachPics_00001112.jpg
00001113.JPG renamed as BeachPics_00001113.jpg
```

---

### Post by Motorhead Kaze on 2009-08-31
I tell ya, Googling is a skill. I did 'rename multiple files ubuntu' and didn't get what you guys offered. 

Thanks.

---

### Post by Motorhead Kaze on 2009-08-31
I found Pyrenamer in Synaptic and Bulk Rename was in Add/Remove. HOWEVER, both seem to want my files to have a similar name to start with -- beginning with the same prefix, etc. This will be fine when renaming photos, but not when renaming files that have dissimilar names. For example if I have "Chagall.jpg, Matisse.jpg, Picasso.jpg" and want to rename all these to "artist-image(1).jpg" then this seems to be something neither of the above programs can handle. This is why I didn't use the terminal before, because sometimes the file names to be renamed are entirely differently. 

That changes my original question, and I am sorry about that. I will continue to do Google searches, but if any of you know how to rename multiple files that have **dissimilar** filenames, then please post your reply.

Again, thanks!

---

### Post by Motorhead Kaze on 2009-08-31
YOWZA! 

The winner is: Krename.
Was in the repos, allows drag-n-drop, and let me change all the names and add suffix/prefix to the name.

As much as I don't want to say this...why can't we do this by selecting all the files in the folder, right-click and rename from there? Any reason we have to install a special program for this simple task? I know that my expectations are based on experience with other systems but this one seems like a given...

Thanks Krename, x33a and others who replied.

---

### Post by kaibob on 2009-08-31
Post deleted by Kaibob.

---

### Post by Big_astur on 2009-08-31
I use pyrenamer with a script i found for nautilus that with a right click inside any folder makes it appear.

Once in pyrenamer u can just select the files to rename and start adding your new name, example:

The field box where the {1} is, it's the place to add your new name:
artist-image({num2+1}).jpg

By hovering the mouse on the field u get the options, but {num2+1} means two digits number 00, 01, 02... and +1 it's so it stars in 01 instead of 00

Of course num3 means 3 digits, ...

Then click preview and if it's what u want u can apply the changes.

You would end with:
artist-image(01).jpg
artist-image(02).jpg
artist-image(03).jpg
artist-image(04).jpg
....

---

### Post by Motorhead Kaze on 2009-08-31
Awesome! I tried pyRenamer again with your advice on how to rename the files and that did it. You rule.
I did not know this command ({num2+1}) and that is really the key isn't it. Perhaps this piece of knowledge was keeping me from being able to use the other methods mentioned above as well? I will spread the word! 
Thanks again!

---

### Post by Big_astur on 2009-08-31
You're welcome.

In case u also want the script for nautilus is this one:

```
#!/bin/bash

#Open pyrenamer with the currentdir of nautilus as workdir.
#Don't need to select any file in the currentdir.
##########################################################################
# Nautilus "pyRenamer" Script #
##########################################################################
if [ "$1" = "" ];then
wdir=${NAUTILUS_SCRIPT_CURRENT_URI#file://}
wdir=${wdir//%20/ }
else
filetype=$(file "$1")
filetype=${filetype##*: }

if [ "$filetype" = "directory" ];then
wdir=${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS%%$1*}
wdir=$wdir$1
else
wdir=${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS%%$1*}
fi
fi
pyrenamer "$wdir"
```

To use it:
1- open nautilus
2- right click inside any folder (in the blank space not over any file)
3- select scripts ---> open scripts folder (should open the folder /home/yourusername/.gnome2/nautilus-scripts)
4- right click and select "create a new document" --> empty document (sorry mine is in Spanish)
5- paste the previous code on it and save it for example as **Rename** (this is how it will show in your nautilus/scripts sections)
6- right click on the file u created and select options ---> permissions
7- mark allow to be executable box
8- close nautilus
9- now open nautilus again and do the right click inside any folder
10- in the scripts section u should see Rename, select it and pyRenamer should be opened listing the files in the folder u are in.

PS: sorry but i don't remember where i got the script from so that's why i tell u to follow those steps instead of giving u the file directly.

---

### Post by Motorhead Kaze on 2009-09-08
Big Astur, Hey now there's something that looks like fun! I actually do want this. I will try this out tonight.
Thanks

---

### Post by longtom on 2009-09-08
Big_astur

this works well.  Thank you very much!

---

### Post by MrWES on 2009-09-08
There is a bulk renaming utility with a GUI called purrr;

```
sudo apt-get install purrr
```

I use it all the time and it works great.

---

### Post by Motorhead Kaze on 2009-09-09
Well...why can't Gnome just do this anyway without us having to find ways to do it? I understand that my expectations were created by using Windows for 10 years before I found Ubuntu, but it does seem to be as common a tool as viewing files by name, or having thumbnails of .jpgs. The fact that Gnome isn't just set up like this puzzles me.

---

