---
title: "VNC and compiz not work -- shortcut to metacity"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by _nikolaos on 2010-05-07
As I read about, the VNC server of Ubuntu (vino) cannot support transmitting the OpenGL effects of compiz to the remote machine. It's doubtful if there is some VNC server for linux to do this. 

Also other remote desktop implementations (such as nx) find a hard time with compiz. They usually don't cooperate.

Until something new appears, I have to revert to metacity before starting a VNC session:

```

metacity --replace

```

which I execute after connecting with a terminal (ssh putty for example). After this, it's possible to work with windows through VNC. In the same fashion, after I close my VNC session, I can connect again with putty and restore compiz.

```

compiz --replace

```

My question is about shortcutting the whole sequence.

If I compare with RDP-rdesktop, there is (i think) an option to execute a command before the graphics come up in the session -- that's already in the client side. 

You can guess now my idea. Executing a **metacity --replace** command before establishing the graphics session with the vncviewer is the case.

However, vncviewer (and I suppose most vnc clients) doesn't support this feature. Evenso, why not triggering the "metacity" command whenever GNOME itself reports that a remote connetion takes place? Make our system responsible to change to metacity to serve well the remote connection, and replace compiz when the remote client is over with us.

Any suggestions to implement this on my system?

---

### Post by bbriand on 2010-05-17
I second this.  In fact over the last few months I've had occasion to search for Ubuntu having a remote connection event that could fire off the metacity command.

I mean who wants to write a script that polls for a remote connection every x seconds when there must be some way to have the remote desktop connection event fire off the metacity command.

The googling continues. ;)

Cheers,
Bill

---

### Post by Excedio on 2010-05-17
I'm all for this. However.. I would prefer the bug gets..you know...fixed.

---

### Post by _nikolaos on 2010-07-09
I am going to install Xming in a computer with Windows, and connect to my remote Ubuntu Gnome from it. I am not interested in the fancy Compiz graphics while connecting, I want only substantially functional windows; it is a matter of bandwidth as well.

Considering the problem with VNC and Compiz, I hope that this will not be a case with Xming. But can anybody tell me if Compiz is not going to interfere with Xming, or tell me the opposite thing will happen?

---

