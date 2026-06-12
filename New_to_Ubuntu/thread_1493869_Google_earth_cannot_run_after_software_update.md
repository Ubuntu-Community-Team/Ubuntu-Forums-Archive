---
title: "Google earth cannot run after software update"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by chuuninkid on 2010-05-26
okay, about 2 weeks ago i install google earth successfully (and it runs well), but then i select those recommended items in the update manager, and after it is completed (and restart) i found that ubuntu have install new kernel. and then recently (yesterday) when i want to run google earth, nothings happened after i double clicked the icon.

i googled up for solutions to no avail, and i thought perhaps its something about the kernel, so i restart and select the old kernel, but it still not working.... and then when i tried to run GE from terminal these are the errors
```
/usr/lib/googleearth/googleearth-bin: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

```i'm only using ubuntu for two and a half month so im still new about linux and i even had a hard time to found which directory that my GE is installed :D
im using amd64 lucid lynx

---

### Post by Paddy Landau on 2010-05-26
Google Earth is one of the most unreliable packages for Linux, unfortunately.

You have to have just the right hardware, and I don't think that no one knows what it is.

For some people, Google Earth works great; for some, it works with some restrictions; for others, it just doesn't work.

Try [Google Maps]("http://maps.google.com/") instead. It's not anywhere as good, but it's something.

---

### Post by fooman on 2010-05-26
i would try deleting the old "hidden" config files....then try opening google earth again (don't worry,  new config files will be created when GE is started):

open your home folder (places > home folder)...in the toolbar, go to view and put a check next to "show hidden files"

now find the ".googleearth" file,  right-click on it and choose "move to trash".

next go to the .config folder, open it,  right-click on the "Google" folder,  and send that one to the trash as well.

try google earth again.

hope that helps.

---

### Post by chuuninkid on 2010-05-26
> **Paddy Landau said:**
> Google Earth is one of the most unreliable packages for Linux, unfortunately.

You have to have just the right hardware, and I don't think that no one knows what it is.

For some people, Google Earth works great; for some, it works with some restrictions; for others, it just doesn't work.

Try [Google Maps]("http://maps.google.com/") instead. It's not anywhere as good, but it's something.
it previously working, so i wonder the GE is not the problem, but the the update manager.... but oh well
> **fooman said:**
> i would try deleting the old "hidden" config  files....then try opening google earth again (don't worry,  new config  files will be created when GE is started):

open your home folder (places > home folder)...in the toolbar, go to  view and put a check next to "show hidden files"

now find the ".googleearth" file,  right-click on it and choose "move to  trash".

next go to the .config folder, open it,  right-click on the "Google"  folder,  and send that one to the trash as well.

try google earth again.

hope that helps.
did you mean .googleearth folder? because there's no file named .googleearth
i moved it (the folder) to trash but still the same errors

---

### Post by fooman on 2010-05-26
> **chuuninkid said:**
> did you mean .googleearth folder? because there's no file named .googleearth
i moved it (the folder) to trash but still the same errors

sorry,  yes it is a folder.  ...have you deleted both the folders i mentioned?

---

### Post by philinux on 2010-05-26
> **chuuninkid said:**
> okay, about 2 weeks ago i install google earth successfully (and it runs well), but then i select those recommended items in the update manager, and after it is completed (and restart) i found that ubuntu have install new kernel. and then recently (yesterday) when i want to run google earth, nothings happened after i double clicked the icon.

i googled up for solutions to no avail, and i thought perhaps its something about the kernel, so i restart and select the old kernel, but it still not working.... and then when i tried to run GE from terminal these are the errors
```
/usr/lib/googleearth/googleearth-bin: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

```i'm only using ubuntu for two and a half month so im still new about linux and i even had a hard time to found which directory that my GE is installed :D
im using amd64 lucid lynx

Does it run with the old kernel? If so use that.

---

### Post by Paddy Landau on 2010-05-26
Well, well, well, what have I found!

Google Earth originally worked for me on Hardy, but slow, and I had to turn off the Atmosphere option otherwise it would be like a snail.

Later, it just stopped working (as for you) and after many attempts I eventually uninstalled it.

Now, I've upgraded to Lucid 10.04, and guess what I found...

In the Ubuntu Software Centre there is a utility to [install Google Earth]("apt:googleearth-package") on a deb machine. I ran it and then installed the resulting file, and not only does it work, but I can leave the Atmosphere option on. How strange!

Try it, if you have Lucid, in case it works. But, first uninstall Google and delete the directory [FONT=Courier New].googleearth[/FONT] from your home directory.

---

### Post by chuuninkid on 2010-05-27
> **philinux said:**
> Does it run with the old kernel? If so use that.

> **chuuninkid said:**
> ** so i restart and select the old kernel, but it still not working....** 

> **Paddy Landau said:**
> Well, well, well, what have I found!

Google Earth originally worked for me on Hardy, but slow, and I had to turn off the Atmosphere option otherwise it would be like a snail.

Later, it just stopped working (as for you) and after many attempts I eventually uninstalled it.

Now, I've upgraded to Lucid 10.04, and guess what I found...

In the Ubuntu Software Centre there is a utility to [install Google Earth]("apt:googleearth-package") on a deb machine. I ran it and then installed the resulting file, and not only does it work, but I can leave the Atmosphere option on. How strange!

Try it, if you have Lucid, in case it works. But, first uninstall Google and delete the directory [FONT=Courier New].googleearth[/FONT] from your home directory.
> **chuuninkid said:**
> 
im using amd64 lucid lynx

yes, as i mention in previous post, i've already tried to trash the folders but still not working

---

### Post by Paddy Landau on 2010-05-27
> **chuuninkid said:**
> yes, as i mention in previous post, i've already tried to trash the folders but still not working
Did you install Lucid's Google Earth build package?

[LIST=1]
[*]System > Administration > Synaptic Package Manager. Find googleearth and *Mark for Complete Removal*. Apply.
[*]Delete the [two folders]("http://ubuntuforums.org/showthread.php?p=9362971#post9362971") as already posted.
[*]Go to either Ubuntu Software Centre or Synaptic Package Manager and install [googleearth-package]("apt:googleearth-package").
[*]Go to a terminal and enter:
```
cd ~/Desktop
make-googleearth-package --download
```
[*]Close the terminal. Go to your Desktop, find the googleearth deb file that make-googleearth-package created, double-click (or right-click and Open), and install.
[/LIST]
When finished, you can delete the deb file.

Good luck.

---

### Post by chuuninkid on 2010-05-30
> **Paddy Landau said:**
> Did you install Lucid's Google Earth build package?

[LIST=1]
[*]System > Administration > Synaptic Package Manager. Find googleearth and *Mark for Complete Removal*. Apply.
[*]Delete the [two folders]("http://ubuntuforums.org/showthread.php?p=9362971#post9362971") as already posted.
[*]Go to either Ubuntu Software Centre or Synaptic Package Manager and install [googleearth-package]("apt:googleearth-package").
[*]Go to a terminal and enter:
```
cd ~/Desktop
make-googleearth-package --download
```
[*]Close the terminal. Go to your Desktop, find the googleearth deb file that make-googleearth-package created, double-click (or right-click and Open), and install.
[/LIST]
When finished, you can delete the deb file.

Good luck.
that's the first thing i tried after googling :) (not working though) but don't worry, this problem already solved by running thru recovery mode and run "dpkg" (gosh why shouldn't i tried it earlier :D), as it appears some library is missing

---

