---
title: "Uninstalling Google Earth"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by guv999 on 2009-03-28
Hi I am attempting to uninstall google earth (I installed it direct from the web site and not through symantic).   
I have seen several threads already on this, and can see people struggle with.  
I use the Get Help With Ubuntu and followed the instructions using:
   

So far I have carried out this command:
dave@dave-desktop:~$ sudo apt-get remove google-earth

The response was that Google Earth is not installed.  I am really confused and would appreciate any help available

---

### Post by gandaran on 2009-03-28
> sudo apt-get remove google-earth
only works if you install google earth through apt-get/synaptic (medibuntu repository)
installing google earth from .bin file you have to find the uninstall file in google earth install directory (I think in /opt), open terminal and cd to the folder where the uninstall file is, type **sudo ./uninstall** and hit enter, done.

---

### Post by guv999 on 2009-03-28
Thanks for your help.
Just want to clarify a few things.
I open the terminal as notmal via applications-accessories-terminal
what should I actually type? - I am still a bit uncertain about the command line in general

---

### Post by gandaran on 2009-03-28
> **guv999 said:**
> Thanks for your help.
Just want to clarify a few things.
I open the terminal as notmal via applications-accessories-terminal
what should I actually type? - I am still a bit uncertain about the command line in general
first, have you found the uninstall file?
well, the command line is a bit complicated for some linux newbies so I would recommend to install **nautillus-open-terminal** package, reboot after installing this package, then go to the folder where the uninstall file is located, right click the folder choose from the drop down menu open in terminal and just type **sudo ./uninstall** in the terminal, easy! it's very easy once you understand you have to cd the terminal or be on the path of the folder that contains the uninstall file.

---

### Post by mvalviar on 2009-03-28
To uninstall the google earth from the website open a terminal. Then type ```
cd google-earth
``` then press enter. Then type ```
./uninstall
``` then press enter.

---

### Post by gandaran on 2009-03-28
> **mvalviar said:**
> To uninstall the google earth from the website open a terminal. Then type ```
cd google-earth
``` then press enter. Then type ```
./uninstall
``` then press enter.
have you tried your own recipe?
how can you cd to *cd google-earth*
how can you run ./uninstall without sudo?, you need root permission for installing or removing anything from the file system!

---

### Post by mvalviar on 2009-03-28
I am assuming he ran the *.bin file from the google earth site without sudo. If he did so googleearth in his home directory. 
[IMG]http://i225.photobucket.com/albums/dd230/mvalviar/Screenshot-mvalviarubuntu-google-ea.png[/IMG]

---

### Post by gandaran on 2009-03-28
> **mvalviar said:**
> I am assuming he ran the *.bin file from the google earth site without sudo. If he did so googleearth in his home directory. 
[IMG]http://i225.photobucket.com/albums/dd230/mvalviar/Screenshot-mvalviarubuntu-google-ea.png[/IMG]
quite correct then, I was assuming he installed it on root file system!

---

### Post by guv999 on 2009-03-28
Thanks very much - I am all sorted now, and learnt that bit more into the process.  Thanks for taking the time to help:P

---

