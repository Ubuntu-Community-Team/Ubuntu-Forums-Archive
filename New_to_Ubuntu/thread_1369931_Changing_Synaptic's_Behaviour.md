---
title: "Changing Synaptic's Behaviour"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by wyatt roberts on 2010-01-01
I downloaded and used APTonCD to make recovery easier when needed.  Last night I tried to use synaptics package manager to download a set of packages.  Everything worked as it usually does and then I got a message to "please insert AptOnCD121909..." I tried to insert the CD and it tried to auto start and I cancelled that but then it failled and the package manager failed too.  It was really late and I should have paid more attention but I used the console to do something sudo...( sorry, I can't recall) and I was successful with downloading and installing my packages with synaptics.  But it is the behaviour I want to change.  I removed CD-ROM from Settings > Repositories > Other Software and from Settings > Repositories > Ubuntu Software (Unchecked the checkboxes).  But still, having made those changes, it still insisted that I insert that AptOnCD CD and then failed as described above.  I even restarted and still met the same result untill I did whatever-I-did using Sudo...
I am even more unhappy that I don't recall what I did, because until I fix the behaviour of the synaptics package manager, I will have to go stumbling around again next time I am afraid.

Thanks for any advice.
wr

---

### Post by jbrown96 on 2010-01-01
You might have entered it manually in /etc/apt/sources.list or perhaps there was an error removing it from there.

Take a look at the file and try to remove anything that looks like > deb cdrom:[Kubuntu 9.10 _Karmic Koala_ - Beta amd64 (20090929.2)]/ karmic main restricted
 but will say aptoncd or whatever (just CD related).

You can edit the file with ```
gksu gedit /etc/apt/sources.list
```

---

### Post by wyatt roberts on 2010-01-01
> **jbrown96 said:**
> You might have entered it manually in /etc/apt/sources.list or perhaps there was an error removing it from there.

Take a look at the file and try to remove anything that looks like  but will say aptoncd or whatever (just CD related).

You can edit the file with ```
gksu gedit /etc/apt/sources.list
```

I looked as you suggested.  Those lines were there and have been removed successfully. I will have to look for something to install via synaptics to test it. 

Your suggestion makes sense.  I would have expected that making the correction in the GUI would have corrected the sources.list.  In any event, I truly appreciate you help.

I'm pretty sure this should do it.  When I check it I will investigate how to mark this one "Solved."  Thanks again.

Sincerely,
Wyatt

---

