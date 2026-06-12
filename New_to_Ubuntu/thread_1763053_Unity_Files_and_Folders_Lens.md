---
title: "Unity Files and Folders Lens"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by audiosnow on 2011-05-19
I recently installed Ubuntu 11.04 with Unity. I had a bootup-mounted NTFS hard drive, with a folder on that drive listed as a favorite in Nautilus.

That NTFS drive was removed from Fstab, and then replaced under a different label. The old, invalid favorite shortcut is invisible in Nautilus, with its updated brother working perfectly. In the Unity "Files and Folders" lens, the invalid "Favorite Folders" link sits beside the new, working one.

```
Unity --reset
``` and ```
Unity --reset-icons
``` didn't reboot the Lens.

Is there any way to edit the Unity Lens configuration files directly? Any idea where they are located?

Thank you for your time and responses.

---

### Post by wildmanne39 on 2011-05-19
> **audiosnow said:**
> I recently installed Ubuntu 11.04 with Unity. I had a bootup-mounted NTFS hard drive, with a folder on that drive listed as a favorite in Nautilus.

That NTFS drive was removed from Fstab, and then replaced under a different label. The old, invalid favorite shortcut is invisible in Nautilus, with its updated brother working perfectly. In the Unity "Files and Folders" lens, the invalid "Favorite Folders" link sits beside the new, working one.

```
Unity --reset
``` and ```
Unity --reset-icons
``` didn't reboot the Lens.

Is there any way to edit the Unity Lens configuration files directly? Any idea where they are located?

Thank you for your time and responses.
HI, look at the unity power user guide in my signature below this text. Then information on lenses is towards the bottom of the page.

---

### Post by audiosnow on 2011-05-20
I appreciate your time and reply.

The Unity Lens Documentation put me on the right track, but I'm unsure where to go from here.
Before posting this thread, while searching around on the hard drive and Google I discovered the "/usr/share/unity/places/files.place" file. Contents below:

```
[Place]
DBusName=com.canonical.Unity.FilesPlace
DBusObjectPath=/com/canonical/unity/filesplace

[Entry:Files]
DBusObjectPath=/com/canonical/unity/filesplace/files
Icon=/usr/share/unity/themes/files.png
Name=Files & Folders
Name[da]=Filer og mapper
Description=Find documents, downloads, and other files
Description[da]=Find dokumenter, downloads og andre filer
SearchHint=Search Files & Folders
Shortcut=f

[Desktop Entry]
X-Ubuntu-Gettext-Domain=unity-place-files
```

I assume that I must find this "/com/canonical/unity/filesplace" file and edit it, assuming it actually is a file and not a daemon. Is this theory correct, and if so do you know where it is?

Thank you.

---

### Post by wildmanne39 on 2011-05-20
> **audiosnow said:**
> I appreciate your time and reply.

The Unity Lens Documentation put me on the right track, but I'm unsure where to go from here.
Before posting this thread, while searching around on the hard drive and Google I discovered the "/usr/share/unity/places/files.place" file. Contents below:

```
[Place]
DBusName=com.canonical.Unity.FilesPlace
DBusObjectPath=/com/canonical/unity/filesplace

[Entry:Files]
DBusObjectPath=/com/canonical/unity/filesplace/files
Icon=/usr/share/unity/themes/files.png
Name=Files & Folders
Name[da]=Filer og mapper
Description=Find documents, downloads, and other files
Description[da]=Find dokumenter, downloads og andre filer
SearchHint=Search Files & Folders
Shortcut=f

[Desktop Entry]
X-Ubuntu-Gettext-Domain=unity-place-files
```

I assume that I must find this "/com/canonical/unity/filesplace" file and edit it, assuming it actually is a file and not a daemon. Is this theory correct, and if so do you know where it is?

Thank you.
Hi, no I do not no anything about that file.

---

### Post by audiosnow on 2011-05-20
It ended up being a simple matter of opening Nautilus, clicking "Bookmarks -> Edit Bookmarks", and removing the invalid shortcut. While invalid shortcuts do not appear in the Nautilus "Places" pane, they do in the Unity "Files and Folders" Lens.

Thank you for your help.

---

