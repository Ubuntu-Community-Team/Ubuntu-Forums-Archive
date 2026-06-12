---
title: "Is it possible to display a desktop computer harddrive onto a laptop screen?"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-04-20
My desktop has XP and my laptop has lubuntu. I tried using the black monitor cable to connect my desktop to my laptop, and turned both computers on, but I got a screen on my desktop that said infinite loop error. My laptop did not recognize the connection.

---

### Post by An Sanct on 2011-04-20
WOW!!!!!

Slow down!

Does it look like this???
[IMG]http://www.idealtec.net/zstore/images/cable-vga-m-m.gif[/IMG]
If yes, that is wrong, that is no way to connect two computers, you could have burned both of them!

---

### Post by brawnypandora0 on 2011-04-20
Yes, it looks like that...I don't know what it's called.

I could have harmed my computer? Why? Which part?

---

### Post by An Sanct on 2011-04-20
That is not a computer to computer connection cable, It is a cable for graphical output, not originally designed to communicate "two ways".

If both machines still work okay, then nothing is broken ;)

Take a look at both computers (if you would specify which they are, I could tell you right away). Find something like this:
[IMG]http://www.zytrax.com/images/rj45_top_front.gif[/IMG]
(left the cable connector, right the port on the machine), This is normal LAN, designed for networking.

---

### Post by brawnypandora0 on 2011-04-20
But why would it cause "burning"? Is there a more scientific explanation instead of "burning"?

---

### Post by An Sanct on 2011-04-20
The scientific explanation would be: "unwanted voltage/current, where it is not expected" - thus burning.

To connect two computers, use [network hardware]("http://en.wikipedia.org/wiki/Networking_hardware"), appropriate for networking (in your case, sharing of discs/drives).

---

### Post by Blasphemist on 2011-04-20
Time out a moment. How do these machines connect to the internet? What exactly would you like to do? Are you needing access to files on one machine to be available to the other? Just what is your need?

If both of these machines already have access to the internet through the same connection such as a router, you already have network hardware and software installed and working. It sounds like either there is confusion here or your understanding of computer interaction is incomplete. Is it possible all you really want to do is share a monitor? There are switches available to let you connect one monitor to two machines but what they accomplish is to make the connection to the monitor to only one machine at a time. They allow you to do this without having to keep changing physical cable connections.

---

### Post by An Sanct on 2011-04-20
hm .. looking at the first post here ...

"*I tried using the black monitor cable to connect my desktop to my laptop*"

Told me to warn him about that ... and no networking hardware is mentioned, just the wish to share the disk in the netbook to the desktop with: "**Is it possible to display a desktop computer harddrive onto a laptop screen?**" (being the topic here ...)

---

### Post by brawnypandora0 on 2011-07-03
> **Blasphemist said:**
> Time out a moment. How do these machines connect to the internet? What exactly would you like to do? Are you needing access to files on one machine to be available to the other? Just what is your need?

If both of these machines already have access to the internet through the same connection such as a router, you already have network hardware and software installed and working. It sounds like either there is confusion here or your understanding of computer interaction is incomplete. Is it possible all you really want to do is share a monitor? There are switches available to let you connect one monitor to two machines but what they accomplish is to make the connection to the monitor to only one machine at a time. They allow you to do this without having to keep changing physical cable connections.

But what does the same Internet router connection have anything to do with what is on my desktop harddrive? I want to display (not transfer) a video on my desktop harddrive using my laptop screen. So is there another cable I'm supposed to use?

---

### Post by wep940 on 2011-07-04
A couple of notes:

(1)  You most definitely could have done irreparable harm to both computers with that cable - including yes a small fire.  DO NOT DO THIS AGAIN.

(2)  How you are connecting to the internet is very important here.  Why?  If both machines connect wirelessly to the net via a router, you don't need any cable connection between the 2 computers.  You can do it just by sharing the drive on the desktop and setting up a share on the laptop.  No cables, no hassle, can do when ever you need to.  This then becomes a network-shared drive, so yes you will be able to see the drive and its' contents on your laptop.

IF, however, you are trying to use the desktop computers' hard drive as the boot device for your laptop, that won't be the case.


SO........


[LIST]
[*]specify what you mean by "see the hard drive on the laptop screen"
[*]specify how you connect to the internet with both computers
[/LIST]

We really need this information.  And PLEASE, don't go plugging anymore cables into either PC without asking first what they are for and if they will work for what you want to do.  Failure to do so could result in a very expensive lesson - by ruining both computers.

---

### Post by rosencrantz on 2011-07-04
You have two kinds of sockets in your setup: the one on the graphics card outputting the screen information and one at the back of your desktop monitor inputting the data.
Your laptop screen has no external input, so it's impossible to use it as an external screen for another device. It sounds as if you tried to connect the output sockets of your two computers' graphics cards which is not going to work.
What the other posters suggested was hooking both computers up to the internet and connecting e.g. via desktop sharing ([https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)).
If you don't have an internet connection, you can create a mini-network with a crossover cable ([http://arstechnica.com/civis/viewtopic.php?f=10&t=703172](http://arstechnica.com/civis/viewtopic.php?f=10&t=703172)). That's a special cable with slightly different wiring from a standard ethernet cable, you should be able to get it in any electronics shop.

