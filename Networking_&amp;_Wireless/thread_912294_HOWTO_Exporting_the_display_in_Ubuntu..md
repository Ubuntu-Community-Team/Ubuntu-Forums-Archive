---
title: "HOWTO: Exporting the display in Ubuntu."
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by Gnea on 2008-09-06
[SIZE="4"][COLOR="Red"]***Disclaimer:* This method is the kind that just plain works.  It could be made more secure.  If you have any advice on the subject, please reply below and I will, over time, improve this howto.**[/COLOR]

Okay, so you've got your shiny new Ubuntu server all setup.  But it doesn't have a GUI.  That is no problem, since you've got Ubuntu (or some variant of Ubuntu or Linux) running on your desktop or portable system already.  However, there are a few steps that you need to take before everything will "just work".

:popcorn:

[COLOR="Blue"]First of all, this document works on the assumption that you are connecting to your server using either a secured lan or wireless method.  _At the time of writing, Ubuntu 8.04.1 'Hardy Herring' was the latest stable release being used._  By "secured wireless" method, either using something like WPA or OpenVPN to encrypt your communication across wireless links.  Such configuration is beyond the scope of this document and it is up to you to make sure that no one can mess your remote display connection up![/COLOR]

So, let's say that you have your server installed and booted up and running like a champ.  You've named it, got it to connect to the internet, got the firewall setup, have some services running.  You've got more than 1 NIC card and have even setup a private network.  You can remotely connect via SSH and configure things.

But now, you're starting to wish that you could run zenmap instead of just nmap so that you can secure your network a little easier.  There are a number of GUI applications that you'd like to run, but Server does not have a GUI!  This is where we solve that problem: by running GUI applications without a GUI, over the network.

First of all, install your GUI program on the server:
```
gnea@server:~$ sudo apt-get install zenmap
```

If all goes well, it will ask you to install some dependencies.  Some of them are probably going to be some X-related libraries.  Go ahead and allow these by saying [Y]es.  This won't actually install X on your server, only the library files required to display the program that you're installing.  This is important, because it means that it won't take up nearly as much hard drive space (usually less than 3-5 megabytes).

Next, you need to make sure that your desktop system is ready to accept remote connections.  There are two ways to do this:  The insecure way, and the secure way.  Both methods will be discussed here, since both have their merits and pitfalls.

***[COLOR="Purple"]The Insecure Method: Xhost[/COLOR]***

This is, by far, the easiest method to use, since it involves minimal work to get up and running.  Unfortunately, it makes it easier for others to sniff your connection and obtain private information.  However, if you're network is setup correctly, you won't have to worry about it.

On the desktop end, you will need to tell the Xserver to allow remote connections.  This has 2 steps.  The first involves clicking on System->Administration->Login Window, entering your password, and clicking on the '[COLOR="Lime"]Security[/COLOR]' tab.  The option that you will need to find is called "[COLOR="Teal"]Deny TCP connections to Xserver[/COLOR]".  It is likely already checkmarked.  Click on it so that it is un-checked.  This will open up tcp port 6000 into LISTEN mode.  [COLOR="Red"]Please adjust your firewall accordingly[/COLOR].

[IMG]http://garson.org/~gnea/image/xhost_gdm.jpg[/IMG]

Now, you will need to restart X.  Simply press the ctrl-alt-backspace keys together, or simply restart the system.

Finally, you cannot connect to the system yet, you will need to authorize it to happen with the *xhost* command, telling it the name of the remote system that can connect.

```
gnea@desktop:~$ xhost +server
server being added to access control list
gnea@desktop:~$
```

Now, go back to your server terminal window, and tell it which system to export the display of the GUI to:

```
gnea@server:~$ export DISPLAY="desktop:0.0"
gnea@server:~$
```

Finally, type the name of the GUI command you wish to see on the remote end and watch it display on your desktop:

```
gnea@server:~$ zenmap
```

You will note the appearance of the [COLOR="Red"](on server)[/COLOR] to let you know that the application is displaying on your system, but actually running on your remote server.  This is very important if you decide to open and save files, as they will open and save on the remote server, NOT on your desktop!

[IMG]http://garson.org/~gnea/image/zenmap-remote.jpg[/IMG]

And that's it! :guitar:

***[COLOR="Purple"]The Secure Method: Xauth[/COLOR]***

*SEE THE NEXT REVISION BELOW!*
TODO: link add-in: [http://www.xs4all.nl/~zweije/xauth-6.html#ss6.2]("http://www.xs4all.nl/~zweije/xauth-6.html#ss6.2")

[/SIZE]

---

