---
title: "Where did everything go?"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by godonholiday on 2011-02-11
I am on a Mac and installed Ubuntu 10 ( as of 10th Fed 2011) using vmware the toher day.

I have had loads of fun downloading apps and playing with the themes and so on.

I have had an issue with the screen resolution being really low and someone guided me to type: nvidia-xconfig and restart my x server as i wasnt using the driver or something (this didnt work)

So I logged off/shut down

Then I loaded it up this morning and all I see is the terminal window?

How do I launch the GUI of ubuntu?

Why did this happen and do I always have to go through the terminal to load it?

Sorry if this is an obvious thing, only just making the switch over and not sure what I might have done?

Thanks for any help.:confused:

---

### Post by Bölvaður on 2011-02-11
> **godonholiday said:**
> I am on a Mac and installed Ubuntu 10 ( as of 10th Fed 2011) using vmware the toher day.

I have had an issue with the screen resolution being really low and someone guided me to type: nvidia-xconfig and restart my x server as i wasnt using the driver or something (this didnt work)

So I logged off/shut down

Then I loaded it up this morning and all I see is the terminal window?


There is something missing. What happened was that the driver you are using is an incorrect one. Last time I knew no virtual machine could directly utilize hardware so installing any drivers would not be advised. (after some googling I see that there has been no new technology allowing this.. so this is impossible what you are trying.)

There was another guy having same problem
[http://communities.vmware.com/thread/119099](http://communities.vmware.com/thread/119099)
Ignore that some sentences are in bold, because it doesnt make sense if not in context. What the support guy is NOT saying is that you should install nvidia driver on a virtual machine, he's saying (changing this to make it apply to you) you should install driver for mac, not ubuntu running on vmware.

So the only thing you need to do is use the default graphics driver named VESA. I have no idea how you installed the nividia driver, if you installed it through synaptic or any graphical installer (nvidia drivers from their website come with text based installer only last time I checked) then you need to uninstall it.


**The easiest and quickest way for someone just starting out is to_ reinstall the os_ and do not install any drivers in an OS running inside of a virtual machine.**

Hope you know more about how virtual machines work now :)




> **godonholiday said:**
> 
How do I launch the GUI of ubuntu?
 
startx
but it will not work because your ubuntu has to have default graphics driver to be able to utilize the hardware. So you will need to go back to using the default video driver for this to work.

---

### Post by godonholiday on 2011-02-11
Wow thanks for the quick reply.

As I have to then use the default diver, does that mean I wont be able to have a higher resolution?

Thanks again, doing the install again now

---

### Post by Bölvaður on 2011-02-11
> **godonholiday said:**
> Wow thanks for the quick reply.

As I have to then use the default diver, does that mean I wont be able to have a higher resolution?

Thanks again, doing the install again now

**[B]PC Pro magazine**[/B] did a 1 day with only ubuntu so they installed it on every single computer and server for that day and I remember seeing a twitter post from one of the guys with a mac he installed ubuntu on parallel and everything worked automatically. He could have any resolution/screensize he wanted.

I also remember about 3 years ago when I wanted to use virtual machine I could change screensize by changing the resolution of the guest os.
[B]
So try go to System &#8594; Preferences &#8594; Monitors and select another resolution.[/B]

---

