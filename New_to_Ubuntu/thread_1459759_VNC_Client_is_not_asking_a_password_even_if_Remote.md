---
title: "VNC Client is not asking a password even if Remote Desktop is set to require password"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by h3000 on 2010-04-21
Hi,

I am currently trying to setup remote access to my ubuntu server.  However, it seems the Remote Desktop settings is not being implemented as specified.

I have set the Remote Desktop to require a password when accessing the server.  However, when I use a VNC client to access the server, I am not asked for any password???

The following is my Ubuntu setup
Ubuntu 9.04
Gnome 2.26.1

On the client side I use a windows machine to access the server
the VNC client that I use is RealVNC 4.1.3

Now I tried to disable remote access completely but it still does not work!  The VNC client can still access the server!

Is this a known bug?  I have searched other forums but could not find a similar issue.

Thanks in advance.

---

### Post by _0R10N on 2010-04-21
On the "Remote Desktop" window there's an option labeled "Allow other users to view your desktop". Are you sure that this option is unchecked?

Kind regards!

_0R10N >>

---

### Post by h3000 on 2010-04-22
Yes - the option is unchecked.

I have restarted the server after making the change.

Still same thing.

Is there a shell command to disable remote access?

---

### Post by Gone fishing on 2010-04-22
wouldn't using ssh be more secure? You can also run X apps over ssh if you need to for example with 

ssh -X -C adminuser@192.168.1.1

I also use webmin to do remote stuff on the server it has some cool tools one I use is to add hundreds of new users or ldap users from a batch file. It also has squid, postfix etc etc tools.

---

### Post by h3000 on 2010-04-22
Yes ssh would be more secure.

But my question is why is the VNC Client not asking a password when I have already required a password?

Right now, I am just trying to disable Remote Desktop which I cannot do as well.  The option to not allow other people remote access is not working at all.

Does this mean that all ubuntu servers are accessible via VNC Client?  This is a major security hole for all servers running on Ubuntu.

---

### Post by h3000 on 2010-04-22
@Gone Fishing, I also noticed that in your avatar, you are on Ubuntu 9.04 - I am on the same version of Ubuntu - can you test on your end if remote desktop is working as it should? Password is asked whenever password is required, remote access is disabled when the setting is disabled... etc...

If you can confirm that your copy is working that would be much appreciated! Thanks in advance.

---

### Post by _0R10N on 2010-04-22
I think you have a serious problem going on. My best advice for you is to reinstall the remote desktop packages. Uninstall them, reboot. Try to access from other system, you'll fail, of course. Then, install them again, and start over.


Kind regards!

_0R10N >>

---

### Post by Gone fishing on 2010-04-22
> Gone Fishing, I also noticed that in your avatar, you are on Ubuntu 9.04

Ooops changed to Karmic, however, I do have 9.04 at work I'll check tomorrow

---

### Post by HermanAB on 2010-04-23
Howdy,

VNC is primarily a Windows thing. On Linux, SSH is the preferred tool for managing servers.

If you search these forums, then you will find many tales of woe from people who had their machines hacked after installing VNC.  It is not secure, and it does a few nasty things with Plug and Play which can leave your machine wide open, after which it is just a matter of time for an attack script to find you.

Sooooo, remove VNC and ensure with 'ps-e', that it *really* is not running, then install ssh-server.  You can run X programs over SSH.  You can even run the Gnome taskbar and then go click happy:
$ ssh -X -C -c blowfish user@serveripaddress "gnome-panel"

Move that panel to the side of your screen, to reduce confusion with your local panels, and go click happy.  Any remote program launched from that panel, will run transparently on your local desktop.

---

### Post by h3000 on 2010-04-23
Hi HermanAB,

Yes - I am currently trying to find out how to remove remote desktop from the server - how do I do that from the command line?

Probably Remote Desktop should be removed from standard ubuntu installations if it is not that stable or is not well implemented and opens up a security hole on the server.

Thanks for the tip on running X programs - will try it out.

---

### Post by Gone fishing on 2010-04-23
Can't you just uninstall vnc server using apt then make sure the port 5900 or 5901 (I think)is closed. I seem to remember having a similar vnc problem with Opensuse and just disabled it.

I think if you disable graphical login you will still be able to use X apps if you ssh like so:

ssh -X -C adminuser@192.168.1.1

My users are ldap users and cannot login to the server only the local users (very few) can do that

---

