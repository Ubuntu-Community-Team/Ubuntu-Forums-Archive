---
title: "GRUB not updating"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by Cliff Hanger on 2011-07-23
HI, for some reason my GRUB does not seem to update even after I run 'sudo update-grub' and this gives out a 'done' result... It is really frustrating because my Ubuntu won't let me use any new kernels that I install on it. Right now, its stuck with the latest kernel being 2.6.35.25 when I actually have .38.10 installed and others!! Using Ubuntu 10.10 64bit on Sony F11 series... Please Help! 

Thanks in advance!

---

### Post by JASONFUSARO on 2011-07-23
> **Cliff Hanger said:**
> HI, for some reason my GRUB does not seem to update even after I run 'sudo update-grub' and this gives out a 'done' result... It is really frustrating because my Ubuntu won't let me use any new kernels that I install on it. Right now, its stuck with the latest kernel being 2.6.35.25 when I actually have .38.10 installed and others!! Using Ubuntu 10.10 64bit on Sony F11 series... Please Help! 

Thanks in advance!



What version of grub?

---

### Post by Cliff Hanger on 2011-07-23
1.98 *** a really long number. I think its a release candidate that got in there somehow by ubuntu. I've tried reinstalling and stuff from synaptic but it hasn't worked.

---

### Post by JASONFUSARO on 2011-07-23
> **Cliff Hanger said:**
> 1.98 *** a really long number. I think its a release candidate that got in there somehow by ubuntu. I've tried reinstalling and stuff from synaptic but it hasn't worked.


did you try running just grub-mkconfig -o /boot/grub/grub.cfg   or just grub-mkconfig to see what would be sent to the file

---

### Post by JASONFUSARO on 2011-07-23
Check out this site

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=514705](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=514705)


the problem may be something similar if you say there is a number folowing

actually do a search on that grub version number the whole thing



[https://launchpad.net/ubuntu/+source/grub2/1.98~20100101-1ubuntu1](https://launchpad.net/ubuntu/+source/grub2/1.98~20100101-1ubuntu1)


check this site out to maybe it was an unstable version

---

### Post by JASONFUSARO on 2011-07-23
What is the whole number?

[http://www.google.com/search?client=ubuntu&channel=fs&q=grub2+1.98+not+updating+grub&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=grub2+1.98+not+updating+grub&ie=utf-8&oe=utf-8)

---

### Post by JASONFUSARO on 2011-07-23
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421?comments=all)



its weird that kernel 2.6.35.25 does not update my kernel at all
 still stuck at 2.6.35.24

---

### Post by amjjawad on 2011-07-24
> **Cliff Hanger said:**
> HI, for some reason my GRUB does not seem to update even after I run 'sudo update-grub' and this gives out a 'done' result... It is really frustrating because my Ubuntu won't let me use any new kernels that I install on it. Right now, its stuck with the latest kernel being 2.6.35.25 when I actually have .38.10 installed and others!! Using Ubuntu 10.10 64bit on Sony F11 series... Please Help! 

Thanks in advance!

How did you install Ubuntu?

If you are updating your Kernel from The Update Manager, you do NOT need to run

```
sudo update-grub

```

I think the issue is your kernel is NOT updating not your grub :)

---

### Post by drs305 on 2011-07-24
Do you have two installations of Ubuntu (since you mention both 35 and [noparse]38[/noparse])?

When you run the update command watch the terminal. Do you see the missing kernels in the terminal output as the command is executed?

Do you see the newer kernels in /boot ?

---

### Post by oldfred on 2011-07-24
Lets see all the details:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

