---
title: "googleearth-package 0.5.4"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by GrenadierExercise on 2009-02-18
I have installed and running Ubuntu 8.10 64bit version on my Compaq Presario AMD 64 Athlon and the system is running all of the installed applications satisfactorily.
I would like to install Google Earth and have downloaded in the synaptic manager "googleearth-package 0.5.4" to manage the installation in good system order and hopefully painlessly.  Being new to the system I am unsure how to proceed with the use of this package.  Could someone advise me on the correct use of this package?

---

### Post by fooman on 2009-02-18
i do not know what the googleearth-package 0.5.4 is...but if you just want to run googleearth,  then all you should need to install is the package "googleearth-4.3" from synaptic.  if i were you,  i would uninstall that 0.5.4 package and just get the 4.3.

i am using ubuntu 8.10 64bit and was running the 4.3 package from synaptic up until a week or 2 ago,  when i switched over to the new 5.0 (beta) package from google.  it is not in synaptic,  but is available from here:

[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

please be aware that it is a beta,  but runs very well for me.  in fact it seems to load up and run much smoother for me then the versions from the repos.  to install it,  right click on the downloaded .bin file and choose "properties" from the drop-down menu.  in the box that pops up, choose "permissions" and put a check next to "allow executing file as a program".  then close that box and double click the .bin file to proceed with the installation.

after it installs,  find it in applications > internet > google earth

good luck,  i hope that helps.

---

### Post by GrenadierExercise on 2009-02-20
Thanks for your very helpful suggestion which I think I will follow.
Since my original post I have searched around the topic in ubuntu and found what is for me a very confused situation regarding googleearth packages which seems to be best sumarised here - [https://launchpad.net/ubuntu/+source/googleearth-package](https://launchpad.net/ubuntu/+source/googleearth-package)
It seems that "googleeart-package 0.5.4" may be bugged in its present existance and best avoided by learners like myself.
Other users experience with this particular package would be welcome.

---

### Post by GrenadierExercise on 2009-02-21
As suggested by FOOMAN i downloaded the google earth 5 beta version but was unable to install.  On double clicking on the .bin file, after enabling execution, I received the message "Could not display ......GoogleEarthLinux.bin"  "There is no application installed for this file type".
What is needed to open/run this .bin file?

Following my failure to install GoogleEarth5beta I have successfully installed version 4.3 using Synaptic Package Manager (after enabling medibuntu rep and key).  The program appears to load and run smoothly.
Use of the Synaptic Package Manager would seem to be the advisable method at least for beginners like myself.
Accordingly I shall mark question as solved.

---

### Post by lucamanu on 2009-02-22
Grenadier, you must have admin empowerment (sudo) to install a package. You can alternatively:
- open a terminal and type
# sudo ./GoogleEarthLinux.bin

or open the Nautilus in sudo mode and double click on the file name.

Hope this helps

---

### Post by GrenadierExercise on 2009-02-22
> **lucamanu said:**
> Grenadier, you must have admin empowerment (sudo) to install a package. You can alternatively:
- open a terminal and type
# sudo ./GoogleEarthLinux.bin

or open the Nautilus in sudo mode and double click on the file name.

Hope this helps
Many thanks for your good advice. I am just getting used to the very necessary security features of linux.
I have managed to install Google Earth 4.3 using Synaptic Package Manager which facility is great for me until I really get to grips with command line installations.
Again many thanks.

---

