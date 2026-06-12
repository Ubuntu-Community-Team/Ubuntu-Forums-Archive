---
title: "Gnome Panel; Places $ Problem"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Ducalex on 2010-12-04
When I scroll to the Places tab and try to bring up anything from Home Folder through Downloads I get an error saying File Not Found. Could anyone help me fix this? I have tried fixing it myself to no avail.   

     Thanks, Alex 


The Code I used attempting to fix it was:
> 
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panelThe problem persists.

---

### Post by XeonBloomfield on 2010-12-04
Open Nautilus and look on "Bookmarks" panel. Next click on "Edit Bookmarks" button to edit it.

Gnome Panel using Nautilus bookmarks to show it in "Places" menu.

---

### Post by Ducalex on 2010-12-04
All of the Bookmarks are there Under Nautilus>Bookmarks.

I even opened up the edit window to review the strings and all of those are correct.

/home/username/Downloads

So on and so forth.

---

### Post by XeonBloomfield on 2010-12-04
Does folders in your "/home/username/" exist?

---

### Post by Ducalex on 2010-12-04
All of the folders it is looking for exist in /home/username/

---

### Post by XeonBloomfield on 2010-12-04
Paste here output of "ls -l" command in "/home/username/". Did you try to do something with these folders?

---

### Post by Ducalex on 2010-12-04
> Paste here output of "ls -l" command in "/home/username/".

-I don't know how to do this.

No I didn't try to modify these folders or Gnome-Panel in any way before the occurrence of this error.

---

### Post by XeonBloomfield on 2010-12-04
Click on "Applications" > Accessories > Terminal. Enter "ls -l" here and press enter. Next copy output of it here. 

Hmm, it's interesting what happened with these folders...

---

### Post by Ducalex on 2010-12-04
I figured out how to do it.

---

### Post by plucky on 2010-12-04
Right click on a folder in Nautilus and select **Open with Other Application** and in the list that opens select **File Browser** then select **Open**.


Good Luck

---

### Post by Ducalex on 2010-12-04
> **plucky said:**
> Right click on a folder in Nautilus and select **Open with Other Application** and in the list that opens select **File Browser** then select **Open**.


Good Luck

Thanks a lot this fixed my problem. Thank you as well Xeno.

---

