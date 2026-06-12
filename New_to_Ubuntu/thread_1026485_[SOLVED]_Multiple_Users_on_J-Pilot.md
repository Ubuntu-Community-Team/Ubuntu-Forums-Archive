---
title: "[SOLVED] Multiple Users on J-Pilot?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by LNB on 2008-12-31
Hi everyone, trying to setup my new Xubuntu box still and find replacements for some of my Windows apps.  I've come across J-Pilot to replace my Palm Desktop Organizer.  Does anyone know how to make _multiple_ Palm's synch and display like the Window's version?  Is this the best replacement software to use?

Thank you.

---

### Post by blueridgedog on 2009-01-02
I think it is the state of the art for the palm and Linux.  When the second user logs in to Ubuntu is the first user's data shown for the syncronization?  I thought j-pilot used settings and data unique to each user login.

---

### Post by LNB on 2009-01-03
Thanks for your response.  What you are saying makes sense, but was hoping to do this under a single account in Xubuntu since I'm really new to LINUX.

I contacte the program creator and got the response below.  Seems to be an "easy" solution, but not exactly sure what this means since I'm a beginner with LINUX... Does it make sense to anyone in the forum?  Thank you.

> > Question:  Does the software support multiple Palm users?  I have two Palm devices at my home, and wondering if I will be able to view both data sets on your program.

Yes, it does, but not through the GUI  I use a few Palms for testing.  I just write a script to launch each one.  Here is the script for my treo 680.

#!/bin/bash
export JPILOT_HOME=/home/mouse/TREO680

Just set JPILOT_HOME for a directory for each one you use.

---

### Post by blueridgedog on 2009-01-03
The right solution is to use different users for different pilots.  The solution given by the developer is to artificially change "home directories" and I think it would be more complex than the option of creating another user and simply switching.

What is implied is that you will manually create seperate directories for each device, then prior to running them point the device to it.  This is reasonable for an advanced user, but far more complex than each user having a login and a palm device.  If you want to go the one user and many devices account, I can probably walk you through the process.

---

### Post by LNB on 2009-01-03
Thank you.  This is all a bit complicated for me so appreciate any help that you can give me.  (BTW, I noticed that you have a very handy signature line, so will be taking a look at your other links next...particularly the one on mounting windows partitions...)

Ok, I think what you are saying is that if I created multiple Xubutu logins, then J-Pilot would automatically load up/synch that user's info onto the software.  If that is so, that does not sound too bad.

However, do you think there is an easy way to create something like two icons on my desktop where I could double click and have each load one of my two users info and start J-Pilot?  I guess I'm trying to figure out a workaround to me inputting code each time I want to switch J-Pilot users...

Thanks again.

---

### Post by blueridgedog on 2009-01-04
It all can be done with icons (if it works as he described...keep in mind that we are still dealing in the realm of theory).

For starters, let's see what your current jpilot home is.  Bring up a terminal and type:

```
echo $JPILOT_HOME
```

White this down.  We will call it "myhome", but when I use "myhome" you will use your real home, which should be /home/youruser/something.

Now, while still in the terminal, make a new directory that you want to use for the second device.  For sake of this example, I will call it treo2, but you can substitute your name for what I call it.  You use the command:

```
mkdir treo2
```

Do this while inside your home directory (which you should be by default).  Leave the terminal up (in your home directory as you will need it in a bit)

Now bring up your text editor, Applications -> Accessories -> Text Editor

Type in the following:

```
#!/bin/bash
export JPILOT_HOME="myhome"
```

Don't use the quotes.  Save it on your desktop, naming it something that makes sense to you to identify that it is your device.  I will assume the name is "mydevice".  Remember to change "myhome" to be exactly what you recorded above and leave off the "".

Create a new file.  Type in the following:

```
#!/bin/bash
export JPILOT_HOME="treo2"
```

Don't use the quotes.  Save it on your desktop, naming it something that makes sense to you to identify that it is your other device.  I will assume the name is "otherdevice", though you will obviously name it something different.

So, on your desktop you will have to files.  Go back to the terminal and change directories into your Desktop directory:

```
cd ./Desktop
```

And make these two files executable:

```
chmod 744 otherdevice
chmod 744 mydevice 
```

Again, keep in mind that you may use other names and these names are for example only.  Now, when you click one, jpilot will expect to find the files where it normally looks for them, when you click the other, it will look for them in the new directory you made, which will be empty the first time.  Note that you will get a dialogue box that asks if you want to open or run these, you will select "run".  You can test these by going to the same terminal after you run each and run:

