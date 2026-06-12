---
title: "Start x11vnc on startup"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by ThreeLies on 2010-11-16
Hello,

Some of these instructions have changed but I have been finding random things here and there. What I have is a fresh install of Ubuntu 10.10 and I have installed x11vnc. What I want to do is have it startup (as root I believe) when Ubuntu starts.

I think it has as root so it shows the login screen to let you login. I am trying to figure out how to get it to that point, so I can run a server headless.

Thanks

---

### Post by krunge on 2010-11-16
Are you able to get the X server and GDM to start up headless?  Sometimes that can be tricky.

x11vnc is also able to serve virtual X sessions (e.g. via inetd) if you install the 'xvfb' package.  This avoids needing to get the X server running headless:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-userlogin](http://www.karlrunge.com/x11vnc/faq.html#faq-userlogin)[/INDENT]

vncserver can do a similar thing (and will be somewhat faster.)

---

### Post by Shobuz99 on 2011-01-06
Karl,
Thank you for the link you posted in response to ThreeLies question/issue.
I went to the link to search for an answer to my question about x11vnc startup; but I couldn't find it after scanning the whole FAQ. Here's my situation/question:

I want to be able to startup x11vnc and have it go through the entire process, including auto-input of the, port, password, etc. so that once the machine is completely booted I can allow connection to it from inside my home network.

I'm using Ubuntu 10.04 LTS on 2 machines. One is a AMD64 machine and the other is an old 32 bit pc that I have installed the 32-bit version of Ubuntu 10.04 LTS.

So far I've set up the AMD64 machine to startup x11vnc but I still have to manually select the connect options on the menu, and then "apply" and click ok. I want this to be automated so I don't need to intervene at every startup.

Also, I can't get the 32bit machine to work even to the above. I've tried the  x11vnc -rc command and created a startup file, (x11vncserv2); but it doesn't work like it does on my AMD64 machine. Once the 32 bit machine is booted, I have to manually select the port number and ultravnc options, and then ok and then the next screen for the "accept connections", etc.
I want this to startup the same way I want the AMD64 machine to start...no intervention on my part.

Is there a stock command line that I can include in the "Startup applications"
file I created for x11vnc on both machines, that will do this for me?

Sorry for the naive question. I'm not very experienced with linux command line options at this point.

Thank you for your help
Rick (Shobuz99)

---

### Post by perspectoff on 2011-01-06
* You can create a startup script so that X11VNC is automatically loaded at startup (with password settings): 

echo "/usr/bin/x11vnc -forever -rfbport 5900 -rfbauth ~/.vnc/x11vnc.pass -o ~/.vnc/x11vnc.log -loopbg -display :0" > ~/.kde/Autostart/x11vnc.sh

chmod +x ~/.kde/Autostart/x11vnc.sh

These instructions use the Autostart folder for KDE/Kubuntu (~/.kde/Autostart). In Gnome/Ubuntu use the Autostart folder ~/.config/autostart instead.

Here are the full instructions copied from Kubuntuguide.org at:
[http://kubuntuguide.org/Maverick#X11VNC_Server](http://kubuntuguide.org/Maverick#X11VNC_Server)

(or Ubuntuguide.org at:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#X11VNC_Server](http://ubuntuguide.org/wiki/Ubuntu:Maverick#X11VNC_Server) )


    * Install the X11VNC server to share your desktop with other computers: 

sudo apt-get install x11vnc

    * Run X11VNC without a password: 

x11vnc -forever -rfbport 5900

    Note: -rfbport 5900 specifies the port to listen on. The port number can be changed. This option is not required if the default port 5900 will be used. Don't forget to open/forward this port in your firewall/router. By default X11VNC server exits after the first client disconnects. To keep it running (and allow future connections), use the -forever option. See
[http://www.karlrunge.com/x11vnc/x11vnc_opts.html](http://www.karlrunge.com/x11vnc/x11vnc_opts.html)
for more command line options. 

    * You can create a password: 

mkdir ~/.vnc
x11vnc -storepasswd YOUR_PASSWORD ~/.vnc/x11vnc.pass

    * Run X11VNC, requiring a password: 

x11vnc -forever -rfbport 5900 -rfbauth ~/.vnc/x11vnc.pass -o ~/.vnc/x11vnc.log -loopbg -display :0

    * You can create a startup script so that X11VNC is automatically loaded at startup (with password settings): 

echo "/usr/bin/x11vnc -forever -rfbport 5900 -rfbauth ~/.vnc/x11vnc.pass -o ~/.vnc/x11vnc.log -loopbg -display :0" > ~/.kde/Autostart/x11vnc.sh

chmod +x ~/.kde/Autostart/x11vnc.sh

     * You can test the startup script: 

~/.kde/Autostart/x11vnc.sh

---

### Post by Shobuz99 on 2011-01-06
> **perspectoff said:**
> * You can create a startup script so that X11VNC is automatically loaded at startup (with password settings): 

echo "/usr/bin/x11vnc -forever -rfbport 5900 -rfbauth ~/.vnc/x11vnc.pass -o ~/.vnc/x11vnc.log -loopbg -display :0" > ~/.kde/Autostart/x11vnc.sh

chmod +x ~/.kde/Autostart/x11vnc.sh

These instructions use the Autostart folder for KDE/Kubuntu (~/.kde/Autostart). In Gnome/Ubuntu use the Autostart folder ~/.config/autostart instead.

Here are the full instructions copied from Kubuntuguide.org at:
[http://kubuntuguide.org/Maverick#X11VNC_Server](http://kubuntuguide.org/Maverick#X11VNC_Server)

(or Ubuntuguide.org at:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#X11VNC_Server](http://ubuntuguide.org/wiki/Ubuntu:Maverick#X11VNC_Server) )


    * Install the X11VNC server to share your desktop with other computers: 

sudo apt-get install x11vnc

    * Run X11VNC without a password: 

x11vnc -forever -rfbport 5900

    Note: -rfbport 5900 specifies the port to listen on. The port number can be changed. This option is not required if the default port 5900 will be used. Don't forget to open/forward this port in your firewall/router. By default X11VNC server exits after the first client disconnects. To keep it running (and allow future connections), use the -forever option. See
[http://www.karlrunge.com/x11vnc/x11vnc_opts.html](http://www.karlrunge.com/x11vnc/x11vnc_opts.html)
for more command line options. 

    * You can create a password: 

mkdir ~/.vnc
x11vnc -storepasswd YOUR_PASSWORD ~/.vnc/x11vnc.pass

    * Run X11VNC, requiring a password: 

x11vnc -forever -rfbport 5900 -rfbauth ~/.vnc/x11vnc.pass -o ~/.vnc/x11vnc.log -loopbg -display :0

    * You can create a startup script so that X11VNC is automatically loaded at startup (with password settings): 

echo "/usr/bin/x11vnc -forever -rfbport 5900 -rfbauth ~/.vnc/x11vnc.pass -o ~/.vnc/x11vnc.log -loopbg -display :0" > ~/.kde/Autostart/x11vnc.sh

chmod +x ~/.kde/Autostart/x11vnc.sh

     * You can test the startup script: 

~/.kde/Autostart/x11vnc.sh

Thanks for all the information. I tried different variations of these commands
from a "Terminal" and from command properties in a launch icon I created on my desktop.
In every case, the second menu screen appears and waits for the selection of 
an "Accept connections" and/or the manual input of the password.

I get that same result if I just put the following command in the X11vnc startup applications command line and point it:
 x11vnc -rc x11vncserv (where 'x11vncserv' is the file in my /home/rick folder)

I want x11vnc to start during startup, and auto-enter my password from the .pass file 
and "accept connections" without any intervention from me.

So what am I doing wrong? 

Rick (shobuz99)

---

### Post by Shobuz99 on 2011-01-10
perspectoff, krunge

I have tried the following command in a 'Startup' I added in my "Startup Applications" section of "System Preferences": 
**x11vnc -forever -rfbport 5909 -rfbauth ~/.vnc/x11vnc.pass -o /.vnc/x11vnc.log -loopbg -display :0**

What happens is an endless loop of x11vnc sessions that open and continue to open, 
until I delete the command line in the 'startup' and restart my machine!
This is not working for me. What am I doing wrong, and what other information do you need from me to help me get this working properly?
I can provide my x11vnc.log if that will help.

As I said, I'm running Ubuntu 10.04 LTS on a AMD64 machine.
I want to simply startup x11vnc with one session, that automatically selects the port, inputs the password from my /.vnc password file, 
and basically requires no manual intervention from me.
So far, I have not been able to get this to work.
The farthest I can get with ANY variation of x11vnc commands is to arrive at the 2nd dialog box that allows me to click "Accept Connections"
as one of the options I want, and asks me for my password. 
I want to automatically get past the 2nd dialog box and avoid all this when I startup my machine. Is this even possible?

What am I doing that is either stupid, naive, or just plain wrong?
I want to learn and understand this application so I can use it on my home network of two desktops, a laptop, and a netbook.
Can you help me?

Rick (shobuz99)

---

### Post by krunge on 2011-01-10
The log file will probably tell you what is going wrong.

I suggest getting rid of -loopbg until you know what is going on.

---

### Post by Shobuz99 on 2011-01-11
> **krunge said:**
> The log file will probably tell you what is going wrong.

I suggest getting rid of -loopbg until you know what is going on.

Thank you, Karl. I appreciate your help.
BTW.. I'm not sure if I made this clear. X11vnc is a great piece of software.
I like it very much. 
It is so much better to use than WinVNC on my former windows machine.
I just want to be able to load the VNC Server the same way I did with WinVNC on my windows machine, at startup. 
No intervention. All Admin settings saved previously (including port, pw) and no fuss and no muss. 
That's why I've asked for help here. I don't want to be a pain-in-the-neck or wherever.
I will try to figure this out and I will let you know what my x11vnc.log says,
if I can't decipher it and take the appropriate action.
Thank you again, for your help.

Rick (shobuz99)

---

### Post by krunge on 2011-01-11
You can send the log to this thread if you like.  I suggest attaching it as a file instead of pasting it in.

BTW, here are some general ways to have x11vnc available at startup:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-service](http://www.karlrunge.com/x11vnc/faq.html#faq-service)
[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)  (section 'Continuously')[/INDENT]

The files you need to edit to make this happen may be distro and time dependent.

Another thing that really confuses me is you say you get a GUI or something when x11vnc starts up...  Do you have an ~/.x11vncrc file that you perhaps accidentally created via the gui?  I suggest deleting it.  Also, some distros will have a x11vnc.desktop menu item if you install x11vnc, and the  x11vnc operation mode induced by that menu item also sounds like what you describe...

---

### Post by Shobuz99 on 2011-01-12
> **krunge said:**
> You can send the log to this thread if you like.  I suggest attaching it as a file instead of pasting it in.

BTW, here are some general ways to have x11vnc available at startup:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-service](http://www.karlrunge.com/x11vnc/faq.html#faq-service)
[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)  (section 'Continuously')[/INDENT]

The files you need to edit to make this happen may be distro and time dependent.

Another thing that really confuses me is you say you get a GUI or something when x11vnc starts up...  Do you have an ~/.x11vncrc file that you perhaps accidentally created via the gui?  I suggest deleting it.  Also, some distros will have a x11vnc.desktop menu item if you install x11vnc, and the x11vnc operation mode induced by that menu item also sounds like what you describe...
Thank you, Karl. Yes, I have a file /.x11vncrc. When I installed x11vnc, I did create that file. 
I also created an alternative file called x11vncserv that was just a copy of /.x11vncrc, 
with some parms changed by me to experiment with to get x11vnc to auto-start, etc. as I explained previously.
I deleted x11vncserv and I have been editing /.x11vncrc and trying set the parms to auto start there. 
I confess that I'm not having much luck.
I think I need to clear my head, delete /.x11vncrc as you have instructed, and start all over again.
My question is, would the command line you suggest in the help for "Continuously" 
work for me with the specific parms edited to fit my machine?
What I read in the help file:
/usr/local/bin/x11vnc -rfbauth /path/to/the/vnc/passwd -o /var/log/x11vnc.log -forever -bg
Which would translate for me:
 /usr/local/bin/x11vnc -rfbauth ~/.vnc/x11vnc.pass -o ~/.vnc/x11vnc.log -forever -bg
I would be pasting the above command in the Startup Applications file for X11vnc
as is, in the command line, correct?

As to your question about the GUI. When I installed x11vnc through Synaptic Package; 
it added the command to the "Applications->internet" menu list.
It's default command is: x11vnc -gui tray=setpass -rfbport PROMPT -bg -o %%HOME/.x11vnc.log.%%VNCDISPLAY
I began using this until I decided that I was tired of the GUI screens to manually select the port#,
ultravnc option, and then go to the 2nd screen (x11vnc properties) and select "Accept Connections",
and enter a password and a "viewonly password" and then click OK.
I wanted this to all be automated and for the GUI screens to be skipped.
So, I edited the command to x11vnc -rc x11vncserv and tried using that
to startup automaticaly. It wasn't doing the trick, as I explained.
I've since deleted my logfile, through some of my own mistakes and I don't  have the original anymore;
but based on what you've told me, that may not be necessary to post, anyway.
I've been monitoring my .x11vnc.log.rick-desktop:5907 file, while I was
experimenting with the /.x11vncrc file parms.
At one point I received this error message there:
12/01/2011 10:52:39 cannot open passwdfile: "~/.vnc/x11vnc.pass"
12/01/2011 10:52:39 fopen: No such file or directory

I was also getting this error within the x11vnc properties dialog box:

"The x11vnc program failed to start! 

 Maybe there is another VNC server
 already listening on port 5907?

 You will need to start over after
 you make sure x11vnc can start."

I don't get these errors any more, after correcting some of my own mistakes. Sorry for the scattered details. 

I am going to try what you suggest above. 
I will let you know how it all turns out.

Thank you very much for your help and patience with me.
I'm an old IBM computer geek from the 1980's and I'm still getting used to Linux
after using it, instead of windows, since I started with version Ubuntu 6.10..
I'm now using Ubuntu 10.04 LTS.

Thanks again.
Rick (shobuz99)

---

### Post by justicelaw on 2011-01-12
Hi,
A solution that works for me on Kubuntu 10.04 (done this 3/4 times), Gnome should be similar, but I've never tried it.

Install x11vnc as normal on your to be headless machine
In a terminal window type

x11vnc -storepasswd

enter your password (I use the same as the user I'll login as, though that's not compulsory)
confirm your password
Accept the default location for storing the password (usually /home/username/.vnc/passwd)
Go to System Settings > Advanced > Autostart > Add Program
Navigate to X11VNC Server, & highlight it, click OK
In the Properties box that opens, switch to the Application tab, delete everything in the Command box, then insert the following

x11vnc -usepw -forever >/dev/null

Click OK to finish, close System Settings.
To make things simpler at this stage, set your user to auto-logon.
You can alter that after its working, to ake it more secure.
To test, start System Monitor, and sort by name in reverse order, then restart the machine.
Once it's up & running again, the top entry should be x11vnc, running as your user.
Now try to connect from your other machine using its VNC client.
Should be working ok.
HTH
Dave

---

### Post by Shobuz99 on 2011-01-13
> **justicelaw said:**
> Hi,
A solution that works for me on Kubuntu 10.04 (done this 3/4 times), Gnome should be similar, but I've never tried it.

Install x11vnc as normal on your to be headless machine
In a terminal window type

x11vnc -storepasswd

enter your password (I use the same as the user I'll login as, though that's not compulsory)
confirm your password
Accept the default location for storing the password (usually /home/username/.vnc/passwd)
Go to System Settings > Advanced > Autostart > Add Program
Navigate to X11VNC Server, & highlight it, click OK
In the Properties box that opens, switch to the Application tab, delete everything in the Command box, then insert the following

x11vnc -usepw -forever >/dev/null

Click OK to finish, close System Settings.
To make things simpler at this stage, set your user to auto-logon.
You can alter that after its working, to ake it more secure.
To test, start System Monitor, and sort by name in reverse order, then restart the machine.
Once it's up & running again, the top entry should be x11vnc, running as your user.
Now try to connect from your other machine using its VNC client.
Should be working ok.
HTH
Dave

Thank you Dave, but it didn't work for me.
Ubuntu 10.04 LTS is a little different than Kubuntu 10.04, I guess.

First let me explain that I'm not using a headless machine to setup X11vnc.
I don't think that matters, but I realized that you may be giving advice
to me or someone based on the original post in this forum. 
I apologize if that's the case. I've only posted here because I wanted
a method to startup x11vnc without my intervention, 
on two of the machines in my home network, and then be able to connect to either of them remote
when I'm OOT on business, or whatever.

You did help me, even so. I forgot about checking the system monitor
all this time and decided to do that. I use Htop for that, but I can sort it by
command and see if x11vnc is listed.
I tried your sequence of steps but I got a little bit different setup in Ubuntu 10.04 LTS,  as I said.
I stored the password and verified it. That was the same. 
However, my Autostart is different.
the path is: System -> Preferences -> Startup Applications
Then I added an item & called it: x11vnc startup
I removed the command I had there and edited that item's command line with what you suggested. 
I first, tried the x11vnc -usepw -forever >/dev/null
saved it, and clicked close. Restarted my machine.
Once it was finished restart, I saw no evidence that x11vnc had started.
I opened an Htop session and sorted the command column and found
no instance of x11vnc.
I went back, and changed the command line you gave,
to: x11vnc -usepw -forever >/home/rick/.vnc/passwd
I thought that pointing it to the specific password path would help. 
It did not work.
Thank you for your help and thanks for reminding me that I can use
Htop to check if x11vnc is running.
I have other issues though, yet to resolve.

Thanks again,
Rick (Shobuz99)

---

### Post by Shobuz99 on 2011-01-13
Karl, Dave et al,

Thanks to you, I got it working basically the way I want.
I discovered one weird thing about x11vnc that may not be the reason;
but when I used it everything started to work. 
The command that I ended up using in the "Startup Applications"
in my x11vnc startup item is:

x11vnc -rfbversion 3.6 -rfbport 5907 -rfbauth /home/rick/.vnc/passwd -forever -bg

Prior to this, I did not use rfbversion and the 3.6 argument.
I could not get x11vnc to load with the following command:

x11vnc -rfbauth /home/rick/.vnc/passwd -forever -bg

It never worked.
I added in the rfbport 5907 switch but it would not connect.
Then I began looking at a saved xsession-errors log and discovered
that when I was using the /.x11vncrc file while using the GUI, that
it always loaded the version 3.6. In some cases it would load it twice.
I don't know why.
So I went back to my command line and added the -rfbversion 3.6 
and -rfbport 5907 switches and it connected.
I checked my Htop command, sorted so x11vnc was on top, and there it was.
Next I went to my other machine and tried the SSL/SSH VNC Viewer
to connect to the first machine. It worked.
I'm still not sure why it won't connect unless I use the -rfbversion 3.6 switch.

Anyway, thank you all for all your help.
My next question would be is there a switch that would put the icon or the tray symbol up so I know it's connected? No big deal, I just wondered.
I can still check it out using the other machine or make sure it loaded
by viewing Htop and sort the commands so that x11vnc is on top.
If it's there, it means I'm all set.

Update/Edit: I also needed to add the -ultrafilexfer switch so i could transfer files. The whole command is now set as follows:
x11vnc -rfbversion 3.6 -rfbport 5909 -ultrafilexfer -rfbauth /home/rick/.vnc/passwd  -o /home/rick/.vnc/x11vnc.log -forever -b

Thank you once again for all your help.
Rick (Shobuz99)

---

### Post by justdave68 on 2011-06-08
Rick, thank you very much for following up with what worked for you. I also needed to add the -rfbversion flag to get it to work.

The flag to add the icon is "-gui tray" (without the quotes). When I use that flag starting x11vnc at bootup, I get an error message "Error: tail: cannot watch '/tmp/x11vnc.tray.******'" where ****** is a random string. However, x11vnc still works fine, and if I launch it manually (not in the autostart) I do not get the error. 

Karl, thank you very much for the great software, and for your ongoing involvement and help here in the newbie forums.

Best regards and thanks again,
Dave

---

### Post by krunge on 2011-06-08
I believe the problem "Error: tail: cannot watch '/tmp/x11vnc.tray...." is fixed in the development version of x11vnc (0.9.13)

---

### Post by justdave68 on 2011-06-09
Thanks Karl, I will give that a try when I get a chance.

---

### Post by mcapri76 on 2013-04-10
Folks this is a really cracking thread, Thanks.

In the end this is what worked for me: x11vnc -rfbversion 3.6 -rfbport 5907 -rfbauth /home/rick/.vnc/passwd -forever -bg

One problem is when I set the command in 'Startup applications' it does not work, the only way to make it work is to manually sudo su and try again.
I followed a guide to run x11vnc as root (sudo visudo) but it did not work. Any idea?

---

### Post by oldos2er on 2013-04-10
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

