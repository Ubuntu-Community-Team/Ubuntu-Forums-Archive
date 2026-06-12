---
title: "Virus or Bug?"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by ubalderdash on 2009-03-02
I am running the Intrepid Ibex in a 32bit file system with Nvidia graphics. Recently, I have encountered a recurring problem that manifests itself in a manner that suggests a virus attack. I realise that this cannot be so in a Linux based system, but the impersonation is almost perfect. What happens is that occasionally (roughly two or three times per hour) my mouse pointer will suddenly take off on its own and go whizzing about at great speed opening all sorts of files, creating four or five untitled folders and flashing from one workspace to the other. After about five seconds it settles back to normal and I'm able to repair the damages and return to my work. I have not been able to pinpoint any software that may be causing this except perhaps a suspicion of internet interactive programs such as Firefox, Transmission, Songbird, or Google Earth? Naturally I have tried eliminating each of these by un-installing them, but so far to no avail. However if none of the above are working the problem seems to remain dormant.
Before anyone asks, I do have the Avast anti-virus program installed although I also understand that this serves only to protect my Windows based correspondents.
Any help or suggestions would be very much appreciated.

---

### Post by hyperyoda on 2009-03-02
> **ubalderdash said:**
> I am running the Intrepid Ibex in a 32bit file system with Nvidia graphics. Recently, I have encountered a recurring problem that manifests itself in a manner that suggests a virus attack. I realise that this cannot be so in a Linux based system, but the impersonation is almost perfect. What happens is that occasionally (roughly two or three times per hour) my mouse pointer will suddenly take off on its own and go whizzing about at great speed opening all sorts of files, creating four or five untitled folders and flashing from one workspace to the other. After about five seconds it settles back to normal and I'm able to repair the damages and return to my work. I have not been able to pinpoint any software that may be causing this except perhaps a suspicion of internet interactive programs such as Firefox, Transmission, Songbird, or Google Earth? Naturally I have tried eliminating each of these by un-installing them, but so far to no avail. However if none of the above are working the problem seems to remain dormant.
Before anyone asks, I do have the Avast anti-virus program installed although I also understand that this serves only to protect my Windows based correspondents.
Any help or suggestions would be very much appreciated.

I'd bet on it being a driver problem, specifically with the mouse. What type of mouse do you have? Look in /var/log/messages for an error such as:

messages.0:Mar  2 08:14:07 ubuntu kernel: [4329456.490000] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.


Zach

---

### Post by sahabcse on 2009-03-02
Hi

Have you install wine? Also check same issue in all the user in your system

---

### Post by ubalderdash on 2009-03-02
Well spotted and absolutely correct, I have lots of messages of that type concerning my rather ordinary Logitech PS2 Optical Mouse.
How could I update my mouse driver?

---

### Post by ubalderdash on 2009-03-02
> **sahabcse said:**
> Hi

Have you install wine? Also check same issue in all the user in your system

Thanks for that reply and yes I do have Wine installed. However, for the moment I am not using it for any programs.

---

### Post by gandaran on 2009-03-02
> **ubalderdash said:**
> Well spotted and absolutely correct, I have lots of messages of that type concerning my rather ordinary Logitech PS2 Optical Mouse.
How could I update my mouse driver?
buy a new one, I had the same problem, bought a new one and problem fixed!

---

### Post by ubalderdash on 2009-03-02
Thanks to all of you for helping me tame my mouse. I have run my computer with a USB mouse I usually use with my notebook and it does seem to be the solution.

Because the port is there and cannot be used otherwise, I will replace my mouse with another PS2 rather than USB.

Can anyone recommend a brand that works well with Ubuntu?

---

### Post by Trebaruna on 2009-03-02
Basically a mouse should Just Work AFAIK. I've used Logitech mice and trackballs and now I've got an el-cheapo "Genius" brand mouse. They all work just fine.

---

### Post by scratman on 2009-03-02
If you manage to find a PS/2 mouse that doesn't work, we'll send you a prize!

---

### Post by boof1988 on 2009-03-02
> **scratman said:**
> If you manage to find a PS/2 mouse that doesn't work, we'll send you a prize!

I'll help chip in on the prize money ;)

I found a cheapo ($10) laser mouse at a local (independent) computer shop.  It says MTG on the top and the wire is very small (small wire can be good and bad).  But it works like a charm.  Scroll-wheel schrolls and clicks for the (middle-click).  Everything works as needed OOB.

---

### Post by Bearly Able on 2009-03-02
We had a Logitech optical mouse that did a similar thing under Windows XP, although not nearly so spectacularly!  The mouse we have now is a Logitech RX250 optical mouse, which can be used as USB or PS2.  We have it in the PS2 port and it works fine with both XP and Ubuntu.  (Oddly enough, I gave the previous mouse to someone else with an XP system and they've had no trouble with it.)

---

