---
title: "Printing Over the Web?"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by Chrissd on 2011-06-06
Hi all,

Apologies if I understand this wrong, however, I currently have a network printer which works perfectly. I want to be able to print remotely, could I just set up my router to forward the relevant port to the printer and point cups to my DynDNS address?

Is there a better way of being able to print remotely? Perhaps using SSH somehow?

I asked at University and VPNs were mentioned a lot, and despite reading several websites, I don't really understand much about them and it seems a lot of hard work for something that I think must be relatively simple to achieve.

---

### Post by iclestu on 2011-06-06
> **Chrissd said:**
> Hi all,

Apologies if I understand this wrong, however, I currently have a network printer which works perfectly. I want to be able to print remotely, could I just set up my router to forward the relevant port to the printer and point cups to my DynDNS address?

Is there a better way of being able to print remotely? Perhaps using SSH somehow?

I asked at University and VPNs were mentioned a lot, and despite reading several websites, I don't really understand much about them and it seems a lot of hard work for something that I think must be relatively simple to achieve.

forgive the question....

why???
I mean i just dont understand the logistics... why print from over the internet when you surely need to be AT the printer to collect the hard copy of the document?

Am I missing something?

---

### Post by JustinR on 2011-06-06
I have a wireless printer at home - its much easier to print from it without having to set it down and attach it to a bunch of cords - especially if it's a laptop computer.

What kind of printer do you have, is it a wired (ethernet) or wireless printer? And what brand is it? HP's work exceptionally better than the rest.

According to your original post though, it appears to be wired. So you should be correct in the sense that you can plug it straight into the router.
The easiest way to set it up after that would be to go into (I'm not sure if this is different on Xubuntu 11.04) Applications > System > Printing, then click the green + sign, Click 'Network Printer' and then 'Find Network Printer', if that doesn't work, enter in the IP address of the printer and it should find it.

Good Luck!

---

### Post by iclestu on 2011-06-06
yeah - wireless I get. Remote over internet i dont...

 (I have a wireless printer myself working under linux but cant really  offer any support assistance as the manufacturer for mine kindly  supplies a .deb that was justa double click and go... :) )

---

### Post by Chrissd on 2011-06-06
Hi,

It is a wired HP Laserjet. It works fine at the moment, just internally on the network.

As to why, simply because when at University, especially between lectures. I often have to read bits and pieces of documents for assignments, and it'd be nice to be able to print them without having to save the whole document or bookmark the page so when I get home I can grab what it was I wanted printed.

---

### Post by mikewhatever on 2011-06-06
I doubt that exposing a printer to the web is a good idea. Sure, it's easy, and you'll be able to print, but how do you prevent the rest of the world from using it?

A better way would be to set up a secure remote login to one of the computers at home and print from it. VPN is one of the ways, but a simply remote desktop login would be easier. I'd suggest using TeamViewer (really easy), or to tunnel VNC over SSH (somewhat advanced).

---

### Post by Chrissd on 2011-06-06
Cool, I'll look into other options.

I'll mark it down to a non-starter.

---

