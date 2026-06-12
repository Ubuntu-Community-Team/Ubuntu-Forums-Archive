---
title: "FreeNX problem"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by gyzer on 2008-05-26
I am very new to this. I found the tutorial in the archives to get it up and running, and it was simple enough.

My setup is a desktop running Ubuntu 8.04 which is the host, while I've got a laptop running Xubuntu 8.04 with IceWM which is the client. I am able to get NX working, running nxclient on the laptop and vncviewer(I enabled remote desktop viewing on my desktop), I can view the desktop of the host desktop but when I move the cursor on the laptop, it doesn't move it in the desktop, but if I create a file on the desktop of the desktop comp via the laptop, it apears a second after I create it. If I try to open up firefox via the laptop in the session,and if I have it already open on the desktop, I get an error saying the program is already running. Also when I'm chatting in pidgen, messages I send via the laptop through the session don't apear on the window on the desktop comp, but messages I recieve apear on both. 

Now how do I make it so that when I log into the session from my laptop that I can see any open programs on my desktop and if I open up a program or new window on the laptop via the session that it will show up on the desktop comp's desktop?

I hope this makes sense to someone. I am really only asking this cause of seeing how RDPing works in windows, and I was at least under the impression that this would work the same way.

---

### Post by gyzer on 2008-05-27
Is there some other way that this is supposed to be used that I might just not be getting?

---

### Post by gyzer on 2008-05-27
Ok, so does FreeNX with VNC running allow you to log into an already running desktop and interact with programs that are already running on that desktop?

---

### Post by jtrindle on 2008-05-27
VNCViewer would let you log in from remote and control your Ubuntu desktop.  

FreeNX is a competing system to VNC, and so the nxclient and nxserver together accomplish the same kind of thing as VNC Server and VNC Client together.  

I am unsure what you are trying to do here by mixing both systems.

---

### Post by gyzer on 2008-05-27
Don't I need to have remote desktop enabled on the ubuntu machine? And isn't that VNC?

I some of the stuff I've read, it has said that you can use nx with vnc. Like I said I am a noob to this subject.

---

### Post by gyzer on 2008-05-27
I turned off the remote desktop settings in ubuntu on the desktop machine. 

Still with just using nx, when I connect to the desktop it doesn't show any of the windows for the programs I was running. But the screen saver was on the desktop machine and I did see that when I connected.

I'd just like to be able to see the windows for currently running programs on the desktop machine when I'm connected to it via nx from my laptop.

---

