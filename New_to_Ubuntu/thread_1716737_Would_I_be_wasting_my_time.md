---
title: "Would I be wasting my time??"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by larrypg on 2011-03-28
Hello all...I have an old pc (Dell Dimension 8200 1.9 256M ram).  I am not sure I can install more memory as it seems nobody (other than ebay) sells it anymore. By the way I have an Nvidia GeForce3 ti200 video card with 64M ram.   I bought this computer back in 2001 or 2002 and nothing has been upgraded other than a larger disk and sound since.

I have used several versions of Redhat with both Gnome and KDE that worked fine but that was a few years back.  Back in 1995 I even used Redhat with a laptop that only had 16M ram although that was command line only.  

Now back to the current situation...everything I read says that you must have at least 512M and better if 1 gig of ram.  WinXP works fine with my current configuration and in past years so did linux with Gnome and KDE.  Have things changed so much that all I can run is either an old Xwindows manager or the command line?

---

### Post by mick8985 on 2011-03-28
> **larrypg said:**
> Hello all...I have an old pc (Dell Dimension 8200 1.9 256M ram).  I am not sure I can install more memory as it seems nobody (other than ebay) sells it anymore. By the way I have an Nvidia GeForce3 ti200 video card with 64M ram.   I bought this computer back in 2001 or 2002 and nothing has been upgraded other than a larger disk and sound since.

I have used several versions of Redhat with both Gnome and KDE that worked fine but that was a few years back.  Back in 1995 I even used Redhat with a laptop that only had 16M ram although that was command line only.  

Now back to the current situation...everything I read says that you must have at least 512M and better if 1 gig of ram.  WinXP works fine with my current configuration and in past years so did linux with Gnome and KDE.  Have things changed so much that all I can run is either an old Xwindows manager or the command line?

I wouldn't bother tbh, unless you want to use it for a fileserver or similar.

---

### Post by papibe on 2011-03-28
> **mick8985 said:**
> I wouldn't bother tbh, unless you want to use it for a fileserver or similar.
+1

Similar to Windows and Mac OS, most modern Linux distros have put their efforts into the desktop experience. As mick said it, installing a server version and using it as a file server would be a very viable idea.

However, there are special distros for old hardware. Look in the forums or google for suggestions. Some ideas: Lubuntu, DSL, Crunchbang, etc.

Regards.

---

### Post by spillin_dylan on 2011-03-28
You can very likely get Debian running on that, especially with a light desktop like LXDE.  I had a Pentium 3 800mHz running that with 128MB of RAM.  I have since upgraded with another 256MB, which makes a HUGE difference, but it could certainly be done with 256 megs.

USABILITY may be another thing, of course....

---

### Post by SirBartholomew on 2011-03-28
You could try kubuntu I got a dell Dimension running with that pretty good it might of had 512 mb of ram in it  though it could definiatly surf the web.

---

### Post by bodhi.zazen on 2011-03-28
There are several light weight linux distros that you can try.

Personally I like slitaz

Tinycore is an alternate.

---

### Post by larrypg on 2011-03-29
Hello all again,  I am not sure that I asked the correct way...I sort of asked if it was possible to run A thru Z Ubuntu (and how) with a P4 1.9G, 256M ram, 112 G hd, with WinXP on drive C and any Linux distro on drive D with 40 G available.  I do NOT want to use it from a USB stick or a LiveCD.  I just want to use it because for what ever reason using an alternate system to Windows sort of gets my brain going (although using Linux in command line today would probably send it into overdrive).  Yes I know there are other distro's that will work on  lower end pc's. 

In searching through things I noticed that Ubuntu will run with "ONLY" 256M in the command line and as I mentioned at one point I have used Linux with only 16 M ram in command line. I no longer am happy with just the command line though.  

This brings me back to why I just don't install it to the D drive and if I do not like it then poof it is gone...

It seems that there is a possibility of the install overwriting WindowsXP and making it unusable.  I have 10 years of things on that drive and would not be very happy about losing a decade of files.  yes I know..BACKUP...but that is not the same as having a smooth running system.   

I have sort of decided on Ubuntu or it's various derivations because it seems to have a live and active community of people that are willing to help.  

I hope it some way I have included what I really meant to say.

---

### Post by leclerc65 on 2011-03-29
I would also try Puppy.

---

### Post by bodhi.zazen on 2011-03-29
> **larrypg said:**
> I have sort of decided on Ubuntu or it's various derivations because it seems to have a live and active community of people that are willing to help.  

I hope it some way I have included what I really meant to say.

This is a great community, but that does not change the fact that you do not have enough RAM to run Ubuntu + a GUI interface.

Your best option would be slitaz, tinycore, or puppy linux.

---

### Post by ridetheteapot on 2011-03-29
ok i will say to your clarification that ubuntu or kubuntu would not be what you want. Gnome or Kde = too heavy if you strip gnome down good maybe you can manage.
You could use ubuntu with another DE but why not just go for an openbox derivative (or if your brave cough *ratpoisen*) and choose the right apps.
Really don't bother with gnome on that machine.

ps if you ask me, i dunno what you need the box for, but cpu power is cheap nowadays and you could use a cheap looow watt machine to do the same -- i mean if you think green

---

### Post by collisionystm on 2011-03-29
try blackbox window manager. Its lightweight. you can install ubuntu 32 bit. When it boots, instead of logging in and hogging your system resources, just hit ctrl + alt + f1 

login

sudo apt-get update
sudo apt-get install blackbox

Now hit ctrl + alt + f6 to go back to your login, and choose blackbox for your x manager.

