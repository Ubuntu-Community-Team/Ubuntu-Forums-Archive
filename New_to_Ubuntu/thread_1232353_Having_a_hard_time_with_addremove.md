---
title: "Having a hard time with add/remove"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by anotherghost on 2009-08-05
Hello forums:

I'm having a hard time installing DosBox through the repositories.  When I search for it, it comes up and I click it and add it, but then during downloading, I get this:


> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/s/sdl-net1.2/libsdl-net1.2_1.2.5-7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/s/sdl-net1.2/libsdl-net1.2_1.2.5-7_i386.deb)
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/d/dosbox/dosbox_0.71-0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/d/dosbox/dosbox_0.71-0.1_i386.deb)
  404 Not Found [IP: 91.189.88.46 80]


I have no idea what to do about that.  Can anyone point me in the right direction?

Thank you!

---

### Post by rCXer on 2009-08-05
Try downloading it from the karmic repositories [here at the bottom of the page](http://packages.ubuntu.com/karmic/dosbox).

---

### Post by anotherghost on 2009-08-05
Hmmm... well, tried that, but now when I open the package installer it's saying "Error: Dependency is not satisfiable: libasound2."

---

### Post by oldos2er on 2009-08-05
Which version of Ubuntu are you using?

---

### Post by colau on 2009-08-16
> **anotherghost said:**
> Hello forums:

I'm having a hard time installing DosBox through the repositories.  When I search for it, it comes up and I click it and add it, but then during downloading, I get this:




I have no idea what to do about that.  Can anyone point me in the right direction?

Thank you!
Broken mirror.

---

### Post by mrbiggbrain on 2009-08-16
> **colau said:**
> Broken mirror.

you could try commenting out the bad mirror if its not a major one and retrying :-) it should be in your sources.list file.

---

### Post by zvacet on 2009-08-16
**System>admin>software sources**>check that you have **universe **repository enabled.If you do then try to change server.

---

### Post by colau on 2009-08-16
> **mrbiggbrain said:**
> you could try commenting out the bad mirror if its not a major one and retrying :-) it should be in your sources.list file.
Thank you for your suggestion.

---

