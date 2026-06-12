---
title: "Add Home Folder to Unity Dock"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by pianoplayer123 on 2011-05-08
Sorry if this question sounds kind of stupid, but I deleted the home folder icon from the dock, and now I want it back. Is there anyway to add it directly to the Unity bar?

---

### Post by roger_1960 on 2011-05-08
Hi

Try

> Ctr Alt T
to open terminal
> nautilus
To open a home folder session
and then right click on the folder icon in the launcher and click on "keep in launcher"

Not sure if it works as I don't want to remove my home folder icon to try it!!

---

### Post by Meynstey on 2011-05-08
Had the same exact problem, but found the solution here: [http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html](http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html)

Basically, you just need to drag-drop the nautilus-home.desktop back onto the Unity bar.  This file lives in /usr/share/applications.

---

### Post by CaptainMark on 2011-05-08
this link is excellent, id like to see these patches worked into the next unity update, they make it so much more bearable

---

### Post by Allsixcolours on 2011-07-22
Now, just saying, but the first suggestion works just fine... I honestly did have a bit of trouble finding how to get to my home folder, I typically just use the Unity Dash. I minimized all of my windows, then used the shortcuts on the universal bar at the top, places, to open the home folder. Lo and behold, the icon shows up on the Unity Dock. Then its a simple right-click and select "keep in launcher". But all that fancy stuff works, too, I guess...

---

### Post by Frogs Hair on 2011-07-22
I really like some of quick of lists and hope they are added . With the files and folders search already installed , I didn't see the need for places menu quick list . It will be interesting to see what happens .

---

### Post by CaptainMark on 2011-07-22
The software sources quick list is the most useful, add synaptic to that list to bundle all the package management together and its even better. I would love to see a menu to customize the launchers and quick list in a graphical fashion, as it stands unity is not easily customizable for beginners

---

