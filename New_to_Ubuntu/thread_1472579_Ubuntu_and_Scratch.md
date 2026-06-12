---
title: "Ubuntu and Scratch"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by hpesson on 2010-05-04
Hi all, 
I recently upgraded a computer running Ubuntu 8.1 to Ubuntu 9.1.  It is my understanding that this upgrade, would allow the Sounds blocks in Scratch to work.  It didn't.  Someone suggested that I then reinstall Scratch.  So, I downloaded the package and tried to install, but I keep getting an error message that says 'Failed to install package, Errors were encountered wile processing'.  
Any suggestions? [IMG]http://mediamashup.ning.com/proflies/blogs/teen-tech-camp-and-computer?xg_source=activity[/IMG]

---

### Post by AXBX7C on 2010-05-04
I assume you did remove the package before trying to re-install it?

---

### Post by hpesson on 2010-05-05
Actually, I am a complete novice when it comes to using Ubuntu.  I looked in the Add/Remove Programs Utility...I think that in 9.1 it is called Software Manager.  Anyway, I couldn't find the Scratch file listed anywhere in the Installed Programs area.  So, I couldn't figure out how to delete it.
Any ideas how to find and delete the file?

---

### Post by AXBX7C on 2010-05-05
Open the terminal and type in "sudo apt-get autoremove scratch". You'll need to provide your root password. This should remove scratch and all dependencies... Then try to re-install...

Btw: Scratch is listed as an option to install in my download manager (10.04)

---

