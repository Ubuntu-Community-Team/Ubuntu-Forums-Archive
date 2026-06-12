---
title: "resizing windows within virtualbox"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by djs03004 on 2010-01-23
Okay, I really am an absolute beginner, so I figured this would be the best place to post this. I'm running ubuntu within virtualbox for a class I'm taking. 

I've successfully started up ubuntu within virtualbox, but I'm stuck on something. I took a screenshot within virtualbox, and saved the screenshot to the virtual desktop. I didn't know how to get the screenshot I'd taken within the virtual system to my real system, I figured I could email the screen shot to myself to use for the homework assignment, but when I tried to configure Evolution (the email application included with ubuntu) I found that the Evolution window is larger than the virtualbox window that contains it, and I can't figure out how to resize either. Without being able to see or access the entire Evolution window, I can't see all of the buttons in the program, which means I can't configure the program. this is something that will definitely become a problem with other applications if I don't know how to do this. I can't figure this out, can anyone help me out? I included a couple of screenshots to show you what the issue is. 

Just so you know, I'm not trying to use VBox's snapshot feature. I just want to be able to resize applications, or the vbox window, so that I can access the application. 

screenshots:

[http://i48.tinypic.com/5o9rvr.jpg]("http://i48.tinypic.com/5o9rvr.jpg%5B/IMG%5D")

[http://i46.tinypic.com/2j4a7x2.jpg]("http://i46.tinypic.com/2j4a7x2.jpg%5B/IMG%5D")

thanks in advance!

---

### Post by rogue_0111 on 2010-01-23
1. Click your mouse anywhere on the Desktop in Ubuntu
2. Press **Ctrl** (*the one on the right of your keyboard*) + **F**

Once again press **Ctrl + F** (*use the Ctrl button on the right side of your keyboard*)

To exit do it again.


--

---

### Post by jflaker on 2010-01-23
Install guest additions in your VirtualBox guest then you can set up a share to your host system so you can move files to and from you virtual machine.

I figured I'd point you in a direction so you can learn....if you want further info let us know

> **djs03004 said:**
> Okay, I really am an absolute beginner, so I figured this would be the best place to post this. I'm running ubuntu within virtualbox for a class I'm taking. 

I've successfully started up ubuntu within virtualbox, but I'm stuck on something. I took a screenshot within virtualbox, and saved the screenshot to the virtual desktop. I didn't know how to get the screenshot I'd taken within the virtual system to my real system, I figured I could email the screen shot to myself to use for the homework assignment, but when I tried to configure Evolution (the email application included with ubuntu) I found that the Evolution window is larger than the virtualbox window that contains it, and I can't figure out how to resize either. Without being able to see or access the entire Evolution window, I can't see all of the buttons in the program, which means I can't configure the program. this is something that will definitely become a problem with other applications if I don't know how to do this. I can't figure this out, can anyone help me out? I included a couple of screenshots to show you what the issue is. 

Just so you know, I'm not trying to use VBox's snapshot feature. I just want to be able to resize applications, or the vbox window, so that I can access the application. 

screenshots:

[http://i48.tinypic.com/5o9rvr.jpg]("http://i48.tinypic.com/5o9rvr.jpg%5B/IMG%5D")

[http://i46.tinypic.com/2j4a7x2.jpg]("http://i46.tinypic.com/2j4a7x2.jpg%5B/IMG%5D")

thanks in advance!

---

### Post by djs03004 on 2010-01-24
Hey guys, thanks very much for your help. As it turns out, when I installed virtualbox, I had set the video display driver to use only 16 mb of memory, which meant that it would only create a tiny little window. 

jflaker, where can i learn more about guest additions? Right now I'm not even sure what it is.

---

### Post by head2head on 2010-01-24
There should be an option to install guest additions under the devices menu in virtualbox.

---

### Post by Paqman on 2010-01-24
> **djs03004 said:**
> Right now I'm not even sure what it is.

It's a set of drivers and tools that enhance your virtual machine. It'll give you higher screen resolution, integrate your mouse, give you a bi-directional clipboard, etc, etc.

---

### Post by J V on 2010-01-24
middle-click and drag will resize for you :P

Edit: wtf? it stopped working! :/

---

