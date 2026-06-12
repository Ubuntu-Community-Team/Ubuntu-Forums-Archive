---
title: "Initiating a VNC reverse connection to throw desktop to a central computer over SSH"
date: 2020-05-13
forum: Networking &amp; Wireless
---

### Post by m-j-malone on 2020-05-13
OK, I am using VNC, specifically x11vnc on the computer throwing its monitor desktop screen and xtightvncviewer on the machine catching the monitor screen desktop.  I am unable to figure out the proper sequence of commands to make the throwing computer initiate the SSH channel.   

The application is, I want to deploy a computer to a relative on cable internet connection with no public IP address.   I want them to be able to use the computer, but if they get stuck, I want to be able to walk to my server that does have a public IP address and catch their screen and navigate for them to solve their problem.   Physically going to the computer is not an option -- it is prohibited by quarantine and will be until Covi-19 is completely gone.  I need the deployed computer to take care of initiating the throwing of the monitor desktop screen because it may be on a private network with no NAT and it is the only one that knows the fixed IP address of the other.    I cannot rely on the user to type any commands, or click anything -- that is what they are typically having problems with and what I want to do for them so I do not have to puzzle through with a bunch of questions what they see on their screen.  If anyone has done computer support for an elder relative over the telephone, you know half the frustration is figuring out what is on their screen with only elder descriptions.

I say "monitor desktop screen" to be specific.  Naturally Ubuntu can make up a new desktop virtual screen and throw that, but that is not what I want.  I want to see what they see.   Trial and error with xtightvncserver seemed like it could only throw virtual desktops, not the one that is also displayed on the monitor.   x11vnc will throw either, and it throws the monitor desktop by default.

I am using SSH because I want the connection to be secure.   


Now I will show the proper way to do all other other types of screen sharing I do not want to do:


Ask a Remote Computer to Send a Virtual Desktop Over SSH
===============================================


I use this to access my digitalocean droplet, a public server that is in fact headless -- it has no monitor on it.   I SSH to the digitalocean droplet, install and start an xtightvncserver using this reference:  _*[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04)*_   This part is a one-time prep.

Following those instructions, each time I want to check in on my droplet, I open one terminal window on my local computer and type:

 ```
ssh -L 5901:127.0.0.1:5901 -C -N -l ***login_name***   ***digitalocean_droplet_IP***
```

and log in.  I then open a second terminal window on my local computer and type: 


```
 vncviewer localhost:5901


```

A window appears in which there is a complete desktop onto my droplet.   My digital ocean droplet has a fixed IP, so, I have no problem scripting this.  It is headless, so there is only an option to ask for a virtual desktop.   Working from a remote computer, working through an SSH tunnel, I can pop open a window that is a virtual desktop on the droplet at any time.  

It would work for any computer that has a fixed, public IP address, and server.   This does not display the same desktop as one would see on the monitor if they were to sit in front of the remote computer.   If I open an application on my virtual desktop, it is like the computer has two monitors, one I am working on, and the one displayed to someone sitting in front of it.  If I move the mouse, click or type, only I see the virtual desktop.  The person sitting in front of the screen sees only the desktop displayed on the physical monitor.   The instructions involve the xfce desktop interface which is a lot lighter than Gnome.   Hint the Applications menu is under the right mouse button.


Ask a Remote Computer to Send the Same Desktop as is Displayed on its Monitor Over SSH
========================================================================

This time, I am accessing a physical computer that has a monitor, and a native desktop, a server in another location.  I want to remote sysadmin it.   I use these instructions: _*[https://linuxconfig.org/how-to-share-your-desktop-in-linux-using-x11vnc](https://linuxconfig.org/how-to-share-your-desktop-in-linux-using-x11vnc)*_  I first install x11vnc on the remote server according to those instructions, and tightvncviewer on my local computer.  These are one-time installs.   

Following those instructions, each time I want to check what is going on on my server's desktop screen, I open one terminal window on my local computer and type:

```
 ssh -t -L 5900:localhost:5900 192.168.0.38 'x11vnc -localhost'


```


And complete the login process.   Then I open a second terminal window on my local computer and type:

```
 vncviewer localhost::5900


```
A window appears in which there is the complete desktop for my server, the exact same desktop that another person would see if they were sitting in front of the server when I access it.  If I move my mouse, click, or type, the person sitting in front of the server spectating sees exactly what I see.  My server has a fixed IP (via NAT / port forwarding) so I have no problem  scripting this.    


A Computer Throws The Desktop Displayed on its Monitor to A Remote Computer That Catches It -- not using SSH
========================================================================================

This is totally unsafe to use over the open internet.  I have tested it only within my LAN, and have been trying to modify it to use SSH to no success.   I have gotten the previous methods to work both within my LAN and to digitalocean.   In this method, one uses this reference:  _*[https://caedesnotes.wordpress.com/2010/01/08/remote-administrationtech-support-with-reverse-vnc/](https://caedesnotes.wordpress.com/2010/01/08/remote-administrationtech-support-with-reverse-vnc/)*_, the second method for "reverse" VNC.  

The computer wanting to catch the desktop that is thrown to it, has to enter this into a terminal window:

```
vncviewer -listen
```

The receiving computer is now listening, ready to catch.   The computer wanting to throw its desktop has to execute this in a terminal window:

```
x11vnc -connect ***receiving_server_ip***
```

This is a process than can be automated with automatic scripts to re-listen and re-connect at each end when the connection is dropped.    The only problem is, SSH is not being used and this is very unsecure over the open internet.   

What I need is a way for the throwing computer (not the catching computer) to initiate the SSH tunnel and then tell x11vnc to send its packets down that tunnel.  I have tried it every which way I can think of and it just does not work.   In all other examples, the receiving computer is the one to initiate the SSH tunnel and that will not work in my application because of the cable internet and local network on the end were the computer throwing its desktop is located.   I am hoping it is something simple with options on the SSH command.

---