```
echo $JPILOT_HOME
```

And verify that it is set right...

Keep in mind that I don't have a palm device any more so if things go really wrong, we may want to get some other people in on the thread.

---

### Post by LNB on 2009-01-04
Thanks so much for your detailed reply.  I'm really showing my lack of experience with Linux here, but do I have to run your initial echo command in any particular directory?  I ran it in the terminal window and it returns an empty line only.

> 
LNB@ubuntu:/$ echo $JPILOT_HOME

LNB@ubuntu:/$ 


---

### Post by blueridgedog on 2009-01-04
No, you don't have to be in a particular directory.  Try echoing the value of the $JPILOT_HOME variable when jpilot is running, so run jpilot then in a terminal try:


```
echo $JPILOT_HOME
```

---

### Post by LNB on 2009-01-04
Thanks for your response.  

Tried running J-Pilot first then running the echo command, but I'm still getting the same output as before.

---

### Post by blueridgedog on 2009-01-04
Hmmm...then I am stumped.  Perhaps another email to the developer?

---

### Post by LNB on 2009-01-05
Here is what the developer said.  Does this help move me along to a solution?  Thank you.

>I've tried to follow your instructions, but I don't seem to have any
>prior/initial JPILOT_HOME entry when I tried to echo it in a terminal. 
>J-Pilot seems to be running fine.  May I trouble you for some more
>directions?

JPILOT_HOME won't be set and if you don't set it, jpilot will just write to a directory called $HOME/.jpilot, where $HOME is your home directory.  To make it write somewhere else you can set JPILOT_HOME to somewhere else and then run jpilot from the same terminal window.  Environment variables are only set in the shell that you set them in and not system wide.

---

### Post by blueridgedog on 2009-01-06
Ok, I have mocked this up on my PC and it works as you want.  For your use, you can use the jpilot icon on your menu, for your other user, you will need an icon on your desktop that we will create.

(I will call your other user Jill and your user account Jack, change as you need - but be certain to use the real names you intend to use in place of Jack and Jill below).

Right click on your desktop and select create document, then empty file.  Name the file jpilotJill.sh.  Right click jpilotJill.sh and select "open with text editor.

Paste in:

```
#!/bin/bash
export JPILOT_HOME="/home/Jack/jpilotJill"
jpilot
```

Note that this is a folder inside YOUR home directory.  This icon will be used to launch jpilot to use Jill's data and to synchronize with Jill's device.

Save the file.  Right click it again and select properties, then the permissions tab then check the box that states "allow executing file as program" and close properties.

Bring up nautilus (places -> home folder) and right click in your home directory and select "create folder".  Name the folder jpilotJill and note that the location of the file should be EXACTLY as you specified in the export statement above.

Close nautilus.

If you have an issue with nautilus, just open a terminal and type:

```
mkdir /home/Jack/jpilotJill
```

(remember, changing Jack/Jill as needed).

Double click the jpilotJill.sh file and select "run".  It should bring up an empty calendar.  Put in a test event.  Close.

Run jpilot from your regular icon and your data should be there.  You should be able to go back and forth with ease.

PS:  If you tell me your user names I can re-write the above using actual names so things are a bit clearer.

---

### Post by LNB on 2009-01-06
Thank you again for your detailed help.  Really appreciate it.  I'm having a little trouble with this part:

> Save the file. Right click it again and select properties, then the permissions tab then check the box that states "allow executing file as program" and close properties.


My properties menu has two tabs: General and Permissions.  However, neither has a "allow executing file as program" option.   The properties window is recognizing the file as a shell script, but no option...  Is this because I'm using Xubuntu?

Thank you.

---

### Post by LNB on 2009-01-06
Success, I think I've figured it out!  

I looked back at your earlier message with the "chmod 744" code and it worked!

Thanks again for all your assistance.  Would have never been able to do this without your help!

---

### Post by blueridgedog on 2009-01-06
Glad to help...and you have learned a great deal in the process.

Linux gives you control at the expense of having, at times, to learn how to use it.  You can do great things simply, at the expense at times of having to work greatly to do simple things.

Right clicking the script you made, then going to properties and making it executable should have done the same thing, but you did it the old-fashioned way.  744 actually means:

Owner of the file can read (4) write (2) and execute (1) for a total of 7
Members of the group that owns the files can read (4) for a total of 4
Others can read the file (4) for a total of 4

So, all that can be done at the command line by simply making the "mode" of the file 744.

Enjoy Ubuntu.  I am.

---

### Post by LNB on 2009-01-07
Thanks again!

---

