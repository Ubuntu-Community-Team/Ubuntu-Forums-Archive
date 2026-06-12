---
title: "Samba file server"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by msimon1960 on 2007-11-19
I check in every six months to see whether Ubuntu developers have come up with a realistic (i.e. getting it working without having a MSc. in Computer Science) system for networking for small office and home networking.

What I want is a Ubuntu desktop that will provide a common file area that my family can access (full read/write permissions) from their Windows XP desktops.   I tried SAMBA again last spring -- horrifying experience -- I never found anyone who successfully setup a SAMBA installation.  I read all the manuals but never got it to work.

Has anyone setup a Gutsy Desktop and networked it with Windows XP so that all users could read/write to a common file area?  This would be my definition of the absolutely simplest file server setup.

Matt.

---

### Post by Fri13 on 2007-11-19
Have you asked from Samba developers who would know little bit better this thing?
I use Mandriva and i have always got working Samba, with Ubuntu and SUSE distros and Windows XP OS's.

Just a tip, ask samba developers if you dont get anything up to mind from manuals or google.;-)

---

### Post by msimon1960 on 2007-11-19
I tried contacting the developers last spring -- I came to the conclusion that SAMBA really wasn't up to the job of providing practical file sharing without all users having an in-depth knowledge of the underlying permission system (something I still don't understand).  I never got past being able to grant read only permissions.

Linux seems to come from the perspective of locking everything down and then requiring the user to grant permissions instead of starting from an open environment and then locking down as Windows does.

I don't have a problem philosophically with the approach except that the GUI interface for setting folder access permissions didn't work (you could click on boxes until your fingers fell off and nothing happened).  The arcane '777' lingo escapes me -- I haven't been able to find a simple document for the syntax for setting file permissions in Ubuntu.

I was hoping that someone actually got SAMBA working in Ubuntu -- common share with full read/write access.

Matt.

---

### Post by dmizer on 2007-11-20
if you're willing to use the command line and do some text edits, i'm more than willing to walk you through it.

p.s. i'm no msce but i didn't have any problem getting it to work with the howto linked in my sig.

---

### Post by jhetrick62 on 2007-11-20
I have just this thing set up, BUT, my file server is running on FC5 currently.  I am moving most of my Linux desktops to Ubuntu although I have no desire to move my file server currently, maybe eventually.

BUT, I don't see why the principles would be any different between the two systems as SAMBA is not exclusive to any Linux distro.

In my current systems, I can access from Windows XP by defining a network place or drive mapping the share and all of my family can also access through Nautilus by clicking on their share in the Nautilus browser window.  Works like a champ for me.

Now I do have defined shares in my fstab for the linux access (the linux machines they use are either FC6 or Ubuntu).  My windows machines as I said, I define the network place or map the drive using the ip address of the server with the share name.  \\192.168.0.48\jeff  for example.

You will have to edit your smb.conf file with gedit to begin with and keep it simple until it works well. After that, you can experiment with more exotic permissions if you desire, ONE at a time to see their effects.

This should work easily for you if set up right.  I think this is a far better solution that file serving in a windows environment.  Maybe simple windows file sharing is easier to set up, but WAY more  secure.

Follow the link in dmizer's sig as it's very straightforward.


Jeff

---

