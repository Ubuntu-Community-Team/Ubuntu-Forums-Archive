---
title: "Moving files around help.."
date: 2010-06-08
forum: New to Ubuntu
---

### Post by hopelessone on 2010-06-08
Hi All,

I have a directory with lots of files and i want to move files containing the letters: **(U)** to a separate directory..

How can i achieve this?

e.g.
**/some** <- has all the files 
blah**(U**).whatever
blah(K).whatever

**/thing** <- want to move all the files in **/some** containing in the filename **(U)**

so:
**/thing**
blah**(U**).whatever
new**(U**).whatever
ok**(U**).whatever

Many Thanks..

---

### Post by expatCM on 2010-06-08
Why not use gnome-commander.  This is a two pane file manager.  You could open the source directory and then click on the title to sort alphabetically and then block and move over the files to a second directory in the second pane.

gnome-commander is found with synaptic.

Or do you want to use the command line to do this?

---

### Post by hopelessone on 2010-06-08
Hi,

Theres approx 16,000 files i was looking into the mv command but don't know how to get started...

---

### Post by nitstorm on 2010-06-08
```

mv path-to-the-source-folder/u* path-to-the-destination-folder

```

that's the code to move the files **that start with u**, so maybe some variation with the star thing? Gonna try something similar and post back..

---

### Post by hopelessone on 2010-06-08
Could it be as simple as something like:?
```
mv path-to-the-source-folder/*(U)* path-to-the-destination-folder
```
or:
```
mv path-to-the-source-folder/*\(U\)* path-to-the-destination-folder
```
I'm at work so I can't try it...

---

### Post by Breambutt on 2010-06-08
```
mv path-to-the-source-folder/*\(U\)* path-to-the-destination-folder
```

I suggest you don't try the first one. ;(

---

