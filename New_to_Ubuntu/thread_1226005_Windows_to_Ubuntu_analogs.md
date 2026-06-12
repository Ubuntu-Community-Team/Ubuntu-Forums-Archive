---
title: "Windows to Ubuntu analogs?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by BobJam on 2009-07-29
Having migrated from Windows XP (transition is going nicely), I'm still in the "Windows mode".  What I mean is that I'm still referencing everything by what was shown in Windows.

For example, I'm wondering what the Ubuntu analog for C:\Documents and Settings\<user name> would be.  And is there a Ubuntu analog for the Windows Restore Point function?
[INDENT] (digression)I used Thunderbird and Firefox in Windows and now use both in Ubuntu.  I think I've found  the folder that stores the profiles, but I've already gotten them the way I want in Ubuntu . . . so transferring profiles is something I don't want or need to do.

I would like to, however, import all my saved emails from Thunderbird in Windows.  The mail import function in Tools just gives me a selection for "Communicator 4.x" and then goes no further . . . so that seems to be out.

I will probably post those Thunderbird and Firefox questions on the Mozilla Newsgroups and MozillaZine.(end digression)
[/INDENT]Back to Windows and Ubuntu analogs.

Another question I have relative to Ubuntu analogs is .exe files.  In Windows I could navigate to an .exe file, double click it, and the app would run.  (Though most were on the menu or desktop anyway).

So what's the way to run an app if it's not on the Ubuntu menu?  For example, I have qsynaptics (gsynaptics IS on the System>Preferences menu as "Touchpad"), which is not on the menu but I can run from a terminal simply by typing in "qsynaptics" at the prompt (without the quotes obviously).  That brings up the qsynaptics GUI, and I can do the settings from there.

What I would like to know is if I can navigate to a Ubuntu executable (AND WHAT'S THE EXTENSION FOR THAT?), double click it, and have it run.  IOW, what's the Ubuntu analog for Windows .exe files?

But my main question is:  Can someone point me to pages specifically designed to show the Ubuntu analogs for Windows commands and system files?

Or does that not exist?  Should I just flat out ditch my "Windows mode" thinking, and approach Ubuntu with a blank slate?

But so far I have been relatively successful in approaching Ubuntu with Windows in mind . . . which is why I'm asking the question about a Windows/Ubuntu guide.

---

### Post by sisco311 on 2009-07-29
Ubuntu Pocket Guide and Reference by Keir Thomas. (link in my signature)

---

### Post by jmszr on 2009-07-29
BobJam,


        I would suggest this sticky by umg6hr: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) . The links to Psychocats Ubuntu Guide:  [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)  and Free Ubuntu Pocket Guide by Keir Thomas:  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  are of particular note but the entire sticky is full of a lot of good information.

