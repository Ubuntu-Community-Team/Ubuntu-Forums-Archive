---
title: "Ubuntu 10.10 Troubles: extreme errors"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by AlvitrValkyrie on 2011-02-18
So, things have been working very horribly lately.

The Linux version of Skype seems to not work well, and the upgraded version is worse. however, I believe that's not a problem with Ubuntu.

I tried to install Goober, a service much like Skype. The instructions for installation made me think I should add something to the repositories. [as root] I did. Everything was working fine until I refreshed the Synaptic Manager.

Now I get an error: 
[B]E: Malformed line 53 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/B]

I rebooted my computer, and the update manager opened.
I got an error again:
[B]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 53 in source list /etc/apt/sources.list (dist parse)'

[/B]Any ideas of how I could fix this? And could anyone tell me how to install goober properly?
Thanks!

---

### Post by AlvitrValkyrie on 2011-02-18
Fix:

Sort of obvious... I right clicked the Update icon and meandered my way to deleting my goober entries.

Can someone still help me install Goober ^^ Ah... I wonder if the new Skype update will work. I believe it's the one I tried...

---

### Post by Evanfox on 2011-04-05
Hi I kinda have the same issue as you did, so I would appreciate if you could let me know how exactly you sorted that out!

Cheers
Evan

---

