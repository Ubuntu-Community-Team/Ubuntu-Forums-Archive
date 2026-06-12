---
title: "Redirecting outputs?"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by zcacogp on 2009-07-26
Chaps, 

I'll approach this one very cautiously. I fear that a) I may be asking something very difficult, b) I may make an idiot of myself by (and in) asking, and c) it may all be a bit too complex for me to understand. 

But .... 

I have two Ubuntu machines. (Actually I have three, but that's beside the point.) 

Remote Desktop doesn't work very well with 9.04 (which I have on each machine). But I can SSH from one machine to another, and when I have the terminal open on a local machine I can run things from it. For instance, if I open a terminal on this machine and type "amarok" then Amarok opens and works very nicely - displaying and playing on this machine. 

BUT, if I SSH to another machine (so the terminal prompt says that I am logged in somewhere else), and type 'amarok', then I get an error. (It says ```
<unknown program name>(15920)/: KUniqueApplication: Cannot find the D-Bus session server 

<unknown program name>(15919)/: KUniqueApplication: Pipe closed unexpectedly. 
``` ). Had I been sitting at the machine itself and typed "amarok" it would have worked fine. 

So, two questions. 

1. Why did I get this error? Why will a program work when logged in directly but not when logged in remotely via SSH? 

2. (You will have seen this one coming). If I can log in remotely, can I redirect the screen output (i.e. the graphical front end of amarok) to the computer that I am sitting at? Can I do this while leaving the sound output at the remote computer? (i.e. the one I am SSH'd in to) This would allow me to use a laptop as a 'remote control' to a music computer in another room. 

3. (You may have seen this one coming as well). In the scenario above, what if I wanted to bring the sound with me to the machine I am sitting at? i.e. Sitting at a laptop, SSH'd into another machine, with amarok running on that other machine, but with the display on the laptop and the sound coming out of the laptop speakers? 

Hope these questions made sense. (Hope the answer is comprehensible to me as well ... speak slowly.) 

Thanks. 


Oli.

---

### Post by vruum on 2009-07-26
I don't have a remote machine to test with right now, but from ssh'ing the machine I'm sitting at, I might have some ideas.
1)dbus only listens for connection on localhost.
2)try ssh -X [remote ip]
3)it might be easy, Amarok might even support it in some option, but I think it would require you to reroute the sound output to an external machine(pulseaudio is intended for this, but I don't have any experience with it.)something like a samba share or nfs mount might be better for this.

also, you might want to look into something like  [mpd]("http://mpd.wikia.com/") for question 2, which is basically a music playing server running on the remote machine, allowing access from clients running on the network. (remote control)

---

### Post by CatKiller on 2009-07-26
I can confirm that PulseAudio works to do the task in 3). The easiest way is to configure the local machine to use the remote PulseAudio server. You may need to install some of the PulseAudio configuration tools, since I don't think they are installed by default, and then configure the remote machine's PulseAudio Preferences tool to "Enable network access to local sound devices" and "Allow other machines on the LAN to discover local sound devices." You'll then want to configure the local machine's PulseAudio to "Make dicoverable network sound devices available locally."

Alternatively, you could set up multicast streaming with the remote PulseAudio server, but I don't know how one makes that work.

For 2), that is the way it works without something like PulseAudio. X forwarding over SSH will only move the display and input devices to the local machine, since that's what X does. Something simple like MPlayer would work in exactly this way. For the specific case of Amarok, I should imagine that vruum's suggestion that D-Bus only works for localhost (at least by default) is correct. I don't know enough about D-Bus to know if that behaviour can be changed.

Actually, it looks like it is possible in principle, but hasn't been done yet. [This]("http://www.freedesktop.org/wiki/Software/DBusRemote") is the page for the proposed framework.

---

### Post by zcacogp on 2010-05-26
OK, coming back to this after nearly a year, and I have tried it. 

And it works! Two machines, 10.04 on each, and if I ssh using the command vrruum gave me, like this ```
ssh -X <machine name>
``` then fire up amarok from the terminal, the Amarok interface opens on the machine I am sitting at, and the sound comes out of the machine I have ssh'd into!

And it is really pretty cool. I am sure it is simple, but I'm still chuffed! Thanks! 


Oli.

---

