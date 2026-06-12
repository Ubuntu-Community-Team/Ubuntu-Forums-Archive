---
title: "Problems with keryx project"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by Kilron on 2010-07-20
Ok, last week I used Wubi to install Lucid Linux on my offline Windows XP machine. So far I like it a lot, but I'm having problems installing software using keryx. The first time I did it, it worked fine. But now, every single time I try to use it again, I either get opcode errors with my old project I created, or my new projects show absolutely nothing to download and say it's up to date (which I know it's not). To clarify, the machines I download packages on all run Windows 7 and again, Keryx worked fine on there the first time.
 
What should I do? I still have the packages backed up on a flash drive, so should I just wipe Ubuntu off and reinstall? Or is there something I'm missing? Or should I even just make a script and do it that way? I don't get many opportunities to come back and redownload stuff, so I really hope I don't have to go back to my Ubuntu/XP machine to fix this. :/

---

### Post by EXCiD3 on 2010-07-20
Kilron, there is nothing wrong with your Ubuntu machine. Keryx is still under development (Just me and one other programmer so it's hard trying to keep up!)

The opcode problem comes from trying to run Keryx on a 64bit machine. We ran into the issue recently. What versions are Ubuntu and Windows that you are using? The best thing you can do with Keryx right now is to install Python and wxPython on both machines and run Keryx from the source/keryx.py file. This will make sure that it works properly on all your machines.

We are just running into problems trying to make the executable files for Windows and Linux and haven't found a good fix yet.

---

### Post by Kilron on 2010-07-20
My computer uses Ubuntu 10.04 32 bit, and the Windows 7 machines are the Professional 32 bit version.  Anyway, I'll try installing python on this machine and see what happens.

---

### Post by EXCiD3 on 2010-07-20
Okay, I haven't been able to reproduce the opcode problem except on a 64bit machine. Either way, our executables need some work, but we are actually just trying to get our next version out the door more importantly.

Let me know how it goes. I'll do whatever I can to help get it up and running for you.

---

### Post by Kilron on 2010-07-20
Well, I ran from source, and opened the old project, and got this:
 
Loading config: E:\Non DSL stuff\keryx_0.92.4\keryx\source\keryx.conf
wxWidgets interface loaded
Plugin loaded: ColorMap v1.0
Plugin loaded: Debian v0.92.4
Plugin loaded: Search v1.0
Opened project: project
Traceback (most recent call last):
  File "E:\Non DSL stuff\keryx_0.92.4\keryx\source\keryx.py", line 132, in <module>
    lib.wxkeryx.Start()
  File "E:\Non DSL stuff\keryx_0.92.4\keryx\source\lib\wxkeryx\__init__.py", line 49, in Start
    keryx = wxKeryx(0)
  File "C:\Python27\lib\site-packages\wx-2.8-msw-unicode\wx\_core.py", line 7978, in __init__
    self._BootstrapApp()
  File "C:\Python27\lib\site-packages\wx-2.8-msw-unicode\wx\_core.py", line 7552, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "E:\Non DSL stuff\keryx_0.92.4\keryx\source\lib\wxkeryx\__init__.py", line 40, in OnInit
    main.Refresh(project.projects[len(project.projects) - 1].GetData())
  File "E:\Non DSL stuff\keryx_0.92.4\keryx\source\lib\wxkeryx\main.py", line 482, in Refresh
    self.projectDetails.AppendText(_("Drive Free Space:") + '\t' + lib.driveFreeSpace() + '\n')
  File "E:\Non DSL stuff\keryx_0.92.4\keryx\source\lib\__init__.py", line 36, in driveFreeSpace
    d_size = win32file.GetDiskFreeSpaceEx(drive)
NameError: global name 'win32file' is not defined
 
Opening the new project gives me the exact same error, just with the new filename instead of 'project'.  Keryx crashes in both cases.

---

### Post by EXCiD3 on 2010-07-20
Ah yep, for Windows I forgot that you also need to install pywin32. Install the one for your version of Python from here: [http://sourceforge.net/projects/pywin32/files/](http://sourceforge.net/projects/pywin32/files/)

I usually use Python 2.5 or 2.6 so try to use one of those versions if you can.

---

### Post by Kilron on 2010-07-20
Alright, seems to be running fine now.  Thanks for your help!

---

### Post by EXCiD3 on 2010-07-20
Awesome, sorry for the trouble. Maybe I can recruit another developer or two to help me get the next version out sooner! ;)

---

### Post by Kilron on 2010-07-20
Sorry to bother you again, but I'm still having trouble. I got home with the installed packages and updates, and now I have a bunch of broken packages. And I can't install or uninstall anything because of them, it keeps telling me to fix them first. Now a bunch of programs don't work. ):

EDIT: I couldn't get Keryx to work either, I had to use the command line to install everything.

---

### Post by EXCiD3 on 2010-07-20
If you installed using "dpkg -i --force" that can break packages. The way Keryx installs it through the interface (You need to run it from source on Ubuntu too if you are having problems still) uses a repository format so it won't break anything. Did you use dpkg? If so, you can try dpkg --configure -a and it should be able to fix the packages.

Sorry for all the trouble you are having, this problem with offline package installation is actually pretty complicated so I apologize for your troubles. :(

---

### Post by mahela007 on 2010-07-23
Hi.. I had similar problems when working with keryx. There's good news and bad news. The good news is that I had 300MB worth of packages and keryx installed almost all of them perfectly. However, (and here's the bad news) I found that 13 packages had been broken after the installation. 
I did have a working internet connection at home so I was able to fix the packages (download was only 30 MB :-)).
What could be causing this? 
I installed the packages downloaded by keryx using 
```

sudo dpkg -i * 

```
One other thing, when I created the new project on keryx, I didn't download the new package lists when keryx prompted me to do so..

---

### Post by EXCiD3 on 2010-07-23
Using dpkg -i will not install the packages properly. Some packages need to be installed before others and this will not follow the proper order which may cause packages to break.

You can use Keryx to try to install them, but if it missed some dependencies like you mentioned you will have to manually download those as well. The dependency calculations can be kind of complicated and I haven't gotten it perfected yet so there's always a chance things will be missing but it comes close.

---

### Post by mahela007 on 2010-07-23
Are there any better commands (or command option to use with dpkg) to use to install the downloaded packages? 

PS How's version 1.0 coming along?

---

### Post by EXCiD3 on 2010-07-23
> **mahela007 said:**
> Are there any better commands (or command option to use with dpkg) to use to install the downloaded packages? 


The best way to do it I have come across is to take the packages Keryx downloads, copy them into /var/cache/apt/archives/ and take the lists that Keryx downloads and copy them into /var/lib/apt/lists/. Then you can run a "sudo apt-get update" (ignore the errors it gives you, it will still read the new list files you copied over) and then "sudo apt-get install <packages>" that you told Keryx to download. This way your offline machine is updated like it normally would if you had internet, Keryx is just supplying the downloads and apt-get will resolve dependencies and install them the correct way. If something goes wrong, it will simply be Keryx missing a dependency and you'll have only a couple files to get yourself.

> PS How's version 1.0 coming along?

It's looking really good! Yesterday I got a LOT of work done on it and have been testing some features that minimize the amount of bandwidth used. :) I'm working on installation next and then it's simply a matter of building a pretty new interface for you guys and we should be ready! I am looking towards a late August official release but I'll have a couple preview releases out before so you can help me test if you like. :)