This may help: [https://help.ubuntu.com/9.04/switching/index.html](https://help.ubuntu.com/9.04/switching/index.html)

Hope that is some help.

Edit: This is an interesting read: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
Edit: Removed incorrect information

---

### Post by MelDJ on 2009-07-29
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by ad_267 on 2009-07-29
C:\Documents and Settings\<user name> would be /home/<user name>

To see the "settings" directories you have to turn on the "show hidden files" option. Hidden files and directories start with a "."

A .exe doesn't really have an equivalent in Linux. Linux doesn't place as much importance on file extensions as Windows does, and most executables actually have no extension. Some will have a .sh extension if they are shell scripts.

A .deb is a debian package which is used for installing applications. This is a good guide for installing software in Ubuntu: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Mornedhel on 2009-07-29
> **BobJam said:**
> For example, I'm wondering what the Ubuntu analog for C:\Documents and Settings\<user name> would be.

It's /home/<user name>. If using the terminal, you can use ~<user name> to refer to that user's home directory, or just ~ for yours.

> **BobJam said:**
> Another question I have relative to Ubuntu analogs is .exe files.  In Windows I could navigate to an .exe file, double click it, and the app would run.  (Though most were on the menu or desktop anyway).

So what's the way to run an app if it's not on the Ubuntu menu?  For example, I have qsynaptics (gsynaptics IS on the System>Preferences menu as "Touchpad"), which is not on the menu but I can run from a terminal simply by typing in "qsynaptics" at the prompt (without the quotes obviously).  That brings up the qsynaptics GUI, and I can do the settings from there.

What I would like to know is if I can navigate to a Ubuntu executable (AND WHAT'S THE EXTENSION FOR THAT?), double click it, and have it run.  IOW, what's the Ubuntu analog for Windows .exe files?

They don't have extensions. Most compiled binaries don't, anyway ; scripts usually do have one (.pl for Perl scripts, .py for Python scripts, .sh for shell scripts, etc.).

You can go to /usr/bin and double-click applications from there, but that's not really the correct way to do it. If you installed them properly, you should always be able to call them from the terminal, like you did with qsynaptic ; from there it's simple to add a launcher in the panel or the menu (which most GUI applications do anyway).

> **BobJam said:**
> Or does that not exist?  Should I just flat out ditch my "Windows mode" thinking, and approach Ubuntu with a blank slate?

You should anyway. It may work for you now, but only if you don't go too deep -- there are too many differences at the core.

---

### Post by AndyCee on 2009-07-29
I don't think it's a bad thing to look for analagies between the two. Sometimes they're not there, or require a lot more understanding of how Windows works than you'd expect (as I've discovered).

[This link]("http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293.html") might answer a few low-level questions you might have.

While I'm here, I'll answer the specifics you've given:

* C:\Documents and Settings\<user name> correlates closely to /home/<user name>.
* Not sure about importing mail in Thunderbird.
* Linux traditionally doesn't rely on extensions (eg. exe or txt) to determine what a file is, though it is helpful for users. Generally, the closest to an 'exe' in Ubuntu is a binary file (which often has no extension or 'bin'). The terminal keeps a setting which has locations of where executable binary files are. This makes it easier to run any program in terminal, without having to know where the binary is. If you really want to know where it is getting the file in terminal, type:

```
which <program name>
```

If it's in a menu, right-click the menu->edit menus, find the app and look at its properties.

---

### Post by mikechant on 2009-07-29
Edit: Some of the following stuff duplicates the above posts because I started writing it before they were posted.


> The Ubuntu analog for .exe is .deb 

Not really. The general equivalent of a windows .exe is an unsuffixed binary file with an 'executable' flag set. E.g. the firefox executable is just called 'firefox'.

A .deb file is more like a windows .msi file - i.e. an installer. (although lots of windows installers are packed in .exe files - I think that's just to make them self-extracting zip files).

You can download .deb files and install them by double-clicking them, in a similar way to windows, but this is not the recommended install method in general. 

Normally you install from the repositories, which contain tens of thousands of application packages generated specifically for Ubuntu and stored securely. The add/remove programs tool and the more advanced Synaptic tool are available from the menus to do this via a gui. 

I'd suggest you have a look in synaptic (System > Administration > Synaptic Package Manager) and have a browse around using the various search/selection methods (e.g. browse by category). When you go into Synaptic it will prompt you for a password - this is just your normal logon password - in roder to be able to install packages).  

> I'm wondering what the Ubuntu analog for C:\Documents and Settings\<user name>

All your user specific data and settings are stored by default in /home/<user name>
This is usually the default location if you open the file manager (e.g. nautilus), and is just referred to as your 'home directory'.

You can have any directory structure you like under this, but the will be various default directories set up. For example, there will be a 'Desktop' directory with your desktop contents in it, and Ubuntu creates folders like 'Music','Video','Documents' etc. but as per Windows you don't have to use them.

Settings for particular programs are typically stored in directories called '.appname' in your home directory. The leading '.' indicates this is a hidden file/directory and you will usually need to select a 'view hidden files' option to make them visible.

The term 'directory' used above is 'more correct' but it's essentially interchangable with 'folder'.

---

### Post by ajgreeny on 2009-07-29
Most people have already answered you many of the questions, but unless I've missed it no one has said where your mail is in windows and how easy it is to move it to ubuntu.

In you windows Documents and settings there is a folder for the thunderbird profile, I think in **Documents and Settings/User/Application Data/Thunderbird/Profiles/9bxwbftc.default/Mail** from which you can copy the folders to the same place in your hidden thunderbird profile in ubuntu which is **~/.mozilla-thunderbird/rqxrmg4n.default/Mail/**

It is a simple job, and in my experience causes no problems.  The one thing to look out for if you keep booting to both systems and downloading your mail with both, is to ensure that you leave messages on the mail server after getting them on at least one of the systems, but preferably both.  You can the get all mail on both OSs.

---

### Post by oldfred on 2009-07-30
If you boot both windows and Ubuntu often you can have the same firefox and thunderbird data in a common partition.
I created a FAT32 partition (before NTFS linux driver wrote reliably) 2-3 years ago and moved both firefox and thunderbird to the shared partition. I then edited the profiles in windows and linux to look the the common partition rather than the local one. It still worked even when I converted from Thunderbird version 2 to 3 on both windows & ubuntu. I have not tried 3.5 yet.
More info:
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)

---

