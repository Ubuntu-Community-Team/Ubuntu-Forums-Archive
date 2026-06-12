---
title: "Not all folders accessible in network"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by chalewa on 2007-12-10
i have a network set up to share the music that is on my desktop with various laptops througout the house. 


now, i can access the folder fine, and all the appropriate music folders are in there. however, when i try to access some of the albums on the desktop on another laptop, they will not play. but other alubms in the music folder will play fine. it is always the same folders that will play and always the same ones that will not. 


any ideas?

---

### Post by zorkerz on 2007-12-10
are these all ubuntu machines?
How are they shared?

---

### Post by jetsam on 2007-12-10
Probably the unix permissions and/or file ownership is different in the directories that work versus in the directories that don't.   Likely the read permissions for others are not set on the non-working directories. You can check this by doing ls -l in the relevent directories and probably fix it with:
```
sudo chmod o+r -R <your directory path>
```
Chmod changes permissions.  o+r tells it to set the read permissions for others.  -R sets the command to work recursively on all subdirectories and files of the specified directory.  

If you need help on the basics of unix permissions, this looks like a decent overview: [http://www.perlfect.com/articles/chmod.shtml]("http://www.perlfect.com/articles/chmod.shtml").

---