---

### Post by mahela007 on 2010-07-23
Yup.. I'd be happy to be a tester.. :D
err... where do I sign up?

---

### Post by EXCiD3 on 2010-07-23
Just watch the blog at [http://keryxproject.org/blog](http://keryxproject.org/blog) and we will post a link to download it there. Thanks for your support! :D

---

### Post by Elludium_Q-36 on 2011-12-22
Keryx seems to have gone fully commercial but at the time of this posting the site is under construction without documentation or a working download link.

I have another idea but I'm no developer...

[CENTER]_**[COLOR="Blue"]S[/COLOR]**imple **[COLOR="Blue"]O[/COLOR]**ffline **[COLOR="Blue"]U[/COLOR]**sb **[COLOR="Blue"]P[/COLOR]**ackage management_[/CENTER]
                                                                         


Yeah, uh-kay...  People are still pointing to Keryx, which was promising while it lasted but it's now fully commercial $$$ and the website is currently broken/under construction withOUT a download or support.

From what I saw of keryx_0.92.4.1, it seemed to work okay on the garden variety Windows XP box but was not quite so automagic on my wonky Kubuntu 8.04 box. Methinks a dependency, perhaps python.
> 
==========================
       Requirements
==========================

Windows: None

Linux: Python, wxPython

Ubuntu users need the following packages in order to have wxPython successfully
installed:

libwxbase2.8-0
libwxgtk2.8-0
python-wxversion
python-wxgtk2.8

wxPython is only required for using Keryx's interface. Project creation can be 
done via command line parameters. See USAGE for more information.



About the commercialization, I wonder if Keryx should be bound by a GPL/LGPL, etc. Since it's, in part, based on GNU/Linux.  It has components that run under Windows and Linux.  Does charging a fee, instead of asking for donations violate the letter of the law of the GPL?  It's sure against the spirit of "free and open" Software!!!

I also got referred to sushi, huh?  "Huh" is just what I uttered.  From the read-me file generated by the .deb package:

> Read **[COLOR="Blue"]Carrefully[/COLOR]**!!!
==================

Hi, to all users and possibly **[COLOR="Blue"]devellopers[/COLOR]** of Sushi, huh?, I'm desired to stop working on Sushi, huh? because now I have no need to use it, I have not fun coding it(it becomes really boring now), and I can not retrieve monetary retribution from it. Also I want to start a new **[COLOR="Blue"]proyect[/COLOR]** and this is a waste of time...

Great, the developer finds it to be useless, boring and a waste of time; so what of an end user?  Okay so it's only spelling but can we trust code from someone who doesn't spell-check?  Eng**[COLOR="Blue"]r[/COLOR]**ish; do you speak it..?

I don't know, I may have copies of:
[LIST]
[*]keryx_0.92.4.1.tar.gz
[*]keryx_0.92.4.1.zip
[*]keryx_1.0-public21_all.deb
[/LIST]
around but am not sure it they are of any help now.  Maybe PM me about those ;)

