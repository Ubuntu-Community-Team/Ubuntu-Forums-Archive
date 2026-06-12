---
title: "Bookmarks in panel"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-05-01
I am running Ubuntu 10.10. Is there a way to add the nautilus Bookmarks to the panel (not web shortcuts) Just a folder that I could click and see all my bookmarked folders. Google had nothing I could find.

---

### Post by corncob on 2011-05-01
> **cmcanulty said:**
> I am running Ubuntu 10.10. Is there a way to add the nautilus Bookmarks to the panel (not web shortcuts) Just a folder that I could click and see all my bookmarked folders. Google had nothing I could find.

I don't know if this is what you're looking for but its all I can figure:  Right-click on the panel (the upper or the lower) and select 'Add to Panel..', double click on 'Custom Application Launcher'.  Enter 'Bookmarks' for the name and 'nautilus' for the command and click OK.  The icon should appear in your selected panel.

---

### Post by cmcanulty on 2011-05-01
Thanks that goes to the home folder I am looking to go to my Bookmarks folder

---

### Post by corncob on 2011-05-02
> **cmcanulty said:**
> Thanks that goes to the home folder I am looking to go to my Bookmarks folder

I don't have any directory named 'Bookmarks' on my machine so I guess this is something you created.  So, in the command line after 'nautilus' (and a space) add the path to this Bookmarks directory.  Say, I wanted to create a launcher to open my Downloads directory -- I would put
```
nautilus ~/Downloads
```
in the command space.
If this is not really a folder but a file containing a list of your bookmarks you would use the command 'cat' instead of 'nautilus' to open it.

---

### Post by stoneage on 2011-05-02
You don't already have the Bookmarks listed in the 'Places' dropdown?

---

### Post by cmcanulty on 2011-05-02
I think the bookmarks that show up under Places menu are just the bottom part of the left side pane in the file browser. Do I use the dropdown box of application or location? Nothing is working I just get a couldn't open error.

---

### Post by stoneage on 2011-05-02
Yep, those are the Nautilus bookmarks, aren't they? Yours are different?

Maybe you need it repaired rather than added to?

When you select 'Edit Bookmarks' do the directory names and locations match up?

---

### Post by cmcanulty on 2011-05-02
My bookmarks are  fine I just wanted a shortcut to them in panel but no big deal. At least I didn't upgrade to Natty right off as I usually do, it sounds like a mess.

---

### Post by stoneage on 2011-05-02
> **cmcanulty said:**
> I think the bookmarks that show up under Places menu are just the bottom part of the left side pane in the file browser. Do I use the dropdown box of application or location? Nothing is working I just get a couldn't open error.

Then I don't understand. What did you mean by 'Nothing is working', and why do you need two sets of bookmarks on the panel? 

Doesn't 'Places' include shortcuts to the Nautilus bookmarks?

---

### Post by cmcanulty on 2011-05-03
I can't get any shortcut to bookmarks in panel. None of the mentioned shortcuts return anything but error.Places does have bookmarks but I was hoping to have places in panel as I use them constantly thanks

---

### Post by corncob on 2011-05-03
> **cmcanulty said:**
> I can't get any shortcut to bookmarks in panel. None of the mentioned shortcuts return anything but error.Places does have bookmarks but I was hoping to have places in panel as I use them constantly thanks

Since my first post isn't what you wanted (although you said it worked), could I ask what you are calling 'bookmarks'?  I think of them as the Documents, Music, Pictures, Videos, Downloads directories you see on the left when you open your home directory.  If there is something you want in there but it isn't, drag it into that space.

---

### Post by dcsoldschool53 on 2011-05-03
[B]> **cmcanulty said:**
> I am running Ubuntu 10.10. Is there a way to add the nautilus Bookmarks to the panel (not web shortcuts) Just a folder that I could click and see all my bookmarked folders. Google had nothing I could find.

I'm not sure what you are asking either, but the bookmark is a file not a folder. It is located in /home/user-name. The name of the file is called .gtk-bookmarks.

In the terminal, type in ```
gedit ~/.gtk-bookmarks
```to view file. 

Hope this helps:D[/B]

---

### Post by stoneage on 2011-05-03
ok

You can create a folder called Bookmarks and drag it onto the panel, than drag your bookmark folders into it. The only drawback is that clicking on it will open the folder in Nautilus rather than giving a drop down menu to select from.

You can also create a custom menubar applet on the panel, but I can't yet figure how to remove the 'Applications' and 'System' headings from it.

I think you might have to settle for 'Places' until someone more knowledgeable turns up. Hope the bump helps keep the thread alive until then  :D

---

### Post by cmcanulty on 2011-05-03
Wow that worked I made a folder on desktop called Bookmarks and dragged all my bookmarked folders to it, then dragged Bookmarks folder to panel and voila bookmarks accessible from panel. Thanks all I will mark as solved.

---

