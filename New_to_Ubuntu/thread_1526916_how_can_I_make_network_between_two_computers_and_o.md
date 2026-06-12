---
title: "how can I make network between two computers and one monitor ?"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by medya on 2010-07-08
hey Guys ,  I have two computers and one Monitor, 

the second computer is in another room, and it doesnt have a monitor, 
whenver I wanna use it, [I usualy use it to download big files] I plug a monitor to it .

I wanna know is there any way to see the Second computer 's screen in my First computer's monitor with a networking ?

I never made a network between two computers .

do I have to buy a monitor for the second computer too ? 

I use ubuntu Lucid , 
your suggestions would be greatly apperciated .

---

### Post by linux-hack on 2010-07-08
why not just use VNC ? This way you can use bouth computers from on.. Or you could buy a KVM switch so that you can use bouth computers with just one monitor, keyboard and mouse. I don't rely know if you can see the screen on the network and don't know if that is possible...

---

### Post by lisati on 2010-07-08
If the computers were physically closer, one option might be a [KVM switc]("http://en.wikipedia.org/wiki/KVM_switch")h of some kind. 

Another option is to use [SSH]("https://help.ubuntu.com/community/SSH").

---

### Post by medya on 2010-07-08
> **boogy9 said:**
> why not just use VNC ? This way you can use bouth computers from on.. Or you could buy a KVM switch so that you can use bouth computers with just one monitor, keyboard and mouse. I don't rely know if you can see the screen on the network and don't know if that is possible...

the other computer is in another room, if I buy a KVM, it has to have a long wire ...

and I dont wanna use internet bandwith to make connection between two computers, I wanna use network . [I have slow internet connection]

---

### Post by linux-hack on 2010-07-08
or something like this may be ???

[http://www.linuxjournal.com/content/2-computers-1-keyboard-mouse](http://www.linuxjournal.com/content/2-computers-1-keyboard-mouse)

---

### Post by medya on 2010-07-08
so in networking , there is no way for admin to see the screen of users and control them ?

---

### Post by linux-hack on 2010-07-08
> **medya said:**
> so in networking , there is no way for admin to see the screen of users and control them ?

Yes there is VNC :lolflag: and many orher tools ... like this one : [http://www.nchsoftware.com/screen/index.html](http://www.nchsoftware.com/screen/index.html)

But the best way is to use VNC with SSH

---

### Post by spiky001 on 2010-07-08
there is remote desktop system preferences remote desktop you can set it up so you can view the other pc and even control it from your 1

---

### Post by medya on 2010-07-08
Guys , do I need to use internet for " remote desktop system" or  "VNC"  ?

do they work under LAN or WLAN ?

---

### Post by spiky001 on 2010-07-08
no it,s a straight connction between the 2 pc,s as long as there are on the same network no injternet required even if you transfer files from 1 pc to the other

---

### Post by Paddy Landau on 2010-07-08
You will tell VNC your local IP address. It will use your network.

---

### Post by linux-hack on 2010-07-08
Ok here is a rely nice thing to try :D 

[http://www.youtube.com/watch?v=BSYmajttVDw&playnext_from=TL&videos=Ejh492X21TI&feature=sub](http://www.youtube.com/watch?v=BSYmajttVDw&playnext_from=TL&videos=Ejh492X21TI&feature=sub)

---

### Post by xpod on 2010-07-08
> **boogy9 said:**
> or something like this may be ???

[http://www.linuxjournal.com/content/2-computers-1-keyboard-mouse](http://www.linuxjournal.com/content/2-computers-1-keyboard-mouse)

Synergy is actually used over multiple computers & their screens but the OP only has the one screen. 
It turns all your computers screens into the one big virtual screen that you can control with just the one mouse & keyboard.

I do like the copy/pasting from one computer across to the other with it.

---

### Post by medya on 2010-07-08
Synergy looks very nice, the problem is I have just one LAN ethernet , and I use it for internet , 
does Synergy work with Wireless LAN ?  I am thinking about buying a Wireles Lan card

---

### Post by xpod on 2010-07-09
> **medya said:**
> Synergy looks very nice, the problem is I have just one LAN ethernet , and I use it for internet , 
does Synergy work with Wireless LAN ?  I am thinking about buying a Wireles Lan card

As i said in my previous post you only have one monitor according to your own opening post so Synergy aint much use to you with your current setup.

[http://synergy2.sourceforge.net/about.html](http://synergy2.sourceforge.net/about.html)

If you did have screens for each computer though then Synergy should work with your networked machines regardless of whether it`s wired or wireless.

---

### Post by audiomick on 2010-07-09
xpod is right: synergy is not what you want. I use synergy, and love it. What it is for is using one mouse and keyboard across the monitors of more than one computer, so it is not the solution you need.

You seem to not be clear about the distinction between a network and the internet.

When you connect 2 or more computers via an ethernet
[http://en.wikipedia.org/wiki/Ethernet](http://en.wikipedia.org/wiki/Ethernet)
you have established a network. This is something that does not automatically mean you have internet access. When you establish an internet connection, it runs through your network, but communication between two local computers (i.e. in your case the computer with the monitor and the one without) do not go via the internet. The speed of transmission between local computers is determined by the slowest LAN / WLAN connection in those computers, and has nothing to do with your internet bandwidth.

I think the suggestion to use VNC via SSH is your best bet. This should work via a WLAN connection between your 2 computers.

---

### Post by linux-hack on 2010-07-09
take a look at this : [http://www.tuxien.org/tutos/linux-tutos/fun-xnest-howto/](http://www.tuxien.org/tutos/linux-tutos/fun-xnest-howto/)

and I found a new software that can be rely nice (x2x)
[http://www.youtube.com/watch?gl=US&v=90RIRmGhjiw](http://www.youtube.com/watch?gl=US&v=90RIRmGhjiw)

---

### Post by steveneddy on 2010-07-09
If it's simply at your home, just use Remote Desktop under Preferences.

Hook a monitor up to the remote just once and open Remote Desktop and give permission to view and control the desktop - and give it a password so you must enter a password to see the remote desktop.

Get the local IP address of the remote PC while you have the monitor up.

Should be something like - 192.168.0.2 or something like that.

Unhook the monitor and go to the other machine and try and connect. You should be able to access your remote machine in another room easily now and work "remotely" anytime that you wish.

---

