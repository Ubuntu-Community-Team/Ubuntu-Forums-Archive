---
title: "Remote connection verification"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by grantj on 2010-05-14
Hi,

I just set-up a connection to access my desk-top Ubuntu PC (9.04)with my vista laptop remotely using Putty and TightVNC Viewer. I followed the instructions at this link:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Everything connects perfectly but the problem is that the Ubuntu PC  asks the user to verify that it is okay for the remote computer to connect. Clearly this won't work and defeats the whole point.

Once connected the following is entered into Putty:

x11vnc -safer -localhost -nopw -once -display :0

Is there an additional command that will remove the verification prompt?

Much thanks,

Josh

---

### Post by scorp123 on 2010-05-14
> **grantj said:**
>  x11vnc -safer -localhost -nopw -once -display :0

Is there an additional command that will remove the verification prompt? No idea. I never use "x11vnc" ... but perhaps you could simply read the manual? Type this into a terminal:
```
man x11vnc
```

Use the cursor keys to navigate, use "Q" to leave the manual again. I am sure you will find the answer there.

Edit: I forgot ... you can use the slash "/" to search for stuff. So let's assume you're reading a manual page and now you want to find the word 'password', you'd simply type this right into your manual session (and hit the 'Enter' key):

***/password***

All instances of that word would then get highlighted. Now by pressing the **"n"** key ('n' as in 'next') you'd jump to the next location in the manual text where the word was found.

This should make it easier to actually find what you're interested in instead of having to read long manual pages in full (which can get you tired, because some of those manual pages tend to be super-long).

---

### Post by krunge on 2010-05-14
> **grantj said:**
> 
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Everything connects perfectly but the problem is that the Ubuntu PC  asks the user to verify that it is okay for the remote computer to connect. Clearly this won't work and defeats the whole point.

It sounds like you accidentally have "vino" (GNOME's VNC Remote Destkop Server) running.  Maybe you enabled it via the "Remote Desktop" menu item in the desktop menus and forgot to disable it.

x11vnc doesn't have a gui and would not ask if it is okay for the remote computer to connect (actually it does, but they are disabled by default and your x11vnc command line would not invoke either one.)

So I say disable GNOME's "vino" via the desktop menus and try again. Your putty x11vnc cmd looks good.  If you have the putty port redir set up it should work.  I suggest adding "-rfbport 5900" to your x11vnc cmdline to force x11vnc to use port 5900 and not autoprobe for a free port.  Of course, make the 5900 match your putty port redir.

---

### Post by grantj on 2010-05-17
Problem solved.

It was very simple. The Ubuntu machine has an icon in the top left corner with remote desktop options, one of which is requiring verification for access.

Thanks for the replies.

---

### Post by krunge on 2010-05-17
> The Ubuntu machine has an icon in the top left corner with remote desktop options, one of which is requiring verification for access.
Sounds like you are not using x11vnc (i.e. you are using vino.)

So if you are still starting x11vnc with putty (your original post) you might as well stop doing that.

---

