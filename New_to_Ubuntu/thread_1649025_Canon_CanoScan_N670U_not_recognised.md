---
title: "Canon CanoScan N670U not recognised"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-12-19
Im trying to scan some pictures with a canoScan N670U, when it is plug in through usb nothing seems to happen, I have installed XSane which still doesn't pick the scanner up. 

Is there any drivers available for this scanner?

---

### Post by PhantmKllr on 2010-12-19
> **Rave Gloves said:**
> Im trying to scan some pictures with a canoScan N670U, when it is plug in through usb nothing seems to happen, I have installed XSane which still doesn't pick the scanner up. 

Is there any drivers available for this scanner?
Check the cannon support site for Linux drivers. If none, then your scanner is not yet supported.

[http://www.usa.canon.com/cusa/consumer/standard_display/support]("http://www.usa.canon.com/cusa/consumer/standard_display/support")

---

### Post by Rave Gloves on 2010-12-19
Cannon don't actually do any linux drivers, I have heard of people getting it to work with sane, but i've got no idea how they did get it working, it's an old scanner so i assumed it would work out of the box

---

### Post by PhantmKllr on 2010-12-19
Some printers/scanners never get Linux support. Sorry.

---

### Post by Rave Gloves on 2010-12-19
Aw man :(, i need to get some pictures scanned in and uploaded for a college project thats due :(, ive got a lexmark all in one with the scanner but when the installed prompts me to plug in the usb nothing happens. Is there any way to get the usb to pick the printer up?.

---

### Post by PhantmKllr on 2010-12-19
> **Rave Gloves said:**
> Aw man :(, i need to get some pictures scanned in and uploaded for a college project thats due :(, ive got a lexmark all in one with the scanner but when the installed prompts me to plug in the usb nothing happens. Is there any way to get the usb to pick the printer up?.
In Ubuntu? You should be able to just plug it in, and it should work. No "installer" necessary.

---

### Post by karrank% on 2010-12-19
I've got a N650U that's recognized no prob in my Lucid build. Using the simple scan app provided natively. Don't know why there would be a functional difference between the two models. Will reply if I find any diff.

---

### Post by karrank% on 2010-12-19
Just caught your remark about Lexmark all in one. I had a lexmark printer that was never provided linux drivers, and sadly, I believe that's still the case with MOST lexmarks. My HP 812c plays fine with lucid and my canon.maybe you could find an hp around somewhere near? most of those are plug n play with linux.

---

### Post by Rave Gloves on 2010-12-19
When i plug the N670 in nothing at all happens, i just checked my usb ports and they are fine, might actually be the scanner it's self. Ive just installed XP in a virtual machine to use it. i think my lexmark is a X450, Can't remember. Will the scanner work with the virtual machine?

---

### Post by PhantmKllr on 2010-12-19
> **Rave Gloves said:**
> When i plug the N670 in nothing at all happens, i just checked my usb ports and they are fine, might actually be the scanner it's self. Ive just installed XP in a virtual machine to use it. i think my lexmark is a X450, Can't remember. Will the scanner work with the virtual machine?
It should. If you're using VirtualBox, you have to add the printer to the list of VM recognized USB devices, located in the machine specific settings.

---

### Post by Rave Gloves on 2010-12-19
You cannot use USB support on the open source version of VB by default. Im looking for a way to activate it.

---

### Post by PhantmKllr on 2010-12-19
> **Rave Gloves said:**
> You cannot use USB support on the open source version of VB by default. Im looking for a way to activate it.
Why not use the commercial version of Virtual Box?

---

### Post by Rave Gloves on 2010-12-19
> **PhantmKllr said:**
> Why not use the commercial version of Virtual Box?

As far as im aware it costs money, if not do you have a guide handy to installing it?

---

### Post by Rave Gloves on 2010-12-19
I tried to install from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

And i got an error on the software centre:

```
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at http://launchpad.net/aptdaemon/+filebug and retry.
```

Any guesses on the problem?

---

### Post by Rave Gloves on 2010-12-19
to fix this problem i had to do this 

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
```


```
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by PhantmKllr on 2010-12-20
> **Rave Gloves said:**
> As far as im aware it costs money...

Actually, the commercial version doesn't cost any money. It just isn't open source.

> **Rave Gloves said:**
> I tried to install from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Looks like you've already found the commercial version.

---

### Post by Rave Gloves on 2010-12-20
Cheers for your help :) , Only now need to get windows xp installed to it. When i go to install it there is just a black screen and nothing happens. do i maybe need more ram set in the partition or more space on the partition?

---

### Post by 741Baus on 2010-12-20
Hi Rave Gloves , have you installed printconf 

  ```
sudo apt-get install printconf
``` 
 
I had a similar problem getting a canon all in one to be even recognized installing this enabled me to print, scan from browser and e-mail client.

---

### Post by laidback on 2010-12-20
I have a CanonScan N670U with USB, v9.04 picks it up without any problem. I don't have printconf installed either.
No doubt there is something I have installed that makes the difference, but what?

I've just checked my new version of 10.04LTS with the default Simple Scan app. That works too. I've hardly done anything to this installation yet apart from installing the Nvidia driver and standard codecs for DVDs and CDs.

I know that doesn't really help but it gives some confirmation to the idea that there's something unusual with your setup.

---

### Post by Rave Gloves on 2010-12-20
Im starting to think that the scanner is actually broken, i installed windows XP on a virtual machine and still nothing. No idea how it could be broken mind you.

---

### Post by laidback on 2010-12-21
Perhaps the cable

---

### Post by adrianj2012 on 2012-07-06
I hope I'm not reviving a dead topic since this is a bit old, but here's a bit of an update:

I have a CanoScan N670U and it turns out that it only worked with the 32-bit distros. Even in Windows there was no 64-bit support for it, I believe.  However, I did manage to get it working on Ubuntu and Linux Mint, but it only works half the time.  I do have some good news, though. 

When looking to install drivers, I found a program called VueScan.  It works with Linux, Windows, and Macs.  At first, I was a bit discouraged because you needed to buy a license to use it without watermarks, but it seems that the developer has made the *basic* scanning free to use without them.  It's only the more advanced features that you need to pay for.  There is a very large number of supported scanners, so give it a shot.  It worked flawlessly for me, and if all you want to do is scan, then this might be a workaround. (The fix would be to have your computer scan without any additional help, but a roughly 7 MB downloadable program that you simply double-click to open seems like an easy alternative.)

Here's the story on the now free basic functionality:
[http://www.prweb.com/releases/2012/7/prweb9656711.htm](http://www.prweb.com/releases/2012/7/prweb9656711.htm)

... and here's the website itself:
[http://www.hamrick.com/](http://www.hamrick.com/)

Just click the Linux version you want (32 or 64 bit), extract to the folder of your choosing, double-click the "vuescan" program, and you're set!

Hope this helps!

---

### Post by wildmanne39 on 2012-07-06
Hi, this is an old thread so it has been closed, thanks for sharing.

---

