---
title: "What ports need to be open for Ubuntu Printer Sharing to work?"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by diablo75 on 2010-03-20
I used to have no problem printing to a computer in the next room on the network that has a printer attached to it.  But then I installed Firestarter for some reason and I'm having a hard time figuring out what it might be blocking.  I have all the settings on both PCs the way their supposed to be, per the community guides that tell you how to share a printer over a network:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Ubuntu%209.04](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Ubuntu%209.04)

This method does not use Samba, and if possible, I'd rather like to avoid using Samba if I can use the default stuff instead.  I just think it somehow might be blocking a port necessary for this to work on perhaps one or both computers.

---

### Post by Ozymandias_117 on 2010-03-20
Are you saying that you can't see the printer on the other computer at all? Or just can't connect?

If it's just that you can't connect, you can try running firestarter, attempting to connect, then looking at the "Events" tab. You should be able to see the ports it's trying to connect through.

---

### Post by doorknob60 on 2010-03-20
631 maybe? I know that's the port used for the CUPS web interface, so that's my educated guess :)

---

### Post by diablo75 on 2010-03-20
I can't see the printer at all.  The server is running and supposedly publishing shared printers.  The client is supposed to be showing published printers but isn't.  I even tried to open port 631 on both computers via firestarter.  No dice.  I also tried to trigger events in firestarter by doing refreshes but nothing showed up.

---

### Post by diablo75 on 2010-03-21
Holy crap, I just figured out the problem.  Or at least something that fixes it.

First, for good measure, I went into Firestarter and made a blanket policy on each PC that basically allows connections of all types from my PC's IP address, as well as the server to my PC.

That didn't work.

But then, while I had my Printer Configuration panel up, I click on Server>Connect...

It asks you to type in a CUPS server address and there's a bunch of stuff already in the line that looks more like a local system pathway.  So I just replaced it with the IP address of the server.  BOOM!  There's the printer!  That was all I had to do.  Wow, I feel dumb.


BIG EDIT:  Take all the above back.  What did happen was I got the Printer to appear on the client PC like I've been trying.  But I still can't print to it.  I just tried to print from Gimp and nothing shows up in the Print Setup dialog except the Print To File feature.  If I double-click on the printer icon in the printer configuration panel and attempt to send a test-page, it just does nothing.  No error message, no icon on the task bar on the server to indicate a job is processing and printing.  Not sure what's wrong now...

---

