---
title: "Send files over bluetooth."
date: 2009-02-02
forum: New to Ubuntu
---

### Post by pHreaksYcle on 2009-02-02
bluetooth is pretty damn complicated I am finding. 

I'm trying to send a file to a blackberry storm, the attached is what happens when I do that.

"org.openobex.Error.ConnectionAttemptFailed"

Note that I am using 8.10 with the gnome bluetooth and blue utils installed, and that I can transfer files from phone to computer, just not other way.

All help appreciated.

---

### Post by seanodonnell on 2009-02-02
do you see the phone if you run hcitool scan?

Try right clicking on the bluetooth applet and using send-files, it may be a problem withe the nautilus integration rather than bluetooth.

---

### Post by pHreaksYcle on 2009-02-02
That's how I was doing it, right click on the Bluetooth toolbar icon and Send File, not the Right Click Nautilus integration.

As a matter of fact, I don't believe the Nautilus integration is even in the menu.

In any event, I have found a bug report [here]("https://bugs.launchpad.net/nautilus-sendto/+bug/285283") and have also found a personal workaround, but will leave this open in case any one has the same issue/answer.

---

### Post by seanodonnell on 2009-02-02
it might be a good idea to post your workaround, so other people googling for the same problem can use it.

---

### Post by eznet on 2009-02-02
I think you need to install Obex.  Check libopenobex1.  I can transfer to my W580i with the Bluetooth Applet, but only after getting Obex installed... Took me awhile to figure that out the first time I played with bluetooth in Linux.

Hope this helps.

---

### Post by icyest on 2009-02-03
Obex? Is that a thing that has to come with yet another program not included in the basic 8.10 edition that we must find?

---

### Post by eznet on 2009-02-03
> **icyest said:**
> Obex? Is that a thing that has to come with yet another program not included in the basic 8.10 edition that we must find?

Hmm...  [Obex ]("http://en.wikipedia.org/wiki/OBEX")is a transfer protocol - one not needed on many machines (many laptops as well as most desktops).  So yea, I guess it is "another program not included" by default with a standard install, though it is very easily added via Synapics if you need it. 

IMHO, packages like this should not be part of the standard install in most cases since it adds overhead to the OS - unnecessary overhead adds unnecessary load times and resource demands...  That's what makes Windows work out of the box for any Tom, Dick, or Harry that decides he wants to use a computer - it is also what causes these machines to run slower than they should.  

If you want a customized OS that runs faster than its MS counterpart, you have to make concessions that will require you to learn and exert a bit of effort to get it. "Nothing worth having in life is free" - although Linux doesn't cost money, if you want a OS worth having, you have to spend a little time on it.

I feel your pain -  I made the swap to Linux back when Slackware and Gentoo were used to cut your teeth on and can't remember how many times I thought it was a stupid OS that was to blame for things not working on my PC. I now know it wasn't the OS, but instead was just my ignorance and lack of experience that was to blame... Not that that is the case with you, but none the less, I know it can be frustrating - thats where you have to decide what you want from your computer and your OS and decide what community you want to call 127.0.0.1

Best of luck!

---

