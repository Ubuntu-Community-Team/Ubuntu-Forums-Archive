---
title: "Proprietary drivers on Lucid 64 bit?"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by Druegan on 2010-09-22
Hi Ubuntu Wizard folk, 

This is probably going to sound a little nutty, but I'm a noob, and I need a hand.

Whilst attempting to install Lucid 64 bit version, I blew up my video card. I happened to be able to get a loaner, but it's a little old. It's an ATI Radeon X800 XL.  I'm looking to install the proprietary drivers for it, as I'm hoping to get a little better resolution and whatnot on some games I play..

I went to System>Administration>Hardware Drivers, and it says "No proprietary drivers are in use on this system".. and the page is totally blank underneath. Just the "help" and "close" buttons. 

Is this meaning that there are no drivers available, or do I need to enable something to get access to them?

I did some googling, and read the BinaryDriverHowto/ATI page from the Ubuntu Community Documentation site.  I went to ATI's site, and downloaded the appropriate driver package..  in this case "ati-driver-installer-9-3-x86.x86_64.run"

Now, the Community Docs howto bit was written for Karmic, and for a more advanced version of the Catalyst drivers... but I figured that the basic syntax and procedures would likely be applicable, with the suitable adjustments for the package name and ubuntu version..   Which, converted such as my noob skills allow, came out as:

```
sudo sh ./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/Lucid
```

Which looks to me like it should work.  But it doesn't.

I get the following:
```
Generating package: Ubuntu/Lucid
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
```

So, using the --listpkg instead of --buildpkg, 

```
Ubuntu Packages:
	Ubuntu/7.10
	Ubuntu/8.04
	Ubuntu/8.10
	Ubuntu/9.04
	Ubuntu/gutsy
	Ubuntu/hardy
	Ubuntu/intrepid
	Ubuntu/jaunty
	Ubuntu/source

```

Apparently there is no package bit for this for Lucid?

So, I'm kinda fresh out of ideas.  Am I totally out of luck here, or can some sage out there suggest a way I can get these to work?

I'm really sorta lost, so any help would be appreciated.

Thanks, 
    Druegan

---

### Post by Mark Phelps on 2010-09-23
The "Version ... not supported" should be a clue ...

There is NO ATI fglrx driver that will work with your card and current versions of Ubuntu.  ATI dropped fglrx support for your card a LONG time ago.

The last driver that DID work will not work with X-server versions newer than that present in Ubuntu 8.10.

So basically, you are forced to use the already-installed open-source driver.

IF you force the installation of ANY ATI fglrx driver, you will only hose up your display big time and have to go through a lot of work to restore the drivers you already have in place.

---

### Post by Druegan on 2010-09-23
ah, ok.. thanks :)  New graphics card should arrive monday, so not a big deal.

---

### Post by hsantanna on 2010-09-23
> **Druegan said:**
> ah, ok.. thanks :)  New graphics card should arrive monday, so not a big deal.
You will have better luck this time if your new card is not an ATI.

---

