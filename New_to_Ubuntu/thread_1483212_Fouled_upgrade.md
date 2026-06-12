---
title: "Fouled upgrade"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by Shenachie on 2010-05-14
10.04 doing nothing. 

I went through the upgrade method and on restarting the purple screen is sitting there with the four dots changing colour in sequence. Effectively one useless lappie. 

Thoughts please?

---

### Post by tom.swartz07 on 2010-05-14
> **Shenachie said:**
> 10.04 doing nothing. 

I went through the upgrade method and on restarting the purple screen is sitting there with the four dots changing colour in sequence. Effectively one useless lappie. 

Thoughts please?

I believe you could hit the ESC while that is doing its thing, and it will switch to text mode, see if that has anything relevant and post it here? If that doesnt work, try CTRL ALT F1

Was it a system upgrade from 9.10 to 10.04 or was it a normal 'programs' update?

---

### Post by scorp123 on 2010-05-14
> **Shenachie said:**
> 10.04 doing nothing. 

I went through the upgrade method and on restarting the purple screen is sitting there with the four dots changing colour in sequence. Effectively one useless lappie. 

Thoughts please? Press the ESC key and see if there is any text output, e.g. an error message of some sorts?

I just had a problem too ... pressing the ESC key makes that purple screen go away and instead the black & white messages from the OS are revealed. The OS will tell you precisely what it is doing (e.g. "Reading config ... OK /  Starting service .... FAIL ... ") or at least where it got stuck.

---

### Post by Shenachie on 2010-05-14
Something about a script job stuck and now Upstart?

Cant copy it over as it is too long.

Cursor is just stuck there flashing

would I be better to re-install from a disc and stuff the info on the HD?

---

### Post by dca on 2010-05-14
I know the dist-upgrade feature is there to use but I haven't found one OS where it works 100%, whether it was Ubuntu, Win2k -> XP -> Vista, or OSX.  Somehow something is missed, in Ubuntu it was either a compatibilty/settings issue between Gnome versions where I changed or customized a theme too much to cause issues.

---

### Post by utnubuuser on 2010-05-14
If you've got a seperate /home partition you can re-install without over-writing the existing files/folders

---

### Post by Shenachie on 2010-05-14
I am installing again. Potential loss of data is pretty much zero so on it goes.

---

### Post by mustard greens on 2010-05-14
can anyone walk me through a fresh install?  I have the liveCD and a separate home partition.  tried it on my own but became unsure of the partition options.

---

### Post by baddnady23 on 2010-05-14
put the live cd in and boot to your CD drive.  When you get in the option to install drom the cd, go ahead and do it.  You will eventually be prompted with a screen for the partition manager and this is where you need to do some work manually and tell ubuntu to use your seperate home partion as the home partition for the new install.  Any more questions feel free to ask.  I don't have a machine in front of me to tell you exactly which screens the screens look like, maybe someone can elaborate?

---

### Post by mustard greens on 2010-05-14
I appreciate your response baddnady23, but that is the point which I came to and was unable to proceed.  I need a step by step walk through of the repartitioning if anyone has the time.  I have searched google for tutorials but none address my specific issues.

---

### Post by baddnady23 on 2010-05-14
Ah sorry i got ya. I'm on a road trip right now otherwise I'd bust out an old machine of mine and spell it out for ya.  Hopefully someone else can do just that for ya. Don't get discouraged, these forums are a wonderful resource with some very knowledgeable people in them!

---

### Post by Sealbhach on 2010-05-14
> **mustard greens said:**
> I appreciate your response baddnady23, but that is the point which I came to and was unable to proceed.  I need a step by step walk through of the repartitioning if anyone has the time.  I have searched google for tutorials but none address my specific issues.

What you do is specify partitions manually. Then tell the installer which partitions you want to use.

Pick your root partition, use as ext4, label as / and format = yes.

Pick your /home partition, use as ext4, label as /home and format = NO!!!!!!!

Swap pretty much can be left as it is.

Really, it's a very simple process and if you already know how to partition your hard drive this will not be a challenge for you.

Just make your you identify the right partitions that you are already using, this should be easy because the /home partition will be much larger than the / partition.

Just think very clearly about what you're doing and go for it. The main thing is, DO NOT FORMAT your /home partition.

.

---

### Post by baddnady23 on 2010-05-14
And if possible BACKUP your important files. Can't stress this enough.  Were all human and on occasion things do go wrong :-)

---

