---
title: "What do I need to install to run &quot;firefox&amp;&quot; via SSH?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by TMcKSmith on 2009-01-30
I just installed Ubuntu Server on my home server.
I've had a server before but it was bloated with a lot of things, like a desktop.
What do I need to install to be able to SSH into the server and run "firefox&" (besides Firefox obviously) so it will open up a firefox window from the server remotely?

I guess this just doesn't apply to firefox - but to any app.  Do I NEED a desktop on my server in order for this to be possible??

I'd like to install the very least amount of packages needed.

Thanks.

---

### Post by Hospadar on 2009-01-30
well a couple things, on the server, you need to install firefox since it doesn't come with server out of the box
```
 sudo apt-get install firefox
```Then, if you are ssh-ing from a linux machine, you have to add a command line option to ssh to enable X11 forwarding, this allows you to get graphical windows remotely.
So let's say I get into my machine with:```
ssh myusername@mymachine
```i need to add a -Y to get X11 forwarded```
ssh -Y myusername@mymachine
```then you can just log in and run firefox.

If you are logging in from a windows machine, you can install a windows x server like xming or the cygwin X server (I use Xming). and you'll have to enable X11 forwarding in whatever ssh client you use.  I use putty, when you're starting a connection, scroll down to "tunneling" and "X11" and there's a checkbox for forwarding.  Make sure you actually start the X server (xming) before  you try to use it.

That's really all you need.  You can run any other applications off your server the same way.  just install the app you want on the server and go for it (good suggestions include installing a file browser like thunar on your server for convenient management, or installing synaptic if you don't like using apt-get from the command line)

EDIT:
It didn't occur to me that maybe you don't have ssh all working great already, it comes installed on servers by default, but if you just want to check, to install it you would do ```
sudo apt-get install ssh
``` and then to connect (from a different linux machine) ```
ssh your-username-on-the-server@ip-address-or-domain-name-of-server
``` with a -Y as above if you want X11.  If you don't know the IP of your server, run "ifconfig" at the server to find out all about your server's internet connection.

If you want to connect from outside your home network (assuming you use a router), you'll need to forward port 22 to your server, and figure out what your external IP is, a quick way is to run something like ```
curl -s whatismyip.org
``` from your server, then use that ip address in your ssh command to connect to your server.  You will probably also want to set up your router so your server's internal IP address never changes.

---

### Post by binbash on 2009-01-30
> **TMcKSmith said:**
> I just installed Ubuntu Server on my home server.
I've had a server before but it was bloated with a lot of things, like a desktop.
What do I need to install to be able to SSH into the server and run "firefox&" (besides Firefox obviously) so it will open up a firefox window from the server remotely?

I guess this just doesn't apply to firefox - but to any app.  Do I NEED a desktop on my server in order for this to be possible??

I'd like to install the very least amount of packages needed.

Thanks.

But you cant see the firefox pop up.You have to use remote connect not ssh.

---

### Post by Cypher on 2009-01-30
> **binbash said:**
> But you cant see the firefox pop up.You have to use remote connect not ssh.
Not true, SSH allows for X11 port forwarding and you can show remote GUI applications as long as you can running a local X11 server..

---

### Post by albinootje on 2009-01-30
> **TMcKSmith said:**
> 
I'd like to install the very least amount of packages needed.


You need to have the application called xauth, and xorg libs and some xorg fonts installed, that is the bare minimum.

---

### Post by albinootje on 2009-01-30
And I've always (since years) used "ssh -X", this is from "man ssh" :
> 
     -X      Enables X11 forwarding.  This can also be specified on a per-host basis in a configuration file.

             X11 forwarding should be enabled with caution.  Users with the ability to bypass file permissions on the remote host (for the user’s X
             authorization database) can access the local X11 display through the forwarded connection.  An attacker may then be able to perform activi&#8208;
             ties such as keystroke monitoring.

             For this reason, X11 forwarding is subjected to X11 SECURITY extension restrictions by default.  Please refer to the ssh -Y option and the
             ForwardX11Trusted directive in ssh_config(5) for more information.

     -x      Disables X11 forwarding.

     -Y      Enables trusted X11 forwarding.  Trusted X11 forwardings are not subjected to the X11 SECURITY extension controls.


---

### Post by bodhi.zazen on 2009-01-30
Firefox is odd ;)

even though you forward X via ssh, firefox launches locally (test it for yourself if you wish ;) ).

You have tow options :

1. Port forwarding. With this you forward port 80 over ssh.

2. run firefox with the "-no-remote" flag :twisted:

```
firefox -p -no-remote
```

---

### Post by TMcKSmith on 2009-01-30
> **albinootje said:**
> You need to have the application called xauth, and xorg libs and some xorg fonts installed, that is the bare minimum.

Do you know the specific package names?

---

### Post by albinootje on 2009-01-30
> **TMcKSmith said:**
> Do you know the specific package names?

```

$ dpkg -S $(which xauth)
xauth: /usr/bin/xauth

```
For fonts this is probably enough : xfonts-base, xfonts-75dpi, xfonts-100dpi

So.. try :
```

sudo apt-get install xauth xfonts-base xfonts-75dpi xfonts-100dpi

```
That will probably install the required xorg libs.
After that test it, and see how it goes.
You might want to install more fonts, like ttf-liberation.

---