and if all else fails, atleast you have the satisfaction that you tried. I myself have tried puppy linux, dsl etc... They are a headache. Ubuntu is the easiest and worth the try.

---

### Post by spcwingo on 2011-03-29
I can't believe nobody has mentioned Lubuntu (Ubuntu with LXDE by default).  You can check it out here:

[http://lubuntu.net/]("http://lubuntu.net/")

Another alternative is Bodhi Linux.  More on that here:

[http://www.bodhilinux.com/]("http://www.bodhilinux.com/")

Anyways, good luck with whatever you choose.  :)

---

### Post by Irihapeti on 2011-03-29
I had an old Toshiba laptop with 256MB ram. I did a command-line install of Ubuntu 10.04, using the alternate CD. Then I installed Openbox and just the minimum of programs that I wanted.

It did reasonably well, though I have to say that performance improved a lot when I added another 512MB of ram.

I guess it depends what you are trying to do. If you want to show what can be done, then go for it. If you want something that doesn't lag too much for stuff like browsing and so on, a newer machine (or one with more memory) would make more sense.

---

### Post by bodhi.zazen on 2011-03-29
> **ridetheteapot said:**
> ok i will say to your clarification that ubuntu or kubuntu would not be what you want. Gnome or Kde = too heavy if you strip gnome down good maybe you can manage.
You could use ubuntu with another DE but why not just go for an openbox derivative (or if your brave cough *ratpoisen*) and choose the right apps.
Really don't bother with gnome on that machine.

ps if you ask me, i dunno what you need the box for, but cpu power is cheap nowadays and you could use a cheap looow watt machine to do the same -- i mean if you think green

The minimal requirements for lubuntu are listed as 128 Mb

[http://lubuntu.net/news](http://lubuntu.net/news)

Well above the 64 Mb we are working with.

64 mb is the minimal for Debian without a desktop :

[http://www.debian.org/releases/stable/i386/ch03s04.html.en](http://www.debian.org/releases/stable/i386/ch03s04.html.en)

with a desktop (X) , 128 is listed as the minimal, same as (l)ubuntu.

Well you need to differentiate a Window manager from a desktop environment.

If you use *box (blackbox, fluxbox, or openbox), xfce, or a minimal kde / gnome on a minimal ubuntu / debian install, the end result is about the same.

It is difficult to get a graphical interface using (using ubuntu or debian as the OS) in less then 80 mb or so. It can be done, but it will be slow on your system.

IMO you are trying to pound a square peg through a round hole, it can be done, but you will have better performance with an alternate tool.

Slitaz requires only 16 Mb Ram (post-install) , far less then the 128 mb of Ubuntu.

---

### Post by Irihapeti on 2011-03-30
@Bodhi.zazen

I think that the 64MB relates to a graphics card. The computer itself, if I've read correctly, has 256MB of ram.

That might make a difference to what the OP can run.

---

### Post by spcwingo on 2011-03-30
Sorry, completely off-subject, but @ bodhi.zazen are you the creator of Bodhi Linux?  I was just curious.  If so, why no plug for your distro?  E17 would probably run respectably well on that machine given the specs.

---

### Post by Supergoo on 2011-03-30
Take a look at Crunchbang.

---

### Post by bodhi.zazen on 2011-03-30
> **spcwingo said:**
> Sorry, completely off-subject, but @ bodhi.zazen are you the creator of Bodhi Linux?  I was just curious.  If so, why no plug for your distro?  E17 would probably run respectably well on that machine given the specs.

No relation =)

> **Irihapeti said:**
> @Bodhi.zazen

I think that the 64MB relates to a graphics card. The computer itself, if I've read correctly, has 256MB of ram.

That might make a difference to what the OP can run.

Oh, my mistake then. With 256 Mb I would either use Lubuntu, Xubuntu, or a minimal install + most any window manager (gnome and not ubuntu-desktop).

---

### Post by galacticaboy on 2011-03-30
I agree, I would TRY a distro with LXDE, like Lubuntu, but ultimately, and I know it is old, but try Damn Small Linux, EXCELLENT SMALL DISRO! It is old and has not been updated in a while, but it will run smoothly! It is only 50mb small! I run it off of a flash drive with 256mb ram. It works like a charm. Runs lightning fast, and the flash drive is only 1GB!

> **spillin_dylan said:**
> You can very likely get Debian running on that, especially with a light desktop like LXDE.  I had a Pentium 3 800mHz running that with 128MB of RAM.  I have since upgraded with another 256MB, which makes a HUGE difference, but it could certainly be done with 256 megs.

USABILITY may be another thing, of course....

---

### Post by crispy_420 on 2011-03-30
+1 for either Lubuntu or Budhi

Just keep in mind this system will have some drawbacks but if you set your expectations you will be OK. I've had Lubuntu running decently on an old Dell laptop with a Celeron 800MHz and 384MB decently.

That uses RDRAM right? Depending on where you are try craigslist to get more memory and even post looking to buy. You never know someone may be looking to dump some.

---

### Post by Canime on 2011-03-30
I tried running Damn Small Linux on a laptop of similar specifications and it worked fairly well, although it took a little while to configure everything. Installation of new software was key to this flavor in my opinion.

---

### Post by larrypg on 2011-05-10
Hello all again,

It has probably been over a month since I have said something in this thread.  In the mean time I have tried (via the LiveCD) X 10.10, U 10.10 and X 11.04.  So far I like U 10.10 the best but X 11.04 seems to run the best.  A combination of both would be really good.  I really do not like X 10.10 as much as the other's.  

It would seem to me that running the Live cd would be harder than an installed version because everything is in memory (except the swap if you have already used gparted  ).  

I am going to mark this as solved so that I can start other threads.

---

