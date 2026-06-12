---
title: "Diskless workstation.."
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by marko on 2007-06-22
Just read about a school in Canada doing something similar to Edubuntu.  Asked them about their configuration and they seem sold on diskless workstations/hybrid clients/network computers..  They point to this link as their reference point:

[http://en.wikipedia.org/wiki/Diskless_workstation](http://en.wikipedia.org/wiki/Diskless_workstation)

Reading it over, I understand what they like about it.  So am curious if Edubuntu has ever considered this type of setup in addition to LTSP?..  As great as LTSP is, the server does become the bottleneck pretty quickly.  This alternative needs better client machines, but at the prices for hardware these days, it seems this option of decent clients and modest server vs throwaway clients and incredible server may be a draw.

Thanks for any comments, especially from those who drive the Edubuntu train.  =)

---

### Post by marko on 2007-06-28
People are looking at this, but no one is jumping up and saying 'I did it.  Here's how!'..  Bummer.  Would have liked to see this done.  Would have liked this as an option in Edubuntu.  Does anyone agree?

---

### Post by netztier on 2007-06-29
> **marko said:**
> People are looking at this, but no one is jumping up and saying 'I did it.  Here's how!'..  Bummer.  Would have liked to see this done.  Would have liked this as an option in Edubuntu.  Does anyone agree?

I talked to someone who is involved quite deeply in Edubuntu. He indicated to me that the project left out the diskless client option because Edubuntu is meant to run on hardware that schools (and ones in development countries) get "for free" - as you say  "throwaway" machines: Pentium 200MHz with 128MByte RAM.

These don't have the power to be diskless workstations - which themselves need to be up to par with every other PC running ubuntu (in terms of CPU, RAM and Graphics) - bar the disk capacity.

If you're interested in setting up an environment with centralised logins, "roaming profiles" and home directories, we've had that in here not too long ago.:

[http://ubuntuforums.org/showthread.php?t=462816](http://ubuntuforums.org/showthread.php?t=462816)

Searching on Google for Diskless Ubuntu brought me here: [http://www.xs4all.nl/~rjb/fatclient.html](http://www.xs4all.nl/~rjb/fatclient.html)

And then there's always this: [https://wiki.edubuntu.org/LTSPFatClients](https://wiki.edubuntu.org/LTSPFatClients) - which comes pretty close, doesn't it?

best regards

Marc

---

### Post by marko on 2007-07-02
I will read up on your links.  Many thanks for the detailed response!

I appreciate the direction of the Edubuntu project.  One reason I am uncomfortable with it is that it really demands a lot out of the server and network.  If a beefy server can only handle 25-50 clients before it starts to bog (due to server memory limitations), it seems to make sense to attack in the other direction: letting client PCs take advantage of their RAM and CPUs. 

I realize that a 500MB 2Gig machine is a lot to ask for, but maybe the edubuntu image is too fat..  =0  (did i just speak heresy..?)  What I meant to say is:  with the advent of ISOs like Antix, where the target hardware is 128 RAM and 500 Mhz, most throwaways/leftover/school PCs fall into that range.  So, if Edubuntu added this network computing deployment configuration, and allowed 2 images to deploy (one based on Antix, one based on standard Edubuntu) depending on the hardware, it would seem a very efficient, and effective setup.  The PCs would use their capabilities, the server and network would only work as needed, and nothing extraordinary would be required on either side.

I will look over your links.  Maybe they will provide the base info to create what I am looking for.  If not, I will continue to hope Edubuntu will look into this configuration option.

Maybe this option should not even fall under the Edubuntu domain.  Maybe it will become Entubuntu.  I imagine Enterprises prefer this setup over the huge servers required for LTSP or MS Terminal Server

---

### Post by marko on 2007-07-02
LTSP fat clients was the link.  Sounds like others have already started to work on this.  Many thanks for the links.  Will be following their progress.  =)

---

### Post by BatsotO on 2007-07-29
ubuntu diskless for two years, using pxes.

---

### Post by marko on 2007-08-07
pxes?  More details please..  Very curious to hear what you did and how. And how well it is working for you.

---

### Post by fletcherthunder on 2007-08-20
i just did it this weekend, these will get you there - 
[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)
[http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless](http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless)

you can use the first link for 90% of it, but it leaves out the configuring of the networking for fiesty, look at the bottom of the second link for that.  
and, for configuring the tftp to actually work - 
[http://ubuntuforums.org/showthread.php?t=236518](http://ubuntuforums.org/showthread.php?t=236518)

i'm pretty impressed with it so far, speed is there, just not sure how to do swap yet, if i'll need it...

---

### Post by getut on 2007-08-21
This is so close to what I'm looking for but not quite. Hopefully you guys won't think I'm hijacking a thread because this is so close.

I like the diskless Ubuntu, except that it seems to be geared toward a specific PC network booting from the image. I want something somewhere in between this diskless booting option and the LTSP (terminal services option).

I basically want to be able to boot an image similar to the cd image. A single PXE boot image that will work on many different hardware types and can have multiple users booted on it at the same time. Also,like the CD, no state saved... in other words write nothing back to the image.

---

### Post by marko on 2007-09-23
> **fletcherthunder said:**
> i just did it this weekend, these will get you there - 

i'm pretty impressed with it so far, speed is there, just not sure how to do swap yet, if i'll need it...

Thanks for the additional details!  And the confirmation that this is a good working solution.   Will attempt to replicate myself in the near future.

---

