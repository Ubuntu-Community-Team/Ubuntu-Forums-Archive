---
title: "read/write permissions"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by NutmegCT on 2009-11-20
I want to follow a suggestion I was referred to in another topic:

[http://ubuntuforums.org/showpost.php?p=7276275&postcount=8](http://ubuntuforums.org/showpost.php?p=7276275&postcount=8)

the idea is to comment out (#) a reference and reboot.

I found the file (dhclient.conf), opened with gedit, and made the changes.  But system won't let me save the modified file (says I'm not the owner).

I tried moving the file to the desktop, and writing a new file in the original location.  Same problem.

How can I edit that .conf file?  I think I need to know how to get permission to edit it.  As I'm new to Ubuntu, maybe someone could give me the step by step?

Thanks.
Tom

---

### Post by camaron1 on 2009-11-20
> **NutmegCT said:**
> I want to follow a suggestion I was referred to in another topic:

[http://ubuntuforums.org/showpost.php?p=7276275&postcount=8](http://ubuntuforums.org/showpost.php?p=7276275&postcount=8)

the idea is to comment out (#) a reference and reboot.

I found the file (dhclient.conf), opened with gedit, and made the changes.  But system won't let me save the modified file (says I'm not the owner).

I tried moving the file to the desktop, and writing a new file in the original location.  Same problem.

How can I edit that .conf file?  I think I need to know how to get permission to edit it.  As I'm new to Ubuntu, maybe someone could give me the step by step?

Thanks.
Tom

On a terminal write:

**sudo gedit /**(here either write the full name of the file or drag and drop the file)

You'll be asked for you password and Gedit (text editor) will open the file with administrative privileges. Now you can modify and save it

---

### Post by 3rdalbum on 2009-11-20
That should be:

```
gksudo gedit 
```

which opens Gedit as root; now you can use File > Open to open the file and edit it as you please.

You should also install the "nautilus-gksu" package from Synaptic. When you next log in after installing the package, you'll be able to right-click a file or folder and choose "Open as Administrator"; this will open the file as root, or a new root file browser window with the selected folder.

---

### Post by camaron1 on 2009-11-20
> **3rdalbum said:**
> That should be:

```
gksudo gedit 
```which opens Gedit as root; now you can use File > Open to open the file and edit it as you please.

You should also install the "nautilus-gksu" package from Synaptic. When you next log in after installing the package, you'll be able to right-click a file or folder and choose "Open as Administrator"; this will open the file as root, or a new root file browser window with the selected folder.

Just asking, would you not be able to change and save the file using sudo? What is the difference?

---

### Post by nothingspecial on 2009-11-20
See [[COLOR="Magenta"]here[/COLOR]]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by camaron1 on 2009-11-20
> **nothingspecial said:**
> See [[COLOR=Magenta]here[/COLOR]]("http://www.psychocats.net/ubuntu/graphicalsudo")

Thanks for the link, I take note

---

### Post by NutmegCT on 2009-11-20
Thank you!  I figured it was a permissions issue, but didn't know about the sudo/gksudo difference.

Tom

---

