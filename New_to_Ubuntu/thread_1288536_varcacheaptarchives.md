---
title: "/var/cache/apt/archives"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by dineshs on 2009-10-11
I am using 9.04 .I want to install all packages in my machine to my friends system.The problem now is that I cant see all packages in /var/cache/apt/archives ,Where could it be? Kindly help

---

### Post by drs305 on 2009-10-11
The easiest way for you to do this is via Synaptic. On your machine, open Synaptic and go to File, Save Markings As. Select a filename and make sure you tick "Save full state" in the lower left.

When you save the file, it will make a list of all your installed apps. Copy the file to your friend's machine, open Synaptic, and select Read Markings to import your packages.

If you select Custom Filters, Marked Changes you can view the packages that will be installed (green background) and removed (red background) to match your computer. You can unmark any packages you don't want to install or that your friend wants to keep.

---

### Post by dineshs on 2009-10-11
Will it be possible to get the whole packages or only the list?

---

### Post by drs305 on 2009-10-11
> **dineshs said:**
> Will it be possible to get the whole packages or only the list?

This would only create the list. Once imported on your friend's computer the packages would have to be downloaded from the server selected in Synaptic or Software Sources.

Back to your original post: the chances are fairly good that you don't have *all* the packages in your /var/cache/apt/archives folder either. If you are trying to copy them so that not so many have to be downloaded to the new machine, make sure you are using a browser while you have admin rights:
```

gksu nautilus /var/cache/apt/archives

```

---

### Post by mcduck on 2009-10-11
That will only create a list of the packages.

If your friend doesn't have Internet connection you can download the packages with the "-d" option of apt-get, it will download the packages into /var/cache/apt/archives without installing them. You could, for example, create the list in Synaptic and then use that with apt-get to download all the package on your machine.

What comes to the packages not already being in that directory, they should be there unless you have at some point cleaned apt's cache (by running "sudo apt-get clean").

---

### Post by dineshs on 2009-10-11
But I see only a few packages there.(I have KDE,Gnome and Xubuntu but packages related to that are not seen)

---

### Post by dineshs on 2009-10-11
> **mcduck said:**
> 
What comes to the packages not already being in that directory, they should be there unless you have at some point cleaned apt's cache (by running "sudo apt-get clean").
I havent done that

---

### Post by mcduck on 2009-10-11
Then you must have at some point cleaned the cache, either with the apt-get clean command or by using the equivalent feature in Synaptic. (I'm not very familiar with KDE's package management tools, perhaps they clean the cache automatically?)

Sorry, but that's where the packages are cached. If you don't see them there then you don't have them any more.

---

### Post by lukjad on 2009-10-11
For people without Internet, there is always the option of giving them the repositories [on disk]("ubuntuforums.org/showthread.php?t=352460"). Then you could just use the list to install those programs that are needed.

---

