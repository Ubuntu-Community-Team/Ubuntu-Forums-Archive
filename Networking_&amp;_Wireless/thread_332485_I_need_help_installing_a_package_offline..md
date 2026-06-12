---
title: "I need help installing a package offline."
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by Quillz on 2007-01-06
I'm trying to install ndisgtk on my desktop computer, which has no Internet access, since my DWL-122 network USB network adapter isn't currently recognized by Ubuntu. Unfortunately, wireless is my only means of connecting the desktop to the Internet; I simply have no means of using an Ethernet cable. As such, I've downloaded the .deb for ndisgtk, as well as its dependency, ndiswrapper_utilities. Unfortunately, every time I try to install ndisgtk, it fails because it's trying to install ndiswrapper_utilities from the Internet. Is there any way to somehow merge the two packages together, or force ndisgtk to search my hard drive for the dependency?

---

### Post by xiaoxin on 2007-01-06
install ndiswrapper_utilities first after that install ndisgtk

---

### Post by Quillz on 2007-01-06
I can't install ndiswrapper_utilities. I get an error message about "dependency is not satisfiable."

---

### Post by xiaoxin on 2007-01-06
so look in the messages you get what ndiswrapper_utilities depends on and install those first

---

### Post by Quillz on 2007-01-06
> **xiaoxin said:**
> so look in the messages you get what ndiswrapper_utilities depends on and install those first
Here's what I see when I try to install the package...

---

### Post by xiaoxin on 2007-01-06
Ok got it, you didn't download the real ndiswrapper utilities but the dummy package, which in an online system would download the needed packages.
download this one and try again [http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils-1.1]("http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils-1.1")

---

### Post by Quillz on 2007-01-06
I just turned off my desktop, so I'll try this first thing tomorrow and let you know if it's worked or not. Thanks.

---

### Post by Quillz on 2007-01-06
Alright, I still haven't been able to install anything yet because of all the dependencies.  It seems now I need the module_source package, as well as the PERL package. So there is no way whatsoever to combine _everything_ into one huge package, and just install that?

---

### Post by xiaoxin on 2007-01-06
no not really, why dont you just download all dependencies from the packages site.
you can see there which package relies on what.
or compile from source the dependencies are faster to fix than the .deb way

---

### Post by xiaoxin on 2007-01-06
if i were you i would save myself a lot of time and headaches and just buy a NIC which are very cheap

---

### Post by Quillz on 2007-01-06
> **xiaoxin said:**
> if i were you i would save myself a lot of time and headaches and just buy a NIC which are very cheap
I most likely will. They seem to be recognized natively, as opposed to a USB dongle.

---

### Post by Quillz on 2007-01-06
Do you have any suggestions for what desktop NIC I should purchase? I was hoping to use D-Link, but I'm not sure if they work well with Ubuntu.

---

### Post by xiaoxin on 2007-01-06
I have no experience with dlink but any card with a realtek or 3com chip will work out of the box

---

### Post by Quillz on 2007-01-06
And it will say on the box if it has a realtek or 3com chip?

And you've been very active in all my help threads, so thanks very much.

---

### Post by xiaoxin on 2007-01-06
well i guess if it doesnt say you can always ask them to let the show you the card so you can check most of the time they don't make a problem about that, and i assume the person selling it will also know.

No problem glad to help :)

---

