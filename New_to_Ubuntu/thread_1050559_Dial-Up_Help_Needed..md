---
title: "Dial-Up Help Needed."
date: 2009-01-25
forum: New to Ubuntu
---

### Post by TeeSquare on 2009-01-25
I have a Dell Inspiron 1520 laptop with Windows XP pre-installed, in which I was able to add Ubuntu 8.04.1 for dual booting. I have a dial-up internet account, and with much help from the LinModem website I could configure the internal modem and just about succeeded in connecting to the web.
Now all that has taken me several months because I'm completely new to Linux and have limited time to spare. I first need help in using the dial-up facilities *efficiently* so that I can shift operations from my rickety old desktop with Windows 98. Later I will need a lot of other help from the Ubuntu and Linux forums. Three priority questions for the present:-
(1.) Does Ubuntu/Linux have an equivalent or alternative for the internet connection icon? I would like to have a pop-up window which displays connection speed and a 'disconnect' button. At present I have to run 'wvdial' command from a terminal screen and ctrl+C to exit, which I hope is not really necessary.
(2.) Is it possible to record my internet usage in some sort of log file to show connection speed, time and bytes sent/recd for each session?
(3.) How can I view  the web pages offline (like temporary internet files are stored in Windows)? With dial-up I have to disconnect fast.
Please let me have some *detailed* advice on the above points, especially command line requirements like sudo, root, etc, as I don't understand most of it.
I hope to do all my internet access through Ubuntu and Firefox as I understand the virus risks are much less than with Windows.
It may take me two or three days to acknowledge any responses, so please bear with me.
Thanks, =TeeSquare=

---

### Post by utnubuuser on 2009-01-26
There is a usage log program, I've heard about it though I can't recall what it is.-Mostly meant for cellular I believe.

If you've got a webserver installed on your machine, (apache2 with php), you can save any web page by right clicking and doing a save-as.  I suggest a web server with php, because most web pages are .php these days, so you have to have a server to process them. -(apache2 and php5 are in Synaptic Package Manager). 
Firefox has a scrapbooking plugin/add-on/extension that saves web pages (I think it's even in Synaptics by now) Check for Firefox plugins in synaptic, or just go to the add-ons section of the Mozilla site (through your "Tools" in Firefox.

---

### Post by niteshifter on 2009-01-26
Hi,

> (1.) Does Ubuntu/Linux have an equivalent or alternative for the internet connection icon? I would like to have a pop-up window which displays connection speed and a 'disconnect' button. At present I have to run 'wvdial' command from a terminal screen and ctrl+C to exit, which I hope is not really necessary.

The package gnome-ppp will do this. It's a graphical front-end for wvdial, lets you start - stop connections with your mouse. Doesn't show the connection speed IIRC. For that you need the Netspeed applet - you probably already have it installed - you just need to add it to a GNOME panel. I believe that between gnome-ppp and netspeed-applet2 your second question would be covered. Search within synaptic for "gnome-ppp" and "netspeed" and let Synaptic do all the install work for you. 

> 
(3.) How can I view the web pages offline (like temporary internet files are stored in Windows)? With dial-up I have to disconnect fast.
Please let me have some detailed advice on the above points, especially command line requirements like sudo, root, etc, as I don't understand most of it.


> If you've got a webserver installed on your machine, (apache2 with php), you can save any web page by right clicking and doing a save-as. I suggest a web server with php, because most web pages are .php these days, so you have to have a server to process them. -(apache2 and php5 are in Synaptic Package Manager).
Firefox has a scrapbooking plugin/add-on/extension that saves web pages (I think it's even in Synaptics by now) Check for Firefox plugins in synaptic, or just go to the add-ons section of the Mozilla site (through your "Tools" in Firefox.

Whoa ... why make it so complicated? It's very easy to save a web page for offline viewing in FireFox for nearly all uses: Click File, then Save As. Down in the lower right corner is a pick-list:

Web Page, HTML (just grabs the HTML, frequently readable off-line, but images and the like will be missing)

**Web Page, complete  <--- Use this.** Will save to where you specify saving the page as an HTML file and creates a folder for the images & etc that the file needs. Just click on the saved .html file and the page will show properly in most cases. What won't work is the scripted portions that reach out to resources within the source domain. But the page will be readable, by and large.

---

### Post by TeeSquare on 2009-01-27
Thanks, I will try out the gnome-ppp (might take me a few days!). I don't know what is a webserver or php, so won't attempt anything like that yet. Never even used Synaptic, but I'm slowly learning to figure out the Linux terminology. I've successfully loaded Ubuntu HH, and followed verbatim the advice from the the LinModem website (very helpful experts there!) to make a dialup connection. The command line stuff is still quite intimidating for me. I find that even in this "Absolute Beginner Talk" forum, the posts are mostly at geek level by my standards. No doubt it is only through practice that I can get over my problems.
Regarding my point (3) I suppose I should conclude that web pages (when fully downloaded) will not get saved automatically in Ubuntu/Linux/Firefox. So I must do a "file > save as" etc for each page if I wish to see it later.
I have so far used only the now-obsolete Windows98, where most pages could be retrieved from "history" or "C:\Windows\temporary internet files" after disconnecting. So I could save time on dialup. But of late many pages would not save -- presumably the new php or other complicated types. Simple html would save OK with images etc in a folder of the same name.
If I can get some help to create a quick *keyboard shortcut to save the web pages* I want to see later, it will save me a lot of online time, because I'm rather slow at navigating the screen, finding the proper options and clicking in the right places!
I will post again to report progress (or difficulties). Thanks again for the advice. =TeeSquare=

---

