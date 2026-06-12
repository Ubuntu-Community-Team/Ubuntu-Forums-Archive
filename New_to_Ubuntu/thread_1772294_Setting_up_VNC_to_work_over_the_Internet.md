---
title: "Setting up VNC to work over the Internet"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by mkhaytman on 2011-05-31
Hello,

As the title suggests, I am looking for a way to set up VNC on my Linux machine so that I can remotely view the desktop over the internet. I am running **Ubuntu Lucid Lynx 10.04.2**  There are a few features that are important to me:


[LIST]
[*]VNC starts when Ubuntu starts, without the user having to start the service
[*]VNC is configured after each restart: server-side user should not have to re-enter the password or ports or other configuration settings after restarting.
[*]Session can be initialized without server-side user having to accept/refuse the connection.
[*]VNC server can run without displaying a notification when a connection is established.
[/LIST]
Basically, I've got multiple workstations set up and I want to be able to view (just view, control not important) the users desktop without the user knowing when I connect. I've gone through many tutorials on setting up VNC but each one fails to meet my requirements at some point down the line. This seems like such a basic function, I'm surprised I'm having so much trouble setting it up. Hopefully there is something simple I've overlooked that you guys can point me towards.

Thanks in advance!

---

### Post by crispy_420 on 2011-06-15
Are all of these users on a separate LAN away from you or are they local?

---

