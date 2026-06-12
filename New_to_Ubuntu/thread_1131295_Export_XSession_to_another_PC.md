---
title: "Export XSession to another PC?"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by chris062689 on 2009-04-20
I've heard your able to do such a thing.
Is that kind of like VNC?
Is it the whole XSession, or simply programs?
Will it render everything on the server, and then send it to the client?
(Meaning, I can play Videos, Games w/ Wine, and then have it sent to an Eee PC?)

Would there be lag?

If someone could explain to me what exactly is possible with Exporting an XSession, that would be great!

---

### Post by boblemur on 2009-04-20
you should look at ssh -Y or -X they both provide xforwarding.

so for example you can run..

ssh -Y user@serverip

and once you login

run firefox

and it will open firefox on your local machine even though its actaully running on the server.

i found it hard to get the entire session to work. but it is possible by running startX from within somewhere that dosent already have a running copy of X.

if you have anymore qn's ask away.

---

### Post by chris062689 on 2009-04-20
So say I run a graphically intense program, does it do the processing on the client or server?

In theory, could I run say... Half Life 2 (or a Playstation emulator) through "run wine hl2.exe" or run pcsx2" and have it use the GPU and CPU from the server, and then send it on to the client?

I have an Eee PC 1000HE and a E7200 @ 3.7Ghz / 9600 GT and wanted to see if it was possible to use more intensive apps like that through exporting the Xsession.

---

### Post by chris062689 on 2009-04-21
I just tried doing it.
PCSX2 didn't run at all, and the NES emulator ran painfully slow.
So my reasoning is, that it does all of the CPU / GPU rendering on the client.

What I'd love to put together is a way to setup a server stream, while controling the mouse / keyboard of the server.

That way, I could play GPU intensive content, while not having to worry about having a powerful enough netbook!

Does something like this exist?  :O
(I know streammygame does, but it doesn't have a Linux Server, plus it kind of sucks.)

---

