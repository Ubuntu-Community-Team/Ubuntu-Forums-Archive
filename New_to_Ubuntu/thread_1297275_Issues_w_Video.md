---
title: "Issues w Video"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by MiRee446 on 2009-10-21
I managed to mess up the video output on my Ubuntu machine.  I believe I did this while either trying to follow for the Dual monitor tutorial for Nvidia cards (I don't have an nvidia card) or trying to install a Java viewer on my program.

Now I can't enable Visual Effects and programs like boxee and Google earth don't work anymore.  Google earth does work but it has to run in OpenGL mode, it gives a message that the drivers need to be updated (not entirely sure this is the problem), and it runs very slow.

When I try to run boxee I just get a black screen, Visual effects it tells me that my driver doesn't support them (they used to work).  Also, when I stream video on Hulu and view it full screen its very choppy.

Obviously I didn't include enough information but I'm not sure which information to give.  I don't know what video card I'm using, is there a way to find this out?  I think theres a terminal command that will list the system components I just don't know what it is.

Any advice on troubleshooting this?

---

### Post by k33bz on 2009-10-21
to list your components you can use ```
lspci
```

---

### Post by Dougie187 on 2009-10-21
also,
```
lshw -c video
```

---

### Post by MiRee446 on 2009-10-21
> **Dougie187 said:**
> also,
```
lshw -c video
```

thanks. i get this as an output:

*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

---

### Post by MiRee446 on 2009-10-22
any thoughts on what to do based on this particular video card?

---

### Post by k33bz on 2009-10-29
Just in case you have not figured out how to do this yet. First you will need to go into the terminal. Applications ~~> Accessories ~~> Terminal

Once your terminal pops up enter this in exactly
```
sudo rm /etc/X11/xorg.conf
```
This removes your current xorg.conf file, basically your xscreen configurations. Keep your terminal open and after the previous step is done type this in:
```
startx
```
This will re-start your xscreen. Now since you dont have xorg.conf file anymore, it will now create a brand new one. Which should be configured automatically for the Vid Card you have.

Again sorry it took me awhile to get back.

---

### Post by MiRee446 on 2009-11-17
after i typed in sudo startx i got this:

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
xinit:  Server error.

---

### Post by MiRee446 on 2009-12-11
fixed a few of my issues, but full screen streams are very choppy.  especially youtube and hulu...

---

