---
title: "Ubuntu 10 won't open files and folders"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by HellsingBAT on 2010-11-05
Hey there, I'm brand new to ubuntu and I have no idea what I'm doing and the ubuntu help website isn't doing any more than confusing me.  

My problem is simple.  Today I went to open some folders and files on my computer after installing some upgrades, and now they won't open. The loading symbol will come up and then just load for eternity until it decides to quite. Thats it. So I can't open my folders at all, even though they were working just fine this morning.  Please help me, I have no idea what to do!:mad::confused:

---

### Post by tkoco on 2010-11-05
> **HellsingBAT said:**
> Hey there, I'm brand new to ubuntu and I have no idea what I'm doing and the ubuntu help website isn't doing any more than confusing me.  

My problem is simple.  Today I went to open some folders and files on my computer after installing some upgrades, and now they won't open. The loading symbol will come up and then just load for eternity until it decides to quite. Thats it. So I can't open my folders at all, even though they were working just fine this morning.  Please help me, I have no idea what to do!:mad::confused:

On the surface, it sounds like something went wrong with the update. Which version of Ubuntu are you using? 10.04 or 10.10?

---

### Post by HellsingBAT on 2010-11-06
I'm not sure, I think its 10.10. Sorry, I really don't know what I'm doing. Do you think there is a possibility that it will be fixed the next time my computer updates itself?

---

### Post by tajiknomi on 2010-11-06
[I][SIZE=2]What kind a message u get while entering the folder...?
Can u post the screen-shot of that message...?
[/SIZE][/I]

---

### Post by azertyh on 2010-11-06
and what application do you use to open these folders and files?

---

### Post by HellsingBAT on 2010-11-06
I'm not sure what application is being used to open my folders, I suppose its whatever came with ubuntu when I downloaded and installed it for the first time.  There isn't an error message at all that shows up.

I start up my computer first thing in the morning usually, and once my desktop is up then all I really do is go up to the top of my screen where it says "Places" and I click on it to open the drop down menu with all those options like: Pictures; Homefolder; Documents; Videos; Downloads...etc   I click on "pictures" or some other folder, and thats it.  There aren't any error messages at all, it simply loads the document/folder for eternity and then finally vanishes without ever actually opening the folder. No messages left behind, no nothing, just gone.  Its really weird, because my Internet opens just fine. :confused:

---

### Post by [::AP::] on 2010-11-07
I am having the same problem. I am using 10.04.
I have been using Ubuntu for only a few months, I am more than a beginner, but still don't have tons of knowledge and experience. 
(I love Ubuntu though).

