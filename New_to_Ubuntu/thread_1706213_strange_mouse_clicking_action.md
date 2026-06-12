---
title: "strange mouse clicking action"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by gcomito11 on 2011-03-13
I have been messing around with torrents adn so using a ton of archive manager which as a noobie is extreme guess work, I think I am ready to give up becuase once I finally get a file to download all the way, it is in some wierd format that i cannot use nor tanslate into file liek an iso that I know how to use.... frustrated.

Well now that I am done everytime I click on any file folder or even and especially annoying is when I go to application->places->home or anything else it opens up archive manager which is really realy annoying and I cannot figure out how to go back to opening the darn folder please someone help!!!!!!!!!!!!!  It is really making me feel rather stupid. really stupid.  :confused:

also if you can answer the question of how to convert wfps files to iso or rar files to iso that would really be helpful as well.:confused:

---

### Post by gcomito11 on 2011-03-14
Here's the answer I found after 3 days of frustration!!  Works great!!
   gedit ~/.local/share/applications/mimeapps.list
 Change the line starting:
  inode/directory=
 to read:
  inode/directory=nautilus-folder-handler.desktop;*

little disapointed this question is posted everywhere and no answer anywhere

credit goes to matt blowers at [http://askubuntu.com/questions/6869/places-folders-open-in-archive-manager](http://askubuntu.com/questions/6869/places-folders-open-in-archive-manager)

---

