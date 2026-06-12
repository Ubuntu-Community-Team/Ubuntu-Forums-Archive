---
title: "A few questions about ubuntu..."
date: 2010-08-06
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-08-06
Hello:

I have a few questions about ubuntu:

1.  Can the length of time used by the auto time-out (lock) feature be lengthened?

2.  Is there a difference between a document file created by MS Word and a document created by OO Word? 

3.  Does Wine (or VirtualBox or VMware) require that the Windows OS still exist on the PC to launch Windows applications?

4.  Are there any performance advantages to be gained by deleting installed programs that I do not use?

5.  Does Synaptic Package Manager delete _all_ files and directories during its' uninstall process.

6.  Are there any advantages (aside from increasing disk space) or disadvantages (aside from direct boot to ubuntu) in deleting Windows XP completely from my computer?

Thank you.

Rob.

---

### Post by diablo75 on 2010-08-06
> **Robert.Thompson said:**
> Hello:

I have a few questions about ubuntu:

1.  Can the length of time used by the auto time-out (lock) feature be lengthened?


I am assuming you mean the screensaver that requires a password when you come back.  You can go into System>Preferences>Screen Saver to change the amount of time to let pass before it starts.
> 
2.  Is there a difference between a document file created by MS Word and a document created by OO Word?

Yes, both file formats are different, but OO can read and save as both formats, while Microsoft Office only handles their own formats and not ODT (as far as I know).  So unless someone you send an ODT file to has OO installed, they won't be able to read it.  Check the File>Save As menu to change the file formats; there is a Word 98/2000/XP format that works well.
> 
3.  Does Wine (or VirtualBox or VMware) require that the Windows OS still exist on the PC to launch Windows applications?

WINE doesn't require Windows; it stands on it's own.  Virtualbox/VMware are virtual machines.  Think of them as fake computers that you can install an OS on top of.  It treats the OS as if it's just another application, in a sense, and these machines are totally separate from any Windows installations you may already have on your computer.
> 
4.  Are there any performance advantages to be gained by deleting installed programs that I do not use?

Eh, depends on the program in question.  If it's a service, something that runs in the background all the time, then you might consider removing it.  Otherwise, if it's not running at all, it won't matter if it's installed or not (usually).  Same thing goes for Windows really:  If it's not running, then it's not slowing your machine down because the CPU isn't being tasked by it to do anything.
> 
5.  Does Synaptic Package Manager delete _all_ files and directories during its' uninstall process.

Sometimes a few files are left behind (such as user preferences).  If you want these to be wiped out as well, it's best to use this command in terminal:  

sudo apt-get purge packagename
> 
6.  Are there any advantages (aside from increasing disk space) or disadvantages (aside from direct boot to ubuntu) in deleting Windows XP completely from my computer?

No, not really.  Dual-boot to your hearts content.

---

### Post by Robert.Thompson on 2010-08-06
Wow!!!

Thank you _very_ much!

Rob.

---

### Post by 3rdalbum on 2010-08-06
> **Robert.Thompson said:**
> Hello:

I have a few questions about ubuntu:

1.  Can the length of time used by the auto time-out (lock) feature be lengthened?

Yes, it's in System > Preferences > Screensaver.

> 2.  Is there a difference between a document file created by MS Word and a document created by OO Word?

By default, OOo Writer saves into OpenDocument format. You can change this at save-time to MS Word format, or change the default in the preferences. Support for Word format is not perfect, however, and some formatting may not come across properly. For documents created on OOo Writer and read on Word, you should be fine, at least.

> 3.  Does Wine (or VirtualBox or VMware) require that the Windows OS still exist on the PC to launch Windows applications?

Wine is self-contained and contains a reimplementation of Windows DLLs (some of them can be replaced with the real Windows DLLs, for greater accuracy). Virtualbox, VMWare and other virtualisation programs create a "virtual machine" which of course requires an operating system. As far as I know you couldn't really use your existing copy of Windows for this, you need to install Windows within the virtual machine.

> 4.  Are there any performance advantages to be gained by deleting installed programs that I do not use?

Only if the program runs at startup or login. Deleting F-Spot, for instance, will not increase performance. If the program is not running, then it's not using any RAM or CPU time. If you're looking at programs that are running on startup, then you should be very careful before fiddling with them - it's very possible to delete something essential.

> 5.  Does Synaptic Package Manager delete _all_ files and directories during its' uninstall process.

It deletes all files and folders that have been created as a result of the installation process. You can also delete system-wide configuration files by using the "Complete Remove" option when you right-click the package.

Documents and per-user settings are never removed, partly because they are not kept track of, and partly because they belong to users and not to the administrator.

> 6.  Are there any advantages (aside from increasing disk space) or disadvantages (aside from direct boot to ubuntu) in deleting Windows XP completely from my computer?

None that I can think of.

---

### Post by Robert.Thompson on 2010-08-06
Wow, again!!!

Thank you very much!

Rob.

---

### Post by Paddy Landau on 2010-08-06
Some extra points.

[LIST]
[*]OO can save files as PDF, suitable to send to anyone on Windows, Linux or Mac.
[/LIST]

[LIST]
[*]To purge a package from the GUI, go to System > Administration > Synaptic Package Manager, find your program, and select Mark for Complete Removal. (Even then, it doesn't always remove your user settings, but they're easy to delete. Almost all user settings are stored in hidden directories in your home folder. There's no "registry" as in Windows.)
[/LIST]

[LIST]
[*]If you want to use Wine, I strongly recommend that you install [PlayOnLinux]("http://playonlinux.com/"). PlayOnLinux is a front-end to Wine, making it much easier to install, run and uninstall Wine programs. Wine is not a Windows replacement, so expect many Windows programs to have problems or to not run at all. If you specifically want Windows programs, keep your dual-boot.
[/LIST]

---

### Post by 3rdalbum on 2010-08-06
> **Paddy Landau said:**
> Some extra points.
[*]OO can save files as PDF, suitable to send to anyone on Windows, Linux or Mac.

True, and in fact any program can "print to PDF". PDF is truly cross-platform. But PDF is not easily editable, so it's more of a final output document format.

---

### Post by Zorgoth on 2010-08-06
I believe the very latest Microsoft Office products support the .odt format.

The .doc support in OpenOffice is fine for reading ordinary documents, but if the documents are heavily formatted there may be problems.

I personally find that single-boot systems are FAR more stable than dual-boot systems when Windows is involved; Windows does not play nice, particularly if it breaks; I once had Windows Recovery departition my hard drive without me even clicking anything; I booted into it by mistake and pressed "Exit."

---

### Post by Paddy Landau on 2010-08-06
> **Zorgoth said:**
> I believe the very latest Microsoft Office products support the .odt format.
[Yes, supposedly]("http://office.microsoft.com/en-us/word-help/use-word-to-open-or-save-a-document-in-the-opendocument-text-odt-format-HA010355766.aspx"). Though MS has claimed to support something but subtly 'changed' the standards (e.g. Java); let's hope not this time.

---

