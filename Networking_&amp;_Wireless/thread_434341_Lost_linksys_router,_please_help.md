---
title: "Lost linksys router, please help"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by pneaveill on 2007-05-05
Someone at another forum suggested that I install pppoe to "enhance" my sbc/att DSL signal. It somehow crashed my linksys router (BEFSR41) preventing it from reaching the dsl modem and internet.  I have reset the BEFSR41 back to factory specs and still no success.  Someone else suggested that linksys will not see my DSL until and unless I remove pppoe. Guess despite hours of google searching, I still don't have enough of an idea of what I am missing here.

From what little I understand, sbc/att dsl does not and cannot use pppoe at all. 

I can see the router when it is hooked up or (if router is removed) then I can get to internet directly. What happened with the pppoe and how did it mess up the router? Better question: how do I fix it?

I have done a lot of googling. Maybe I am just not using the right search terms or something.](*,)

THanks in advance

---

### Post by PilotJLR on 2007-05-05
Remove pppoe... do not change anything else.

I mean this in a lighthearted way - if you change something in a computer, and it causes the changed component to fail, undo what you did!!

pppoe definitely does not "enhance" your signal... it either works or it doesnt. SBC does require a pppoe client, so your modem is most likely serving that role. Having it installed locally is not needed.

---

### Post by pneaveill on 2007-05-05
> **PilotJLR said:**
> Remove pppoe... do not change anything else.

I mean this in a lighthearted way - if you change something in a computer, and it causes the changed component to fail, undo what you did!!

pppoe definitely does not "enhance" your signal... it either works or it doesnt. SBC does require a pppoe client, so your modem is most likely serving that role. Having it installed locally is not needed.

Still a bit of a newb, so am not sure how to remove pppoe. Additionally, what to do with the router?

---

### Post by PilotJLR on 2007-05-06
Try this:
```

sudo apt-get remove pppoe

```

You can also do this graphically through Synaptic... but it's easier to just post text commands here.


After doing this, your connection will probably still not work. What you need to do is go to the router setup page (likely 192.168.1.1) and give it your pppoe login again. This is most likely your sbcglobal email address and the password you created. When you give this information to the router, you're basically making the router be a pppoe client. Almost all DSL providers require this.

---

### Post by pneaveill on 2007-05-06
> **PilotJLR said:**
> Try this:
```

sudo apt-get remove pppoe

```You can also do this graphically through Synaptic... but it's easier to just post text commands here.


After doing this, your connection will probably still not work. What you need to do is go to the router setup page (likely 192.168.1.1) and give it your pppoe login again. This is most likely your sbcglobal email address and the password you created. When you give this information to the router, you're basically making the router be a pppoe client. Almost all DSL providers require this.

Alright.  I did the sudo remove, as suggested above without reboot and then with it and neither option worked. If I bypass the router, then I can get this machine to access internet....

Still wondering if I messed something up in the router itself. Anyone have ideas?

---

### Post by pneaveill on 2007-05-16
Committed treason, but no one was able to help me with the linux way of reseting the linksys box.:mad:

Had to resort to building a Win2k box long enough to get the beasty running. Reset the linksys router and all with the win2k box and used their software.

There has to be a better way to do this.:confused:

---

