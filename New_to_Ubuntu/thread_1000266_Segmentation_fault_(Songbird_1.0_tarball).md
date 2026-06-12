---
title: "Segmentation fault? (Songbird 1.0 tarball)"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by koffeinöverdos on 2008-12-02
I have been trying for a couple of hours to install songbird and it is killing me here.

I know that the Songbird tar is pre-compiled or whatever so I should simply be able to double click the songbird file inside the extracted folder. When I do, it launches a blank and extremely small window. When I execute it from the terminal it just says 'segmentation fault'. I have tried deleting the .songbird2 folder in my user folder, and i tried doing a file search for 'songbird' on my whole linux installation and deleting everything that has to do with it. This same thing happened to me once in Windows with Songbird 0.4...

Anyone have any ideas?

---

### Post by Diabolis on 2008-12-03
If you know how to program, a segmentation fault would mean that you tried to access a non existent memory space.

Since you didn't write Songbird, all what it means is that the code is screwed and you should get a different version. Don't forget to report the bug at Songbird site.

---

### Post by OldGrey on 2008-12-03
To make you life easier I suggest that you try the deb file from GetDeb - [www.getdeb.net](www.getdeb.net) I am using the 64bit version and it works really well.

---

### Post by thirdgen89gta on 2009-03-18
Does anyone else have an idea what else to look at?  I've tried the straight tar file, I've tried the debs too.  This just recently happened to my system and I'd previously happily been using Ubuntu 8.10 x64 with Songbird 1.0 on my machine.

I've tried launching it from a terminal window and I end up with the segmentation fault.

Is there any other way to get more details out of the error?  searches on google for songbird segmentation fault don't turn up much.

While I have no problems setting up a ubuntu system I am still very much a n00b with linux and am not totally familiar with all of the command line stuff.  I can follow directions well enough though.

I've completely uninstalled songbird.  As well as tried launching it with songbird -p to open the profile manager, i've also deleted my profile to see if it is my profile thats causing the problem but the error remains all the same.


I'm not sure if this will work for everyone, or even how related it may be.  I started having a problems with Songbird a few days ago, and couldn't figure out why.  I recently had a thought that perhaps the global menu I installed through synaptic might have caused some problems (it made other problems for me as well).  So I uninstalled the global menu, and wala, the next time I started Songbird it came up asking to create a new profile, instead of a segmentation fault like before.

This may help others, or may not have anything to do with the segmentation fault.  This is the only change i've made since the problem started up.

---

### Post by arcane14 on 2009-08-11
> **koffeinöverdos said:**
> I have been trying for a couple of hours to install songbird and it is killing me here.

I know that the Songbird tar is pre-compiled or whatever so I should simply be able to double click the songbird file inside the extracted folder. When I do, it launches a blank and extremely small window. When I execute it from the terminal it just says 'segmentation fault'. I have tried deleting the .songbird2 folder in my user folder, and i tried doing a file search for 'songbird' on my whole linux installation and deleting everything that has to do with it. This same thing happened to me once in Windows with Songbird 0.4...

Anyone have any ideas?
Bump. 

Same problem. Totally removed Songbird. Then manually removed every file containing songbird. Removed libvisuals plugins. Reinstalled. Still crashes on segmentation fault. Terminal output below: 

joe@Arcanix:~$ songbird
LOGIN PHASE: handshake
handshake session key: ddcdb5c049136bc215a96be7d05c0ef8
LOGIN PHASE: user info/profile download
LOGIN PHASE: not actively logging in
Segmentation fault

---

### Post by gardara on 2009-08-12
It could be a good idea to give the guys at the songbird irc channel a shout

---

### Post by lestwilley on 2009-08-16
I had the same problem; after removing all packages supporting gnome global menu from synaptic, songbird worked fine.

---

