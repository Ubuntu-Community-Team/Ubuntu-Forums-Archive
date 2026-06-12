---
title: "[SOLVED] Installing Songbird problems"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Archie69 on 2009-01-03
Hello,
 t
My problem is just that installing songbird.  I'm having issues yet again.
I have downloaded the latest .deb from the songbird website ([http://getsongbird.com/](http://getsongbird.com/)) 

I then extract it in my user file as ".songbird"
Next I open the edit menus option and go to sound and video
Then I add "New Item" pick the file .songbird then pick the songbird.png file

I then give it a name in the name section and it automatically finds the icon for songbird.  I close the "create launcher screen" and go to applications to open songbird but it wont allow me.  Says permission denied.

I don't get where I went wrong.  Can anyone help?

---

### Post by ibuclaw on 2009-01-03
From what I can see, the songbird site does not provide the songbird deb installer package.

However, a contributed build can be downloaded from here:
[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)
Download the one that matches your OS and arch, and double-click it to install.
The panel icon should be installed along with it so you don't have to set it up yourself.


Alternatively, another source of the software is also available at Fabien Tassin's ppa:
[https://launchpad.net/~fta/+archive](https://launchpad.net/~fta/+archive)
Select your OS and add the deb line to your sources list, and install through synaptic.

Regards
Iain

---

### Post by homemadejam on 2009-01-03
There is also a good step-by-step installation guide here: [http://jamsubuntu.blogspot.com/2008/12/goodbye-rhythmbox-welcome-songbird.html](http://jamsubuntu.blogspot.com/2008/12/goodbye-rhythmbox-welcome-songbird.html)

It gives details on how to add Songbird into the Menu like you are trying to do.

Jam

---

### Post by Archie69 on 2009-01-04
So I got songbird installed but now its not playing any music.
Something about songbird needing GStreamer plugins.  I tried to run this in terminal but it did nothing:

sudo apt-get install  libgstreamer0.10-0 gstreamer0.10-x gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-pulseaudio libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev

doesn't look like it worked cause my music still isn't playing.  I got that command from here: [http://wiki.songbirdnest.com/Developer/Articles/Media_Cores/GStreamer_Setup](http://wiki.songbirdnest.com/Developer/Articles/Media_Cores/GStreamer_Setup)

Can anyone help?

---

### Post by Archie69 on 2009-01-04
This is the message that i see in terminal:

marco@marco-laptop:~$ sudo apt-get install  libgstreamer0.10-0 gstreamer0.10-x gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-pulseaudio libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgstreamer0.10-0 is already the newest version.
gstreamer0.10-x is already the newest version.
gstreamer0.10-gnomevfs is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-pulseaudio is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libgstreamer-plugins-base0.10-dev: Depends: libglib2.0-dev but it is not going to be installed
                                     Depends: libxml2-dev but it is not going to be installed
  libgstreamer0.10-dev: Depends: libglib2.0-dev but it is not going to be installed
                        Depends: libgstreamer0.10-0 (= 0.10.18-4ubuntu1) but 0.10.18-4ubuntu2 is to be installed
                        Depends: libxml2-dev but it is not going to be installed
E: Broken packages

---

### Post by birddog165 on 2009-01-25
> **homemadejam said:**
> There is also a good step-by-step installation guide here: [http://jamsubuntu.blogspot.com/2008/12/goodbye-rhythmbox-welcome-songbird.html](http://jamsubuntu.blogspot.com/2008/12/goodbye-rhythmbox-welcome-songbird.html)

It gives details on how to add Songbird into the Menu like you are trying to do.

Jam

Thank you. This works perfect!

---

