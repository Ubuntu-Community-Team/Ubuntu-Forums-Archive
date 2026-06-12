---
title: "Connecting to windows file share from Ubuntu"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by wookaru on 2007-08-10
I too have a windows share on another computer that I'm trying to access from my Ubuntu desktop. From any other XP computer on our home network I access the share by typing "\\wooktop" into an explorer address bar. Then I am prompted for my user name (guest) and password (***) then I can all my shared folders. Heres what I have tried from Ubuntu:

Places->Connect to Server...

Server Type: Windows share
Server: wooktop
Share: (blank)
Folder: (blank)
User Name: guest
Domain Name: (blank)
Name to use for Connection: (blank)

Click Connect

Then what happens is a folder appears in Nautilus thats named wooktop with a SMB folder icon. But when I try to open that folder I get an error:
"Nautilus cannot display "smb://wooktop/" Please select another viewer and try again"

What am I doing wrong? The crazy thing is I can access my samba share on the desktop from the laptop, but its like the desktop cant see the laptop.

(PS i have a workgroup setup named 'WORKGROUP')

---

### Post by hypgnosis on 2007-08-10
I have almost the same setup at my office. We have lots of Windows shares (accessed by the \\shareName path). In Ubuntu, all I've done to access them is opened Places -> Network. In there should show up something like Windows Network. You should be able to drill down through there to find the actual share names and choose which one you're after. It'll still prompt you for a login if one is required but either way you should be golden.

-h

---

### Post by jimrz on 2007-08-10
> **wookaru said:**
> I too have a windows share on another computer that I'm trying to access from my Ubuntu desktop. From any other XP computer on our home network I access the share by typing "\\wooktop" into an explorer address bar. Then I am prompted for my user name (guest) and password (***) then I can all my shared folders. Heres what I have tried from Ubuntu:

Places->Connect to Server...

Server Type: Windows share
Server: wooktop
Share: (blank)
Folder: (blank)
User Name: guest
Domain Name: (blank)
Name to use for Connection: (blank)

Click Connect

Then what happens is a folder appears in Nautilus thats named wooktop with a SMB folder icon. But when I try to open that folder I get an error:
"Nautilus cannot display "smb://wooktop/" Please select another viewer and try again"

What am I doing wrong? The crazy thing is I can access my samba share on the desktop from the laptop, but its like the desktop cant see the laptop.

(PS i have a workgroup setup named 'WORKGROUP')

try using samba to connect ... Places > Network

                              -OR-

try Server but using the ip address of the target machine, rather than the computer name

---

### Post by wookaru on 2007-08-11
Ok, I tried going to Places->Network.  When I do that it opens a browser with a WIndows Network Icon.  But when I click the icon, nothing happens.  It doesnt open anything.  :/

Is there something I need to set in the samba config file smb.conf for browsing windows shares?

---

### Post by hypgnosis on 2007-08-11
I did not have to set anything - the networked machines were just there for me. In all honesty, I did notice that once or twice the shares would not be visible when I clicked the network link. I'm not sure why. They would usually come back after 5 minutes or so. Sorry I can't be clearer - I'm new to this too. :) -h

---

