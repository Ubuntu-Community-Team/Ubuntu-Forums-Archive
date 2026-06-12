---
title: "Problem with root permissions / file renaming"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by TomSahz on 2010-10-24
Hi everyone,

Ubuntu Maverick 10.10 on Asus eee 1000HA netbook, Ubuntu experience fairly limited.

A while ago i moved to chrome from firefox. I was using an extension on FF called "scrapbook" which saves the components of a webpage into a folder along with an 'index.html' file which i assume puts it all together for offline viewing. I found a way to move my pages from the 'Scrapbook' addon over into chrome by opening the "index.html" file from each page with chrome and saving it into the bookmarks bar in a folder hierarchy. The problem is, i searched for all the index files and then deleted them from the search window as i opened them with chrome and saved them. I wasnt aware that deleting items from the search window meant you actually deleted the file :( 

So i restored them all back to their original places which is opt/google/chrome. (To move the scrapbook folder containing all the index files into the /opt directory in the first place i used the gksudo nautilus)

Anyway, now that they have been moved back, the names are now in the format "index.x.html" where 'x' is a number. I guess that happened when they were all moved into the same trash directory to differentiate them. So now obviously chrome cant find the index files because they are named differently. 

All the index files are in their own  subdirectory together with the relevent webpage component files that i want them to be in, the problem is, how do i rename all of them at once to "index.html"?

I can bring them all up in the search window but i cant rename them in there as I dont have root privileges. I need a way to rename all of them to the same filename "index.html" within the search window, or something similar. I appreciate any help and i thank you immensely in advance!

---

### Post by trikster_x on 2010-10-24
> **TomSahz said:**
> Hi everyone,

Ubuntu Maverick 10.10 on Asus eee 1000HA netbook, Ubuntu experience fairly limited.

A while ago i moved to chrome from firefox. I was using an extension on FF called "scrapbook" which saves the components of a webpage into a folder along with an 'index.html' file which i assume puts it all together for offline viewing. I found a way to move my pages from the 'Scrapbook' addon over into chrome by opening the "index.html" file from each page with chrome and saving it into the bookmarks bar in a folder hierarchy. The problem is, i searched for all the index files and then deleted them from the search window as i opened them with chrome and saved them. I wasnt aware that deleting items from the search window meant you actually deleted the file :( 

So i restored them all back to their original places which is opt/google/chrome. (To move the scrapbook folder containing all the index files into the /opt directory in the first place i used the gksudo nautilus)

Anyway, now that they have been moved back, the names are now in the format "index.x.html" where 'x' is a number. I guess that happened when they were all moved into the same trash directory to differentiate them. So now obviously chrome cant find the index files because they are named differently. 

All the index files are in their own  subdirectory together with the relevent webpage component files that i want them to be in, the problem is, how do i rename all of them at once to "index.html"?

I can bring them all up in the search window but i cant rename them in there as I dont have root privileges. I need a way to rename all of them to the same filename "index.html" within the search window, or something similar. I appreciate any help and i thank you immensely in advance!

The quickesst way to do it is enter in a terminal:

```
sudo chown -R username:usergroup /opt/google/chrome
```

Where username is your user name(obviously) and user group would be whichever group you are a part of(generally the same as your username, unless there are multiple users on your comp)

Then change all the file names like you normally would through nautilus or whichever file manager you use.  When you are done, simply put this command in a terminal:

```
sudo chown -R root:root /opt/google/chrome
```

The only problem you might run into is that you won't be able to have multiple files with the same name.  Unfortunately the only options you will have is to replace the file or name it to something else, which is why the filenames have the numbers to begin with.

---

### Post by Elfy on 2010-10-24
or open nautilus as root  - ```
gksudo nautilus /opt/google/chrome
``` and change the filenames without worrying about chown

---

### Post by trikster_x on 2010-10-24
> **forestpiskie said:**
> or open nautilus as root  - ```
gksudo nautilus /opt/google/chrome
``` and change the filenames without worrying about chown

I had considered giving him this, but it allows too much room for an accidental deletion of a root folder, since you are able to retain root permissions while moving in and out of a folder.  Whereas the chown method makes it so changes are confined to a specific directory or file.  Just seems the safer thing for someone not too familiar with commandline options.

---

