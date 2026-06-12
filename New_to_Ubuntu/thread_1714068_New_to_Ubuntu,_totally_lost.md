---
title: "New to Ubuntu, totally lost"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by jenningsfamily06 on 2011-03-24
Hello everyone.  After many years of severe aggravation and at the urging of a friend I have decided to give Ubuntu a shot.  I downloaded and installed 10.04 32bit.  I have no idea how to use the OS or install the drivers for my wireless card (broadcom).  Could someone point me in the right direction please?  My computer is dual boot 10.04/Windows 7.:confused:

---

### Post by Old *ix Geek on 2011-03-24
Hello, and welcome to the wonderful world of Linux. :D

There used to be some issues with Broadcom wireless drivers, but now it's usually a simple matter of clicking a driver from a list and activating it. I use KDE so I can't tell you exactly where to find this if you're [apparently] using GNOME, but look for something on your menu like "Additional Drivers" or "Hardware Drivers" or similar. Open that and see if there's anything listed for Broadcom. I've found that using its STA driver works flawlessly, so if that's a choice, pick it! Follow the prompts. If you're unable to find any such thing or if it doesn't solve your problem, post again.

Also, I just want to mention that the *Ubuntu family is famous for its ease of use. I say this all the time--but it's true!--my mother is over 80 and she uses Kubuntu all day long, and loves it. She made the switch--from years of using windows to Kubuntu, 100% (no dual booting in this house allowed!)--effortlessly. You might want to try KDE/Kubuntu; you can install it via Synaptic. Its interface is exceptionally easy for new switchers to use. (I use it because I like it *MUCH* better than GNOME, not because of its similarity to that other OS or because I don't know my way around Linux--when I started using UNIX there was no such thing as a GUI! :lolflag: )

---

### Post by samcot on 2011-03-24
I've seen many threads dealing with Broadcom issues. You're new to the forum, and I would encourage you to make use of the wonderful search feature (both basic and advanced). You might just find a thread in which your problem has already been solved!

---

### Post by sammiev on 2011-03-24
Hello and welcome jenningsfamily06, you will find your answer in the search bar and I found spending time reading all post when I was starting out to help me with other problems down the road. When asking a question please supply as much info as possible so the find folks here can help you with your problems. Make sure you recored all your computer info and equipment as it will surly help you down the road. GL :)

---

### Post by Zzl1xndd on 2011-03-24
As was mentioned it might be a simple thing to enable the driver. 

You will want to check System > Administration > Additional Drivers to see if anything is listed.

---

### Post by 3rdalbum on 2011-03-24
> **tweakedenigma said:**
> As was mentioned it might be a simple thing to enable the driver. 

You will want to check System > Administration > Additional Drivers to see if anything is listed.

You'll first need to be connected to the internet in some way, usually via an Ethernet cable to your router (but if you have access to a mobile broadband stick or a tethering-enabled Android phone, this will do too).

---

### Post by Learning Linux 2011 on 2011-03-24
Hi, I've made the switch recently to Ubuntu

There is a bit of a learning curve,  I recommend getting a printed book  like "Ubuntu Linux Bible".  It tells you almost everything you need to  know to get going.

Ubuntu has an Update Manager program in the System -> Administration   menu at the top of your screen that keeps everything up to date  automatically.  Make sure you use that to keep your system updated.  It  will prompt you to update it eventually anyway, but not as annoying as  Windows if you ask me.  Also, there is no "activation" like in Windows.

Ubuntu is alot like Windows once you start to get used to it.  

The desktop is called "GNOME", and is fundamentally the same idea as Windows and Mac.  
The things at the top and bottom are called "panels".  The panel at the  bottom shows running programs just like Windows and the Macintosh OS X  "dock".  It also has the trash can just like Windows and you can drag  items there and empty it just like in Windows. 
Feel free to right-click on different things for more options.

Probably the main difference between Linux and Windows is that the "Start" menu is at the top of  the screen (the top panel) and essentially there are 3 menus there. 

The "Application" menu has the programs that you will use, organized into categories, similar to 
"Start -> Programs" in Windows.  

The "Places" menu is kind of like Windows Explorer or your "My  documents" folder.  You will probably recognize the folders there; they  are similar, if not identical, to Windows, such as the Music folder,  Pictures folder, Videos folder, Downloads folder, etc.  Same idea as  Windows.  Clicking on one will bring up a Windows Explorer-like window  that should be familiar.  Linux's file manager is called "Nautilus".

