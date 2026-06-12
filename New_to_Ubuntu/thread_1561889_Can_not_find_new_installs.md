---
title: "Can not find new installs"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by Sleven7 on 2010-08-26
I have installed two different webcam programs and can not find either.

1. Cheese

2. CamStream

They do not appear under any application.  I opened the menu to see if by chance they were not checked and could not find them there either.  I used the Ubuntu Software Center to download both.  How do I find these programs?

---

### Post by jtarin on 2010-08-26
Try left clicking on the menu button and select edit menu and see if you can find them there and unchecked. Simply check them and they should show in the menu. Sometimes a simple reboot will allow them to show.
To find things on your computer easier run the command ```
sudo updatedb
``` every once in awhile. Then when it finishes running you can use the command ```
locate <filename>
``` to find anything.

---

### Post by Sleven7 on 2010-08-26
jtarin, I feel like an idiot, I don't even know where the "menu" button is located.
I did go to the "main menu" under System --> Preferences but saw no edit button.
I looked thru the programs there to make sure that they were not unchecked as you said, which is what I think you wanted me to do anyway, just don't know how to do it the way you said to.  Thank you for the help again, going to do the update now.

---

### Post by Sleven7 on 2010-08-26
I did the updatedb and was able to use the locate command to find both programs.
There are more than 100 locations mostly in the /usr file relating to both programs, but neither are showing up in the "Applications" folder or main menu, checked or unchecked.  I have used the Ubuntu Software Center to install other programs and they show up in the Apps file.

---

### Post by Sleven7 on 2010-08-26
Thank you again for your help, I went back to the Software center to look for another webcam and noticed that "Cheese" was showing as not installed.  When I first installed it the install took several minutes to complete.  I hit install again, this time it installed in a few seconds and showed up in the Apps.

---

### Post by -kg- on 2010-08-26
Very odd.

I installed both using Software Center.  Cheese shows up under "Applications/Sound and Video" but Camstream doesn't show up anywhere I can find, either.

I am able to launch it from the terminal by opening a terminal window and typing "camstream" (without quotes).  It launches and runs, but I'm a bit surprised that it didn't install an icon in any of the "Applications" sub-menus.

You can create a launcher yourself, though.  If you want it in one of the "Applications" sub-menus, just right-click on "Applications" and click "Edit Menus".  Once that launches, select the sub-menu you want to create the launcher in on the left (I selected "Sound and Video").  In the window that pops up, put in the name of the launcher to you are making (I inserted "CamStream"), then in the box below (labeled "Command") I typed "camstream".  That is the command I used to launch it in the terminal window.  Click OK, and the launcher will be in that sub-menu under the "Applications" menu.

If you want the launcher on your desktop, do the above steps except you will need to right-click on the desktop and select "Create Launcher".  You will be presented with the same pop-up window I mentioned above to create the launcher.

I notice that you found the problem with Cheese.  If you're still having the same problem with CamStream, though, the above will help.

---

### Post by jtarin on 2010-08-26
When something like this happens in the future you can try the command [dpkg-reconfigure]("http://manpages.ubuntu.com/manpages/jaunty/man8/dpkg-reconfigure.8.html").

---

### Post by Sleven7 on 2010-08-26
Creating the launcher worked beautifully, thanks

---

