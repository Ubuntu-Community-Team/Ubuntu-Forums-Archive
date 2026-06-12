---
title: "graphics card"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by stef-l on 2009-05-10
I hope this is the right place for this query from a relative newcomer.  I've been trying to install Google Earth, and posts have suggested that I need a graphics card with 3D hardware acceleration.  I'm mystified.  The system tells me the card I have is a SiS 741.

Can anyone tell me is this good enough? do I need to download drivers & if so where from?  System/admin/hardware drivers offers no possibilities.  

Grateful for any suggestions. If it's any help, when I used to use Windows XP the card worked fine with Google Earth.

Thanks

---

### Post by overdrank on 2009-05-10
Hi and as stated in your other [thread]("http://ubuntuforums.org/showthread.php?t=1147034") Google earth requires 3D but the sis chipsets are not supported well in linux. You may look in this [thread ]("http://ubuntuforums.org/showthread.php?t=958967&highlight=SiS+741.")for some help.

---

### Post by Didius Falco on 2009-05-10
> **stef-l said:**
> I hope this is the right place for this query from a relative newcomer.  I've been trying to install Google Earth, and posts have suggested that I need a graphics card with 3D hardware acceleration.  I'm mystified.  The system tells me the card I have is a SiS 741.

Can anyone tell me is this good enough? do I need to download drivers & if so where from?  System/admin/hardware drivers offers no possibilities.  

Grateful for any suggestions. If it's any help, when I used to use Windows XP the card worked fine with Google Earth.

Thanks

Let's have a look at what your system will tell us about your video card/chip. Open a Terminal shell (**Applications/Accessories/Terminal**) and type  ```
lspci | grep VGA
```The character after spci is a pipe, not an l. This command breaks down as follows:

lspci - tells you information about all the hardware in your PC

| - the pipe acts just like a water pipe - it channels the flow in a certain direction.

grep - this is a filter that can be used to filter out unneeded output

VGA - that's what grep is looking for in this case.

Run that and post the output. After you copy/paste it, put code tags around it by highlighting it and clicking the # on the tool bar.

Then we can see what you have and I'll take a look and see what your options are.

Regards,

Didius

On Edit - n/m If I typed any slower sdrawkcab gnipyt  eb  d'I <G>

---

### Post by stef-l on 2009-05-10
Didius,

```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```

I hope this is what you intended me to find; await possible further instructions.  Thanks

Stef-L

---

