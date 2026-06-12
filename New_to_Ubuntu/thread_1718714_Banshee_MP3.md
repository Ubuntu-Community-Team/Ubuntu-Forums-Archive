---
title: "Banshee MP3"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-03-31
I recently got Banshee Media Player. I subscribed to and downloaded podcasts through Miro Guide, but Banshee won't play them because they are not Ogg Vorbises! Is there any way I can get Banshee to play MP3s? I gotta listen to my MacBreak Weekly!:)

---

### Post by aaaaalex on 2011-03-31
This should do the trick:

Open a terminal. Then execute
```
sudo apt-get install ubuntu-restricted-extras
```

I never used banshee though. So its just a guess ;-)

---

### Post by doppel.ganger on 2011-03-31
I recently got Banshee Media Player. I subscribed to and downloaded podcasts through Miro Guide, but Banshee won't play them because they are not Ogg Vorbises! Is there any way I can get Banshee to play MP3s? I gotta listen to my MacBreak Weekly!:D

---

### Post by bodhi.zazen on 2011-03-31
I merged your two threads.

---

### Post by aaaaalex on 2011-03-31
I must be drunk. I swear i saw this thread just a second ago. :-D

---

### Post by doppel.ganger on 2011-03-31
I got this.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libpango1.0-0 : Breaks: plymouth (< 0.8.2-2ubuntu19) but 0.8.2-2ubuntu5.1 is to be installed
E: Broken packages

---

### Post by aaaaalex on 2011-03-31
Should work now already.

To fix the error message, open Synaptic Package Manager. Select 'Fix Broken Packages' from the 'Edit' menu.

Hope this helps.

---

### Post by doppel.ganger on 2011-03-31
I got the same thing!

COULD SOMEONE PLEEEAAASSSEEE HELP ME!!!?!?!?!?!?!!?

---

### Post by bodhi.zazen on 2011-03-31
Try

```
sudo apt-get update
sudo apt-get -f
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by aaaaalex on 2011-04-01
No need to shout... Had to get some sleep :-P.

Does your issue persist?

---

### Post by euphro on 2012-08-05
Thanks, this sorted it out for me :)

---

### Post by wildmanne39 on 2012-08-05
Old thread closed.

---

