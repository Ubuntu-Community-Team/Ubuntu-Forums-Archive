---
title: "How to Create My own customized ubuntu iso"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by balachandarlinks on 2009-06-07
Hi,
   I want to fully customize ubuntu.Boot screen,log in screen,splash screen,adding/removing softwares everything to my flavour.I already read about UCK.But i want an easy to follow tutorial regarding all.I hope such one is there in the net.
       I m dying to get the tutorials and some help.Pls help me to make it...
          cheers...

---

### Post by kansasnoob on 2009-06-07
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by Flag on 2009-06-07
Install Arch with an Ubuntu login flash screen ?

---

### Post by Dave W. on 2009-06-08
Hello,

I've been looking at this too and with being new I'm not really sure how to do this part "The Remastersys repository needs to be added to your /etc/apt/sources.list"

Can anyone expand on this.

Thanks,
Dave

---

### Post by camper365 on 2009-06-08
it doesn't look like they have a repository. But if there was one, you would add the following line to /etc/apt/sources.list

```
deb http://url_of_repository/ubuntu jaunty main
```

This is based on guesswork since it doesn't look like they have a repository. Replace Jaunty with whatever version you are running.

after you add that, run

```
sudo aptitude update
```

---

### Post by Dave W. on 2009-06-08
Thanks, for your reply.  There are a few sites that show how to use remastersys.

I really don't know how to paste what is below to the source.lists

deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/



I think that if someone could tell me this I might be able to follow the directions on this site.

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

Thanks in advance.
Dave

---

### Post by anjilslaire on 2009-06-08
open a terminal and do
```

sudo gedit /etc/apt/sources.list

```

Add the repository line to the bottom of the page, and save/close.

Then refresh the repository list:
```

sudo apt-get update

```

---

### Post by furialis on 2009-06-08
Open a terminal, and type ```
gksudo nautilus
``` at the prompt.

Then navigate to File System > etc > apt.

Then right click the "sources.list" file and select "open with text editor"

Then append this to the bottom of the file 
```
deb http://www.remastersys.klikit-linux.com/repository remastersys/
```

Save that file and then in a terminal type
```
sudo apt-get update && sudo apt-get install remastersys
```

Enjoy!

Edit : You are probably going to need root permissions to change files in the future. You can right click on the desktop and select "Create Launcher" Name it Root Nautilus and for the command typr "gksudo nautilus" without the quotes and save it.

---

### Post by Dave W. on 2009-06-08
That seemed to work.

I had to correct the line

sudo gedit /etc/apt/sources.list

I will post back later....Thank you!!:D

Dave

---

### Post by Dave W. on 2009-06-08
Well, I'm not really sure what I'm doing wrong.  I've got to mull over what you both have said and do some more reading.  I will post back with more questions I'm sure.

Thanks,
Dave):P

---

### Post by furialis on 2009-06-08
There was a typo in my last post, I corrected it.

I'm not sure where you got that repository from, but the one I listed was from my actual sources.list file, and I have remastersys installed and working.

Protip: I made a couple of coasters before I realized that I needed to remove the proprietary driver before making the backup.

---

### Post by Wiebelhaus on 2009-06-08
You have a few choices which have already been suggested the best one I've used for my tool disc was remastersys.

---

### Post by Dave W. on 2009-06-08
Furialis,

As a newb. I'm still a little hung up on terminal entries.

I'm not really sure what gksudo is.  Is it the same as sudo su? 

Your edit:                                                    Edit : You are probably going to need root permissions to change files in the future. You can right click on the desktop and select "Create Launcher" Name it Root Nautilus and for the command typr "gksudo nautilus" without the quotes and save it. 

I don't know what this is either...but I'm willing to learn.

Thanks,
Dave

---

### Post by furialis on 2009-06-08
Dave, I am also a newb.

Maybe I can speak newb to you.

You'll see in the top left of your screen Applications Places System.

Go to Applications > Accessories > Terminal. *Hint: You can click on it and drag it onto the desktop or your upper panel to make it easier to open. In Ubuntu you'll need the terminal a lot. At first it was scary, but now I can't imagine life without it. You'll get the hang of it.*

