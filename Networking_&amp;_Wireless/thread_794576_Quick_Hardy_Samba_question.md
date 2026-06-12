---
title: "Quick Hardy Samba question"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by phyrko on 2008-05-14
I am looking for the "Windows Networking" section of the General tab of the Network Settings tool but it is not there.

Is this a bug? Why does the Community Documentation claim it is there?

---

### Post by jetsam on 2008-05-14
I think what you're looking for is under System-->Administration-->Shared Folders, not System-->Administration-->Network.  They both have "General Properties" Tabs, but "Shared Folders" has Windows specific stuff while "Network" has your hostname and domain info.  

It might be that "Shared Folders" doesn't show up before you've shared a folder.  There's a Hardy specific glitch with this. See post #4  of this [thread]("http://ubuntuforums.org/showthread.php?t=772706") if there's no "Shared Folders" under  Administration  and you haven't yet shared a folder.

The community docs could be incorrect, or you might have misread them.  Could you post a link to the specific page that confused you?

---

### Post by phyrko on 2008-05-15
OK. I'm not at home and my work PC has Gutsy so I'll have to wait to discover if rebooting/logging out fixes.

The offending article is [here]("https://help.ubuntu.com/community/SettingUpSamba#head-8e150e1996272f3eb37363c960274baed221513e").

Many thanks.

---

### Post by jetsam on 2008-05-15
OK.  I think that screenshot and the instructions are for an old version (Edgy?).  The text explains a bit later, but I can't blame you for not noticing the line: "On Feisty and Gutsy, these settings are in System -> Administration -> Shared Folders."  Hardy too, it should say.

---

### Post by bouta on 2008-05-15
in hardy i cant find any shared folders under administration ..

---

### Post by jetsam on 2008-05-15
Tarnation!  Shows me not to answer a question without testing the solution.  

You're correct.  This seems to be missing functionality from Hardy, and I hope they put it back somehow and soon. 

Workarounds:

**The Somewhat Kludgey GUI Way:**
Open a terminal and type:
```
gksu shares-admin
```
The old "shared folders" control panel will come up.   Click the "General Properties" tab and hit "unlock" at the bottom.  Enter your password, and you can now set your workgroup name.  

I _think_ you shouldn't use this interface to set up individual folder shares.  They've changed how all this works, and you should set individual share properties by right clicking on the shared folder itself and selecting "properties" and then the "share" tab.


**_Or_ use The Stable Old Fashioned Way:**
open a terminal and type:
```
gksu gedit /etc/samba/smb.conf
```
Enter your password.  Find the line in the file which probably reads:
```
workgroup = WORKGROUP
```
and edit it.  Change WORKGROUP to your workgroup name.  Save the file.

---------------------

With either method, you probably need to restart Samba after you change the workgroup name.  Do this in a terminal with:
```
sudo /etc/init.d/samba restart
```


Sorry about that.  I was out of date like the community docs. :?

---

