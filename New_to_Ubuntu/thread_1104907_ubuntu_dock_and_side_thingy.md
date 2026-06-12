---
title: "ubuntu dock and side thingy?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Rockanium on 2009-03-24
where can i download a nice dock and a cool side thingy, when i mean side thingy i mean:

[http://gnome-look.org/CONTENT/content-pre1/74813-1.jpg](http://gnome-look.org/CONTENT/content-pre1/74813-1.jpg)
(**on the right of the screen it has the clock and all that information**)

---

### Post by MaindotC on 2009-03-24
When you say "dock" i believe you're referring to a task bar or similar application.  The common dock is called AWN or Avant Window Navigator.  The thing on the right is called conky, and that can be installed from the repositories.  There's a thread called "post your conky config file" because conky can be configured so many unique ways.

Of course if you google "AWN" or "conky" you will find directions on how to install and configure these.

---

### Post by mcduck on 2009-03-24
From Ubuntu's repositories, of course. ;)

Popular dock applications would be Avant Window Navigator, Cairo-Dock ad Kiba Dock, for example. Thre are many other available as well, and even Gnomes own panels can be configured into a kind of dock.

The program displaying text information on the desktop in that screenshot is Conky.

---

### Post by stumbleUpon on 2009-03-24
There are lots of docks available avant, cairo-dock .. etc ([http://ubuntu-snippets.blogspot.com/2008/05/ubuntu-dock-collection.html](http://ubuntu-snippets.blogspot.com/2008/05/ubuntu-dock-collection.html)). 

My favorite is cairo-dock ([http://www.cairo-dock.org/ww_page.php?p=Accueil&lang=en](http://www.cairo-dock.org/ww_page.php?p=Accueil&lang=en)).

The 'side thing' is probably conky ([http://conky.sourceforge.net/](http://conky.sourceforge.net/)). 
Install it using "sudo aptitude install conky"

Look here for lots of conkyrc files 

[http://ubuntuforums.org/showthread.php?p=6931715](http://ubuntuforums.org/showthread.php?p=6931715)

---

### Post by Rockanium on 2009-03-24
okay thanks, but how do i go to ubuntus repositories

sorry for my lack of knowledge about ubuntu, I have only had it for 2 days :)

EDIT: Is the Ubuntu repositories the synaptic package manager?

---

### Post by blackened on 2009-03-24
There is also the Docky style in Gnome-Do, if you're into that sort of thing.

Software repositories can be accessed through the panel menus: System -> Administration -> Synaptic Package Manager.

---

### Post by stumbleUpon on 2009-03-24
jus open a terminal and type

sudo aptitude install conky

give your password. After the installation, type conky to start it.


For cairo-dock, there are complete instructions in the wiki link i gave above ([http://www.cairo-dock.org/ww_page.php?p=Accueil&lang=en](http://www.cairo-dock.org/ww_page.php?p=Accueil&lang=en)).

---

### Post by MaindotC on 2009-03-24
You can use Synaptic as well - either utility will work.  Just type in the search feature "conky" and "awn".

---

### Post by Rockanium on 2009-03-24
open a terminal? where can i open one?

---

### Post by jespdj on 2009-03-24
Applications > Accessories > Terminal

---

### Post by Rockanium on 2009-03-24
how do i add .conkyrc files to conky?

---

### Post by stumbleUpon on 2009-03-24
you just get the .conkyrc file you like and put it in your home directory.

stop all conky processes and then start it again

'killall conky && conky'

---

### Post by MaindotC on 2009-03-24
You place them in your home directory.  There should be a default conkyrc file there now.

---

### Post by Rockanium on 2009-03-24
wheres the home directory?

---

### Post by VCoolio on 2009-03-24
places > home folder. In nautilus (your file manager) it should be the default folder it opens in. Anyway, it is the folder /home/[yourusername]. The conkyrc file may be hidden, than it is .conkyrc (all files starting with a dot are hidden files).

---

### Post by stumbleUpon on 2009-03-24
In the top bar, you should see a menu 'Places'. Click on that. The first entry is called 'Home folder'. Click on that. That is your home directory

---

### Post by Rockanium on 2009-03-24
okay well i make a .conkyrc file in there with the test i want in it, but it doesnt work




**_EDIT: Never mind i got it, thankyou!!_**

---

### Post by Rockanium on 2009-03-24
hmm

---

### Post by Roadbloc on 2009-03-24
Im sure they will be one available from Add/Remove...

---

