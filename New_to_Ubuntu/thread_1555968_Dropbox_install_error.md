---
title: "Dropbox install error"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by pointyblue on 2010-08-18
This question has most likely been asked before but I havent been able to locate it in the archives, so here goes:

I'm running U10.04. Have dovnloaded the .deb-package from the Dropbox website and when I run it, it adds the Dropbox repo to my software sources + opens a dialogue box to download the Dropbox daemon. Then it asks me to restart Nautilus, which I do, and the nothing happens.

I've tried restarting the computer: It still doesn't start. Tried to reinstall the daemon: It still doesn't start.

I've looked in the list of start-up programs: There's no entry for Dropbox.

Any idea how to fix this??

:-k

---

### Post by Ampi on 2010-08-18
Hmm, I´m not sure if I can help, I installed dropbox more than once on a Ubuntu machine with no problems. 

Maybe if you add dropbox to your synaptic package manager list and then download from there. Maybe that helps..

Another thing, you didn´t do anything from the terminal right? 
Some users run the dropbox start command from the terminal and accidently put sudo in front of it. That gives problems as in dropbox daemon to be installed with no luck..

---

### Post by john newbuntu on 2010-08-19
Like Ampi, I have downloaded it too a few times without problems.  If you have not already done this, go to Applications->Internet and see if you can find Dropbox.  If you click on it, it should open up and ask for your authentication details.  You should then see the icon in your Notification area (the same place which shows your internet connection icon).
You could open up a terminal (Applications->Accessories->Terminal) and run the command:
dropbox

---

