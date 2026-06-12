---
title: "[SOLVED] ndiswrapper question"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by cptrohn on 2009-01-10
Ok I've come across a process that seems to be the solution to my wireless problem here:
[http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html](http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html)

everything was going along good until I get to the step that says: "download 32bit driver Extract the archive and execute the following command from the folder where you extracted the contents"

So being completely new to Ubuntu, I have no idea exactly how to extract the archive...don't know where the archive is exactly what folder to put it into or how to execute a command from said folder that doesn't exist yet.



LOL  What a day!!

---

### Post by Hangwire on 2009-01-10
Download this, as its said there.
[http://www.mediafire.com/download.php?njmdytwnqjz](http://www.mediafire.com/download.php?njmdytwnqjz)

It will open up a window with a big nice Extract button, extract it on the desktop or w/e. Im going to use the desktop in my example.
Lets say you extract the contents in a folder called Driver
Do that, then from the terminal
cd /home/your_username/Desktop/Driver
Hit enter.
Then, again in the terminal type 
```
sudo ndiswraper -i net5211.inf
```
Follow the rest of the guide.

PS. To do this 

>  Now add following line to the file /etc/modprobe.d/ndiswrapper at the end.

In the terminal type

```
sudo gedit /etc/modprobe.d/ndiswrapper
```

and just add the line shown there to the end of the text file. 

CTRL+S to save it for short, and you're done.

---

### Post by cptrohn on 2009-01-11
Oh this GREAT the wireless is now up and running!!!  Even though the little HP wireless assistant button doesn't work anymore...(minor really as long as the wireless connects...
 
if you have the Atheros AR242x internal wireless in a laptop the link I posted works great... if I wasn't so new to Ubuntu I could have got it working much, much fast...


MANY thanks to Hangwire for walking me through the steps... it would have taken much longer to figure it out myself.. many thanks to the rest of the community here for all the help as well... it was all greatly appreciated!

---

### Post by Lupy on 2009-01-11
Do you know if this would work with an Atheros A55007? :confused:

---

