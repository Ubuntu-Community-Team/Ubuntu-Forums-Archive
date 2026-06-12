---
title: "What the HELL do you mean dependency not met!?!?"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by Ninwa on 2011-04-03
Hey, where do I begin to start resolving something like this? How do I dig deeper into exactly what the software center wants from me?

Error:
[IMG]http://i.imgur.com/JTRVt.png[/IMG]

1.7.2 not >= 1.7.1?
[IMG]http://i.imgur.com/inZdd.png[/IMG]

Note: Ogre 1.6.(something-rather) is what is included with 10.10. I had to include Ogre's own sources to upgrade to their 1.7.2 version. I don't know if this is of consequence. Also, OpenMW (A really cool project, check it out) is also not in the standard repository. 

Could it be a problem with their own packaging? Or, more probably, I'm missing something.

Any help appreciated.

Edit: Oh, and yes I've tried 1.7.1, same thing.

---

### Post by wolfen69 on 2011-04-03
First I would open synaptic and go to settings>repositories to make sure they are all checked off.

---

### Post by Ninwa on 2011-04-03
> **wolfen69 said:**
> First I would open synaptic and go to settings>repositories to make sure they are all checked off.

Are synaptic and "ubuntu software center" the same thing? I remember synaptic being the packaging manager before the software center came around.

Edit: Nevermind, opened synaptic with 'synaptic' at command line.

---

### Post by Ninwa on 2011-04-03
> **wolfen69 said:**
> First I would open synaptic and go to settings>repositories to make sure they are all checked off.

Ok, not sure what you meant by "check off." As in, turn them off? Or, check them, turning them on? Either way, these were off, I turned them on and updated.

[IMG]http://i.imgur.com/WVgXP.png[/IMG]

I don't know that this made a difference, I suspect it didn't. I opened Synaptic, but it just seems to be a different interface for what I was already trying. On a lark I used it to uninstall an older version of libogre and try reinstalling 1.7.2

[IMG]http://i.imgur.com/Q4K5V.png[/IMG]

The result is the same, OpenMW thinks I'm missing a version of libogre >= 1.7.1. Shouldn't 1.7.2 meet this requirement?

---

### Post by kevdog on 2011-04-04
Why don't you uninstall 1.72 and reinstall the version just previous to this?

---

### Post by ikt on 2011-04-04
> **Ninwa said:**
> The result is the same, OpenMW thinks I'm missing a version of libogre >= 1.7.1. Shouldn't 1.7.2 meet this requirement?

You would think so but having a guess it might be further along, like 

>= 1.7.1-ubuntu1

which means

1.7.1-ubuntu2
1.7.1-ubuntu3
1.7.1-ubuntu4

or 1.7.1.4

1.7.2 is a whole new level.

That's my guess anyway.

> I had to include Ogre's own sources to upgrade to their 1.7.2 version. I don't know if this is of consequence

Yep that's the consequence, got to keep all the packages in line, but as suggested above, you will have to try removing the 1.7.2 version and go back to 1.7.1 to get it to work.

Otherwise I recommend getting VirtualBox and mucking around in that if you can, a lot easier to mess with because if you screw up can just exit and reload!

---

### Post by Ninwa on 2011-04-04
> **kevdog said:**
> Why don't you uninstall 1.72 and reinstall the version just previous to this?

Both 1.7.1 and 1.7.2 give me the same dependency error when trying to install the OpenMW package. That's my confusion. :)


> **ikt said:**
> You would think so but having a guess it might be further along, like 

>= 1.7.1-ubuntu1

which means

1.7.1-ubuntu2
1.7.1-ubuntu3
1.7.1-ubuntu4

or 1.7.1.4

1.7.2 is a whole new level.

That's my guess anyway.



Yep that's the consequence, got to keep all the packages in line, but as suggested above, you will have to try removing the 1.7.2 version and go back to 1.7.1 to get it to work.

Otherwise I recommend getting VirtualBox and mucking around in that if you can, a lot easier to mess with because if you screw up can just exit and reload!

I'm going to try a little harder to get it working. I'll see if I can find a way to get a 1.7.1-(something higher than 1) installed and I'll let you know if that fixes it.

Edit: Response on the OpenMW forum says that I indeed was reading the dependency list wrong, and that unless I compile OpenMW with 1.7.2 I will need to find 1.7.1-2 or somesuch to use the .deb installer. I'm going to look into this and will report any success.

Second edit: No such minor revision between 1.7.1 and 1.7.2 exist, at least not on Ogre's sourceforge repository. - [http://sourceforge.net/projects/ogre/files/ogre/1.7/](http://sourceforge.net/projects/ogre/files/ogre/1.7/) - Leaves me confused. The OpenMW .deb may be broken, not sure.

Cheers:)

---

### Post by ikt on 2011-04-04
> **Ninwa said:**
> The OpenMW .deb may be broken, not sure.

Cheers:)

I reckon it's broken, not working in Ubuntu 11.04 stock either.

---

### Post by Ninwa on 2011-04-04
> **ikt said:**
> I reckon it's broken, not working in Ubuntu 11.04 stock either.

Well, in the spirit of linux, I built a package myself if anybody else wants to check it out. Only built on amd64.

[IMG]http://i.imgur.com/Y6mAr.png[/IMG]
[http//www.josephbleau.com/openmw_0.10.0-1_amd64.deb]("http//www.josephbleau.com/openmw_0.10.0-1_amd64.deb")

Alternatively, check out [www.openmw.com](www.openmw.com) if you want to build from source yourself.

Cheers all.

---