The "System" menu is kind of like "Start -> Settings" and/or Control Panel in Windows, divided into "Preferences" and "Administration".  
"Task Manager" in Windows is called "System Monitor" in Linux and is located in "System -> Administration".  
The "System -> Preferences" menu is also where you change screen  resolution in Linux, there is a program called simply "Monitors".  You  can also set your screen saver there, just like in Windows.  That is also  where you can change the colors of Linux to a different color scheme  using a program called "Appearance".  I think it is all pretty  self-explanatory.  You can probably figure out everything else in the  system menu just by the names.  

There is a "Disk Utility" in the System menu that is similar to "Disk  Management" in Windows and it allows you to view partitions and add or  change them.  There is also a program in "System -> Administration"  called "System Testing" that will essentially tell you if your hardware  is installed and functioning properly.  You can look up your IP address  and see if you are connected in "System -> Administration" using a  program called "Network tools" (you can even look up who owns any web  site using the "Whois" tab).  If you want to add users or put them into  groups, there is a program in "System -> Administration" called  appropriately enough, "Users and Groups".

The icons to the right of the "System" menu are simply shortcuts, like  the "Quick Launch" in the Windows toolbar.  You can put almost any  shortcut there.

When you want to log out or shut down, that option is located in the upper right corner of the screen.

The Windows' "My Documents" folder is replaced by Linux's "Home"  folder.  Windows XP stores that in "Documents and Settings", and "Users"  in Windows Vista or Windows 7.
If your name is Bob, your Linux user folder would be "/Home/Bob"

The Windows "Administrator" account is called "root" in Linux.  Although  it is generally not recommended to log in as root.  Just log in as  yourself under normal circumstances.

As a side note, the root account has its own folder.  You cannot access  the folder called "root" unless you are actually logged in as root.   Indeed your access to several folders will be limited under normal  circumstances, but that is for security reasons.  Largely, Linux is far  more secure than Windows.
You will have full access to your own "/Home" folder though.

The Windows "C:\" drive is simply referred to in Linux by using a slash "/" 
so like "C:\File.txt" would be "/File.txt" in Linux.  Notice that the  Linux "/" slash is in the opposite direction of the Windows backslash  "C:\"

Linux has alot more folders in the main directory than Windows does, but  you don't really need to know what all of them do.  "/Home" is the main  one where you store your documents like I mentioned.  There really  isn't a 1-to-1 comparison for "C:\Program Files" and the "C:\Windows"  folder.  Linux uses a "kernel", which is the main part/core of the  operating system.  

As far as what you can actually do with Linux, you can play MP3 music  files just like Windows, you can watch videos just like Windows, you can  burn CD's and DVD's without buying any additional programs, you can  edit text with something similar to Notepad called "GEdit".  
Microsoft Office is replaced by "Open Office", which is very similar to  MS Office, but unlike MS Office, it is free of charge.  Adobe Photoshop  is replaced by a program called GIMP (GNU Image Manipulation Program),  which is an excellent replacement.  There is an instant messaging  program called "Empathy".  There is a program similar to MS Paint called  "gpaint".  There is a program in "Applications -> Accessories"  called "Disk Usage Analyzer" that tells you how much space is used up  and free on your hard drive, kind of like right clicking on a drive in  Windows XP and choosing "Properties". 

There is a built-in program for viewing PDF files, but you can still  install Adobe Acrobat Reader for PDF's and Adobe Flash for web videos if  you wish.  
One interesting note is that almost any program in Linux can save files as PDF without additional charge.

