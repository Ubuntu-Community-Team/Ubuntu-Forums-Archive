---
title: "How do I make my Microsoft Office install available to all users?"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by goog64 on 2009-06-23
Hi,
I have UBUNTU 9.04. I Just installed WINE and then Microsoft Office 2007. It works fine for me, but when I log in as one of the other two Users that I set up, Office doesn't appear in the Applications menu (WINE does appear though). How do I fix it so that every User can access Office?
I have only been using Linux/Ubuntu for 24 hours in my life, so a simple solution would be appreciated.
Thank you.
Regards,
John

---

### Post by goog64 on 2009-06-23
Anybody?

---

### Post by TheNad on 2009-06-23
I actually have no clue how to use Office through Wine. Sorry.

I can, however, tell you that you really shouldn't be using Office on Ubuntu. Wine tends to make applications run less effectively and creates bugs that are annoying. A much better option is to use OpenOffice. It's free and should have come with Ubuntu when you installed it (if not or if you uninstalled it then you can download it at openoffice.org). It's compatible with MS Office files (so when your un-enlightened friends send you files you can still view them with ease). Anyway, best of luck!

---

### Post by goog64 on 2009-06-23
Thanks,
I have OpenOffice and have been using it with Vista for a few months, but I would still like to know how to make my Microsoft Office available to all Users on my computer, and not just me.
Does anybody know?

---

### Post by frup on 2009-06-23
I'm going to take a guess here,

If you press Ctrl + H in your home directory you will be able to find a hidden folder called .wine. inside that will be drive_c and then Program Files etc.

For your other users, you could either copy over office (which is silly as it wastes space) or create a link/shortcut to the place where it is installed. It might work.

---

### Post by biriachan on 2009-06-23
I don't have a good answer for you, but I can tell you that when you installed "wine" it created a new folder called ".wine".  This is a hidden folder, thus it will not normally be visible within your home folder.

Any application you install under your user account will be installed to your local user home folder.

Example

/home/<Your User Name>/.wine/drive_c/Program Files/<Application>

Because each users has his/her own home folder wine applications by default will not be shared.

I would suggest you start look for a way to share wine applications between ubuntu user accounts in general.

After a quick google seach I fould the following thread...

