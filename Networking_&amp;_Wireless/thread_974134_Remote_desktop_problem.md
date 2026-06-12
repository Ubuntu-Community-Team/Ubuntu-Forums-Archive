---
title: "Remote desktop problem"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by golusweet on 2008-11-07
Hi there,

I want to connect to my frnd pc,which is also using ubuntu.We both have dynamic ips.How could i connect to his pc using vnc server.

p.s I can't install vncserver in ubuntu 8.10

---

### Post by Coreigh on 2008-11-07
This is a difficult thing to do with dynamic IPs. I am guessing you are each at home and have residential internet like cable or DSL. Remote protocols like vnc are ofter blocked by residential services. You might be able to connect if you have a vnc server on one end and use the java vnc client through a web browser. You will need to know the server's IP address each time you want to connect.

Why are you having trouble installing VNC? Use Synaptic in System >> Administration. There are a variety of packages but basically you want the server and client packages that go together.

---

### Post by golusweet on 2008-11-07
I tried to install VNC server.

got this error:

Failed to completely install all dependencies

---

### Post by Coreigh on 2008-11-07
Tried to install from command line or synaptic? Did it list dependencies? And did you try to install them? Do you have universe and multiverse enabled in your sources?

---

### Post by golusweet on 2008-11-07
Package vncserver is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vncserver has no installation candidate

---

### Post by Coreigh on 2008-11-07
vncserver is not a package for all versions. I don't know which one you are on. Here is a link to all the vnc packages for each version of Ubuntu. You will have to determine which set to use depending on what is available for the version of Ubuntu you are on.

[http://packages.ubuntu.com/search?searchon=names&keywords=vnc]("http://packages.ubuntu.com/search?searchon=names&keywords=vnc")

There might be a better or more well supported way to remote desktop. Also if you do not need the GUI you can use ssh for command line connections.

I wish you luck.

---

### Post by jimv on 2008-11-07
YOu don't need to install vncserver.  You already have one.  Go to System > Preferences > Remote Desktop and enable it.  Viola!  You now have VNC running.

Then all you need to do is forward port 5900 through your routers, and maybe set up a dynamic DNS name for your internet IP address...you can do that at no-ip.com.

---

### Post by Coreigh on 2008-11-07
Thank you JimV. That is good info to know.

---

### Post by golusweet on 2008-11-07
Thanks mate,I will try that.

---

### Post by labrekke on 2008-11-09
Hi, I'm new here and have a similar problem.

I just upgraded to Ubuntu 8.10 on my father's laptop (he is 77 years old so I need to be able to help him... ;)).

On my own Ubuntu laptop (also 8.10) I can see "Remote Desktop" under System --> Preferences, but on his computer I can't see that option. Does anyone know what I need to do to make it show?

Both computers were upgraded from 8.04. I don't quite understand why I can see the menu item on my laptop and not on my father's...

I should also mention that under "Add/Remove..." the "Remote Desktop" shows as installed on his computer.

Sincerely,
Labrekke

---

### Post by labrekke on 2008-11-13
I guess I'll answer my own question: The remote desktop setting can obviously be displayed by editing the main menu under System --> Preferences. I only thought it was possible to edit the menu for programs, but should have checked better. ;)

---

