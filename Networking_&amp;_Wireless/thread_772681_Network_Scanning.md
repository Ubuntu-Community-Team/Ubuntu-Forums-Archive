---
title: "Network Scanning"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by SneakPeak on 2008-04-28
Greetings and salutations

I need some help setting up network scanning.  (I am a bit clueless on Linux and have managed to fumble my way through with the help of Howto's etc.)

I have:

A desktop running Gutsy Gibon 7.10
A laptop running Vista (I know but it has to for work)

They are networked and printers and scanners are attached to the desktop

Printing (from both machines), networking and internet connection sharing also work fine (desktop connects to the internet).

I want to be able to scan directly to the laptop but I can't get it to work.

Scanners connected to desktop work perfectly with XSane.
I have installed Win32 version of XSane on laptop

It seems I have to get either inetd running or xinetd running to get saned running but all the advice I have found on the net so far just confuses me.  

For example: How do I know if I should be using inetd or xinetd?

Network is working, scanners are working it would seem that network scanning shouldn't be that hard to get right.

I'd really appreciate some help.

Thanks

Sneaks

---

### Post by SneakPeak on 2008-04-28
Please help.  Here is some more information on what I am trying to do:

I am following the advice in the attached file.  This comes from:  [http://penguin-breeder.org/sane/saned/](http://penguin-breeder.org/sane/saned/)

> "Make sure /etc/services contains a line like this:              
 sane-port          6566/tcp      # SANE network scanner daemon"

I have done so.  Mine looks like this:

sane-port	6566/tcp	sane saned	# SANE network scanner daemon

When viewed in Kate there appear to be comma like characters between the different parts of the line e.g. sane-port, but copy and paste doesn't bring them through.

I have established that xinetd is not installed on my machine.  I used Adept and did a search for xinetd and discovered that it wasn't installed.  Therefore I assume I am using inetd.

> "Your /etc/inetd.conf should contain a line like this:               
sane-port  stream  tcp  nowait  saned.saned  /usr/local/sbin/saned saned
              
or, if your system is using tcpd, a line like this:             
sane-port  stream  tcp  nowait  saned.saned  /usr/local/sbin/tcpd saned"

This is where I get stuck!  

How do I know if my system is using tcpd or not? (In Adept update-inetd and tcpd show as installed)
Can I have both lines in the inetd.conf file or will they conflict with one another?

For the time being I have the first line in the inet.conf file.  The only difference is saned is in /usr/sbin, not /usr/local/sbin.  My line therefore looks like this:

sane-port stream tcp nowait saned.saned /usr/sbin/saned saned

> If your saned and/or tcpd binary are installed somewhere else you have to supply the correct paths.

I think I have this sorted by taking "local" out of the path.

> Furthermore, you have to make sure user and group saned exist and they have appropriate access rights to your SCSI, parallel port, and USB
devices.


How do I make sure user and group saned exist?
How do I give them appropriate access rights? (Both my scanners are on USB ports)

> If your scanner is attached to /dev/sga for example, you can set the access rights like this:

I don't know where my scanners are attached to and I have tried to find out without success.  I have looked in /dev and I have tried "System Settings" 

If I can sort out some of the above I may be able to go further.

Your help is appreciated!

Sneaks:confused:

---

### Post by SneakPeak on 2008-04-29
Bump!  Please help if you can.  Thanks

---

### Post by needhelpplease on 2008-04-30
Here's a blog entry with the exact steps for setting up [network scanning with Ubuntu](http://chiralsoftware.com/blog/Linux-network-scanning-with-saned-9404a25b8342ba4e.html).  If it doesn't work let me know where you get stuck.

I'm right now trying to figure out how to control xinetd within Kubuntu Hardy Heron KDE4.  I can't find the control panel for it.  I could set it up manually but I should be able to do it all through the controls.

---

### Post by SneakPeak on 2008-05-07
Thanks for the reply.

I followed the instructions but they did not work.  Even the somewhat disturbing approach of changing the user and group to root did not work.

The client machine is a Vista machine, not a Linux / Ubuntu machine.  I have installed the windows version of X-Sane on the machine but it gives the error message that no scanners can be found.

It seems from a number of postings on the web that other people have got this to work.  Scanning over a network machine with a Linux server and a windows client.  I can't figure out why I can't get it to work when I follow the instructions!

I guess I'll just have to keep trying

Sneaks

---

