---
title: "Deleteing files from windows box via network"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by robertpolson on 2007-01-30
Why is it that I cannot delete files properly form windows, I have mounted with full read and write permission my windows box and whenever I try to delete a large file, say 600mg, it kind of hangs as if deleting for Linux means pulling the file from windows box to linux box and then deleting. 

Can I delete files straight from windows box via CIFS mounting ?

---

### Post by jpeddicord on 2007-01-30
When you delete the files, it usually copies it locally to your trash bin, which could explain the lag. To enable a permanent, no-trash delete, open Nautilus preferences from Edit > Prefrences, and on the Behavior tab, make sure "Include a Delete command that bypasses Trash" is checked. In the Windows folder, you can right-click on the file and select Delete instead of Trash. It should then remove the file properly. :)

---

### Post by robertpolson on 2007-02-01
Thank you. Found these settings in Konqueror - Kubuntu. All works.

---

