---
title: "trash won't empty - error"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Smiley Coyote on 2009-03-19
If I right-click on my trash and empty it it goes through the motions as if it is done but the trash, when going to it, is still quite full.  If I open my trash and individually permanently delete files, I get an error message.  Being someone that does a lot of data storage and a lot of file sharing, this poses huge problems for me.  Were I to continue at my usual rate, my disc would be full within a week.

By the way, I am an absolute, absolute beginner and thanks in advance for any help.

---

### Post by supersonicdarky on 2009-03-19
Mind posting the actual error? We aren't phychic.

---

### Post by gandaran on 2009-03-19
trash is located in /home/'user'/.local/Trash, check it out if you can **delete** not empty the files, if you have a permission issue open terminal and type **sudo nautilus** and navigate to this folder with the root window, enable the delete option in the root nautilus window in preferences.

---

### Post by Smiley Coyote on 2009-03-19
> **supersonicdarky said:**
> Mind posting the actual error? We aren't phychic.

Sure: "error deleting trash

       there was an error deleting benjaminfranklin.mp3"

Obviously, had I thought this remotely revealing I would have posted it.

---

### Post by Smiley Coyote on 2009-03-19
> **gandaran said:**
> trash is located in /home/'user'/.local/Trash, check it out if you can **delete** not empty the files, if you have a permission issue open terminal and type **sudo nautilus** and navigate to this folder with the root window, enable the delete option in the root nautilus window in preferences.

Actually, I believe that I have solved it.  I recently copied a lot of backed up files while I switched from Windows and all of them showed as "read only" until I changed those properties.  Apparently, when files are in the trash such properties do not show.  When I restore them, they show as "read only" and I can then change them, delete them, and subsequently empty them from the trash.

I have had a ton of files that I have been editing in this way but some I did not get to, including those in my trash today.

---

