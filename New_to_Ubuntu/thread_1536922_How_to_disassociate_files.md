---
title: "How to disassociate files"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by Jaraqui on 2010-07-22
Hi guys,

   I need to associate files with an specific extension to
none application.

   Right now, in my 10.04, files with this extension are
alredy set wrongly by me to an app that I don´t want
it (neither other one).

   Because of this need I can´t use the "open with..." 
feature.

   Any idea?

Regards
Jaraqui

---

### Post by yetiman64 on 2010-07-22
> I need to associate files with an specific extension to
none application.For the affected filetype, right click a file select Properties > Open With tab, highlight and click remove for the unwanted programs (all of them by the sound of your question).

You can use the same Properties tab to add programs back if needed.

If you are specifically wanting to remove a user added application, look in ~/.local/share/applications for a userapp-*.desktop file (where the * is a wildcard and should be the name of the application and an ID number for it) and delete it - this will remove your excess "Open With" entry.

Note: ~ is a system indicator for your home directory and .local is a hidden folder, CTRL + H while in your home directory will reveal it.

---

### Post by Jaraqui on 2010-07-22
Excellent!

Thank you very much

Case closed
Best Regards
Jaraqui

---

