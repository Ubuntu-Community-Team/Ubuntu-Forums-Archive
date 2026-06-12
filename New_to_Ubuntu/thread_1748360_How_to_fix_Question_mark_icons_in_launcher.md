---
title: "How to fix Question mark icons in launcher"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by mebigfatguy on 2011-05-03
I have eclipse in the unity launch toolbar with a question mark icon. How do i apply a real icon? 

I went to the eclipse executable, and right-clicked properties, and chose an icon, and it shows in the nautilus view, but the unity launcher still shows a question mark?

---

### Post by peely on 2011-06-01
There are ways of doing this in terminal, but the easiest is to right click on your desktop and choose "Create Launcher...".


Leave the "Type" as "Application" and click "Browse" next to "Command". Navigate to your Eclipse installation and binary e.g. /opt/eclipse/eclipse.

Now click the springy icon and change the icon to the eclipse.xpm file in the same folder as your binary.

Click OK then move the icon somewhere out of the way e.g. ~/.local/applications.

Once you have done that, just drag that icon over to your launcher.


Good luck,



Neil.

---

