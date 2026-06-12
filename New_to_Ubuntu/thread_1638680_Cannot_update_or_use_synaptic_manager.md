---
title: "Cannot update or use synaptic manager"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Johnce on 2010-12-05
Hello all! This is my first post and I'm a very new to Ubuntu and *nix systems in general so bear with me a little . . . When I tried to open synaptic manager I got the following error
E: Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/erik-b-andersen-rgba-gtk-maverick.list

The same error pops up if I try to $sudo apt-get update

So I tried to purge the PPA (**ppa:erik-b-andersen/rgba-gtk)** using Ubuntu tweak and using ppa-purge both with no success. 

I'm lost and stuck . . . how do I fix this  . . . 

-johnce

---

### Post by beew on 2010-12-06
This is not what ppa purge is for. You use ppa purge to purge software installed from the ppa and downgrade them to the next available versions in your repositories(excluding said ppa). But you haven't installed anything, the system got stuck trying to parse the ppa.

To remove the ppa, open Synaptic, go to Settings > Repositories > Other Sofware, find the entry for the problematic ppa and uncheck the box, close the dialogue box and reload Synaptic, that's it.

Alternatively you can edit the sources list from the terminal
```
 sudo gedit /etc/apt/sources.list 
```
remove the offending line and save the change.

---

### Post by Johnce on 2010-12-06
This is the error I get when I try to open synaptic 

E: Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/erik-b-andersen-rgba-gtk-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


and synaptic closes

and I could not find the line using the terminal command (to be honest I'm not entirely sure what I was looking at)

sorry, I'm new but trying 

johnce

---

### Post by beew on 2010-12-06
If you cannot even open Synaptic then you only option would be to edit the sources list. See the alternative method in my post above.

P.S. That happened to me before. :)

---

### Post by Johnce on 2010-12-06
I got it to work! 
TY Beew :)

---

