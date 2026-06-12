---
title: "How to change printer port"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by Historynut on 2010-04-09
My printer is set up using the parallel port. It is plugged into the computer's usb port. How do I change the parallel port to usb? When it tries to detect the printer it pops up with parallel and I can't find any way to change it. How do I recall the printer dialog so that this can be corrected? [EMAIL="wileye@sonic.net"]wileye@sonic.net[/EMAIL]

---

### Post by cogier on 2010-04-09
What make and model of printer is it and what version of Ubuntu are you using?

---

### Post by WinterRain on 2010-04-09
Did you check in System>Administration>Printing?

---

### Post by quadproc on 2010-04-09
> **Historynut said:**
> My printer is set up using the parallel port. It is plugged into the computer's usb port. How do I change the parallel port to usb? When it tries to detect the printer it pops up with parallel and I can't find any way to change it. How do I recall the printer dialog so that this can be corrected? [EMAIL="wileye@sonic.net"]wileye@sonic.net[/EMAIL]
You should be able to install another printer (actually the same one, but the computer will think that the printer is different because it is connected to a different port) from System > Administration > Printing; select New.

I am assuming that you are not doing something like a using a printer server, a networked printer, or anything fancy.

quadproc

---

### Post by Historynut on 2010-04-12
I am using Ubuntu 9.1. Printer is HP Deskjet 500. When I try System>Administration>Printing>New (even after deleting the printer) it does a detection search (whether the printer is on or not) and ends up with it out of parallel port #1. There is no parallel port in the computer.

---

### Post by sydbat on 2010-04-12
> **Historynut said:**
> I am using Ubuntu 9.1. Printer is HP Deskjet 500. When I try System>Administration>Printing>New (even after deleting the printer) it does a detection search (whether the printer is on or not) and ends up with it out of parallel port #1. There is no parallel port in the computer.Did you install the HP drivers? Search for hplip in Synaptic.

---

