---
title: "Share Folder"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by yangt299 on 2009-01-04
Hi I'm new to ubuntu and recently I've been using the software for the newest computer. I need to connect to my other computer, which is using Windows Vista, and I'm not sure if I'm doing this correctly. 

This is what I'm doing:

First I selected which folder I want to share. When I'm on that folder's page, I right-click and click on properties. I go to the share tab, and select 'share this folder' I do not change the share name and I don't check any of the other options. Then I click 'Create Share.'

This is the part where I'm stuck. It returns an error message:

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

However, there is only one user account on this computer, so I take this to believe that I am the administrator. 

Is there some way that I am not the administrator of my computer? 

Thanks...

---

### Post by mbzn on 2009-01-04
Ok, you are not the administrator. In linux you have to log in to your root account before you are, which is disabled in ubuntu. You must ure the sudo command, it wil give you the necessary privilages. It would help you to read up on sudo, it can become verry dangerous. The ubuntu help files should be a great start.

---

### Post by Kellemora on 2009-01-04
Hi Y

I see this is only your second post, so I'll try to help you out a little more here.
Linux is a very secure OS, which is why it is NOT plaqued with Viruses, Trojans, Worms, Malware and Spyware like the DOZE!

In Linux, as a USER, you are limited to only USER privileges.
To do anything that can affect the system, you have to become a SUPER-USER (Administrator).

I'm assuming you would like to be able to share files and folders without using command line instructions to do so.  In other words, doing it inside a WINDOW you are more familiar with.  In Linux this is called a GUI for Graphical User Interface.

So, lets get you set up so you can more easily become the ROOT User (same as Super-User).
Up at the top left of your screen is the word Applications.
You can open this drop down and select System Tools to see if Root Terminal is in there, but I doubt it, until you MAKE it show up there.  And here is how that is done.

RIGHT CLICK on APPLICATIONS!  Scroll down and select EDIT MENUS!
This will open a new Window!  Look down the Menu's list until you see System Tools and highlight that line.
In the window on the right under ITEMS you will see Root Terminal.  Place a checkmark in front of Root Terminal and then Just hit the word CLOSE.

NOW, when you go to APPLICATIONS/SystemTools you should find Root Terminal in the listing.  Select it!
A box will pop up asking for your Password.  This is your Administration Password.  In Ubuntu, Root Password and Administration Password are the SAME PASSWORD.  Other OS's use a separate password for Root and another for Administration.

After the Terminal window opens, you would type the word
nautilus
and then hit enter.
This will open the File Browser Screen you saw before, only NOW you will have Root Privileges to Create Shared Folders.

WHEN you create a shared folder, if you want to be able to use it without being ROOT, change the PERMISSIONS for the folder to YOUR Username under the PERMISSIONS TAB, similar to Windows method, you can make only you or everyone, read, or read and write!

Hope this helps you out!

TTUL
Gary

---

### Post by yangt299 on 2009-01-04
Hi.

Ok. I know I just screwed things up BIG TIME.

Before all your helpful posts were made, I decided to take matters into my own hands (BIG MISTAKE), so I found a thread that helped me log in as 'root' and I started messing with the File System. so I screwed that up. Then I restarted my computer, hoping that it would help to solve my problems, but when I tried to log in, two error messages would be displayed, saying that i needed to change user permissions to 644, because apparently, i screwed that up. And after those two error messages are displayed, the system logs me out immediately!! So then I go to the terminal session and now I'm trying to find a command to help me change user permissions. I hope I'm doing it right, but I wasn't sure so I got onto my other computer (the one I'm using to post this message) so I could ask for addition help. So...PLEASE HELP!!! I don't even know if I'm approaching my problem correctly! I know this isn't really the thread for this question but still, just help me!!!

Oh yeah, and sometimes (like 2/3 times) my computer loads ubuntu and this is freezes at this terminal loading screen, and its like loading this, loading that, ok, fail, etc, etc. And I can't exit the screen so then I have to restart the computer. Is this another effect of me mesing with the file system? If you want a more detailed account of what I did, I can give it to you.

Thanks to anyone who could help me with this problem!!!!!

---

### Post by yangt299 on 2009-01-04
And YES, I still want to be able to share my folder

THANKS AGAIN!!!!

---

