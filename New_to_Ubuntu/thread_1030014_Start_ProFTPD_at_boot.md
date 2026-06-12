---
title: "Start ProFTPD at boot?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by cfree220 on 2009-01-04
Hi all,
So first of all, this is my first post on these forums. I've found other people's posts helpful in the past and figured this is probably the best place to turn for help. I should note that I am also new to Linux (hence me posting in the Absolute Beginner Talk forum :)

What I'm trying to do is set up an FTP server on an 8-9 y/o dell desktop. I know that it's a little ambitious for a complete novice, but now that I've started it's like being stuck on a Sudoku puzzle: I know it can be done, I just don't get how.

A major requirement of this project is that the system must always be on and the server must always be running. The first part was easy. All I had to do was go into the BIOS setup and tell it to start on AC resume (In case the system loses power during an outage) and to start everyday at midnight (in case one of my siblings decides to shut it off manually).

What I am having trouble with is ensuring that the server starts on boot, or on logon (I have it configured for automatic login on boot, so either way is fine). I installed ProFTPD (plus graphical frontend) and a DynDNS Update Client and added both to the list of startup programs. I don't know if the update client is starting on boot (my external IP hasn't changed since I started the project), but I'd say that my FTP client's inability to find the server is a good indication that ProFTPD has NOT started and that I'm doing something wrong.

So far, the only way I've managed to get the server running is to start it through the GADMIN-ProFTPD user interface (which requires authentication and does not activate the server until you tell it to). When I start it this way, I have no problems connecting to it (with the exception of passive transfer and FTPS connections, but those are questions for a later post).

So, what I need to know is: How the blazes do I get this thing to start AND activate on boot?

Thanks in advance for any and every bit of help anyone has to offer. Also, I should re-iterate that I am very new to Linux, so the more specific and guided the feedback, the better!

---

### Post by jimmy the saint on 2009-01-04
I have no idea what the issue could be but I can suggest two guides for setting up a server.  The perfect server howto has a section on page 6 that will set you up with proftp in just a couple commands.  I have had no issues with it.

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p6](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p6)
[http://www.howtoforge.com/ubuntu-home-fileserver-p2](http://www.howtoforge.com/ubuntu-home-fileserver-p2)

Also, if you are willing to delve into the command line (just follow one of the guides) then you could install Ubuntu server edition which gives you a choice to install several types of servers (mail, ftp, LAMP etc.)  It is really quite easy.  Just follow the ubuntu-home-fileserver howto.  

Don't stress!  the forums are here to help you through it!
Welcome to the forums

JTS

---

### Post by cfree220 on 2009-01-04
Thanks for pointing me to those pages! I had stumbled on them earlier, but didn't read far enough in to realize they might be useful!

I'm not sure that I'm ready to try for the Ubuntu server yet... my knowledge of command line is limited to a few specific commands in Vista. Maybe I'll take a look at that option if I can't get it to work on the desktop distro...

When I was looking through the perfect server page, I saw a section called ISPconfig. My Google search told me that this is some sort of app that allows you to manage different web oriented services, such as FTP. Does this mean that I need to install this app for the server to function as a service?

Is it possible that I've used the wrong "command" for the startup? The article you sent me shows the start location as being /etc/init.d/proftpd (restart command = /etc/init.d/proftpd restart). I have the startup path (command?) as being /usr/bin/proftpd. If the problem is with the command, then I've got another point of confusion. This morning my external IP changed (at least I'm pretty sure it did... my update client indicated that it updated, but it doesn't log past IPs, so I can't confirm). I'm still able to log into the FTP server using the DynDNS hostname, which is a good sign... but the startup command I used for the updater was also in /usr/bin/[ddclient].

Thanks again for the help!

---

### Post by cfree220 on 2009-01-04
Oh yeah, I also tried changing the startup path for proftpd to /etc/init.d/proftpd. When I tried to connect, I got "Connection attempt failed with "ECONNREFUSED - Connection refused by server" " In the past, it just failed to connect with no information as to why. When I started up the GUI, I got a message saying that:

"GADMIN-PROFTPD could not find the proftpd configuration or you are using a basic configuration that doesn't have all the features this program requires.

Do you want to overwrite your current proftpd configuration with a suitable standard configuration for gadmin-proftpd?"

I got this before and clicked yes, which undid all my settings and put it back to default. I reconfigured it as it was before. I did remove a user and group from the anonymous login section, because it was defaulting my user as an anonymous login, which I did not want. Do I need to simply comment out the anonymous section?

---

