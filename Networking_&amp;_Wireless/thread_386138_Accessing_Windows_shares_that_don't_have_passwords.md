---
title: "Accessing Windows shares that don't have passwords"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by CalcProgrammer1 on 2007-03-16
I'm trying to get my Ubuntu PC's to recognize and access data on my Windows PC's.  I use the "Shared Folders" feature of Windows on all of my PC's (Without passwords) to access the data on other PC's.  I used the System --> Admin --> Networking menu and entered my computer's name, and then I used the Shared Folders menu to put in my network name (Home Network).  My network doesn't have a WINS server.  The PC's are connected using a desktop switch and a router.  I then go to Places --> Network, click the Windows Network, click Home Network, and I see a list of PC's on my network, but when I double click them, it comes up with this error:

[quote="Cannot Open <Computer Name>"]
The filename "<Computer Name>" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.
[/quote]
I mount the computer using the right click menu, then I go to Places --> <computer name>.  I then get:

[quote="The folder contents could not be displayed."]
Sorry, couldn't display all the contents of "<Computer Name>".
[/quote]

This is on 6.10, though I've had problems with 6.06 as well, and I have the same problem on 2 computers (both 6.10).

---