[http://ubuntuforums.org/showthread.php?t=917422]("http://ubuntuforums.org/showthread.php?t=917422")

This is not a recommendation, as I have never tried anything like this, but hopefully it will give you some additional information.

---

### Post by biriachan on 2009-06-23
> **frup said:**
> I'm going to take a guess here,

If you press Ctrl + H in your home directory you will be able to find a hidden folder called .wine. inside that will be drive_c and then Program Files etc.

For your other users, you could either copy over office (which is silly as it wastes space) or create a link/shortcut to the place where it is installed. It might work.

Simple creating a create a link/shortcut will most likely cause permission issues.

---

### Post by ad_267 on 2009-06-23
You can definitely share your wine c drive between users, I've done this to share applications between users.

Just do this while logged in as another user:
```
ln -s /home/your_username/.wine/drive_c /home/other_user/.wine/drive_c
```
You might need to delete their drive_c directory first.

They won't be able to change any settings in the application but it should work. If they experience problems you might need to change the directory permissions so that other users can write to it. You could create a wine_users group if you want and give that group write permissions to the directory.

---

### Post by biriachan on 2009-06-23
> **ad_267 said:**
> You can definitely share your wine c drive between users, I've done this to share applications between users.

Just do this while logged in as another user:
```
ln -s /home/your_username/.wine/drive_c /home/other_user/.wine/drive_c
```
You might need to delete their drive_c directory first.

They won't be able to change any settings in the application but it should work. If they experience problems you might need to change the directory permissions so that other users can write to it. You could create a wine_users group if you want and give that group write permissions to the directory.

I tested out your method and it worked as stated, but the user will need to create a shortcut to the wine application as it does not show up in under "Applications" -> "Wine" -> "Programs"

---

### Post by goog64 on 2009-06-23
Thanks Ad_267.
It sounds promising - I just have to figure out what you are talking about.....I am the newbie of all newbies!
Where do I write this codeln -s /home/your_username/.wine/drive_c /home/other_user/.wine/drive_c that you mention?
Do I substitute the ACTUAL usernames for "your_username" and "other_user"?
How does one change "directory permissions"?
How do I give a group "write permissions to a directory"?
Thanks
J

---

### Post by ad_267 on 2009-06-23
Well you can do it using the graphical file browser. Just show hidden files by pressing Ctrl+H and then go to .wine in your home directory. Right click on the drive_c directory and select "Make Link". Then move this link into the other users .wine directory. 

You won't have write permission to their home directory though so you will have to open the file browser by pressing Alt+F2 and running "gksu nautilus".

Then back in your own .wine directory you can right click on .wine, go to Properties - Permissions. Make the directory writeable for all users and then select "apply permissions to enclosed files". It might be safer not to do this step and only do this if you find you're having issues.

---

### Post by frup on 2009-06-23
You would enter the command in the terminal. (applications > accessories)

You would change the usernames to the ones on your computer.

You would use the command chmod (type chmod --help and man chmod to get a manual and then q to quit the man pages) to change permissions.

---

### Post by tarps87 on 2009-06-23
Just reading thought this thread and although it's solved I would like to make a suggestion.

If you create a folder in /home/ called .wineShare and allow access to all users, now enter the wine config and add this folder as drive (under the drive/devices tab). This drive will now appear when you install programs.
This will not fix the menu short cut problem but will reduce the sym links left behind if you uninstall the program.

It is also possible to copy you .wine folder to a new location and point each users c: drive to this one. (I haven't tried this between users but have done it between an Arch and Ubuntu install on a share partition)

---

### Post by goog64 on 2009-06-23
Thanks everybody,
I will be able to try your suggestions in a couple of hours. (I may have some questions coming...).

---

### Post by SunnyRabbiera on 2009-06-23
Just keep this in mind:
With linux each user has their own settings for each profile, when installing applications with wine they are not installed systemwide.
Thats because wine does not install the apps like that, wine is more of a per user thing.
Wine really wasn't really made for system wide access.
Thats because the different accounts are separated, its a part of linux security model and its why linux is so customizable.

---

### Post by goog64 on 2009-06-23
Is there an application available that does what wine does but *is* capable of installing apps system wide, rather than just installing them per user?

---

### Post by wizard10000 on 2009-06-23
> **goog64 said:**
> Hi,
I have UBUNTU 9.04. I Just installed WINE and then Microsoft Office 2007. It works fine for me, but when I log in as one of the other two Users that I set up, Office doesn't appear in the Applications menu (WINE does appear though). How do I fix it so that every User can access Office?
I have only been using Linux/Ubuntu for 24 hours in my life, so a simple solution would be appreciated.

You install a copy of Office for every user.  Anything else violates license agreements  :)

---

### Post by tarps87 on 2009-06-23
> **goog64 said:**
> Is there an application available that does what wine does but *is* capable of installing apps system wide, rather than just installing them per user?

As far as I know there isn't, the architecture of Linux and windows is very different. It is an achievement to get windows programs to run on Linux.
If you use one folder of each users c: drive this should allow all users to use the installed programs, you may have to manually update the menus. The best solution would be to look of native alternatives or use windows

---

### Post by sadaruwan12 on 2009-06-23
Hey why do you want to run MS 2007 in ubuntu MS is for windows and for none enlightened and OpenOffice for Ubuntu and for the enlightened. Also MS is designed to work with windows not on a environment that emulates windows if the linux people wanted that to happen why the H**L they've designed open office. It's very different the way Ubuntu does things compared to windows and all the software installed with Ubuntu are automatically shared due to those software is native to Ubuntu. But when it comes to MS it's a alien thing that Ubuntu doesn't know anything about. If you rally want to use MS on other users then install the program just like you did the first time.

---

### Post by CatKiller on 2009-06-23
After you've made the symlinks so that each user has access to the same pretend C: drive, you can probably just copy the appropriate .desktop file from ~/.local/applications/wine to /usr/share/applications to have the menu entry appear for each user.

If that doesn't work, you can create your own .desktop file there. The format is pretty straightforward; use one of the other files as a template.

---

### Post by LewRockwell on 2009-06-23
> **wizard10000 said:**
> You install a copy of Office for every user.  Anything else violates license agreements  :)

So when you purchase a computer from Best Buy with Vista and Office pre-installed...you somehow owe additional licensing fees if you create more than ONE user on that computer?

Um...sorry....fail...

---

### Post by goog64 on 2009-06-23
Good point. And thanks everybody, I'll finally get a chance to try and put all this advice to good use today.
Regards. I will report back with my success or failure, so the next newbie will not what to do (or not).
John

---

### Post by goog64 on 2009-06-24
Well, sorry other newbies; so far I have tried every bit of advice written in this thread as well as the advice at the links posted in this thread. I have had no success making my Microsoft Office installation available in the Application/wine menu for all users of this laptop. Not only that, but now it won't even run for me in my own account.
I think the problem is that I'm such a newbie that a lot of the advice leaves out crucial steps that are probably so simple to regular Ubuntu users that they don't bother to mention them. Also, since I don't really understand what I'm doing with these commands, it's very easy to make mistakes and impossible for me to correct them.
At this stage I'm going to have to re-install Ubuntu and start again (after a lot of reading first). If I'm ever able to make Office available to all 4 users (without installing it 4 different times), I'll post it on this thread.

---

### Post by nikogawa on 2009-06-24
Another option is to use the paid version of Wine, called Crossover Linux. Crossover Linux professional provides multi-user support. 

[http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)

---

### Post by tarps87 on 2009-06-25
The suggestions will only allow the program to be run by each user the shortcut are still a manual thing, also you will need to edit your shortcut if you have move the install.

Try this i a terminal
```
wine /home/share/.wine/drive_c/Program\ Files/office/word.exe
```
You will probably need to change the path to the executable (remember Linux is case sensitive)

Once this works as this to a menu entry, wine has not be designed with multi user support which is why editing the menus is a manual task.

As suggested in the previous post you could try Crossover which is based on wine, I think there is a trial version.

---

### Post by wizard10000 on 2009-06-25
> **LewRockwell said:**
> So when you purchase a computer from Best Buy with Vista and Office pre-installed...you somehow owe additional licensing fees if you create more than ONE user on that computer?

Um...sorry....fail...

You're right - I wasn't paying attention.  Office is licensed by device, not by user.

---