There is something similar to a "DOS Prompt" (if you ever used that).   In Linux it is called the "Terminal" and is very similar, but more  advanced.  Many people swear by the Terminal. 
The "dir" command is replaced by "ls" (that's an "el", not a number 1).   "pwd" stands for "print working directory" and that tells you where you  are.  There are lots of references online for more commands.
Always remember that the Terminal is case sensitive, unlike the DOS prompt.  "Bob" is different from "bob".

There is an amazing program/feature that Windows doesn't have called  "Ubuntu Software Center" where you can download over 30,000 programs  completely free of charge.  You just type in what you are looking for  and it brings up a list of programs available.  Practically anything you  can think of. They are also divided into categories for easy browsing.

The main web browser is Firefox (which is also available in Windows if  you haven't used it) it is far safer than Internet Explorer and an  excellent replacement.  There are other web browsers available if you are interested, but I think Firefox is great.

The main e-mail program is called "Evolution" and should look very  familiar.  It is similar to Microsoft Outlook and Outlook Express, with  some more features, but works fundamentally the same.

There is a dictionary to look up words called simply enough  "Dictionary".  And one nice thing about Linux is that Dictionaries are  built into almost every program, unlike Windows where that "feature" is  usually extra or only available in higher end packages.

Linux supports digital camera's and scanners too.  There is a program  called "Shotwell" for managing digital photos.  I'm not sure if Windows  even has a similar program.

There are a number of games available just like Windows.  There is the  old standby "Solitaire" and the old "Mines" game, as well as some  others.

There is also (drum roll please, get ready for it...) a calculator!  similar to Windows.

As you can probably see, the clock is in the upper right corner instead  of the lower right as in Windows, but it functions primarily the same.   There is even a calendar there.  There is also a neat feature that  Windows doesn't have:  You can edit your location and it will give you  the local weather in the panel next to the date and time. 

The four squares at the bottom right are called Virtual Desktops, called  Workspace 1, Workspace 2, Workspace 3, and Workspace 4, which is  something Windows does not have.  It is a little hard to explain, but it  is essentially like 4 desktops that can be accessed by clicking on each  of the squares.  You can have programs running in each one and then  switch back and forth between them. 

Linux is also pretty  good at recognizing printers.  It uses a generic universal printer  driver called "CUPS", which stands for "Common Unix Printing System" and  can recognize most printers.  Printers are installed and configured in  the "System -> Administration -> Printing" tool.

When you first log in you see what is called "GNOME" which is the whole  graphical user interface (GUI).  I don't know if you are old enough or  remember, but Windows 3.1 sat on top of DOS back in the day.  It is  essentially the same thing in Linux.  "Linux" is the operating system  underneath (like DOS), and GNOME is like Windows that sits on top of DOS  and lets you do things graphically instead of using a command line.   GNOME what gives you the menus, windows, mouse, folders, etc.

If you are interested, Ubuntu can also function as a server, similar to  Windows Server 2003 or 2008.  Linux can function as a Web server - like  Internet Information Server (IIS) - using the popular "Apache" server.   Linux can also be an e-mail server similar to Microsoft Exchange.  It  can be a print server and a file server as well.


I hope this is enough to get you started.

---

### Post by daddy0h on 2011-03-25
No answers to your question here, but I can tell you this... I am new to Ubuntu as well and decided to switch because my kids downloaded a couple of viruses from facebook and  i got tired of having to reinstall windows all the time in their computer.
It took a while for us to get going what with the new interface and all, but now we all use Ubuntu and I am back to my regular Windows routine, but now in Ubuntu, without worrying about viruses and other issues... hang in there and put on your thinking cap and enjoy the ride!

Daddy0h

---

### Post by samcot on 2011-03-26
DaddyOh, I don't know if I can get used to the idea of not having to worry about viruses and having to reload the Windows operating system! I've sort of gotten used to doing this: ](*,)

---

### Post by The Cog on 2011-03-26
> **samcot said:**
> DaddyOh, I don't know if I can get used to the idea of not having to worry about viruses and having to reload the Windows operating system! I've sort of gotten used to doing this: ](*,)
<Chuckle.>

I'm not sure I could ever get used to the idea of having to worry about viruses all the time, and reinstall the OS to make it work again on a regular basis. I really don't know how windows users put up with it. Although having said that, I do reinstall every 6 months when the next version is released because I want to see what whizzy new features there are.

---

### Post by samcot on 2011-03-26
Funny you should mention that, Cog, because I installed 10.10 but today I'm going to delete it and install 10.04 instead, not because I'm having a problem with 10.10 but just because both of the books I have are written for 10.04, and I don't want to worry that the books won't match my OS as I'm learning. And, for whatever it's worth, 10.04 is a "supported release."

---

### Post by TroN-0074 on 2011-03-26
I dont think you have to delete it just because the book is for 10.04. I am still reading the Ubuntu Bible Book even though I am using KDE and the book is for Gnome.
However one of the beauties of Linux is that you can do whatever float your boat. Good luck to you.

---

### Post by Miljet on 2011-03-26
When you first start Ubuntu, it polls your hardware and automatically downloads any drivers you may need.

