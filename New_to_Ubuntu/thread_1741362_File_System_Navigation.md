---
title: "File System Navigation"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by tg3793 on 2011-04-28
Is there any freakin' help for me? :-) ... I've been running Linux for several months now. And I'm not going to give up just because of this one silly issue but it certainly is a bother for me. I know that I'm not the average user but I'm sure I'm also not alone either. 

What do you do when your mind (**my mind**) **works in a hierarchal system** but the Linux file system works, how do I put it?; linear?

What I mean is, for years I was able to navigate the Win32 file system that I had created under Windows XP Pro because (for instance) I have a couple thousand folders and I happen to know that the file I want is located in "**g:\tim\projects\newproj\videos\humor**" and then, while I'm there, I happen to remember that there is a another file that I want to get to that is located at "**g:\tim\projects\newproj\clients\tech4u\**". 

Well in my good ol' XP Pro all I had to do was _hit the up arrow_ in explorer a couple of time which got me to "**g:\tim\projects\newproj\**" and then I double-click on the "**client**" folder and then the "**tech4u**" folder.

Well in Nautilus (and I think the CLI also) there is a little wrench in that idea. What if I go to the "**humor**" folder by using a symlink from another folder. Let's say the symlink is located at "**g:/tim/shortcuts/**" and I had crated a "**humor**" symlink that I know mentally that goes to "**g:\tim\projects\newproj\videos\humor**". However when I used the symlink it says "**g:/tim/shortcuts/humor/**" in the navigation area of nautilus (or on the CLI if I do a pwd) ... So then, how do I 'easily' navigate (in Linux) to what I know in a hierarchal file system would have been "**g:/tim/projects/newproj/clients/tech4u/**" ?

... And yes; I know in Linux it would be more correct for me to change all of the "g:/" to "SignatureMini" in my case. But I left the above as is to 'hopefully' make my point more clearly.

---

### Post by mcduck on 2011-04-28
The Linux filesystem is hierarchial just like the one in Windows is. It's juts that you are trying to use symlinks as shortcuts, which they are not.

So that's not a nautilus feature or anyhting, but the basic idea of a [symbolic link]("http://en.wikipedia.org/wiki/Symbolic_link"), they do kind of the same thing a windows shortcut would do, but by pretty much opposite way, instead of taking the user to where the link points they move whatever the link is pointing at where the the symbolic link is located.

If you want something like windows shortcuts, then use shortcuts (launchers) instead. Although if I were you I'd just add all the important locations into the Places menu... ;)

---

### Post by fdrake on 2011-04-28
i don't think you can do that with symbolic links. but you can write a small script that opens the destination folder and save it where you want it.
type :
```

cat >folder_name.shortcut
#!/bin/bash
nautilus '/the path of the folder you want to open'
<press CONTROL-C>
sudo chmod 755 folder_name.shortcut

```

copy and past this script anywhere you want. you can change the destination folder just use a text editor,gedit.
the only bother is that it will ask you every time if you want to diplay or run in terminal. just click on display!

---

### Post by fdrake on 2011-04-28
> **mcduck said:**
> 
If you want something like windows shortcuts, then use shortcuts (launchers) instead. Although if I were you I'd just add all the important locations into the Places menu... ;)

launchers definitely !  did not thought about it! =D>

---

### Post by tg3793 on 2011-04-28
> **fdrake said:**
> i don't think you can do that with symbolic links. but you can write a small script that opens the destination folder and save it where you want it.
type :
```

cat >folder_name.shortcut
#!/bin/bash
nautilus '/the path of the folder you want to open'
<press CONTROL-C>
sudo chmod 755 folder_name.shortcut

```copy and past this script anywhere you want. you can change the destination folder just use a text editor,gedit.
the only bother is that it will ask you every time if you want to diplay or run in terminal. just click on display!

So, let me get this right. I've only done about ten or twelve scripts in the last few months and I've never seen one that started with anything other than #!/bin/bash. So, using my above example; if I wanted one of these that pointed to my video folder I would create a text file called videos.sh and put the following in it.

cat >folder_name.shortcut
#!/bin/bash
nautilus '**/media/SignatureMini/****tim/projects/newproj/videos/humor**'
<press CONTROL-C>
sudo chmod 755 folder_name.shortcut

Then I would simply type videos.sh at the CLI ?

---

### Post by fdrake on 2011-04-28
> **tg3793 said:**
> So, let me get this right. I've only done about ten or twelve scripts in the last few months and I've never seen one that started with anything other than #!/bin/bash. So, using my above example; if I wanted one of these that pointed to my video folder I would create a text file called videos.sh and put the following in it?

Then I would simply type videos.sh at the CLI ?

copy and past this in the txt file.

