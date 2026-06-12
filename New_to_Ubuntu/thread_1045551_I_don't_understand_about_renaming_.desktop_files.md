---
title: "I don't understand about renaming .desktop files"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-01-20
I drag a URL from Firefox to my desktop. Let's use [www.ubuntu.com]("http://www.ubuntu.com/") as an example.

My desktop now has a file named 'Link to Ubuntu Home Page | Ubuntu'. I see this if I look at the icon on my desktop, or if I go to Nautilus and look there.

However, if go to Terminal and list my Desktop files (ls), I see the file with a different name, 'Ubuntu Home Page | Ubuntu.desktop'.

Let's say I click the desktop icon and press F2 (rename), and I rename it to 'Ubuntu rocks'. Now, the name changes on Nautilus; but a listing on Terminal still shows 'Ubuntu Home Page | Ubuntu.desktop.'

Likewise, I go to Nautilus and rename it to 'Ubuntu rolls'. The desktop icon changes, but a listing on Terminal still hasn't changed.

Now, I change the name in Terminal (mv 'Ubuntu Home Page | Ubuntu.desktop' 'Ubuntu raves.desktop'). A listing in Terminal shows the change, whereas the desktop icon and Nautilus still show 'Ubuntu rolls'. Oh, and the icon on the desktop moves to the top-left corner.

In other words, the file name from Terminal and from a script show one thing, but from Nautilus and the Desktop it shows another. It's as if they're two separate files, one invisible from Nautilus and the Desktop, the other invisible from Terminal and scripts; but they're both the same, because I can delete it from one and it disappears from the other.

What's going on?

---

### Post by ibuclaw on 2009-01-20
A .desktop is essentially a 'Shortcut', and when you rename the Shortcut, you are renaming the 'Identifier' (if one may call it that) of the file, not the actual filename itself.

May sound odd, but it's done mostly for GUI reasons. Since nautilus doesn't hide file extensions (except for .desktop, .directory, and .theme files), probably best just calling them "special" files :)
And just considering, it is more beneficial that way rather than the opposite.
Else, when you click "Applications", all you'll see is:
[B]Accessories.directory
Games.directory
Graphics.directory
Internet.directory
[/B]etc...

I could make the exact same argument with the ".hidden" files too.
```
touch foo; echo "foo" > .hidden
```
Type in 'ls' in the terminal and you will see the file **foo** in the directory, but go to it in Nautilus and you won't see it at all unless you press **Ctrl+H**.

Regards
Iain

---

### Post by Tim Sharitt on 2009-01-20
The .desktop files are not just links to applications. They contain information on what application is to be launched, icon for the launcher, name, etc. When nautilus (as well as other file/desktop managers in other desktop environments) sees this type of file it reads it to see what name and icon to display. When you change the launchers name in nautilus you are actually changing the name within the file and not the file name itself.

Terminal shells do adhere to the desktop entry file standards, so bash (or what ever shell you use will simply display the file name.

[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html)

---

### Post by Paddy Landau on 2009-01-21
Thank you, Iain and Tim. That makes sense now.

The standards link was interesting.

---

### Post by Eldersail on 2009-01-21
I also learn, thank you.

---

### Post by The Cog on 2009-01-21
You can get to see the contents of a .desktop file using the command line:
> gedit whatever.desktop
It is interesting to look at (and experiment with) the contents of a .desktop file.

---

