---
title: "Customising startup"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by dave66 on 2009-04-17
Hi,

Okay, just to be clear I'm pretty much a newbie when it comes to Ubuntu so please bear that in mind if you reply ;)

I have equipped our company we a number of Dell Mini-9's all running Ubuntu and thanks to help I got here I've managed to create the same disk image on them all.

The next step for me is to configure the systems so that they can only be used for specific funstions/applications. Really what I'm aiming for is what I call an Application Specific Device. The people using these systems will have no call/reason to use Email/Browsing/OpenOffice etc. and I have uninstalled all those applications. What I need to work out and I'm hoping for some help and guidance on is how to have the systems startup with the normal Ubuntu Uname/Password login and then immediately run an application without going to the normal (Gnome?) desktop. So essentially once the user logs in they are straight into the application and when they exit the application the netbook shuts down. In fact if there was a method to stop the Menu bars being displayed that would be really great.

The application the users will be running will have inbuilt communications for transmitting information view FTP. The people using these systems are not computer literate and have requested a simple Switch on - use the application - shutdown solution.

Any help or suggested reading would be greatly appreciated.

Thanks

Dave

---

### Post by LowSky on 2009-04-17
well you can easily delete the panels form showing up, and get applications to auto boot at login

I personally wouldn't make the application auto-turnoff the machine, as that could be an annoyance by "illiterate" users who like to click on the wrong things time to time.

Also creating easy to click on application icons would also be nice and make things simple just in case of accidental exit. you could even make an icon for shutdown.

you could always turn off the windows manager (so they cant just click on an close or minimize/maximize),  by disabling metacity

---

### Post by Dileeshvar on 2009-04-17
I would recommend that you use preference-->secession option
where you could customize your startup programs.
And generally /etc/init.d is the place where you find
the shortcut for your applications to run !!


Hope this helps :)

---

### Post by dave66 on 2009-04-21
Thanks for the pointers.

I'm getting there now. I have removed Gnome desktop & Dell (Ume) Launcher using Synaptic Packager Manager, which gives a nice clean desktop on which I have the application so a double click will run it.

When I'm ready (finished testing first release) I can also add a call to "shutdown now" in the application when the user exits. LowSky, good point about illerate users selecting the wrong thing from time to time, but I'll have things like "Are you sure you want to exit" followed by "Are you certain you want to exit, this will shutdown the computer"

At present the problem I have is the application uses an external USB device. So at present I have to run the app using sudo and I can't seem to find a method to get the app to run at start up. I have tried adding a call to it in /etc/rc.local but no joy there. 

Thanks for the input.

---

### Post by Dileeshvar on 2009-04-21
ya hope it works :)

---

### Post by dave66 on 2009-04-21
> **Dileeshvar said:**
> ya hope it works :)

Yep, me too!! :D

---

### Post by ushills on 2009-04-21
> **dave66 said:**
> 
At present the problem I have is the application uses an external USB device. So at present I have to run the app using sudo and I can't seem to find a method to get the app to run at start up. I have tried adding a call to it in /etc/rc.local but no joy there. 

Add the device in fstab and it will mount like anynother drive at boot then add the application to sessions.

---

### Post by sdennie on 2009-04-21
> **dave66 said:**
> 
At present the problem I have is the application uses an external USB device. So at present I have to run the app using sudo and I can't seem to find a method to get the app to run at start up. I have tried adding a call to it in /etc/rc.local but no joy there. 


Running an X app in /etc/rc.local probably isn't going to work.  However, whatever exists in ~/.xinitrc is executed as the X server comes up.  That may be what you are looking for if you've uninstalled the normal session management parts of gnome.

---

### Post by dave66 on 2009-04-30
So things are going well, I got the issue with the USB device resolved by creating rules which I put in /etc/udev/rules.d and an executable script to change the owner of /proc/bus/usb to a non-root user.

So things are working well. I'm still getting my head around the concept of taking an image of one unit and then using it to clone the other PCs. This was a minor point as I was only dealing with a few units, however it has now risen to the top of my "to do" list as a customer has seen what we are doing and wants me to provide a quote to do something similar for them. 

The big difference is the customer will likely want about 100-150 PCs, which is great (I think).

Anyhow, I have a new question for the gurus here, I have tried researching this put can't seem to find what I'm looking for so here's hoping somebody here can guide me [-o<.

The PCs we are using are Dell Mini-9's (Ubuntu 8.04) and have a 4GB solid state drive (must say I live these PCs). So what I need to know:

[COLOR="Blue"]Is it possible to create users (username/password) on Ubuntu without having to give each user a home directory?[/COLOR]

While the customer wants 100-150 pieces, they would be likely to have 150-200 people sharing the units and they want any member of staff to grab any PC and use it, so each PC will have to have a username/password but I don't want to start using disk space by having a home directory for all 200 users. 

The next related question is:

[COLOR="Blue"]If I create the system as I want (either with or preferably without a home directory for each user) is there anyway in the future for me to update the user list, I know they will have staff leaving/joining so the user list will change and it would be nice if I could have the user list updating via a download.[/COLOR]

And my final question (for now :redface:):

[COLOR="Blue"]While I want to make sure that the systems are kept up to date, especially with security patches, I would like to control the application of the updates, I want to avoid having a problem because an update causes the application not to run. Is it possible to create "my own" repository where I would place updates once I have checked that their application does not cause a problem?[/COLOR]

Thanks for your help and patience with me, now off to read about cloning systems, looks like remastersys or G4L might do what I want (create an image of one system, which I put on a USB stick and then use the stick to install the image on other PCs).

---

### Post by Paqman on 2009-04-30
> **dave66 said:**
> 
[COLOR="Blue"]Is it possible to create users (username/password) on Ubuntu without having to give each user a home directory?[/COLOR]

While the customer wants 100-150 pieces, they would be likely to have 150-200 people sharing the units and they want any member of staff to grab any PC and use it, so each PC will have to have a username/password but I don't want to start using disk space by having a home directory for all 200 users. 


Do they absolutely have to have a unique login? You could just have them all use the guest session. The guest's home is in /tmp, so it gets wiped every boot (and indeed when they log out) As a bonus the guest session has very limited privileges by default.

> 
And my final question (for now :redface:):

[COLOR="Blue"]While I want to make sure that the systems are kept up to date, especially with security patches, I would like to control the application of the updates, I want to avoid having a problem because an update causes the application not to run. Is it possible to create "my own" repository where I would place updates once I have checked that their application does not cause a problem?[/COLOR]


You can specify exactly what updates you want to subscribe to. In your case i'd go for automatic install of sceurity updates only. Creating your own repo is entirely possible (create a Launchpad account and look at PPAs) but tbh it's probably a lot more work than it's worth. I know you want to retain control, but the core security updates that Ubuntu ship out are well tested and reliable.

---

