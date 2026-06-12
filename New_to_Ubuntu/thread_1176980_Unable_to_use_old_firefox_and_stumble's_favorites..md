---
title: "Unable to use old firefox and stumble's favorites."
date: 2009-06-02
forum: New to Ubuntu
---

### Post by naone on 2009-06-02
Hi, so...I have the firefox's folder with bookmarkbackups, chrome, searchplugins(...) that I've saved when I was using Windows... but now I can't replace the firefox folder on Ubuntu. I even have the stumble favorites, but I have no ideia on how to put them either. I searched for these on the forum but couldn't find any help yet.
If anyone could help me, well...thanks in advance. :)

---

### Post by presence1960 on 2009-06-02
Your firefox profile folder is located in your home directory. once there hit Ctrl + H to show hidden files. your Firefox folder is .mozilla. Copy your profile folder to .mozilla/firefox folder. Then open a terminal and run > firefox -profilemanager Click create to add a new profile and follow the prompts to select the folder you just copied over. After creating the new profile you can safely delete the old profile.

Be aware that some of your windows add-ons in Firefox may not work. You can remove them and then add the corresponding Linux add-ons from mozilla's site.

---

### Post by TheForumTroll on 2009-06-02
You can import your bookmarks from the bookmark menu under Bookmarks > Organize bookmarks.

If i were you I would start from scratch and add everything i need again. That way you know everything is as it should be.

---

### Post by naone on 2009-06-02
Just got it! Did the html backup, I don't know why I didn't think about that. Thanks for the help!

---