---

### Post by wep940 on 2011-07-04
Doesn't even involve desktop sharing - simply sharing the hard disk in question.  And....that's all on the internal side of the router - the local network.  Doesn't go to the internet and back - simply shares the device via the router connections. 

Like a Windows network drive and perhaps samba on the linux side to see the drive.;)

---

### Post by brawnypandora0 on 2011-07-04
> **wep940 said:**
> Doesn't even involve desktop sharing - simply sharing the hard disk in question.  And....that's all on the internal side of the router - the local network.  Doesn't go to the internet and back - simply shares the device via the router connections. ;)

My desktop is XP and my laptop is Ubuntu. What software do I need to do that?

---

### Post by brawnypandora0 on 2011-07-04
Is this really the right website for me to do this?

[https://help.ubuntu.com/community/VNC#accessing-family-pc](https://help.ubuntu.com/community/VNC#accessing-family-pc)

Which section am I supposed to follow?

---

### Post by wep940 on 2011-07-04
No - you shouldn't need VLC at all.  I'm not sure of the exact steps - but I could test them out by booting my desktop in Windows then sharing it in Linux on my laptop.  I've seen this done a lot of times, just not positive on the individual things to do.  So......if you can wait a little while I'll try it here and when I get it to work I'll post back.  Also - is the C: drive of your desktop?  If so, may need to share just the one folder so the whole drive isn't visible to the net.

---

### Post by wep940 on 2011-07-04
Well, don't let my problems make you think this isn't the way - I'm just messing up somewhere so I haven't gotten this to work yet.

I *thought* I just needed to do the following:


[LIST]
[*]in Windows, using Windows Explorer, highlight the folder you want to share
[*]right-click and select sharing options
[*]click the open dot that allows sharing the folder (if you want write access to it, you need to also check the dot below that)
[*]on the Ubuntu box, using places, go to and click on "Network"
[*]double-click on the windows network icon
[*]the folder should show (mine doesn't - so I must be doing something wrong)
[/LIST]

I'm going to search the forum until I either find the answer or else open a thread asking about this, then I'll get back to you.  I know you're a novice, so I'm trying to find the easiest way and then try to explain it in simpler terms.

---

### Post by rosencrantz on 2011-07-04
*VNC*. VLC is a media player ;-)
OK, it was a bit late last night, so I didn't read the OP's post very thoroughly. 
If you just want to access a Windows shared folder on a Linux machine, how about a Samba client on the Linux side?
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)
All you require is both machines being in the same local network.

---

### Post by wep940 on 2011-07-05
Yes, as I mentioned in my previous post, you should just need to enable the Windows share. However, there are a couple of things I ran into:
[LIST]
[*]BTW - the smbclient is already installed by the Ubuntu installation process. The smbclient is what allows Linux/Ubuntu to see Windows shares on the network
[*]I had to edit the /etc/samba/sbm.conf file as follows:
[LIST]
[*]From a terminal window (applications/accessories/terminal), type: sudo gedit /etc/samba/sbm.conf
[*]This opens the /etc/samba/sbm.conf file in an editor
[*]look down just a few lines into that file for a line that says "workgroup = WORKGROUP". Change it to "workgroup = MSHOME" (unless you changed the default workgroup on your Windows machine).
[*]click "save". When the save finishes, close the editor
[/LIST]
 
[*]Restart the Ubuntu machine (easiest way to reset smbclient to use the newly updated /etc/samba/smb.conf file)
[/LIST]
Now, this is the biggest thing I ran into and am still looking for the solution (which will be simple, I just need to find out):
[LIST]
[*]The firewall I'm using on my Windows machine is ZoneAlarm. Turns out Zonealarm is somehow blocking the Windows shares from being shown on the intranet. I had to enable the Windows Firewall and shutdown ZoneAlarm.
[/LIST]
Now, on the Windows machine, open up Windows Explorer and click on the drive that contains the file you want to share. Go to the folder in which the file you want to share is, right-click on the folder, then click on properties. Click on the Sharing tab. Click on the circle for sharing the file or folder and if you also want write access to it click on the circle below that. Put a short name in the share name - as an example my test is using "daves_junk" as the share name.
 
 

Now go to the Ubuntu machine and do the following:
[LIST]
[*]Click on "Places"
[*]Click on "Network".
[*]Click on "Windows Network"
[*]Click on "MSHOME"
[*]You should now see a list of your Windows shares - look for the name you gave for the share name for the folder you are sharing. Click on it to open it.
[/LIST]
rosencrantz - thanks for the correction. I knew it was VNC but sure typed in the wrong thing! ;)

EDIT:  forgot to mention - once you have the share open, it will show as just another folder on your PC.  You can open your movie player on the laptop and open the movie in the share.

EDIT-EDIT:  Jeez, forgot one other thing - you need to be sure your Windows box can see its own shares on the network.  Open up Windows Explorer, go to Network Places and expand it.  There should be an entry for Microsoft Windows network, and it should show your Windows share if you click on it.  If not, post back and we can walk you through enabling it.

---

