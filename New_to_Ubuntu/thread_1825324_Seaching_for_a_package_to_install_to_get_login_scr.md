---
title: "Seaching for a package to install to get login screen?"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by alfa_80 on 2011-08-15
Hi,

My ubuntu is currently on a black screen. It seems that all of my data are preserved since I can still see them after "ls"..The only thing to install now is to find a package that give me an interface(login GUI)..I was already reinstall x-server after following this link: [http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

Any thoughts?

Thanks in advance..

---

### Post by cbowman57 on 2011-08-15
sudo apt-get install gdm

---

### Post by alfa_80 on 2011-08-15
> **cbowman57 said:**
> sudo apt-get install gdm

By the way, the gdm package was already there. Any other possiblities?

---

### Post by cbowman57 on 2011-08-15
You could try to reinstall it, but if there is no problem with gdm then you probably have a video problem.  Have you installed a proprietary video driver lately?

---

### Post by alfa_80 on 2011-08-15
When I run startx on console, it gives some error like below:

[LIST]
[*]Failed to load module "nouveau"
[*]Failed to load module "nv"
[*]Failed to load module "vesa"
[*]Failed to load module "fbdev"
[/LIST]
What are the underlying packages with respect to those missing modules?

---

### Post by alfa_80 on 2011-08-15
> **cbowman57 said:**
> You could try to reinstall it, but if there is no problem with gdm then you probably have a video problem.  Have you installed a proprietary video driver lately?

I've reinstalled it, but still not working..What package to install a proprietary video driver? I'm on MBP 6,2 and here is the link for that if you can help me figuring out([https://help.ubuntu.com/community/MacBookPro6-2/Maverick](https://help.ubuntu.com/community/MacBookPro6-2/Maverick)), but I'm on lucid..

---

### Post by cbowman57 on 2011-08-15
You have no video drivers installed, or xorg doesn't recognize them.

Try this: sudo apt-get install xserver-xorg-video-all

If it says it's already installed then purge it: sudo apt-get purge xserver-xorg-video-all

Or, you could try: sudo apt-get --reinstall install xserver-xorg-video-all

I'm assuming it was working at some pint & quit after you changed or upgrade something.

---

### Post by alfa_80 on 2011-08-15
> **alfa_80 said:**
> I've reinstalled it, but still not working..What package to install a proprietary video driver? I'm on MBP 6,2 and here is the link for that if you can help me figuring out([https://help.ubuntu.com/community/MacBookPro6-2/Maverick](https://help.ubuntu.com/community/MacBookPro6-2/Maverick)), but I'm on lucid..

Following the link, I've tried to find the content of a file by running ```
gksu gedit /etc/X11/xorg.conf
```

But, it gives me an empty file, strange? Must be some packages missing, right?

---

### Post by cbowman57 on 2011-08-15
If you already installed a proprietary video driver than you probably created an xorg.conf in your /etc/X11 directory, if it exists you can delete it & it should boot into vesa (sort of a failsafe)

Ok, to install the proprietary driver, assuming you set your repositories for non-free pacakges, just install nvidia-current.

---

### Post by alfa_80 on 2011-08-15
> **cbowman57 said:**
> You have no video drivers installed, or xorg doesn't recognize them.

Try this: sudo apt-get install xserver-xorg-video-all

If it says it's already installed then purge it: sudo apt-get purge xserver-xorg-video-all

Or, you could try: sudo apt-get --reinstall install xserver-xorg-video-all

I'm assuming it was working at some pint & quit after you changed or upgrade something.

It's progressing..Now, after rebooting, I only got ubuntu "normal sound" and a cursor only..with black screen. Any idea how to further fix it?

---

### Post by cbowman57 on 2011-08-15
Ok, we're going pretty fast so I need to know which of those steps you tried & if you also installed nvidia-current.

---

### Post by alfa_80 on 2011-08-15
> **cbowman57 said:**
> Ok, we're going pretty fast so I need to know which of those steps you tried & if you also installed nvidia-current.

Thanks..I run all the steps and packages that you've recomended..I've just installed nvidia-current, but i was already there..

---

### Post by fdrake on 2011-08-15
> **alfa_80 said:**
> It's progressing..Now, after rebooting, I only got ubuntu "normal sound" and a cursor only..with black screen. Any idea how to further fix it?

well now you have x running . you have missing desktop manager and a window manager.

try now :

```
sudo apt-get install metacity metacity-common metacity-themes gnome
```

---

### Post by alfa_80 on 2011-08-15
> **cbowman57 said:**
> If you already installed a proprietary video driver than you probably created an xorg.conf in your /etc/X11 directory, if it exists you can delete it & it should boot into vesa (sort of a failsafe)

Ok, to install the proprietary driver, assuming you set your repositories for non-free pacakges, just install nvidia-current.

By the way, the file is not yet there, we probably have some missing packages..

---

### Post by cbowman57 on 2011-08-15
fdrake, are you on an ubuntu system right now?  If alfa_80 didn't turn on his non-free repos via synaptic he's not likely able to install nvidia-current.

From the outset I've made the assumption that he had a DE at some point & it broke.  I could be in error.

---

### Post by fdrake on 2011-08-15
> **cbowman57 said:**
> fdrake, are you on an ubuntu system right now?  If alfa_80 didn't turn on his non-free repos via synaptic he's not likely able to install nvidia-current.

From the outset I've made the assumption that he had a DE at some point & it broke.  I could be in error.
if that is the case why is X working only now after the install?

---

### Post by alfa_80 on 2011-08-15
> **fdrake said:**
> well now you have x running . you have missing desktop manager and a window manager.

try now :

```
sudo apt-get install metacity metacity-common metacity-themes gnome
```

I couldn't really run this because of having a lot of dependencies problem..Any other alternatives?

---

### Post by cbowman57 on 2011-08-15
Dunno, better ask him. :)

Alfa_80, has this setup ever gotten you to a desktop environment?

---

### Post by alfa_80 on 2011-08-15
> **fdrake said:**
> if that is the case why is X working only now after the install?

No, actually nvidia-current is not needed to install because it was already there..

---

### Post by anewguy on 2011-08-15
I'm not so sure you're at a GUI.  One thing that has been overlooked from the start is to find out exactly what video adapter you are running.

in the terminal, type:

lspci <press enter>

You should find a line with "VGA" or "Video" on it - post that line back here.

While it appears you have a nVidia adapter, we don't know which specific one yet at this time.

---

### Post by alfa_80 on 2011-08-15
> **cbowman57 said:**
> Dunno, better ask him. :)

Alfa_80, has this setup ever gotten you to a desktop environment?

No desktop environment at all, the maximum I could go is "ubuntu sound" and cursor on a black and blank screen..

---

### Post by cbowman57 on 2011-08-15
Can you get to a desktop booting from a Live CD?

---

### Post by alfa_80 on 2011-08-15
> **cbowman57 said:**
> Can you get to a desktop booting from a Live CD?

How do I do that? you mean to try liveCD, noit to reinstall it, right? Anyway, I think there must be some way to fix it without reinstalling it..I can boot with theliveCD, just to try..

---

### Post by cbowman57 on 2011-08-15
Yeah, just to try it.  If you can get to the desktop with a Live CD then we know the machine is capable of it.  With Ubuntu it really shouldn't be any harder than booting the Live CD, installing it, reboot and be greeted by the gdm then the desktop.

If that doesn't work you might have to try asking the question in the Apple sub-forum.

---

### Post by alfa_80 on 2011-08-15
> **cbowman57 said:**
> Yeah, just to try it.  If you can get to the desktop with a Live CD then we know the machine is capable of it.  With Ubuntu it really shouldn't be any harder than booting the Live CD, installing it, reboot and be greeted by the gdm then the desktop.

If that doesn't work you might have to try asking the question in the Apple sub-forum.

I don't want to reinstall it, because I'll have a lot of data and configurations lost. It already happened before :-(  

Any other ideas? I still believe it's still doable to troubleshoot it..Asking in the Apple sub-forum is harder..huhu

---

### Post by fdrake on 2011-08-15
> **alfa_80 said:**
> I don't want to reinstall it, because I'll have a lot of data and configurations lost. It already happened before :-(  

Any other ideas? I still believe it's still doable to troubleshoot it..Asking in the Apple sub-forum is harder..huhu
we don't want you to reinstall it just check if the desktop env is working and fix the problem with it.

---

### Post by alfa_80 on 2011-08-15
> **fdrake said:**
> we don't want you to reinstall it just check if the desktop env is working and fix the problem with it.

What packages that are responsible for the desktop environment? perhaps i need to install gnome2?

---

### Post by fdrake on 2011-08-15
> **alfa_80 said:**
> What packages that are responsible for the desktop environment? perhaps i need to install gnome2?

the problem is that we don't know what's the cause of the problem... did you try to boot from the live cd? is the desktop working?

---

### Post by alfa_80 on 2011-08-15
> **fdrake said:**
> the problem is that we don't know what's the cause of the problem... did you try to boot from the live cd? is the desktop working?

Yes, I've tried with the live cd and I can see the desktop environment..

---

### Post by alfa_80 on 2011-08-15
> **fdrake said:**
> the problem is that we don't know what's the cause of the problem... did you try to boot from the live cd? is the desktop working?

It perhaps because last 2 day, I was tweaking with GTK+ and some other gtk stuff by installing via synaptic..and I didn't realize that some packages were removed to solve dependency problem by synaptic manager..

---

### Post by fdrake on 2011-08-15
> **alfa_80 said:**
> It perhaps because last 2 day, I was tweaking with GTK+ and some other gtk stuff by installing via synaptic..and I didn't realize that some packages were removed to solve dependency problem by synaptic manager..
i am not sure of the problem but i would try to reinstall the whole desktop env. 

```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---

### Post by alfa_80 on 2011-08-15
> **anewguy said:**
> I'm not so sure you're at a GUI.  One thing that has been overlooked from the start is to find out exactly what video adapter you are running.

in the terminal, type:

lspci <press enter>

You should find a line with "VGA" or "Video" on it - post that line back here.

While it appears you have a nVidia adapter, we don't know which specific one yet at this time.

Sorry, didn't realize this one..after running lspci and looking for vga, it gives "VGA compatible controller: nVidia Corporation Device 0a29 (rev a2)..

---

### Post by alfa_80 on 2011-08-15
Another thing I found, is that when I try to run gparted that expects me to have GUI viewing capability failed to work..it gives some errrors like "(EE) No devices detected, fatal server error:no screen found"..errm, something to do with visualization tool I guess..what GTK is the standard one for ubuntu 10.04?

---

### Post by anewguy on 2011-09-04
Sorry I forgot to get back to you!

At the boot menu, edit the boot line and add:

nomodeset

to the boot line, then let it boot.

If that works, chances are you need the video driver.  The nomodeset option can be added at each boot or permanently, but it really shouldn't be needed.

Once you get it boot to the desktop then go to additional hardware drivers and see if it can find a driver for your video.  If it does, be sure to enable it.

Again, so it took me SO long to get back - I honestly just missed the thread again.

Dave ;)

---

