---
title: "Opera shutting down on me for no reason - again and again"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by longtom on 2009-03-09
Hi,

I am an Opera user from my Windows days and still love it on any platform.

However - in Ubuntu I find it shutting down every so often just like that for no reason.

Oh well - so I used Firefox - which appears to do the same.  

So I start up from where I left and all is well - until the next time.

Anybody had that before?  Anything I can do to better the situation?

Regards

longtom

---

### Post by rzrgenesys187 on 2009-03-09
Did you try running them through the terminal so you can see any error output.  Also see if the firefox error console gives you any information

---

### Post by longtom on 2009-04-17
> **rzrgenesys187 said:**
> Did you try running them through the terminal so you can see any error output.  Also see if the firefox error console gives you any information

Here we go - it is just bugging too much, so let me come back to this thread:

```

 opera
opera: X Shared memory extension is not available. ZPixmap not supported
OpenOffice path is '/usr/lib/openoffice'
OpenOffice path is '/usr/lib/openoffice'
Aborted
cango@cango-desktop:~$ 
(operapluginwrapper:16471): Gdk-WARNING **: GdkWindow 0x4a0018d unexpectedly destroyed

(operapluginwrapper:16471): Gdk-WARNING **: GdkWindow 0x4a0018c unexpectedly destroyed

(operapluginwrapper:16471): Gdk-WARNING **: GdkWindow 0x4a0018b unexpectedly destroyed

(operapluginwrapper:16471): Gdk-WARNING **: GdkWindow 0x4a0016e unexpectedly destroyed
The program 'operapluginwrapper' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 3600 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

This is what I get in the terminal, when opera shuts down.  Also get the shutdowns in firefox and epiphany.

For reliable browsing I go to XP in openbox and browse in firefox...no that's not the idea, is it?

Any suggestions welcome.

---

### Post by Temposs on 2009-04-17
Are you using the versions from the repositories or are you downloading them from the respective browsers' websites?

---

### Post by longtom on 2009-04-17
> **Temposs said:**
> Are you using the versions from the repositories or are you downloading them from the respective browsers' websites?

Firefox and epiphany were installed, opera I got from repositories.

---

### Post by ssdt on 2009-04-17
Is it the new version of Ubuntu that you are using because there might be some problems with old versions. I think that is what happened in your case.

---

### Post by longtom on 2009-04-17
> **ssdt said:**
> Is it the new version of Ubuntu that you are using because there might be some problems with old versions. I think that is what happened in your case.

Using the same version that you are using - Intrepid 8.10.

---

### Post by superprash2003 on 2009-04-17
i face this problem too at times.. do you have a LOT of windows open?

---

### Post by hesjnet on 2009-04-17
This has happened to me to. Not so much lately. It seems like it happens when I'm trying to view flash content(like youtube).

---

### Post by Npl on 2009-04-17
Opera with flashplugin has many problems if I use Metacity-Compositing. Do you use this or the bugridden compiz? Then maybe try without.

---

### Post by ravi_buz on 2009-04-17
i too have a similar problem with skype and stellarium and when i tried it in terminal i got this output

Fatal: Cannot mix incompatible Qt libraries
Aborted

---

### Post by longtom on 2009-04-18
> **superprash2003 said:**
> i face this problem too at times.. do you have a LOT of windows open?

Not really - 5 at most on one desktop...

---

### Post by cowboy7305 on 2009-04-18
My computer started to freeze and shut down on its own  when i used google earth the other day 
iam using 8.01

---

### Post by longtom on 2009-04-18
> **cowboy7305 said:**
> My computer started to freeze and shut down on its own  when i used google earth the other day 
iam using 8.01

Please open a different thread for that - it doesn't appear to be related.

Thank you!

---

### Post by Flywaver on 2009-04-27
Opera doesn't like multiple tabs opened and it will use up to 400mb RAM, to the point where I can't kill it or run anything else...it will just sit there, grayed out with the HD running constantly. I tried disabling the flash plugins but with no luck.

I opened Opera with the terminal and here are the messages when Opera starts to go berzerk!

> (npviewer.bin:6132): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(npviewer.bin:6132): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(npviewer.bin:6132): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

And if I do manage to force quit opera and go in system monitor, opera still appears as running and then I get these messages in the terminal:

> *** NSPlugin Viewer  *** ERROR: NPN_ReleaseObject() wait for reply: Message timeout
*** NSPlugin Viewer  *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-viewer.c:862):invoke_NPN_GetValue: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
*** NSPlugin Viewer  *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-viewer.c:862):invoke_NPN_GetValue: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
*** NSPlugin Viewer  *** ERROR: NPN_GetProperty() wait for reply: Message timeout
*** NSPlugin Viewer  *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-viewer.c:862):invoke_NPN_GetValue: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
*** NSPlugin Viewer  *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-viewer.c:862):invoke_NPN_GetValue: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
*** NSPlugin Viewer  *** ERROR: NPN_GetProperty() wait for reply: Message timeout
*** NSPlugin Viewer  *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-viewer.c:862):invoke_NPN_GetValue: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
*** NSPlugin Viewer  *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-viewer.c:862):invoke_NPN_GetValue: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
*** NSPlugin Viewer  *** ERROR: NPN_Invoke() wait for reply: Message timeout
*** NSPlugin Viewer  *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-viewer.c:862):invoke_NPN_GetValue: assertion failed: (rpc_method_invoke_possible(g_rpc_connection))
Killed


Any ideas??

Btw this is with Jaunty and I run Opera 10 Turbo Edition.

---

