---
title: "request for help compiling Audacity"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Old Jimma on 2009-12-16
Ubuntu Community:

Audacity for linux does not have some of the features that the Win and Mac versions have... like change tempo without changing pitch.

In another discussion ( [http://ubuntuforums.org/showthread.php?t=1349015]("http://ubuntuforums.org/showthread.php?t=1349015") ) it was suggested that I compile the current version of Audacity from scratch. And I need help with this.

So, I have started by downloading Audacity from [http://audacity.sourceforge.net/download/source#recdown]("http://audacity.sourceforge.net/download/source#recdown")

The documentation on that page says:

> The wxWidgets library is required. Audacity 1.2 needs wxGTK 2.4, compiled without the unicode options. The next stable version of Audacity will support newer wxWidgets and GTK libraries. The wxWidgets library is found at: [http://wxwidgets.org/downloads](http://wxwidgets.org/downloads)

So, I went to [http://wxwidgets.org/downloads]("http://wxwidgets.org/downloads") and clicked on wxGTK. It began the download for wxGTK-2.8.10 ... NOT the wxGTK 2.4 that was indicated as being required... I'm not sure this was a problem.

After unpacking the tar.gz file from that download, there is a install-gtk.txt file that recommends the following sequence of commands:

> If you compile wxWidgets on Linux for the first time and don't like to read install instructions just do (in the base dir):

> mkdir buildgtk
> cd buildgtk
> ../configure --with-gtk
> make
> su <type root password>
> make install
> ldconfig

It is at this point where things really start going wrong for me. For example ../configure --with-gtk does not work, but ./configure --with-gtk does... but gives errors.

Can anyone help me through this entire process?

Thanks!
Phil Smith
Duluth, GA

---

### Post by Tyke91 on 2009-12-16
../ means parent directory
./ means current directory

did you skip the step ```

cd buildgtk

```?

EDIT: also, libwxgtk is available through synaptic. you shouldn't need to build it from source in order to build audacity.

EDIT#2: it's also worth mentioning that you should install build essential and the ubuntu linux kernel headers (if that's not in build essential) in order to build anything on your system at all...

---

### Post by Old Jimma on 2009-12-17
Thanks for your reply Tyke91:

I changed directories, and believe that is why ./configure worked, isn't it?

I checked synaptic and found that libwxgt is installed. Should I remove the current version of Audacity?

I"m not sure what you are suggesting by

> EDIT#2: it's also worth mentioning that you should install build essential and the ubuntu linux kernel headers (if that's not in build essential) in order to build anything on your system at all...

Are you suggesting that before I do anything I need to open another command window and type: "install build essential"  ??

I don't know wheat you mean by "... and the ubuntu linux kernel headers (if that is not in build essential)" I'll be grateful for your explanation.

Thanks,
Phil Smith,
Diluth, GA

---

