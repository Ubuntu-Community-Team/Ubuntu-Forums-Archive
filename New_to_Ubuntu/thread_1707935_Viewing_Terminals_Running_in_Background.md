---
title: "Viewing Terminals Running in Background"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by fujinkiller on 2011-03-16
Ubuntu Desktop 10.10
I[B]'ve never used Ubuntu or any Linux distro. before..
[/B]

I have figured out how to install ubuntu 32bit, and run it remotely.  I also figured out how to make the system autostart apps like x11vnc and minecraft server.  

But how do i view the terminals?  The minecraft server is running but i cant seem to find the terminal its running in. Anyway to bring that up?

---

### Post by seawolf167 on 2011-03-16
I'm not familiar with the Minecraft server so I can only offer two suggestions right now

1. Read the documentation for the minecraft server, see how to change its settings while running
2. If you start a program in a terminal and want to let it keep running but be able to close the terminal, start it using [screen]("http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/"), then detach the terminal and reconnect to it if you need to change its settings while running

---

### Post by matt_symes on 2011-03-16
Hi

+1 screen. I use it all the time for session management with remote access via ssh.

Start the screen session, detach and reattach later to continue your session.

Kind regards

---

