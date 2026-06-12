---
title: "NX Server Desktop Sharing"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by greenwc on 2008-06-20
Currently running Ubuntu Hardy 8.04 and recently installed the NX Server from NoMachine.

I'm having a problem getting desktop sharing / session shadowing working.  I'm able to log into a new Gnome session connecting to my Ubuntu box using the NX Client for Windows XP and everything is gravy.  However, I really would *like* the ability to remote into my existing desktop session and do anything that I need to.

I chose the NX Server from NoMachine because I have been able to get FURTHER with desktop sharing than I was with the FreeNX packages in the Hardy repository.  If anyone has gotten desktop sharing working with FreeNX, I would greatly appreciate knowing the steps you did to get it working.  Changing 

```
/etc/nxserver/node.cfg
```

did not yield any positive results.  Regardless of what I chose for enabling desktop sharing with FreeNX, the client would always come back saying session shadowing was not supported.

This led me to trying the NX Server from NoMachine, even though it's limited to 2 sessions.  I have modified /usr/NX/etc/server.cfg to enable desktop sharing and am able to login to the machine using NX Client set as "Shadow".  I'm presented with my desktop as it would appear on my Ubuntu server, but any screen changes are not displayed through the client.  For example, starting at a blank desktop, if I open Nautilus, for instance, the application loads when looking at the screen on my monitor at home.  However, the screen doesn't update on the NX Client to display Nautilus -- it just stays at the desktop forever in a frozen state.

Surely I can't be the only one here - help!

Thanks,
Will

---

### Post by szim90 on 2008-06-23
I'm having the exact same problem - a shadowed session displays the first screen, but then does not update.

Any help would be appreciated.

Thanks,
Sean

---

### Post by trentster on 2008-07-09
Yip I am also having the exact same problem, spent quite some time trying to figure it out, but still no luck. Anyone have a solution for this hardy nomachine shadowing problem?

---

### Post by webaake on 2008-07-14
Same here! Only a frozen desktop when trying to use Shadow. I've enabled all DesktopSahring in /usr/NX/etc/server.cfg, as far as i now.

However, a Unix/Gnome session seems to work, but that's not what I want.

NX also seems faster than VNC.

---

### Post by trentster on 2008-08-24
anyone found a solution yet to this shadow problem, I would really like to get this resolved, and I am assuming this must be effecting everyone who wants to use nomachine for ubuntu shadowing?

---

### Post by Sp00nMan on 2008-09-02
Ditto here.. And I thought it was just me.  Connects fine, no client updates.

---

### Post by hexeroby on 2008-09-25
I had the same problem.

I got shadowing working by deactivating desktop effects on my machine (System->Preferences->Appearance and setting None on the Visual Effects tab). This allows me to shadow my machine from another with NX.

If I leave compiz enabled (visual effects) on my machine, I only see the initial screen and then get no screen refresh (as you have all described).

---

### Post by irvin on 2009-01-07
Hi

I had the same Problem and changed this these in /usr/NX/etc/server.cfg:

EnableFullDesktopSharing = "1"
EnableAdministratorDesktopSharing = "1"
EnableDesktopSharingAuthorization = "0"
EnableSystemDesktopSharingAuthorization = "0"

With this 4 changes look like this it worked to connect with the nx client. In nxclient I choose "shadow" in configure-general-desktop.

BUT !!! I have a real big Problem. I can use the mouse but the keyboard don't work. So I can't log in because I can't type my user and password. only when i press F1 i get a =, that's all.

does anyone has an idea ?

---

### Post by The_Rebel52 on 2009-02-18
Has anyone tried to get shadowing working in Intrepid ?

I keep getting error's on the client side saying "connection pipe broken"

I think the nxagent on the server is crashing..(as i get crash report pop-ups on jaunty - i have apport disabled on my interpid install)

---

### Post by karagiozakos on 2009-05-11
I'm on Intrepid and shadowing doesn't give me the "connection pipe broken" problem you reported. I'm running freenx-server (0.7.3+teambzr104-0freenx) and NXCLIENT v3.3.0-6. 

No properties changed in /etc/nxserver/node.conf. When I connect to the server I get a window depicting the server's desktop at the time of connection, moving the mouse at the client moves it at the server, clicking from the client results in the intended action at the server's desktop, but the client window doesn't update. It stays the same, like a static image.

---

### Post by karagiozakos on 2009-05-11
sorry, hexeroby's post addresses the problem -- need to disable compiz first.

---

### Post by whitecloudboy00 on 2009-05-25
There has got to be a workaround for this problem.  I haven't tried it yet, but I know you can attach scripts to a session start.  What about a shadowing session?  Once we've figured that out then we can write a script presumably to disable visual effects temporarily ... surely... :p  ...I'm going to see if I can't put something together using this: 

[http://ubuntuforums.org/archive/index.php/t-588497.html](http://ubuntuforums.org/archive/index.php/t-588497.html)

Anyone know of better software for the job.... ?  I moved away from VNC and VNC like approaches (UltraVNC) because I didn't like exposing an open port with only an 8 character password.  Maybe I'm just missing something here...

---

### Post by whitecloudboy00 on 2009-05-28
Thought it was worth sharing; I've been tracking this bug as well.  

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126)

So it might help for others to search on vnc + compiz too because this bug appears to be an interaction between drivers, remote desktop services like nx, and compiz and particularly X11 xdamages, which appears to be enabled when advanced desktop effects are enabled.

---

### Post by albinootje on 2009-05-28
> **greenwc said:**
>  I chose the NX Server from NoMachine because I have been able to get FURTHER with desktop sharing than I was with the FreeNX packages in the Hardy repository.  If anyone has gotten desktop sharing working with FreeNX, I would greatly appreciate knowing the steps you did to get it working.  

Have you asked on the FreeNX mailinglist ?

---

### Post by whitecloudboy00 on 2009-05-28
I've come up with a solution that I'm mildly satisfied with (which means I'll still working on it but I have workaround).

Following the bug tracking for vino in Ubuntu there was patch posted to disable the damages extension in compiz.  That link again is pasted below: 

[https://bugs.launchpad.net/ubuntu/+s...iz/+bug/353126]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126")

Installing the patch and/or finding a way to disable the damages extension for whatever remote desktop server being used seems to be at least a temporary solution.  I haven't figured out how to do this with nxserver yet.  

However, if you install and enable vino + the patch in the above link, block port 5900 (for vnc), install ssh and open port 22 (for ssh) then you can ssh port forward into your box remotely and then run vnc.  I'm not going to go into the details of this, because it's a painful amount of steps to solve the problem. .... bear with me though... 

The real solution then is to use nxclient's connect over vnc option.  With this you can hit your remote box and then in the vnc options for nxclient just set the vnc server to localhost display 0.  With this configuration I can easily remote into my box with desktop effects enabled.  Right off though, it seems a little slow.  I'm going to test from a more remote location today though to see if this is acceptable for now.

Thoughts, critism, questions, or other options are appreciated...

---

