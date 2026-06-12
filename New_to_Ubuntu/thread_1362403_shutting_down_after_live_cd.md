---
title: "shutting down after live cd"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by ericgds on 2009-12-23
Hello. I've come back to tinker with ubuntu after quitting a year ago due to not being very techie. 

I'm using a live cd of ubuntu but when I shut down my laptop when finished the computer screen goes blank but the computer stays on as the power light is is still on. The only way I can turn it off is by holding down the power button until it shuts down completely. I've always thought doing so was bad.  

Is this normal after running ubuntu with a live cd?

---

### Post by plusnplus on 2009-12-23
Hi ericgds,
How about if you open the terminal and type: shutdown -h now

---

### Post by wilee-nilee on 2009-12-23
Generally the computer should shutdown and show a screen that says remove disc and hit enter, and the disc player should have opened. Besides the terminal command you can also use this. 
[http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub)
This is a good process to know as once in a while it may be needed. I would also see if trying to burn a new CD or loading a thumb and see if you can get a standard shut-down. The USB should just shut down or restart depending on what you choose.

---

### Post by prshah on 2009-12-23
> **ericgds said:**
> 
I'm using a live cd of ubuntu but when I shut down my laptop when finished the computer screen goes blank but the computer stays on as the power light is is still on. The only way I can turn it off is by holding down the power button until it shuts down completely. I've always thought doing so was bad.  

Is this normal after running ubuntu with a live cd?

When the screen goes blank, it is probably waiting for you to eject/remove the live CD. Just press Enter and it should shutdown normally within a few seconds.

It should not matter that you do a hard-off (holding down power button) a reasonable time after you have already given a shutdown command.

This behavior can also occur if you have ACPI issues with your laptop.

I don't think you have to worry.

---

### Post by ericgds on 2009-12-24
Ok thanks. All I had to do was press enter and it shut down.

---