*Edit: As a probable ex-windows user, you're used to clicking things and stuff happens. Ubuntu does the same thing with it's desktop. When you double click stuff you are sending a command to the computer to do something. The terminal just let's you type in those commands instead of clicks. As it turns out, this is a much more powerful tool. You can type all kinds of commands in without having to have an icon to click on. This can be dangerous, so be careful. Windows kind of won't let you screw it up. Ubuntu will let you break it with a simple yes/no.*

When it opens, at the prompt type ```
gksudo nautilus
```It will prompt you for a password. Type it in and press enter.

*Without getting into too much detail, Nautilus is the name of the program that lets you browse files with a GUI. gksudo is a command that gives a graphical application root power - you'll learn about this later.*

Then on the left side of that window that opened, you'll see root/desktop/file system/ network, etc... click on File System. Then click the etc folder. Then click the apt folder.

Then right click the file named sources.list and select open with Text Editor.

Delete the entry for the other repository. I'm not sure if that one works, I know this one does:```
deb http://www.remastersys.klikit-linux.com/repository remastersys/
```

Then close the browser. It will ask you if you want to save, select yes.

Then go back into the Terminal and at the prompt type:
```
sudo apt-get update && sudo apt-get install remastersys
```

It should then install remastersys.

Like I said, it took me a couple of tries to figure out that the proprietary drivers were messing up remastersys. I'm not sure if it's my system specific or not, but it's better to be safe than sorry.

To run remastersys open a Terminal and type at the prompt:
```
sudo remastersys backup
``` and let it run. The finished backup will be in /home/remastersys.

The purpose of my edit was to give you a shortcut to a root file browser. You'll need that in the future too, and creating an icon (or launcher) on your desktop just for that purpose eliminates the step of opening a terminal and typing gksudo nautilus.

If there are more experienced people who want to intervene, please do so, so that I don't damage a person that is new to the wonderful world of Ubuntu ;)

---

### Post by Dave W. on 2009-06-08
Furialis,

As a Newb you are quite wise...

Thanks for your help.  I'll have to give it a try.

Dave 

):P

---

### Post by Dave W. on 2009-06-09
Well,  I tried first creating a launcher.  I think that went okay.  Then I went into the terminal and got this when I typed "gksudo nautilus".


** (nautilus:7400): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

A root file browser opened up and I followed it to my sources list.

There was an orange file that had a medibuntu.list "sheet inside.  Outside of that orange file were two other sheets.  One said sources.list and the other said source.list.  I think the later is wrong and I created it incorrectly.  It has the remastersys site in it.  What do you think so far?  Something is not quite right.

I've got to go for now to earn a living.

Thanks,
Dave

---

### Post by Bradtek on 2009-06-09
How is something as simple as adding a repository taking so many posts.

Mouse Click way = System Menu | Administration | Software Sources
Then choose Third Party Software Tab, Click the Add button
Paste this into the Apt line box
```
deb http://www.remastersys.klikit-linux.com/repository remastersys/
```
The rest should be self explanatory
Open Synaptic Package Manager
Reload
Search for Remastersys
Mark for installation
Apply


Terminal way (easiest way)
type in a terminal
```
gksudo gedit /etc/apt/sources.list
```

Scroll to the bottom and paste the line
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/
Save / close

In terminal type
```
sudo apt-get update
sudo apt-get install remastersys
Y
Y
```

All done

---

### Post by Bradtek on 2009-06-09
> furialis

While in general your help is sure to be appreciated
Maybe it's not such a great idea having a self confessed newbie 
getting lost and potentially editing the wrong files in nautilus with root permissions.

---

### Post by Dave W. on 2009-06-09
Well to make a long thread even longer.  I just wanted to say that I do appreciate everyone's help.  I also want to say that anything I do,  I know that I do at my own risk. 

As with most things, there are probably many different solutions and methods of attack.  I have learned something from all of you and am greatful.  

I also wanted to say that through everyone's efforts, I have managed to get Remastersys in my box and have not broken my machine.   Atleast I think...:D

Now for the fun part.

---

### Post by grndslm on 2009-06-26
Here's a remastersys guide I created for n00bs like yourself.  Enjoy!

[http://ubuntuforums.org/showthread.php?t=1073838](http://ubuntuforums.org/showthread.php?t=1073838)

---

