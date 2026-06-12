---
title: "Deleting programs"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by grantmcduling on 2011-04-04
Hi,

I would like to know how to go about deleting a program that was loaded without using the Synaptic Package Manager. Do I just highlight the package in my home folder and send it to trash?

Also, if that package is mentioned in the Applications tab that appears on the top right side of the screen, under accessories, how do I get rid of it there?

Regards
Grant

---

### Post by pi3.1415926535... on 2011-04-04
Assuming that you did not use a program (Apt, Softare Center, Synaptic) to install the package deleting it, and it's corresponding configuration folder (.program-name), which is generally a hidden file, that should be fine. As for the menu, right click the menu - edit menu - find the program - delete button on the side bar when it is selected.

---

### Post by jtarin on 2011-04-04
What is the program in question? How did you install it?

---

### Post by grantmcduling on 2011-04-04
It's called cqrlo=g and i downloaded it from their website.

---

### Post by Chronon on 2011-04-04
So, did you run an install script or just untar an archive?  If the latter then you should be able to simply delete the appropriate directory/files (which might be in your home directory).

---

### Post by grantmcduling on 2011-04-04
Deleting the program worked, thanks. Now just to get rid of it from the Accessories menu. When I click on Applications, Accessories and move down to the program in question, and right click on it, the only options I get is: add this launcher to panel, add this launcher to desktop or Entire menu.

Can't seem to get rid of it from there.

---

### Post by grantmcduling on 2011-04-04
To be a bit more specific, this is what I have found: If I right click Accessories and then find the program I want to get rid of, I don't see it is the list of items displayed. It has obviously been deleted as previously mentioned. However, if I click on Applications and then on Accessories, the icon is there. So how do I go about cleaning this list up to reflect what programs are actually live?

---

### Post by beew on 2011-04-05
The icon is a desktop file. It is probably installed in /home/username/.local/share/applications (or in /usr/local/share/applications if you use "sudo" at some point during install) The file .local is hidden so you have to check "show hidden files" to see it when you are in your home directory.

You can search for all installed files associated with the program and delete them (Places > Search For Files)

Alternatively (without removing the desktop file but just to remove it from the menu) go to System > Preference > Main Menu. Choose Accessories from the left panel and then find the entry for your program on the right panel and remove/uncheck it.

---

### Post by jtarin on 2011-04-05
Sometimes a simple reboot will clear these.....when it's been removed.

---

### Post by grantmcduling on 2011-04-05
Thanks for this tip. Rebooting did the trick. I am now happy.

---

