---
title: "File associations in ntfs?"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by donsy on 2009-10-01
I have a lot of .rtf files on my ntfs partition that I would like to open in OpenOffice.org, and in Properties > Open With that is the selected application. However, when I double-click an icon I get a popup asking if I want to Run in Terminal, Display, Cancel, or Run. If I click Run, nothing happens. These files are owned by root, and permissions are rwxrwxrwx. I have a feeling that if I can change the permissions to rw-rw-rw maybe the file associations would work, but sudo chown and sudo chmod don't have any affect. Is there any way to set file associations on a ntfs partition?

---

### Post by mikewhatever on 2009-10-01
First, I don't think OpenOffice.org is an application. What you want is probably ooffice-writer instead. Some text files need to be run, but that's not the same as opening with writer, and permissions have nothing to do with it, although I don't see why these files need to executable. You need to select Display instead of Run, and if you want that done automatically, open Nautilus, Edit->Preferences, Behavior tab, and under Executable Text files select the second option.

---

### Post by donsy on 2009-10-01
Thank you. :P

---

