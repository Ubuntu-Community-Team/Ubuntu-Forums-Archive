---
title: "Web editing"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by horizons on 2008-12-17
The first question is a rhetorical question: why is everything in Linux so painstakingly hard? Okay, deep breath...


So I'm trying to get setup to edit some files on a web server. Easy enough in windows, I've gotta say...

But nothing but trouble on Linux.

First, is there even a good editor out there? Aptana seems like a good one, but can't be installed without olympic style installation gymnastics. Once installed, doing ANYTHING in it takes at least 5 minutes, and that's if it doesn't completely stall out my computer, which is:

Acer Aspire 1640Z
Pentium M 1.7 Gz
1 Gig Ram
Ubuntu 8.04

Not exactly a stone age computer... I wouldn't expect it to run Vista's aero affects or Linux's Beryl flawlessly, but ffs, it shouldn't take 10 minutes to display a directory listing in Aptana from a FTP connection.


But that's not all, I tried Quantus. Same problem there. FTP takes ages to load...

So, I thought, what the hell, let's try using the text editor. I can't be that bad. It does have syntax highlighting, line numbers, bulk indent/outdent. So that suits me great!

Add to that, the fact that browsing the ftp server from the file system (nautilous, I think?) actually goes pretty fast. I like that.

BUT BUT BUT, I load up a javascript file, proceed to edit it, and low and behold, it tells me this is a read only file.
Well, that's weird because I had just created the file using the file browser. I didn't make it read only. And it was made using the current ftp connection so the user/group is set to the current connection's user.


Wth....

I've tried deleting the file, and creating it again. Same problem. Can't edit it.


I don't know how everyone else does it, but I'm about ready to give up.

/end rant

Any suggestions are welcome, thanks.

---

### Post by spiderbatdad on 2008-12-17
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

### Post by horizons on 2008-12-17
I tried Eclipse a while back, using the Aptana plugin. I'm not sure about Eclipse in general, but the Aptana plugin for it ran really slow for me. I've tried just about everything else though, so I might just give Eclipse another shot.

---

### Post by ieee488 on 2008-12-17
I have a PC with P3 1GHz 512MB RAM. I use Filezilla for FTP using settings from XML that I created in the Windows version of Filezilla.

FTP is just as fast as in Windows.

For simple edits, gedit works. You might want to look into Bluefish if you want something fancier.

I'm confused as to what you are looking for exactly.

---

### Post by deputy on 2008-12-17
Eclipse or Quanta are pretty good editors. As for FTP I use Nautilus, or Firefox. As far as permissions go you can always right click on the file and set them there if it's not owned by root, otherwise you can use the chmod command on the command line.

---

### Post by horizons on 2008-12-17
> **deputy said:**
> Eclipse or Quanta are pretty good editors. As for FTP I use Nautilus, or Firefox. As far as permissions go you can always right click on the file and set them there if it's not owned by root, otherwise you can use the chmod command on the command line.

I tried looking at the permissions. Nautilus told me "Permissions on this file could not be determined."

The terminal says this:
-rwx------ 1 floydian floydian 0 2008-12-17 21:24 explore.js

after running this command:
 ls -l explore.js

It's definitely incorrect because there IS NO user named Floydian on that server. That's MY username on MY computer lol.


Fact is though, that I just created that file on the server. Nautilus didn't say there was any error. But if I open it up in the text editor, it WILL NOT save it. It comes up with a few errors. One: the file doesn't exist, and when clicking save anyways, or something to that affect, it just says, error could not save the file.


To ieee488's question about what I'm trying to do, first I'll say that Ubuntu doesn't run slow for me, at least not any slower than any equivelent part of windows, except in the areas I mentioned, i.e., trying to load a file list from an FTP server in Aptana/Quantus. Eclipse Aptana plugin was generally slow for me back when I tried that (six months to a year ago perhaps), but since I've installed it today, it's been running great.

Here's what I want to do: I used to use Zend Studio as a standalone in Windows. With Zend, I could add an FTP server and then the file list of files on that server would be available in the file tree within the program. I could then open a file from the FTP server, edit it, and save it. The file would be saved to the FTP server.

Downloading files, editing them, and then uploading, if that's my ownly option, seems like the how the Flintstones would do it. I just want to be able to edit the file directly.

I do way too much editing on way to many files to worry about downloading them, editing, uploading, everytime I want to do my work as a programmer.


Why don't I test locally? I do all my own programming locally on my own server, but when I work for other folks, I don't have the option of downloading their entire site, their database, and setting up a test site, at least not without charging them a lot more than I do currently.

If you know folks willing to pay for that, let me know, I'll do it. lol

Anyways, to recap, I just want to be able to edit files from an FTP server directly. That's all. Thanks for all the replies so far, I do appreciate it!

---

