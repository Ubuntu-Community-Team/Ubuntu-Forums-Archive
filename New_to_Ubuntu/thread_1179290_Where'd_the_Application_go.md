---
title: "Where'd the Application go?"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by tomreid on 2009-06-05
Hi
I have a real beginner's question here. 

When I install applications through the "add /remove applications" facility and also when I use a ".deb" package I downloaded, the relevant package managers are not telling me where I can access the app after it is installed. 

e.g. 

I installed "handbrake" my clicking on a .deb file. Package manager reported the software was successfully installed, but where do i start the app? In Mac, there is folder I can access via the finder where containers with all the applications are stored, i just look for the app there.

Ubuntu seems to have a "applications" pull down menu in the top right, with a number of sub menus, but sometimes I download an app, and don't see it in this menu structure. Where is the reference to the app stored, so I can access it?

Also, does the package installer chose which one of these sub-menus to install the app in? Sometimes I see a downloaded app in a this "applications" pull down menu, sometines I don't. Sometimes, even more confusingly, I didn't see an application there yesterday and I see it there today (maybe the system needs to re-boot to re-populate this menu?)

cheers

---

### Post by jbruced on 2009-06-05
> **tomreid said:**
> Hi
(maybe the system needs to re-boot to re-populate this menu?)

cheers

Yes that has happened to me a few times. 

If you can't find the link in the menu system after a reboot, use the find command to look for it:
in terminal 

sudo find / -name *nameofyourapplication*

then you can use the menu editor to add any apps you want once you know where they are located. They're usually in /usr/bin or /usr/sbin .

Hope this helped a little.

GL 
Bruce

---

### Post by steeleyuk on 2009-06-05
A large number of the applications you can install are run through the command line. HandBrake is one example, in that there is a command line version and an interface-based version.

---

### Post by bacardiandwatermelon on 2009-06-05
This is the one thing I hate about ubuntu, there are some brainstorm ideas to let you choose where you want the shortcut in synaptic. Handbrake is under Sound and Video on my PC

---

