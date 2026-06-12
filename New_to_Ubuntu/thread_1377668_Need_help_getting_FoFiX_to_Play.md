---
title: "Need help getting FoFiX to Play"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Zyrtec on 2010-01-10
Hi WWGHA :)

---

### Post by ibninja on 2010-01-11
the instructions on their site are:
open a terminal and run:
sudo apt-get install python-pygame python-opengl python-numpy python-imaging python-ogg python-pyvorbis python-pysqlite2 python-xml python2.5-dev gstreamer-plugin-ffmpeg python-gst0.10 python-numeric
sudo mkdir FoFiX
cd FoFiX
svn checkout [http://fofix.googlecode.com/svn/MFH-Mod/tags/Release_3.120_final](http://fofix.googlecode.com/svn/MFH-Mod/tags/Release_3.120_final) fofix-3.120
cd fofix-3.120/src/
sudo chmod +x FoFiX.py
./FoFiX.py
When I tried this, I got a couple of errors: on the first command, it complained about some packages, so I deleted those packages from the command, then it installed the rest.
When I tried the svn command, it complained about subversion not being installed, so I ran sudo apt-get install subversion as it said, then reran the svn command.
Everything else worked, the game opened.
To open it again later, open a terminal, and run: 
cd FoFix/fofix-3.120/src/
./FoFiX.py

---

