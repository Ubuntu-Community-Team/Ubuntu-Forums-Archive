---
title: "Creating Online 3D Environments"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by MaxVK on 2009-05-09
Perhaps a strange question, but here goes:

There is an old building, quite a large one although only a single story high, and it is due to be knocked down. I have a great many photos of the place, and I have access to get more.

I would like to create some kind of online environment where people can use the keyboard much like a FPS to walk around inside the building, which will of course have photos for textures etc. NO characters or animations are required.

Iv been searching about for various X3D/VRML type solutions, but so far Iv come up with nothing that I can use (Things seem to be mostly Windows based). If thats the way it has to be then fine, just so long as the final result can be viewed in a web browser by anyone on any OS.

I have no preference about HOW exactly the environment is made, just so long as it can be used by a browser (or perhaps via a *smallish* viewer download)

Anyone got any ideas?

cheers

Max

---

### Post by Alterax on 2009-05-09
For something like that, I really recommend SecondLife or Opengrid, as all of the tools you need are built into it.

Another option--slightly more difficult but more accessible to people that don't have these viewers--would be to create a wireframe, apply your pictures as a texture, and to write an applet using java and java's irrlicht implementation (jirr).  Irrlicht is an open-source 3D game engine for C++; either it or jirr can be found on sourceforge.net.  

For something akin to what you are doing, it really wouldn't take all that much code, and the applet containing the structure, pictures, and viewer can be embedded in a webpage.

---

### Post by MaxVK on 2009-05-09
Cheers Alterax - Iv looked at SecondLife before, but it would take some considerable money to buy an area and then build on it, and anyone who wanted to look at it would have to join SecondLife and contact me so that I could allow them to enter. Unfortunately that not really an option.

Whatever this ends up as it should be viewable on a web page, or perhaps on the desktop via a small viewer download. Membership etc, should not be a requirement.

Ill take a look at Opengrid when I'm done here, but if its along the same lines as SecondLife the same problems will apply.

Programming is not a problem - I'm currently into Python, but I can swap about without too many issues. Ill look into the Java possibility as well, since that sounds exactly what I need, although to date Iv not written any applets in Java.

Thanks for your input

Max

---

