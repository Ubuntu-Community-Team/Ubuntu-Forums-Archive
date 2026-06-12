---
title: "How do I remove the gnome panel?"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by sTaTic^ on 2010-10-21
Hi, I'm trying to get tint2 working. So pretty much I want to disable the gnome taskbar. Everytime I kill it though it restarts. I type killall gnome-panel and it goes away but then it just restarts again. Tint2 keeps putting itself under it so I can't see it or click it really. How do I make it stop doing that? And how can I start it again later?

---

### Post by sidzen on 2010-10-21
[PHP]sudo apt-get remove gnome-panel[/PHP]

---

### Post by alexandari on 2010-10-21
right click - delete panel?

or  ```
ps aux
```

```
 kill -9 (gnome-panel's PID) 
```

---

### Post by sTaTic^ on 2010-10-21
I don't want to uninstall it. I'm just trying to figure out how to make it stop restarting. And I killed its process but it keeps popping up

---

### Post by na5h on 2010-10-21
Right-click the gnome-panel and select "Delete This Panel" (it does not uninstall the panel, it just removes it from your desktop). It shouldn't pop up again unless you start it yourself, for example by right-clicking the lower panel (if you didn't Delete that one too, of course) and selecting "New Panel" or by typing "gnome-panel" in a terminal.

---

### Post by migs73 on 2010-10-21
> **na5h said:**
> Right-click the gnome-panel and select "Delete This Panel" (it does not uninstall the panel, it just removes it from your desktop). It shouldn't pop up again unless you start it yourself, for example by right-clicking the lower panel (if you didn't Delete that one too, of course) and selecting "New Panel" or by typing "gnome-panel" in a terminal.

You can't do this if you have already deleted one. Gnome always wants you to have one panel. I have stopped mine from appearing (not uninstaled) using Gconf-editor, but can't remember how!!! Searching forums as we speak!

---

### Post by migs73 on 2010-10-21
Found it,

[http://ubuntuforums.org/showthread.php?t=1314315](http://ubuntuforums.org/showthread.php?t=1314315)

post #4. :)

---

### Post by na5h on 2010-10-21
> **migs73 said:**
> You can't do this if you have already deleted one. Gnome always wants you to have one panel.

Whoops! ](*,)My bad...I haven't tried to delete BOTH of the panels! Well...you can delete ONE of the panels like this, anyway :)

---

### Post by migs73 on 2010-10-21
> **na5h said:**
> Whoops! ](*,)My bad...I haven't tried to delete BOTH of the panels! Well...you can delete ONE of the panels like this, anyway :)
I use AWN so wanted rid of both, what a hassle!!

---

### Post by empty_spaces on 2010-10-21
Another easily reversible solution (workaround?) would be to basically keep the panel out of the way by setting the panel properties to autohide.
The only issue here would be that the panel would keep popping out whenever the mouse cursor touched that edge. To prevent this, you can set the "unhide-delay" in gconf-editor to some high value. I believe the "unhide-delay" key is located at apps => panel => top levels => top_panel_screen0, or somewhere around there.

---

### Post by Simian Man on 2010-10-21
> **alexandari said:**
> right click - delete panel?

or  ```
ps aux
```

```
 kill -9 (gnome-panel's PID) 
```
For future reference, you can just do:
```
killall -9 gnome-panel
```
If you know the name of the process, there's no need to check its pid.

> **na5h said:**
> It shouldn't pop up again unless you start it yourself, for example by right-clicking the lower panel (if you didn't Delete that one too, of course) and selecting "New Panel" or by typing "gnome-panel" in a terminal.

Actually Gnome restarts "core" components like the panel automatically if they die.  It does this so that crashes won't leave a user without any interface, but it can be a pain in cases like this.

[This post]("http://ubuntuforums.org/showpost.php?p=8848697&postcount=10") in the link migs gave is the best solution.

---

### Post by AngusH on 2010-10-21
> **empty_spaces said:**
> Another easily reversible solution (workaround?) would be to basically keep the panel out of the way by setting the panel properties to autohide.
The only issue here would be that the panel would keep popping out whenever the mouse cursor touched that edge. To prevent this, you can set the "unhide-delay" in gconf-editor to some high value. I believe the "unhide-delay" key is located at apps => panel => top levels => top_panel_screen0, or somewhere around there.

If your mucking around in gconf-editor then your better of just using migs option which is less of a workaround and more of a fix.
Angus

---

### Post by migs73 on 2010-10-21
> **Simian Man said:**
> 

[This post]("http://ubuntuforums.org/showpost.php?p=8848697&postcount=10") in the link migs gave is the best solution.

Actually this is the option I used!!! How stoopid am I?
Don't answer that!
:mad:

---

### Post by ivarn on 2010-10-21
Have you tried to first remove all the things on the panel, then change the background colour to transparent. It will be there but you will not see it.

---

### Post by migs73 on 2010-10-21
> **ivarn said:**
> Have you tried to first remove all the things on the panel, then change the background colour to transparent. It will be there but you will not see it.
Yes, but when you try to open a window full size, it leaves that gap at the top/bottom. You put it on auto hide and it 'pops' out every time you go to the top/bottom of screen. It is unnecessarily difficult to remove.
But do-able :P

---

### Post by Simian Man on 2010-10-21
> **migs73 said:**
> Actually this is the option I used!!! How stoopid am I?
Don't answer that!
:mad:

No, I assumed that was the one you meant.  I was just clarifying because it was a long thread :).

---

### Post by migs73 on 2010-10-21
> **Simian Man said:**
> No, I assumed that was the one you meant.  I was just clarifying because it was a long thread :).
I stupidly recognised the thread and said do post #4. I should have read on!! (damn autopager add-on for firefox doesn't always load next page, and I just assume end of thread!!)

:):(:)

---

### Post by ivarn on 2010-10-21
if you move it down and colour the background black, will not be that annoying.
Or you can do as mentioned earlier. sudo apt-get remove gnome-panel. It does not take forever to install again.

---

### Post by migs73 on 2010-10-21
> **ivarn said:**
> if you move it down and colour the background black, will not be that annoying.
Or you can do as mentioned earlier. sudo apt-get remove gnome-panel. It does not take forever to install again.

Or just do what is on the post mentioned earlier. No uninstall but panel inhibited via gconf-editor. Ten seconds to put it back.

BTW this means you cannot use Alt-f2 to run programs, but you can add to your dock a launcher for Grun, which is pretty much the same thing.

---

### Post by MooPi on 2010-10-21
Seems like a lot for something so simple. 
This disables
```
sudo chmod -x /usr/bin/gnome-panel
```
The reverse to enable 
```
sudo chmod +x /usr/bin/gnome-panel
```

---

### Post by migs73 on 2010-10-21
> **MooPi said:**
> Seems like a lot for something so simple. 
This disables
```
sudo chmod -x /usr/bin/gnome-panel
```
The reverse to enable 
```
sudo chmod +x /usr/bin/gnome-panel
```

Wouldn't that kill the panels for all users? I am one of 4 (5 when she learns to talk/read/ type) and am the only one not using the panels.

---

### Post by cgroza on 2010-10-21
You can black list it. I did it once but I forgot how to do it.I think there is a file where you have to add "gnome-panel" at the end.

---

### Post by migs73 on 2010-10-21
Instead of us all discussing what I shooda/wooda/cooda done, I think we should leave the OP to post what they want to do or have done to solve (we hope) their problem. They have plenty options. 
I am very happy with my panel (none) arrangement. ;)

---

