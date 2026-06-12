---
title: "Script to run unison automatically?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by geekyhawkes on 2009-03-03
Hi;

I have recently installed unison to ensure my netbook / laptop & NAS all stay up to date with the right version of files when I am working "offline" (I.E away from my NAS). 

Unison is working great for my needs, but I would like to be able to run it automatically each time I am connected to my WIFI network at home (the way i connect to my NAS).

My NAS auto mounts when I have WIFI to my home network and would like some guidance if there is a way to script the running of unison whenever my wifi connects.

Any help would be useful, 

Thanks Andy

---

### Post by geekyhawkes on 2009-03-06
Can someone help me with this?  It must be possible?

---

### Post by keithweddell on 2009-03-06
I'm not well up on this but might have a couple of suggestions that you could look into:

If you look in the /etc/network directory, there are several sub-directories which contain scripts that are run automatically when the network connects or disconnects.  You might be able to do what you want by putting a script in the appropriate sub-directory.

Can you use udev?  Not really sure but you could look in /var/log/messages to see if anything useful is logged when the network connects.  This might then enable you to write a udev rule to trigger a script.

Not very helpful I know but it might give you a starting point.


Keith

---

### Post by geekyhawkes on 2009-03-07
Thanks.  I will have a look and see what i can find.  Any other suggestions welcome.

---

