---
title: "Problems with places menu opening bookmarks with the wrong application"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by spidertattoos on 2011-04-28
I have recently had a problem with the places menu on Ubuntu 10.10, whenever i clicked a bookmark-
  
 
pictures etc.
It was opened with appearance preferences (Computer, Desktop etc worked fine just the folder bookmarks bust) so after scouring the net for two days i found that a bunch of people have had he same issue.
i found the solution 

Simply run the following command in a terminal or via Alt+F2
:
 [COLOR=#3366FF]**gedit ~/.local/share/applications/mimeapps.list**[/COLOR]

[COLOR=#3366ff][B][COLOR=Black]This should pop up in the new terminal window that opens or similar to this[/COLOR]
[/B][/COLOR]
 [CENTER][[IMG]http://ubuntugenius.files.wordpress.com/2010/12/launchers-fix-1.png?w=500&h=68[/IMG]]("http://ubuntugenius.files.wordpress.com/2010/12/launchers-fix-1.png")[/CENTER]
 



When the file opens, look for the line starting with [COLOR=#ff0000]**inode/directory=**[/COLOR] and you should see the offending app listed at the beginning, ahead of [COLOR=#800000]**Nautilus**[/COLOR]. All you have to do is either remove it or put it on the end of the line, making sure that [COLOR=#ff0000]**nautilus-folder-handler.desktop**[/COLOR] is directly after [COLOR=#ff0000]**inode/directory=**[/COLOR].




 [CENTER][IMG]http://ubuntugenius.files.wordpress.com/2010/12/launchers-fix-2.png?w=500&h=69[/IMG][/CENTER]
 

Once you save and exit the file, your location launchers should be back to normal. 



this information is courtesy of Ubuntu Genius
cheers peeps

---

