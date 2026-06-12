---
title: "What is a small OS that could fit on a 512 mb usb memory stick?"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Seithe on 2009-08-31
I was wondering if there is a small OS out there that could fit on a 512 mb usb memory stick. Or can a linux OS even be booted from a usb memory stick?
I was just curious to know since this usb memory stick is just lying around not being used and i was just curious to know if anything could be booted from this small thing at all?
Well if it requires system requirements could you tell me as well?
Well this is only if a linux distro could even be booted from a small sized usb memory stick.

---

### Post by jpeddicord on 2009-08-31
> I was wondering if there is a small OS out there that could fit on a 512 mb usb memory stick. Or can a linux OS even be booted from a usb memory stick?Definitely.
> I was just curious to know since this usb memory stick is just lying around not being used and i was just curious to know if anything could be booted from this small thing at all?
Well if it requires system requirements could you tell me as well?
Well this is only if a linux distro could even be booted from a small sized usb memory stick.
DSL is a popular choice, though I haven't tried it out in quite some time.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by donkyhotay on 2009-08-31
[DSL](http://www.damnsmalllinux.org/) is the first that jumps to my mind. There are undoubtedly many others. Check out [distrowatch](http://distrowatch.com/) for information other linux distros.

---

### Post by earthpigg on 2009-08-31
nearly any linux distro can be installed onto and boot from a thumb drive.

unetbootin - tool that will download/install any of a number of distributions directly to your thumb drive.

Ubuntu's usb-creator - found on your existing Ubuntu system in system -> administration USB Startup Disk Creator. this only works with Ubuntu and Ubuntu-based distributions, but a number of them are well under 512mb. The one in my sig, for example, is a 325mb .iso. :D A much better known and more established ubuntu-based distro that may fit is crunchbang.

for utility, you could consider tossing Super Grub Disk (installable via unetbootin) on that thumb drive. Parted Magic is another option. I'm not sure how large NTPasswd is, but that could come in handy.

puppy linux is well know and very small. same with dsl (damn small linux). gentoo, arch, and freedos are distributions that are command-line based. all available using unetbootin.

---

### Post by gn2 on 2009-08-31
Why bother when larger capacity USB drives are so cheap these days?
Get a 4gb one and your options are massively increased.

---

### Post by earthpigg on 2009-08-31
> **gn2 said:**
> Why bother when larger capacity USB drives are so cheap these days?
Get a 4gb one and your options are massively increased.

meh. im the same way as the OP. if it functions, i would much rather find a use for something than throw it away.

---

### Post by raymondh on 2009-08-31
try crunchbang

---

### Post by gn2 on 2009-08-31
> **earthpigg said:**
>  if it functions, i would much rather find a use for something than throw it away.

Me too, but I would rather put it to more suitable use, e.g. plugging into my car stereo.

---

### Post by Seithe on 2009-08-31
If I download one of the distros can they be used on virtualbox ose?
and if I download a small distro will it be able to run software like firefox, thunderbird, gimp, gdesklets etc.?

---

### Post by steveneddy on 2009-08-31
[DSL]("http://www.damnsmalllinux.org/") is the perfect candidate.

Add the install to ram or run from ram option on boot and after boot you can remove the usb stick, that is if you have more than 512bm of ram.

Or you can order a [USB pen drive with DSL preinstalled.]("http://www.damnsmalllinux.org/usb.html")

[Booting DSL from USB.]("http://www.damnsmalllinux.org/wiki/index.php/USB_Booting")

[DSL Wiki.]("http://www.damnsmalllinux.org/wiki/index.php/Main_Page")

[Have fun.]("http://www.wikihow.com/Have-Fun-at-Home-on-a-Saturday-Night")

---

### Post by snowpine on 2009-08-31
My favorite USB stick distro is SliTaz. It has an awesome USB installer (tazusb) and the entire distro is only 30mb, so you have lots of room left over for documents.

The only catch is, your computer needs to be able to boot from USB, so that rules out most really old computers.

---

### Post by NoaHall on 2009-08-31
Yes, they can.
Yes, they can, although they might have more lightweight alternatives installed instead.

---

### Post by gn2 on 2009-08-31
> **steveneddy said:**
> [USB pen drive with DSL preinstalled.]("http://www.damnsmalllinux.org/usb.html")

65$ plus shipping? :shock:

---

### Post by steveneddy on 2009-08-31
> **gn2 said:**
> 65$ plus shipping? :shock:

Support the community.

---

### Post by tgeer43 on 2009-08-31
If you want a lightweight distro that doesn't skimp much on features and has the look and feel of some of its heavier weight brethren then it's hard to beat Puppy Linux:

[http://www.puppylinux.org/home](http://www.puppylinux.org/home)

Small, super fast, and light on resources. It will run on some pretty meager hardware but can still run most Linux apps including the ones you mentioned. Runs beautifully from USB stick and can be loaded totally in RAM for lightning fast operation.

After Ubuntu, it is my favorite distro.

tgeer

---

### Post by earthpigg on 2009-08-31
> **gn2 said:**
> 65$ plus shipping? :shock:

if a thumb drive of rugged construction was available with the Ubuntu logo on it and Ubuntu pre-installed, I'd consider spending a bit more on it than thumb drives normally cost.

I dunno about $65, though....

---

### Post by Gen2ly on 2009-08-31
Used Fedora's usb-creator on this drive:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820227145](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227145)

runs great.

---

### Post by gn2 on 2009-08-31
> **steveneddy said:**
> Support the community.


No problem with supporting it through making purchases, so long as the product is value for money.
DSL on a flash drive for $65 is a very very long way from that.

---

### Post by Gen2ly on 2009-08-31
Just saw [KolibriOS](http://distrowatch.com/weekly.php?issue=20090831) on Distrowatch. "Kolibri - a desktop operating system in under 3 MB".  Dang.

---

### Post by Seithe on 2009-08-31
Well I wen't with puppy linux but how do I start it up?

---

### Post by tgeer43 on 2009-08-31
You made a great choice.

I have a lot of experience with it and wouldn't mind helping you but the Ubuntu forums is not an appropriate venue for this.

Let's take it here:

[http://www.murga-linux.com/puppy/](http://www.murga-linux.com/puppy/)

tgeer

---

### Post by sideaway on 2009-08-31
Holy crap. Kilibri has a full GUI and it's only 5mb... WTF?

****. Downloading now. That's astounding!

---

### Post by Seithe on 2009-08-31
Thats unique I haven't heard of a OS thats only 5mb.

---

### Post by sideaway on 2009-08-31
I thought the linux kernel itself was 8mb. I guess it could be stripped down :P

3 second boot anyone? :P

---

### Post by matsuzine on 2009-09-01
Puppy.  ~100 meg, lots of fun, and a fave of mine...

---

