---
title: "Unable to install Ubuntu..."
date: 2010-02-27
forum: New to Ubuntu
---

### Post by susannasaurus on 2010-02-27
Hello, everyone -

I am a totally absolute beginner, and a lot of what I have been finding on the Ubuntu community documentation doesn't make a lot of sense to me. I've tried searching for the answers to my questions here on the forum, as I am sure you all get a lot of new folk trying to get answers to questions that have already been asked, and that must get annoying, yet I have not found the answer to what I am looking for, so here goes.

I am currently running 10.4.11 mac os x (867 Mhz Power PC G4, from 2003, with 640 MB RAM), and to the best of my ability, in reading the community documentation on whether Ubuntu will work with my computer, it seems to me that my computer does fit the minimum requirements for the recommended installation. I have used start-up boot discs before to install or reinstall different versions of os x, and that has worked in the past, so it seems that my cd drive should be able to boot up from the Ubuntu disk I created from the downloaded .torrent file.

I originally tried to download the 9.10 .iso file that the main Ubuntu download page recommended for me, but that file wouldn't burn properly from Disk Utility, so I downloaded the .torrent file, and that burned fine to a disc that I can now open and see that it does have all the files shown it is supposed to, according to the documention, not simply showing the .iso file like it was for me before. So I seem to have burned the .iso file correctly now. 

When I try to restart my computer while holding the C key down, to start up from the .iso boot disk, nothing happens and it starts up with os x, as per normal. When I tried to hold down Command - Option - Shift - Delete all at once while restarting, then I got an icon that looked like os 9 era of a Finder folder with a flashing question mark on it, and then when I let go of the four keys, it happily went straight into starting up with os x again. 

I've looked at the documentation for trying to load from a flash drive, and I didn't understand how to do that, according to the documentation for mac users. 

Also, I have been unable to determine the md5 sum check thing, as when I follow the Terminal documentation instructions for how to check the hash number, the Terminal application does not spit out the hash number, as the documentation says that it would. 

I am unsure of what my next step(s) should be, and am feeling pretty confused. I also heard that if I was having trouble with installing Ubuntu correctly on my old machine, that maybe I should try I think it was Yellow Dog Linux or something like that? 

I have just heard that installing Linux on my old mac, and bypassing the os x, will help the computer to remain viable and less clunky for a bit longer.

Any thoughts and help would be greatly appreciated!

Thanks so much!

Susanna

---

### Post by laidback on 2010-02-27
Did you make the CD you created from the iso file bootable. I'm not familiar with your mac software so I'm wondering if whilst burning the CD you need to request "bootable" somewhere along the line. I've never had to do this in Ubuntu but one never knows with other systems.

Once you have a live CD you should be able to boot from it and give Ubuntu a try without changing your hard drive at all.

Do check the BIOS of your Mac to make sure you can boot from the CD even though you have said you've used it in the past. It should be the first boot device.

---

### Post by Merk42 on 2010-02-27
> **susannasaurus said:**
> ...
I am currently running 10.4.11 mac os x (867 Mhz Power PC G4, from 2003, with 640 MB RAM)...
I originally tried to download the 9.10 .iso file that the main Ubuntu download page recommended for me,..
Was this the i386 or AMD64 version?
Either is wrong

You need [the PowerPC version](https://wiki.ubuntu.com/PowerPCDownloads), which [isn't officially supported by Canonical, only supported by the community](https://wiki.ubuntu.com/PowerPCFAQ#Is%20Ubuntu%20supported%20on%20PowerPC?)

---

### Post by susannasaurus on 2010-02-27
Thanks so much for the replies!

It was the AMD64 version! I have now downloaded the desktop-powerpc.iso version, so that will probably do the trick. I will let you know if it works.

I'm also starting to read the Ubuntu pocket guide, which is nice and conversational and easy to understand so far, so that will probably also help!

I am sure I will have more questions later on, even after a successful install, so thanks again for the replies and this helpful forum! I am impressed!

Susanna

---

### Post by samantha_ on 2010-02-27
oh, and you **might** want to look at this.
> The PowerPC Architecture
------------------------

Summary:

  Beginning with Ubuntu 7.04, the PowerPC edition of Ubuntu will be
  reclassified as unofficial.  The PowerPC software itself and supporting
  infrastructure will continue to be available, and supported by a community
  team.

Full decision:

  The Ubuntu Technical Board has decided to reclassify PowerPC as an
  unofficial architecture, rather than a fully supported architecture, for
  Ubuntu 7.04 and subsequent releases. This means that packages and ISO
  images will continue to be produced, but releases will not be delayed due
  to problems which are specific to PowerPC, and the quality of the PowerPC
  release itself will depend very much on the extent to which members of the
  Ubuntu community drive PowerPC testing and bug fixes.

  The rationale for this decision has been recorded in the PowerPC Review
  document at [https://wiki.ubuntu.com/PowerPCReview](https://wiki.ubuntu.com/PowerPCReview), which was derived from
  a discussion at our developer summit in November. The conversation has
  continued, and for some time we have pursued a number of sources for
  funding to continue the official testing and support for the architecture.
  Unfortunately those resources have not been obtained, and we can not make
  the necessary commitments to continue official support for this
  architecture.

  A team of PowerPC users and developers has been formed at
  [https://launchpad.net/~ubuntu-powerpc](https://launchpad.net/~ubuntu-powerpc) and will be the focus of efforts to
  keep Ubuntu's PowerPC support at high quality. We welcome wider
  participation in that team, and if developers devote some additional time
  to the work then there is no reason that Ubuntu on PowerPC should not
  continue to deliver high quality releases.

  It is possible that PowerPC will once again become a fully supported
  architecture in the future, if the resources needed to guarantee its
  quality are found. The architecture is certainly gaining large numbers of
  users in embedded and console devices, and there are many reasons to
  continue to work with the platform. These uses are outside of the core
  Ubuntu mandate, however, so resources cannot be diverted from our server
  and desktop efforts just to address their needs.

  Existing Ubuntu PowerPC releases will continue to be maintained for the
  duration of their supported life cycles, including Ubuntu 6.06 LTS which
  will be supported on PowerPC servers until 2011.
[https://lists.ubuntu.com/archives/ubuntu-announce/2007-February/000098.html](https://lists.ubuntu.com/archives/ubuntu-announce/2007-February/000098.html)

---

### Post by bug67 on 2010-02-28
Yep, what Samantha said.  Might want to give Debian a go.  It fully supports PPC and, Ubuntu is actually a dirivitive of Debian.

[http://www.debian.org/](http://www.debian.org/)

---

### Post by susannasaurus on 2010-02-28
I will definitely check out Debian, and yet I also want to ask a question here about it, because they might not say this on their own website. Is Debian as desktop user friendly as Ubuntu is supposed to be? 

Thanks, everyone, for all this good information!

---

### Post by hislordship on 2010-02-28
I had similar issues the problem was that I burned the installation CD as "data" instead of "image", in nero burning rom one has to close the pop up on start up, than go to recorder and than "image"

---

### Post by 3rdalbum on 2010-02-28
> **susannasaurus said:**
> I will definitely check out Debian, and yet I also want to ask a question here about it, because they might not say this on their own website. Is Debian as desktop user friendly as Ubuntu is supposed to be?

Not quite, but it's still pretty easy to install, and requires minimal configuring if everything works 'out-of-the-box". Which is less likely than Ubuntu, because Debian puts less into their kernel, and Debian Stable is very behind-the-times.

From what I've heard, the PowerPC port of Debian is constantly in danger of being abandoned - only one guy working on it? Not sure if that's true, but if Ubuntu works better on your Mac then that would be why.

---

