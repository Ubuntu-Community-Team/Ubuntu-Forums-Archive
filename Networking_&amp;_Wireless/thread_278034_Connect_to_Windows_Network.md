---
title: "Connect to Windows Network?"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by jschall on 2006-10-15
I have a home wireless network managed through a Linksys WRT54G (default gateway, 192.168.1.1). A Linksys NSLU2 is connected to the 54g, and two USB disks are connected to the NSLU2.

The NSLU2 is on my Mshome Windows Network, where it shows up as "Lkgd7f7d5", with IP address 192.168.1.77. The two USB drives are known as "DISK 2" and "HDD_1_1_1".

I would like to connect to the file servers on the NSLU from my Ubuntu laptop. I can ping the NSLU2 at 192.168.1.77. Under Places/Network Servers, I can see an icon for "Windows Network", but there are no contents. I have tried with Places/Connect to Server/Windows Share, using the Server Name Mshome, but I get this error message:

The folder contents could not be displayed.Sorry, couldn't display all the contents of "Lkgd7f7d5:HDD_1_1_1".

What am I doing wrong? Do I have to set some file sharing on the Windows Network?

- Jeff

---

### Post by Zendarin on 2006-10-18
Hey, I can't help you myself, but I hope someone answers, but this is the same problem I am setting.  Windows connects fine to my Ubuntu machine, but I get cannot display all files.  I think it is a permission issue related to sharing, but am not sure. I wish I could really help you.  I've googled it for a week, but nothing yet.  Don't get discouraged :)

---

### Post by jpmrblood on 2006-10-18
Well, to connect to your Ubuntu box (u-box), you must install Samba server on your u-box. I haven't try it yet via wireless network, but if you could ping your Win-box, you may try to have Win File Sharing enabled on the Win-box and set the drive or directory (folder) that you would like to share. So, your u-box can access it via nautilus:

```
smb://192.168.1.77/
``` 

For the last resort, you may enable ftp access on your Win-box. This works fine.

---

### Post by Iowan on 2006-10-18
> **jschall said:**
> ... but I get this error message:

The folder contents could not be displayed.Sorry, couldn't display all the contents of "Lkgd7f7d5:HDD_1_1_1".

What am I doing wrong? Do I have to set some file sharing on the Windows Network?

- Jeff
That's the error message I see when I either have sharing disabled on my XP box - or have neglected to allow filesharing in the Windows firewall. I'm not familiar with the Linksys NSLU2, so I don't know what kind of sharing setup it might have.

---

### Post by Zendarin on 2006-10-19
That is the exact same message I get, and I use a wired D-Link router.  I have XP Home, does that have anything to do with it??

Now, my Win box doesnt even show up in the network on my Linux box.
Very annoying :mad:

---

### Post by jschall on 2006-10-21
jpmrblood's suggestion of using the NSLU2's ip address directly in Nautilus:

smb://192.168.1.77/

works great for me! So sharing must be set up correctly on the "SLUG" :p 

Now, it would be nice to create an Alias, or shortcut, for that URL. How do I do that in Ubuntu/Nautilus?

Thanks to all!

- Jeff

---

### Post by Zendarin on 2006-10-23
Hey Thanks!!

It does work finally :D   Here is how to mount it permanently

[http://www.ubuntuforums.org/showthread.php?t=255872&highlight=mounting+shares]("http://www.ubuntuforums.org/showthread.php?t=255872&highlight=mounting+shares")

BTW, you can access it in Nautilus as well, but it's easier in Konquerer

---

### Post by Iowa Dave on 2006-10-26
Zendarin's link takes you to an excellent How To: on mounting windows file shares on the command line, meaning things you type into a Terminal window. Here's how I get it to work using the Dapper graphical desktop. 

First, let's call the computer you want to connect to (from Ubuntu) the "target computer." 

Make sure the target computer has Windows file sharing turned on. On Win 98 just right-click on a folder and select Sharing. On Win XP it's trickier, but the directions are in the help files. On Mac OS X it's in System Preferences - Sharing, turn on Windows Sharing. (Also, just for grins, make sure the target computer is turned on, booted up, and connected to the network. I know, I know, but these things happen...)  ;) 

OK, now let's find out the name and address of the target computer. 
[INDENT]Select Places > Connect to Server...[/INDENT]
[INDENT]Click Browse Network[/INDENT]
Wait a few... A window will open. Wait some more... A Windows Network icon  will appear in the window. This is progress!
[INDENT]Double click the Windows Network icon.[/INDENT]
It will open to reveal one or more workgroup icons. The icon name is the name of the workgroup. Write that name down, you're going to need it.
[INDENT]Double-click the windows workgroup icon.[/INDENT]
Your Windows shares should now be visible. Any of them that are not password-protected on the target computer should be available just by double-clicking on the name of the share.

