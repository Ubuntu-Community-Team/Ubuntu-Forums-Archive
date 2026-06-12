---
title: "Apache and IIS"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by corman420 on 2007-06-16
I have an Ubuntu 7.04 Apache2 server running on my network.

The Ubuntu machine is visable via port 80 to the internet.

I also have a Windows Vista Ultimate machine running IIS.

Is there anyway to have a virtual directory on my Ubuntu Apache directory pointing to the IP address of my Vista IIS machine?

Why would I want to do this?  Becuase my Vista machine has a lot of files I would like to be able to access via HTTP BUT I dont want my Vista machine to be visable to the net.  Having a web server with Ubuntu and Apache with a virtual directory to an internal IP sounds like it would be a bit more secure. 

Another reaosn is my router will only forward port 80 to one computer... and it would just be easier to shut-down IIS and not worrying about an open port...

---

### Post by CaptainCommandLine on 2007-06-17
A simple way of doing would be to simply share the folder that you want on the windows machine, mount
it on your linux box with samba, then just update your apache setup to include this directory.

You could also look into using apache as a reverse proxy that points to your IIS, but that might be a bit more complicated for what you need.

Hope this helps!

---

