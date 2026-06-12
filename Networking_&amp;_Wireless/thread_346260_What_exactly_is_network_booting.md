---
title: "What exactly is network booting?"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by elreteipos on 2007-01-25
What exactly is network booting? Does it allow you to let multiple people use the same Ubuntu PC simultaneously?

---

### Post by koenn on 2007-01-25
> **elreteipos said:**
> What exactly is network booting? 
The usual way to boot is from a disk - the disk contains "boot code" in the "Master Boot Record". With Network booting, the computer executes "boot code" from a chip on the network card, then connects to a server to download an operating system to its memory, and continues to boot and run that operating system. 

> **elreteipos said:**
> Does it allow you to let multiple people use the same Ubuntu PC simultaneously?
not really. It allows you to boot a diskless computers - thin clients, terminals, ...
It does, in a way, allow multiple people to use the same computer simultaneously. Edubuntu is set up to work that way, but there numerous other uways to use network boot

However, those multiple people still need something that has a keyboard, a monitor, a network card, some memory,  and so on.

---

### Post by elreteipos on 2007-01-25
Alright, then I guess network booting is not what I was looking for.

I have two PCs: the first one is running a Windows/Ubuntu dual boot and the second one is only running Windows. Is there a way to use the same Ubuntu installation on both computers simultaniously?

[Dutch]
Met andere woorden: is het mogelijk om eenzelfde Ubuntu-installatie te gebruiken op verschillende computers tegelijk, zonder dat de gebruikers elkaar onder de voeten lopen? Ik doel dus niet op een VNC-oplossing.
[/Dutch]

---

### Post by koenn on 2007-01-25
Look at it this way:
asume the dual boot machine ("computer_1") is running ubuntu  (and let someone log in : that's 1 person using that computer)
assume you connect, from a 2nd computer, to the dual bootmachie, eg with telnet or ssh. What you get is a command prompt on **computer_1**. If you run a program from that command line, it would execute on computer_1, eg if you ls -al /etc, you'd get a directory listing of /etc on the computer_1 ubuntu. If you compine source code from /home/gearge/myproject, the compiler would be executed by computer_1 and the source coude would come from computer_1. The only thing happening on computer 2 is keyboard activity and screen output - sort of. 
(From a Windows machine, you could use a terminal emulator such as putty to do this)

Obviously, this can be done from multiple other pc's as well, simultanously, so you can have lots of people using the same machine.

So, yes, you can have multiple people use the same machine. 
You're probably interested in GUI/desktop applications. That is possible to. In principle / concept it is the same as the command line example above, but its a bit more complix to implement because in stead of sending plain text back to computer 2, you'd have to send back a complete gnome desktop. It believe it is possible with Xserver and socalled "X-clients" for Windows but I haven't really looked in to it so I can't help you much further. 

You could also try to use the Microsoft  Remote Desktop Client to connect to the desktop of computer_1

I'm not really sure how this would be different (in user experience) from a vnc sollution. Why do you say you don't want something vnc-like ?

---

### Post by elreteipos on 2007-01-26
VNC allows you to operate the host's desktop remotely. Both the host PC and the VNC program on the guest PC show the same picture and desktop.

That's not what I want. This method doesn't allow two people to work on the same computer simultaneously.

How is the thing called you were describing? *(dan kan ik misschien wat research doen op Google)*

---

### Post by koenn on 2007-01-26
some more theory (as i don't know howt to actually *do* it  - any one else here reading this, feel free to jump in and add on)

On your Linux systeme, there is software called _X-windows server_ (_Xorg_) that generates a thing called "display". Usually, on a desktop machine, you only start 1 display, which is then used by Gnome (or an other desktop environment) to produce whatever it is you see on your screen. 
The interesting part is that, unlike Microsoft Windows, X can produce _multiple displays_. If you run the following command : you'll see that your display is in fact display :0.0 ; you can add more displays (which will get different numbers) and have others use those for their desktop, even on a _remote_ machine. 
```
kn@knix:~$ echo $DISPLAY
:0.0

```

Now, to be able to connect to those X-"displays" over a network, you need a "client", and since you want to do this from a Windows system, you need aan _X-client for windows_. a VNC client can act as such an x-client for windows, because x-server offers multiple displays (called "screens" in vnc, i think) and you can tell the vnc client which "screen" it should connect to. This is different if you vnc ***to***  a Windows machine, because Windows does not support miltiple screens (except maybe with Terminal Server). Anyway, that's beside the point, as you want top connect to a Linux system. 
Here's an example  : [http://www.vncrobot.com/docs/v1.3/gui/viewer.html](http://www.vncrobot.com/docs/v1.3/gui/viewer.html) 
> Unix/Linux - Unix like systems running X-Windows are capable of running multiple window servers. Number of your display actually depends on the number of VNC server instances running on your machine. If you for example start the VNC server three times on a test machine called mymachine, there will be three independent remote desktops available at mymachine:1,mymachine:2 and mymachine:3.

For further research, you could google with (combinations of) the words i underlined; I 'd recommend [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System) as a general introduction and as a source of links or keywords you could use in Google.

I'm not entirely sure all of this is enough to actually create a complete desktop - it should however be enough to start and run GUI applications on a remote machine, as shown here :  [http://ugweb.cs.ualberta.ca/howtos/XForwarding/index.html](http://ugweb.cs.ualberta.ca/howtos/XForwarding/index.html). (the exemple they use can be misleading, because emacs only shows text. but note the typical titlebar on the window it is running in : it's really running in a window on Windows.
This should allow you to run Ubuntu applications (firefox, gimp, gnometris, ...) in a window on the windows machine.


An other thing you could investigate is _XDMCP_ - this should allow for multiple, remote gnome desktops, if i understand correctly (but i could be wrong).
Again, you could start at wikipedia and take it from there : [http://en.wikipedia.org/wiki/X_display_manager](http://en.wikipedia.org/wiki/X_display_manager)

You might have to combine a few things, eg _Xforwarding _+ _gdm_ +_ xdmcp_ ... I really don't know. 
There even could be a very simple application that does all of this without any trouble. If you find it, let me know  :)

have fun

---

### Post by koenn on 2007-01-27
someone else here is trying something similar : 
[http://www.ubuntuforums.org/showthread.php?t=347163](http://www.ubuntuforums.org/showthread.php?t=347163)
looks promising

---

### Post by elreteipos on 2007-01-28
I'll take a look at that.

I think I found what you were describing here:> It does, in a way, allow multiple people to use the same computer simultaneously. Edubuntu is set up to work that way, but there numerous other uways to use network bootTake a look at this: [https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

It looks rather complicated, so I don't really understand what they're describing. Do you think that's what I need?

**Update:** [this]("http://www.nomachine.com/") looks interesting too...

---

### Post by koenn on 2007-01-28
The ThinClientHowto is what I explained earlier - it's a combination of multiple X  sessions (that's what you want) with network boot (so the clients don't need hard disks and operating systems ). Edubuntu takes it 1 step firther and provides a "chroot jail" on top of that, a mechanism to keep (remote) users out of the main system by giving them a dedicated folder that looks like a complete filesystem to them, but isn't really.

---