```
#!/bin/bash
nautilus '/media/SignatureMini/tim/projects/newproj/videos/humor'
```

right click on it select properties and select 'allow execute program' under 'Permission tab'.  but as the previous user said launcher will be easier and cleaner to do.

same thing open a text edito copy this and past:
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Link
Icon[en_US]=gnome-panel-launcher
#name your launcher below
Name[en_US]=videos

#put the path of your folder
URL=file:///media/SignatureMini/tim/projects/newproj/videos/humor

#name your launcher below
Name=videos
Icon=gnome-panel-launcher
```

save as 'videos.desktop', make it executable like before and run it

---

### Post by tg3793 on 2011-04-28
> **mcduck said:**
> 
If you want something like windows shortcuts, then use shortcuts  (launchers) instead.


Well that was nice. That actually did what I wanted. But now that I've been introduced to the Launchers I am curious about something. I checked out what the Launcher looked like on the CLI and it doesn't do anything there (or at least doesn't appear to).

I just wanted to make sure I'm not missing anything. If the launcher isn't supposed to do anything at the CLI then that's ok. My new launcher reads "Videos_Humor" in Nautilus but on the CLI it reads "Videos_Humor.desktop"

Thanks.

---

### Post by vanadium on 2011-04-28
Just like Windows shortcuts, Gnome launchers only work in the graphical environment and not on the command line.

Your initial post did not refer to the use of launchers, though. I would presume that what you described there for Windows would work as efficient if not better in nautilus.

> What I mean is, for years I was able to navigate the Win32 file system that I had created under Windows XP Pro because (for instance) I have a couple thousand folders and I happen to know that the file I want is located in "g:\tim\projects\newproj\videos\humor" and then, while I'm there, I happen to remember that there is a another file that I want to get to that is located at "g:\tim\projects\newproj\clients\tech4u\".

Well in my good ol' XP Pro all I had to do was hit the up arrow in explorer a couple of time which got me to "g:\tim\projects\newproj\" and then I double-click on the "client" folder and then the "tech4u" folder.

Well, all you need to do in nautilus is hit "newproj" in the location bar, then double-click on the "client" folder and then the "tech4u" folder.

Alternatively, "all I have to do is hit the up arrow in nautilus a couple of time which got me to "\tim\projects\newproj\" and then I double-click on the "client" folder and then the "tech4u" folder. this way, it works exactly the same.

Alternatively, using the keyboard, press backspace a couple of times to go up to the \tim\projects\newproj\ folder, press "cl" (or perhaps the c) to highlight the ckients folder and press <enter>.

So what is exactly your issue compared to your old habits in windows?

Indeed, symlinks are another concept than you perceived. They allow you to create a second hierarchical view on your data leaving alone the original data structure. This way, you can provide seamless access to the same folders from within another project, or have another user have seamless access from within his own home directory. This feature is know to linux and unix since more than 40 years. It has made its appearance (probably only "under the hood" in Windows since about two years.

---

### Post by tg3793 on 2011-04-28
The launcher definitely fixed that mental navigational issue that I was having. And it fixed more than one issue for me as well. 

I'm going to try to word my response to help someone else find this answer in the forum. Several weeks ago I had been struggling with a dropbox problem and I looked not only all over this forum but over several forums for the answer. 

Here was the problem. _**DROPBOX follows symlinks**_ ! <ack>. So, since most people only have a 2Gig dropbox, if they want to have a symlink just so they can easily navigate to a larger collection of something on their five hundred Gig drive; then 'whammo', your dropbox decides it wants to do a Johnny5 "Oooo, 'data'; input input" and fills that 2Gig dropbox right up and begs for more.

Well using a launcher fixed that problem. **Put a launcher in your dropbox instead and it doesn't get followed**.

Thanks again guys. You killed two birds with one stone.

---

### Post by grahammechanical on 2011-04-28
When I want two different folders open at the same time in file manager, I just load up another file manager window. Then I can have the two (or more) windows side by side. This works great for copying and pasting between folders.

Regards.

---

### Post by tg3793 on 2011-06-17
This is related to a great deal of what I had in mind when I was struggling with this (and another similar problem) several months ago. 

Hope this helps someone else as well. I found a very cool script on Fresh Meat (call [nautilus-follow-symlink]("http://freshmeat.net/projects/nautilus-follow-symlink")) that would add a context menu entry to nautilus on symbolic links pointing to directories, which once clicked opens the pointed directory (the real path) in a window. 

This lead me to the original thought I had where there must be a command that would reveal this path without having to follow it.

[COLOR="SeaGreen"]**Note that this thread did take a turn at the end that solved another problem that I had had, killing two birds with one stone. This was a great help for me then and even more help to me now with this last little nautilus script that I found and installed.**[/COLOR]

---

