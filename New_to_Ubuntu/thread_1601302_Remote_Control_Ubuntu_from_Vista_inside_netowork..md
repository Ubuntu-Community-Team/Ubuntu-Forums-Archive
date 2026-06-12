---
title: "Remote Control Ubuntu from Vista inside netowork."
date: 2010-10-20
forum: New to Ubuntu
---

### Post by googlo on 2010-10-20
It's my first time trying to set up a remote connection from my Vista  Home Premium to my Ubuntu 10.10 Desktop... withing my network.
I have pretty much tried all I could find on the subject and no luck.

This is what I have don so far:
On the Ubuntu Desktop I have configured the Remote desktop Pref. window by checking the top two boxes and the password box.
I get the following message: 
"your desktop is reachable over the local network. Others can access your computer using 127.0.0.1 or XXX.XX.local"

On my router I have set portforwarding to 5900 TCP & UDP with my  Ubuntu IP address... ( I tried Static but  still same issues )

On my Vista laptop I have installed TightVNC  & have been using the Ubuntu IP to try to access it..192.168.0.XXX  or 192.168.0.XXX::5900.

I have also used Port forwarding's port checker from my Vista machine but I get error: 
" port is not open is not reachable "

I dont know what else there is to do...do I have to change something in my router? is it Vista? 

Im able to share files, but cant seem to figure this out..

Any help I would greatly appreciate it.

---

### Post by HermanAB on 2010-10-20
Howdy,

The best remote control method is with the Secure Shell.  Google uses it to control tens of thousands of servers for example.

So install the ssh server package on Ubuntu and install Cygwin with the ssh client on Windows.  Then simply open a Cygwin console on Windows and go:
$ ssh -X -C -c blowfish [email]user@linux.ip.add.ress[/email] gnome-panel

Any program you then launch from that remote panel, will run transparently on the Windows desktop.  It really works like magic.

---

