---
title: "Installing Second Life"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by FlamingCowboy on 2009-02-01
Hi,


Telstra BigPond provide Second Life to their customers free-of-charge (ie. the data used doesn't count towards one's monthly allowance), in part provided it is downloaded from their servers at:

[http://files.bigpond.com/library/?go=cat&id=2435](http://files.bigpond.com/library/?go=cat&id=2435)


Unfortunately, Second Life is in .tar.bz2 format, which as a noob, I have no idea how to install...


So, how to install Second Life from the link above?


Thanks!

---

### Post by jnorth on 2009-02-01
Unfortunately, I am not on that ISP and the page won't let me download because of that.  BUT - you can try to extract the file and list the contents for us and I'm sure we can work it out.
You can either use the archive manager GUI (right-click and hit extract on the downloaded file), or use the command line to extract the tar.bz2```
tar -jxvf filename.tar.bz2
```
List the contents of the directory for us, or if you see a help file or a readme inside, take a look at it.
HTH get you started on the right track.

---

### Post by taurus on 2009-02-01
Assuming that you have saved it to your desktop, open a terminal and run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvjf SecondLife-i686-1.21.6.99587.tar.bz2
```
At this point, it will unpack into a new directory.  Now, you need to change to that new directory and see if there is a readme or install.  You probably just run the game from there, I would assume.

Otherwise, post the output of this command from a terminal after you ran the first two commands from above.

```
ls -la
```

---

### Post by jnorth on 2009-02-01
Update to that - I found I can download from secondlife's site, and you don't even install the client, this will be simple (knock on wood).

So - here's what I did:
Download the install file```
wget http://download.cloud.secondlife.com/SecondLife-i686-1.21.6.99587.tar.bz2
```Extract and go to that folder```
tar -jxvf SecondLife-i686-1.21.6.99587.tar.bz2
cd SecondLife-i686-1.21.6.99587/
```Make sure you read the readme for known issues, there are a few```
less README-linux.txt
```And now run the program!```
./secondlife
```

If you like it and want to keep it, you could move things around to get it out of your home directory and in a more standard location, plus add links to start it from your menu.  Let's make sure you can run it first though.

---

### Post by jnorth on 2009-02-01
> **taurus said:**
> Assuming that you have saved it to your desktop, open a terminal and run
Applications -> Accessories -> Terminal
I always forget to add the GUI steps to get to this stuff when posting in the beginner forum, good reminder :)

---

### Post by FlamingCowboy on 2009-02-01
Hey, I have done all you said above and I now have a Second Life directory in my Home Folder, but what icon do I click to run it?

I still need to get it running, and create a short-cut in the menu...

---

### Post by taurus on 2009-02-01
You have to run it from a terminal.

Applications -> Accessories -> Terminal
```
cd ~/Desktop/SecondLife-i686-1.21.6.99587
./secondlife
```
Or you can create a shortcut/launcher on the panel.  Place a cursor on the top panel and click the right button.  Then click Add to Panel -> Custom Applications Launcher -> Add.  

In the Name:, type in **Second Life**.  
In the Command:, type in **~/Desktop/SecondLife-i686-1.21.6.99587/secondlife**.
You can leave the Comment: field blank if you wish.

Click OK and click on the icon to see if it starts.

---

### Post by FlamingCowboy on 2009-02-01
Hey, if I just cut-and-paste the Second Life directory into the same directory as all my other programs (not sure what that is, 'cause I'm using that pathetic-excuse-for-an-operating-system-that-is-Vista at the moment...) and then follow your above instructions, will it still create a short-cut?

---

### Post by Tony Flury on 2009-02-01
You can extract the file to anywhere (i extracted it to a sub directory within Home - so i don't get a folder on my dkestop).


You might be ok moving the folder once you have extracted it, but why not extract it to the right place in the first place.

---

### Post by FlamingCowboy on 2009-02-03
> **taurus said:**
> Or you can create a shortcut/launcher on the panel.  Place a cursor on the top panel and click the right button.  Then click Add to Panel -> Custom Applications Launcher -> Add.  

In the Name:, type in **Second Life**.  
In the Command:, type in **~/Desktop/SecondLife-i686-1.21.6.99587/secondlife**.
You can leave the Comment: field blank if you wish.

Click OK and click on the icon to see if it starts.

I got an error message:

[i]Error
**Could not launch application**

Failed to execute child process "~/Desktop/SecondLife-i686-1.21.6.99587/secondlife." (No such file or directory)[/i]


I also tried removing the period at the end of the command (see above), which gave me virtually the same error message:

[i]Error
**Could not launch application**

Failed to execute child process "~/Desktop/SecondLife-i686-1.21.6.99587/secondlife." (No such file or directory)[/i]


My Second Life folder is located in Places-->Gregory Opera *My "Home" folder*-->SecondLife-i686-1.21.6.99587



> **Tony Flury said:**
> You can extract the file to anywhere (i extracted it to a sub directory within Home - so i don't get a folder on my dkestop).


You might be ok moving the folder once you have extracted it


When I try to move it to File System-->usr-->lib (I picked this directory because this is where most of my other applications appear to be installed), I am told:

[i]**Error while moving SecondLife-i686-1.21.6.99587".**

There was an error moving the file into /usr/lib.

Show more details

Error moving file: Permission denied.[/i]


> **Tony Flury said:**
> but why not extract it to the right place in the first place.

Because its current location is where the instructions above told me to extract it...

---

### Post by mustache ride on 2009-10-04
[center]:ks> **taurus said:**
> [font=fixedsys]*[size=4][color=darkred]in the world of linux, who needs windows and gates...[/color][/size]*[/font]:ks
[/center]

---

### Post by blueghoti on 2010-05-02
Hi guys - 

This thread worked for me - thanks!

Chris

---

### Post by da burger on 2010-05-02
From the looks of the second error message it appears that the period was not removed properly. Could you try and remove it again please.

---