My computer was working just fine - then I saved a file in Inkscape onto my desktop.... and  now opening files and folders does not work. The file is sitting on my desktop, with the writing icon (transparent sheet with clock, only lasts for a few seconds before replaced by the actual icon. I cannot click on files saved to the desktop (I have no icons for programs on my desktop, just files and a folder), or drag the cursor to mass select files. Docky works fine, same with the top panel. I can open Chromium, Skype, Terminal, any program. I cannot open any folders from the desktop, Docky, or 'Places'. I have reinstalled Nautilus, and it opens from the Terminal, but the files don't show up. 

HELP! (I have some files for school that I need to edit! - Due tomorrow!) 

Thanks, and Good luck, 

[::AP::]

---

### Post by AngusH on 2010-11-07
Hey, couple of things:
Firstly if you have something that needs doing urgently you can access, backup, print or edit your files from a live cd.
Secondly, can you please use a terminal check your files. If you don't know how to do this just open up a terminal, type ls then hit enter. The result should be a list of files and folders.
Please post back telling us how both of those go.
I think a potential solution may be to reinstall nautilus.
Angus

---

### Post by [::AP::] on 2010-11-08
Thanks, I did those things with a Parted Magic CD. 

Anyways, I shut down and took a break for few hours, and when I booted up, it was stuck in console mode (White box in upper left corner, black screen). It was not the typical Ctrl-Alt-F(1-6), it *was* the Ctrl-Alt-F7. When I typed 'exit', it brought me to the default login screen, and I logged in. Ubuntu then brought me to basically the same situation, a white terminal box in upper left corner, but this time with the default 10.04 wallpaper. I tried reinstalling gnome, and found out it wasn't installed! So, after 'sudo apt-get install gnome', it told me I needed the dependencies, which it should do by itself (?). When I tried to install the dependencies, they removed the other dependencies.

I could open programs from this terminal, like gedit, teamviewer, etc, but once they were open I could not open another window.  

This morning, I boot up, expecting to see the same thing, but it logged in like normal. Gnome, Cmpiz, Docky, Except I still can't open files or folders. 

Back to square one. 

[::AP::]

PS - Yes, I did reinstall nautilus, to no avail.

---

### Post by Verbeck on 2010-11-08
you mean you cant access any folders from the places menu?

---

### Post by [::AP::] on 2010-11-08
I cannot access folders from the 'Places' menu, nor can I open folders from Docky, and cannot open files and folders sitting on my desktop. I can, however, open applications from 'Applications' and 'System', and also open shortcuts from Docky, like Chromium or Skype.

---

### Post by mikechant on 2010-11-08
You could try running nautilus (the default file manager) from a terminal - you might get some relevant messages in the terminal sessions when the problem occurs.

---

### Post by Verbeck on 2010-11-08
k. on the desktop, right click a folder>open with other application> select file browser. or enter enter **nautilus** as a custom command

---

### Post by [::AP::] on 2010-11-08
@ mikechant
Typing

```
nautilus
```

 in terminal gives me this this:

```
(nautilus:2929): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```


If I do this:

```
sudo nautilus
```

Under 'places' on left side of nautilus, it just shows the root file, desktop (although *nothing*  shows up except gparted details, which isn't on the desktop, and partitioning with gparted has nothing to do with this problem),  File System, network, cdrom0, and trash.

---

### Post by [::AP::] on 2010-11-08
@ Verbeck

I cannot right click on the desktop. 

I can click and right click on programs, Docky, and my top panel. 
It is really weird, I still have a tiny bit of functionality. 

I wish I could take screenshots or a video! But I cannot access the files once they are saved! If I get around to it I may take photos/video with an exterior camera. 

Thanks for all your help guys.

---

### Post by [::AP::] on 2010-11-08
If a solution cannot be found - I will do a fresh install of 10.10. I would *prefer* not to though.

---

### Post by Verbeck on 2010-11-09
could you try editing the ~/.local/share/applications/mimeapps.list

from a terminal
```
gedit ~/.local/share/applications/mimeapps.list
```to the file, add the line
```
inode/directory=nautilus;
```

---

### Post by [::AP::] on 2010-11-09
I will try that. 

Its back to kinda terminal. It isn't tty(1-6), its just a white box on a black screen where terminal commands can be inputed. It randomly switches between semi-functional and no desktop at all (between reboots). 

Out of curiosity, was the original problem ever fixed (HellsingBAT)? Sorry I hijacked this thread for my own issue. Thanks for all you support.

---

### Post by [::AP::] on 2010-11-10
Ah... I just burned a 10.10 disc. I am going to just do a fresh install. 

Good luck HellsingBAT, if your problem isn't fixed yet. 

Thanks for the support. 

[::AP::]

---

### Post by [::AP::] on 2010-11-10
I thought Installing right on top of the existing installation would wipe 10.04 and install 10.10? This is not so?

I now am on 10.10, but *most* of my settings are still here, and some of my software is installed, some isn't. I still have all my files. Still have the issue. 

I will WIPE first, then install?

---

### Post by Verbeck on 2010-11-11
you should delete all the folders beginning with a . (dot) in your home folder. those are settings files for applications. press ctrl+H to see them

---

### Post by [::AP::] on 2010-11-11
Its fine now. Thanks. Good luck "HellsingBAT".

---