I have a few links that seem to be less than helpful, without further clarification:

[LIST]
[*][SynapticOffline]("https://help.ubuntu.com/community/Synaptic/Offline")
[*][Simple Way to Update Ubuntu Edgy With Slow/No Internet]("http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/") Connection     
[*][Offline.debian.net]("http://offline.debian.net/") (dead link)          
[*][Synaptic/PackageDownloadScript]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript")            
[*][AptGetOffline]("https://help.ubuntu.com/community/AptGet/Offline")
[/LIST] 

Being mainly offline, when I do manage to get online, I'm concentrating on being a happy end user.

I've not had any luck with Synaptic Package Manager and a Download Script.  It would be on a windows box, as are most public computers...

I'm sure in the current economic state of the world, there are many others in an "internet desert" or "Broadband Desert" who are relegated to "Sneakernet" / "Sneaker Net" with their desktops.

I had hoped that another developer, true to the free and open source nature of GNU/Linux, might take up the cause of a "[COLOR="Blue"]S[/COLOR]imple [COLOR="Blue"]O[/COLOR]ffline [COLOR="Blue"]U[/COLOR]sb [COLOR="Blue"]P[/COLOR]ackage manager".  Hot SOUP for the Chilly-Willy Penguins!!!

---

### Post by oldos2er on 2011-12-22
Closed, necromancy.

---