But what if the share is password protected, or double clicking the icon doesn't work? No fear. The simplest thing I've found to do is write down the name of the workgroup and the name of the target computer, then close the File Browser window and start over. It's fast, it's easy and it works. Here we go:

[INDENT]Places > Connect to Server...[/INDENT]
[INDENT]Change Service type to: Windows share[/INDENT]
[INDENT]Type the target computer's name next to Server. Being case-sensitive won't hurt, but it doesn't seem to matter. (This seems to be a required step.)[/INDENT]
[INDENT]Type the share name next to Shares: (This seems to be optional, but being specific might be useful for getting directly to the share you want to access.)[/INDENT]
[INDENT]Type a folder name, if you wish, next to Folder. (Again, apparently optional. You might want to do this if the folder were one where your user name matters for permission reasons.)[/INDENT]
[INDENT]For User Name type the name of the user account by which you want to log in to the target computer. (Optional, unless the target computer requires it.)[/INDENT]
[INDENT]For Domain Name enter the Windows Workgroup name. (This is required information.)[/INDENT]
[INDENT]Next to Name to use for connection: type the name you want this share to be labeled in your Ubuntu filesystem. (Optional. Ubuntu will give it a meaningful name if you don't.)[/INDENT]
[INDENT]Click Connect[/INDENT]
A folder will appear on your Ubuntu desktop with the name you are using for the connection.
[INDENT]Double-click the folder on your desktop.[/INDENT]
If all goes well, you'll see a message that Ubuntu is opening the share. Wait a few... A window will open. Wait some more... If asked, enter the password for the user account that you are logging into on the target computer. Wait a bit longer...
And there it is!

I have tried leaving various of the fields blank. The ones that matter most are the Server (target computer) name and the Domain (Windows Workgroup) name. 

Frankly, once you make it work this way, you will recognize the bits that you need to type using Zendarin's method. As you gain experience, you'll find that the Terminal (a.k.a. Command Line) way is faster. It is the true Unix Way. But the graphical desktop is nice for taking it step by step. There is more than one way to do things in Ubuntu, and that's a good thing.

Iowa Dave

---

### Post by kylevan on 2006-10-27
wow... I've had a bit of experience getting things shared between Linux and Windows with SAMBA, but this one is new.

things... *seem* to be working in Edgy, but not always.  

When I went to setup the networked printer, things were totally automatic, with the setup utility detecting the different windows shares on the workgroup and even the printers themselves.  Better than previous distros I had used where I had to manually enter the //workgroup/computer/share to get things working.

So, I'm all happy-slappy (new to Ubuntu, lots of stuff seems to "just work") and such, so I open my Places>Network Servers, and the workgroup won't open "not a folder" apparently.  Soooo whatever, do some searching on here, then hit the reload button in nautilus for kicks, and suddenly I can browse through the workgroup... now, of the 3 workstations shared on the network, it seems I can randomly access them through nautilus depending on how many times I press the reload button.  It's actually kinda funny to watch.  No apparent pattern, no nothing, just a sort of crap-shoot to see which will work... ](*,)

I can ping all 3 computers at any time, so it's obviously some goof in nautilus (?) any ideas?

---

### Post by Zendarin on 2006-10-29
For some reason I still can't browse my Windows shares in network browser, but I just type the smb:// address in Nautilus or Konquerer (if you have KDE installed - recommended!) and the share shows up :cool: Also in Konquerer, you can bookmark the share, and it has a "Copy To:" option in the contextual menu.

KDE runs a little slow on my L-Box, but Konquerer in Gnome runs great :)

---

### Post by DoneRightI.T. on 2007-06-06
The problem with your connection I would believe is that your not on the same workgroup....

I had this problem, changed the workgroup on my winxppro box, and rebooted it(good ole windows) and voila, there it was.

I cannot claim to be a guru of Ubuntu, or any version of linux... but I do know a fair bit about windows.... hope this is of some help and I wish you the best of luck.

---

### Post by franck3d on 2007-11-27
> **Zendarin said:**
> For some reason I still can't browse my Windows shares in network browser, but I just type the smb:// address in Nautilus or Konquerer (if you have KDE installed - recommended!) and the share shows up :cool: Also in Konquerer, you can bookmark the share, and it has a "Copy To:" option in the contextual menu.

KDE runs a little slow on my L-Box, but Konquerer in Gnome runs great :)

WhooHooo!   Thanks for that!  I've been trying to get my office computer migrated over to Ubuntu(I'm now dual booting) and that little tip has given me a huge boost!
I just added my networked drive as a "shortcut" and now it appears under "Places"!

Now I just have to get access to the Access database we have and I can boot windows out the door!

---

