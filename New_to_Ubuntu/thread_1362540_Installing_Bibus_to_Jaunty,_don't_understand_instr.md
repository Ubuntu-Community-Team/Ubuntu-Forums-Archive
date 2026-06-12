---
title: "Installing Bibus to Jaunty, don't understand instructions"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by Eldera on 2009-12-23
I have used Linux for less than a year and because I have so much to learn want to wait for Lucid before changing my OS. 

Since Bibus is in synaptic in Karmic but not in Jaunty I am trying to install it to Jaunty 64 bit using this:

```
Bibus is available in the official Ubuntu repository starting with release 9.10 (Karmic Koala). If you run an older release, follow these instructions. This paragraph is a brief translation of a french tutorial written by oswald-p [1]

    * Ubuntu must be breezy release or later
    * Add the following lines to your /etc/apt/sources.list 

## Bibus
deb http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./
deb-src http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./

    * Download the public key with the following command: 

wget -q http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/pmartino.gpgkey -O- | sudo apt-key add -

    * sudo apt-get update
    * sudo apt-get install bibus libsqliteodbc python-pysqlite2 python-wxgtk2.6 python-uno
    * if you run Gutsy, there is a problem with "LD_LIBRARY_PATH", to solve it 

        - gedit bibus 
        - copy the following lines in the editor 

#! /bin/sh
export LD_LIBRARY_PATH="/usr/lib/openoffice/program"
exec /usr/share/bibus/bibus.py

        - sudo rm /usr/bin/bibus 
        - sudo cp bibus /usr/bin 
        - sudo chmod +x /usr/bin/bibus 


    * make bibus and openoffice communicate (not required since Dapper): 

        - sudo ln -s /usr/lib/openoffice2 /usr/lib/openoffice 
        - sudo ln -s /usr/lib/openoffice2/share /usr/lib/openoffice2/user 


    * optional:
          o apt-get install openoffice.org2
          o apt-get install mysql-server mysql-common mysql-client python-mysqldb
```

[http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu](http://bibus-biblio.sourceforge.net/wiki/index.php/Installation#Ubuntu)

I do not understand how to do the first instruction >  Add the following lines to your /etc/apt/sources.list

The screen shot shows what I have tried. What should I be doing?

Googling the forum just brought me to a link to the same tutorial.

Thank you for your help in advance.

My system: S76 panp4n, core 2 duo T5800, 3GB RAM, HD 320GB 5400 RPM, nVidia GeForce 9300M GS; Jaunty 32 bit/Hardy 32 bit/Jaunty 64 bit tri boot

---

### Post by qduck on 2009-12-23
/etc/apt/sources.list is a text file. To edit it, you need to type
```

sudo gedit /etc/apt/sources.list

```
Just add the lines to the end of the file.

---

### Post by Eldera on 2009-12-23
Thank You qduck!

---