However the paradox with wireless drivers is that Ubuntu can't download the drivers because you aren't connected to the Internet, and you can't connect to the Internet because you don't have the proper drivers.

The simple solution is to temporarily use an ethernet cable to connect so Ubuntu can fetch the required drivers. Then it is usually just a matter of going to System -> Administration -> Hardware Drivers and enabling the driver.

---

### Post by steveneddy on 2011-03-26
> **Miljet said:**
> 

**The simple solution is to temporarily use an ethernet cable to connect so Ubuntu can fetch the required drivers. Then it is usually just a matter of going to System -> Administration -> Hardware Drivers and enabling the driver**.

This is the answer here - plug in the cable and get the drivers for your wireless card - then UPDATE!

enjoy

Everything you need is in the upper right hand corner - applications (obvious), places (folders on your hard drive) and system (set preferences for the machine)

Just click around on the desktop and you'll get it.

The learning curve will be steep for a few days, but keep plugging away, you'll get it.

---

### Post by smoobandit on 2011-03-30
The fact that you have to get your wireless internet connection working before you can go online to download the files you need to get your wireless internet connection working has always amused me about Ubuntu.  Well, I say amused, but some other more appropriate and less family friendly words also come to mind.  The reason that I use a wifi network is because I do not want 50 metres of CAT5 cabling littering the house.

 There are a couple of alternatives to getting wifi working on a LiveCD without endangering the household by laying what is essentially a 50 metre long tripwire everywhere.  I would suggest googling for "broadcom firmware ndiswrapper ubuntu" or "broadcom firmware virtual machine ubuntu".  You should find some handy tips on how to use an already working wifi connection on some other OS to get the files you need to make it work under ubuntu.

Edit:  Incidentally [this]("http://ubuntuforums.org/showpost.php?p=10598098&postcount=7") is an excellent post, and I would have significantly fewer grey hairs had I read something like that before trying to get Ubuntu to work.

---

### Post by josephmills on 2011-03-30
Hi there If you go to Applications --> accessories--> terminal (or ctrl+alt+t)a box will pop up with the cli type in ```
lspci
```then paste that back to us. Also could you type in ```
lspci -vnn | grep 14e4
``` and paste that also thanks for your time and welcome to ubuntu.

---

### Post by galacticaboy on 2011-03-30
Welcome to the world of Linux, it's full of fun, joy, bliss, and heartaches. Yes, heartaches. We see so much potential go out the door sometimes, but most of the time, it is made up by something else wonderful! Linux can be confusing at first, but once you learn the basics, the rest comes easy! Don't sweat it, we are here to help! Just wanted to put my two cents in!
David

---

### Post by mastablasta on 2011-03-30
> **The Cog said:**
> <Chuckle.>
 
I'm not sure I could ever get used to the idea of having to worry about viruses all the time, and reinstall the OS to make it work again on a regular basis. I really don't know how windows users put up with it. Although having said that, I do reinstall every 6 months when the next version is released because I want to see what whizzy new features there are.
 
 
I saw this and i just can't help but to comment. I am worried about viruses but antivirus software+Firewall+default open ports closed keep my worries at bay.
 
i keep hearing this constant widnows reinstalling of OS. i hguess this happens when users don't have a clue about the OS and i take it it also happens in the linux world. mess up the system - reinstall. it's the simplest solution isn't it?
 
I have a computer constantly uprgaded since 1999 was hosting Win98 at start (untill we decided to upgrade RAM) and has now been running XP for a while. perhaps about 7,8 years. It has not been infected or reinstalled once! that was family computer used by many people.
 
In addition to that i have my own computer now 4 years old with XP installed (i installed it). this one had 3 reinstalls last one lasted for 3 years. the reason was as i later found out hardware error. once fixed, no resintall was needed. 
 
Don't get me started talking of about 4500 computer running windows that we have at work. they run like clockwork. ofcourse we don't have administrator acocunts on them, are behind firewall and are runnign an antivirus.
 
so i really, really do not understand people doing continuous install. either there is something wrong with hardware (erro, incompatible...) or they are performing some system taks that they shouldn't be performing.
 
Last unstable windows for me were 3.11. And even those were not so bad that would ever need a reinstall. the floppy disks they came on were used only once. later they were replaced by Win95 and the computer is still working today after so many years. 
 
Ofocurse i never put the latest version of the system on computer. Unlike ubuntu where even the latest one won't play CD's (or rather won't mount them propperly in GUI).

---

