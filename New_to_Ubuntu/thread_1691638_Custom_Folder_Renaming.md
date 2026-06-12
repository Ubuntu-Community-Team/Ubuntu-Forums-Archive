---
title: "Custom Folder Renaming?"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-02-20
I know there are any number of Batch File Renamers out there, but I have not yet found anything which would do just what I want: - Repetitive individual file renaming, rather than batch renaming.

Currently, my camera downloads, via Shotwell, into cascaded folders:
2011 > 02 > 19 > 1234.jpg etc

To match my existing filing system, every time I download, I am having to manually rename each new "day" folder from "19" to "2011_02_19" etc.
OK - this is not a big job, so I can easily carry on doing it.

But I would be really pleased if I could find a 1-click way to rename a folder to the format "Grandparent folder"_"Parent folder"_"Old name".

I am carrying on looking at Applications & scripting ideas (starting from scratch, this will be slow...) but I welcome any suggestions!

Thanks!

---

### Post by cjhabs on 2011-02-20
Ok - this is how I would do it.
Install nautilus-actions - this allows custom scripts to be run from a right click - this is a good link for details on how to set it up - you'll need to log out and back in after installing:
[http://www.makeuseof.com/tag/add-custom-functionality-to-nautilus-linux/](http://www.makeuseof.com/tag/add-custom-functionality-to-nautilus-linux/)

I then wrote this bash script to do what you need - it can be simplified, I wrote it for clarity so you can modify it of needs be:

```
#!/bin/bash
folder=$1
file=$2
parent=`echo $folder/$file | awk -F '[|/]' '{parent=NF-1;print $parent}'`
grandparent=`echo $folder/$file | awk -F '[|/]' '{grandparent=NF-2;print $grandparent}'`
mv $folder/$file $folder/${grandparent}_${parent}_$file

```

When you set up the Nautilus action, set the program to your script with the full path.
For the parameters, use "%d %f" without the quotes.
Make sure you allow the condition to work on folders - the script works with folders and files.

---

### Post by yeats on 2011-02-20
If you want to stay graphical. PyRenamer is a fine program for this kind of thing:

```
sudo apt-get install pyrenamer
```

---

### Post by cjhabs on 2011-02-20
> **yeats said:**
> If you want to stay graphical. PyRenamer is a fine program for this kind of thing:

```
sudo apt-get install pyrenamer
```

Sweet!

---

### Post by 2CV67 on 2011-02-20
Thanks, both, for those suggestions.

Especially for cjhabs' first post - that right-click function is exactly the right answer for me!

I had not previously heard of Nautilus-Actions, so that was a good find already.

Your script works perfectly (once I remembered to make it executable :oops:).

Now I just have to continue through my scripting tutorial, to try to understand how it works...

Again - Many Thanks!

---

### Post by cjhabs on 2011-02-20
You are welcome - by the way, I love your car!

---

### Post by 2CV67 on 2012-01-19
This script (& another that I managed to write myself...) have been working perfectly every day. - Thanks!
But I just upgraded to 11.10 & Nautilus Actions no longer works.

There is a lot of comment on this, so it is not just my problem.
[https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/822282](https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/822282)

One solution is to install the latest package for Pangolin (3.1.4-1) in Oneiric from Launchpad, but that looked a bit complicated for me.

Then I found a simpler (?) route via GetDeb:
[http://www.getdeb.net/updates/Ubuntu/11.10#how_to_install](http://www.getdeb.net/updates/Ubuntu/11.10#how_to_install)
and installed Nautilus Actions version 3.1.5-1.

The interface has changed (see screenshot - sorry about size, that is another problem...).

I tried to fill things in, but frankly don't understand what I am doing! 

The result, so far, is that I do see the Nautilus action "Photo Rename" when I right-click on the folders I want to rename, but nothing happens.
I tried this with my own script & the script from above, both of which worked in 11.04.

I would very much appreciate some guidance.

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/Photo-Renamer.jpg[/IMG]

---

### Post by CoffeeRain on 2012-01-19
Have you tried this yet? It may be a good idea to try this in a directory where you can mess with the files.

---

### Post by 2CV67 on 2012-01-19
> **CoffeeRain said:**
> Have you tried this yet? It may be a good idea to try this in a directory where you can mess with the files.

Tried what?

I tried Nautilus Actions 3.1.4-1 & it shows in the menu but does not activate the script...

---

### Post by CoffeeRain on 2012-01-19
Oh, sorry, I didn't see the thing about it not working. :oops:

---

