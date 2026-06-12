---
title: "Installing Octave in Ubuntu Studio"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by najjems on 2011-07-05
Hi, forgive me if there's a previous thread about this, but I just can't find one through search.   anyways, I'm trying to install octave in ubuntu-studio (which is also install in VirtualBox on Win7.)   in the install.txt it says after './configure', I should compile by typing 'make', but when I do it says:   make: *** No targets specified and no makefile found. Stop.  how do i continue with my installation?

---

### Post by beew on 2011-07-05
Octave is in the repository.

---

### Post by najjems on 2011-07-05
uhm, I don't understand. can you expound on that? thanks.

---

### Post by pjd99 on 2011-07-05
Search for it in Synaptic.

or
```

sudo apt-get install octave3.2

```Synaptic is probably the better option, as it will list the extra toolkits available. e.g. if you require dsp, you'll need octave-signal

EDIT: It is also in the Ubuntu software centre, but has very few add-ons listed.

---

### Post by pjd99 on 2011-07-05
> **najjems said:**
> uhm, I don't understand. can you expound on that? thanks.

If the software is in the repositories, it means you don't have to download the source code and compile the software yourself. You just search, select, and install with a few mouse clicks.

---

### Post by najjems on 2011-07-06
okay i understand now, but actually I did those two options before, but amazingly it works now (sort of) I'm not sure what I did wrong the first time.  Thank you so far!  
but now I have a new problem. after I typed "sudo apt-get install octave3.2" it said:  
 unable to lock the administration directory, are you root?   
 possibly I'm not, so does that mean i need to change directory to the root folder? I tried cd root, or sudo cd root, but I can't get in. :P

---

### Post by Elfy on 2011-07-06
If this is the first user then it means that you have another package manager open at the same time as trying to use apt-get. Close synaptic/add-remove/software centre and try again.

---

### Post by pjd99 on 2011-07-06
If you found octave3.2 in Synaptic, don't worry about using apt-get. In this case, Synaptic is the much better option as you can see all the add-ons by searching for "octave" and selecting the ones you need.

If you haven't used Octave before, and it's been sold as a Matlab replacement you just have to get used to to its command line interface, as it's lacking the workspace environment Matlab has.

---

