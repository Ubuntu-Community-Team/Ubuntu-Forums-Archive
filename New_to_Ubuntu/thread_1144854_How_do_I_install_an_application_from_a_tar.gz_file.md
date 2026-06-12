---
title: "How do I install an application from a tar.gz file?"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by bwallum on 2009-05-01
Hi

I'm trying to install an alpha version of kompozer that comes within a downloaded tar.gz file (kompozer-0.8a2-gcc4-i686.tar.gz is the full file name).

When I double click on the file (currently on my Desktop) it invites me to extract through archive manager. I then have a folder called **kompozer-0.8a2** on my Desktop.

Inside the folder I can see a shell script called kompozer.

If I open a terminal, cd to Desktop/kompozer-0.8a2 and then try sudo apt-get install kompozer I just get the repos version (0.7.10 - which is unusable, hence my desire to try the 0.8 alpha2..)

Can somebody nudge me in the right direction please? How do I install kompozer 0.8a2?

---

### Post by zvacet on 2009-05-01
In that folder look for **install file** and there should be instructions for installing.

---

### Post by Malta paul on 2009-05-01
It is sometimes not so easy to install a tar.gz file.
Best to install a .deb package.
But you can find kompozer in Systen>Administration>Synaptic Package manager.
Just do a Search for it.
Good luck:)

---

### Post by nothingspecial on 2009-05-01
Is there a README file in the kompozer-0.8a2 folder on your desktop?

If you don`t understand it post the contents here.


EDIT**** Here are the instructions 
   
 * unzip it somewhere (e.g. in your home directory)
 * rename your ~/.kompozer profile (e.g. ~/.kompozer.bak)
 * start the kompozer script: ~/kompozer/kompozer

                                                       *****EDIT

---

### Post by Bradtek on 2009-05-01
No need to "install it

just copy or move the folder to where you want it to run from and make a launcher.
or make a link to it in /usr/bin  and point the launcher there

edit:
eg. I moved the folder to /usr/share
so now I have /usr/share/kompozer-0.8a2
make a launcher command = /usr/share/kompozer-0.8a2/kompozer

---

### Post by bwallum on 2009-05-01
Thanks everybody!

I chose Bradtek's route because it allows me to try out the alpha without 'installing'. No doubt the repos will catch up when the 0.8 version is released. I can then use the repos and delete the 0.8a2 version.

I needed to be root to move the folder kompozer-0.8a2 to /usr/share. I used ```
sudo nautilus
``` to give me a good view of what I was doing. I'm sure the move could be done quicker with a snappy command but 'seeing' is a good thing for me.

The launcher was added by right clicking in a space on the icons panel, choosing 'Add to Panel' then 'Custom Application Launcher'. Bradtek's command line worked a treat.

Thanks again!
Bob

---

