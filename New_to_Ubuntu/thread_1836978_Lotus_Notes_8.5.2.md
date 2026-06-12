---
title: "Lotus Notes 8.5.2"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by des.mcdermid on 2011-09-01
I am a very new convert to Ubuntu and I am trying to load Lotus Notes - my only obstacle to waving goodbye to windoze. I have read lots of posts about this but most of them speak geek which is way beyond a newbie like me. So far I have managed to download the 413 Meg file from IBM, I have tried to convert it to a deb file using alien but that is as far as I got. It doesn't want to install from there on. Is there someone out there that can explain step by step in non-geek how I can carry on from there. My /home/Downloads has a file CZJ1MEN.tar and a folder CZJ1MEN which appeared after running alien. It also contains files which I downloaded because some of the posts called for them - they are notes_libs_karmic.tgz and libgdk-pixbuf2.0-0_2.22.0-Oubuntu_1.

Help would be greatly appreciated - I would love to say goodbye to windows...

---

### Post by des.mcdermid on 2011-09-03
I finally figured it out and this what I did:

Sign on in the Ubuntu Classic desktop. Before you even start, do all that this guy suggests with regard to downloading the lib files [http://www.browniesblog.com/A55CBC/blog.nsf/dx/26102009193509MBRC42.htm?opendocument&comments#anc1](http://www.browniesblog.com/A55CBC/blog.nsf/dx/26102009193509MBRC42.htm?opendocument&comments#anc1) Download file called CZJ1MEN.tar from IBM's web page - it is a big file 413M so it takes quite a while. Unpack it with tar -xvf. This will cause files to appear with a .rpm extension. Install a program called alien. You will find it in the Ubuntu software centre. Make sure that you are in the folder where the rpm folders were unpacked and then run sudo alien -dcvi ibm_lotus_notes-8.5.2.rpm. This step takes about half an hour to do so while it is busy, locate and download a file called notes_libs_karmic.tgz from [http://linux-aha.de/wordpress/wp-content/uploads/2009/10/notes_libs_karmic.tgz](http://linux-aha.de/wordpress/wp-content/uploads/2009/10/notes_libs_karmic.tgz). Wait for lotus notes to complete the install then unpack notes_libs_karmic.tgz open a terminal and type gksu nautilus. A nautilus screen appears and here you must be careful because this nautilus can cause grievious bodily harm. Go to the folder where the four libs files were unpacked. Select all four lib files - right click on them - go to properties - click on permissions tab and change group and user to read/write. Then copy these file in /opt/ibm/lotus/notes. Then close down everything click on applications-office and you should see two lotus notes icons - Lotus Notes Application Support and Lotus Notes the program launcher. Hold thumbs and click on the launcher. It is very slow to get going the first time so be patient and then set it up as per normal.

---

