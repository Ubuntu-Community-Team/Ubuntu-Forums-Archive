---
title: "Just problems, i need help with."
date: 2009-03-28
forum: New to Ubuntu
---

### Post by Skol312000 on 2009-03-28
Ok guys, hello to everyone here and here goes nothing:

I recently ahd apavilion dv5 and now i got the dv7 with has 4gb of ram AMD Turion 64bit x2 dual core
it has  a ATI Radeon 3200 integrated graphics card and my problems are...


The same problem as on my last laptop..when i fire up a game it will freeze and become verry pixalated and cant even see anything.....

i tried ALL kinds of setting and nothing has worked for me...i figure u guys might know..

at LEAST IF U GUYS COULD HELP me when it does freezez up and i cant do anything besides control de mouse which i can see everything else i dont see.

what combination of keys can i press in order to force quit the game so i cana go back to normla desktop without reboooting the computer?


please help

---

### Post by tombom62 on 2009-03-28
are you running a windows game in wine?

It may be a problem with the game's wine support.

alt+f2 and type xkill.

---

### Post by Skol312000 on 2009-03-28
no its Alien Arena in Add/Remove...
its  made for Linux u know..
lol

i dont understand it...
in windows games work fine....



any other ideas?

---

### Post by rshnike on 2009-03-28
Do you have the closed-source Radeon drivers enabled?

---

### Post by Skol312000 on 2009-03-28
what is that?
and how do i enable it..?/

  
i dont even know what it is..lol

where do i find those settings in order to enable stuff?

---

### Post by tombom62 on 2009-03-28
> **Skol312000 said:**
> what is that?
and how do i enable it..?/

  
i dont even know what it is..lol

where do i find those settings in order to enable stuff?

try this:
system > Administration > Restricted driver managment (or something like that)
enable, and restart the comp

---

### Post by Skol312000 on 2009-03-28
ohh yah in  did that    still bad

---

### Post by talsemgeest on 2009-03-28
Also,l it is a good idea to use a descriptive thread title. Almost thread is about some ones problems ;)

---

### Post by Skol312000 on 2009-03-28
:lolflag:

---

### Post by hristostoev on 2009-03-29
Ok you need this [http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html](http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html) 
 I had the same issue and finally installed this driver and it worked.
Follow the instructions in the guide and you should be ok. 
I will see you in Open Arena

---

### Post by hyper_ch on 2009-03-29
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Skol312000 on 2009-03-29
ok,
will do...

if i can see anything...

---

### Post by Skol312000 on 2009-03-29
> **hristostoev said:**
> Ok you need this [http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html](http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html) 
 I had the same issue and finally installed this driver and it worked.
Follow the instructions in the guide and you should be ok. 
I will see you in Open Arena




i did download it and its a .run file

What do you guys suggest now?





anyone?

---

### Post by talsemgeest on 2009-03-29
> **Skol312000 said:**
> i did download it and its a .run file

What do you guys suggest now?





anyone?
.run files have to be executed. Make sure it is ticked as executable in the file properties menu, then double click it.

---

### Post by Skol312000 on 2009-03-29
ohh ok..will it say "ticked"

its just one file and thats it...with .run at the end..
i dont get it..but thanks.

---

### Post by talsemgeest on 2009-03-29
> **Skol312000 said:**
> ohh ok..will it say "ticked"

its just one file and thats it...with .run at the end..
i dont get it..but thanks.
Ok, right click the file, click "File properties" (Or something like that, Im on windows right now.) Go to the permissions tab, and down the bottom is a line saying something like "Allow executing this file as a program" with a tick box next to it. Make sure it is ticked, close the window, then try double clicking it.

---

### Post by Skol312000 on 2009-03-29
> **talsemgeest said:**
> Ok, right click the file, click "File properties" (Or something like that, Im on windows right now.) Go to the permissions tab, and down the bottom is a line saying something like "Allow executing this file as a program" with a tick box next to it. Make sure it is ticked, close the window, then try double clicking it.


Awesome im halfway there, thanks...now, after i run the file it extracts it all and shows a different folder that i clicked into and then it says that i need to run the installer as a super user.  i am the only user...what should i do now..

and thanks for the help


figured it out with the help of u guys, thaks

---

### Post by mikechant on 2009-03-30
> now, after i run the file it extracts it all and shows a different folder that i clicked into and then it says that i need to run the installer as a super user.


Open a terminal (e.g. using ALT+F2)
Then use the 'cd' command to change directory to where the installer is. E.g. if it was in directory 'installprog' in your home directory:
cd installprog
  
Then run the installer as super user:

sudo ./installername

replacing 'installername' with the actual name of the installer file.

Note that 'sudo' will prompt for your normal password, and when you type it there will be no feedback (i.e. no * characters) - this is normal, just go ahead and type and press enter.

---

