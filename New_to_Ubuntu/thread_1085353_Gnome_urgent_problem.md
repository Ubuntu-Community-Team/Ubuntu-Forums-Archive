---
title: "Gnome urgent problem"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-02
Hi,
I am having trouble with opening my folder explorer, synaptic package manager and update manager and some other applications:

When I click synaptic package manager and update manager , it always repeats saying my password for root is not correct. 

When I click Places -> Computer, I got error like "An error occurred while loading or saving configuration information for Nautilus. Some of your configuration settings may not work properly" and "GConf error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Server ping error: IDL: omg.org/CORBA/COMM_FAILURE:1.0)". 

I googled and found this page [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=666845](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=666845) and I realized that I mananually clean up /tmp. So I tried what one suggested in the post that "sudo rm -rf /tmp && sudo mkdir /tmp && sudo mkdir /tmp/.X11-unix && sudo mkdir /tmp/.ICE-unix". But things still remain and now even now error message comes out.

How could I fix it? Thanks!

---

### Post by flylehe on 2009-03-03
More info:
I just restarted Ubuntu and this is the error I get when I try but fail to login:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

View details (~/.xsession-errors file)
/etcgdm/Xsession: Befinning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /home/ting/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/scim-bridge.
mkdtem: private socket dir: Permission denied"

update:

After logging in with gnome failsafe session, I got this error "There is a problem with configuration server /usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256" and stuck.

---

### Post by Ms_Angel_D on 2009-03-03
Hi,

for your session error message try this thread [http://ubuntuforums.org/showthread.php?t=97540](http://ubuntuforums.org/showthread.php?t=97540).

Good luck,

Angel

---

### Post by flylehe on 2009-03-03
Thank you, MetalHellsAngel!
However I tried all in the post and it doesn't help. I am not sure what the problem is but I uninstall and reinstall my ubuntu-desktop and it doesn't help either.
I just add some update on the error info in my last post. Thank you for your help!

---

