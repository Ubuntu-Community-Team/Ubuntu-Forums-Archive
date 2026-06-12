---
title: "How to install non .deb driver?"
date: 2005-09-10
forum: Networking &amp; Wireless
---

### Post by nathanhill on 2005-09-10
I could really use a hand...
I have a NAS disk with Tons of files I want to access from my Ubuntu machine (over ethernet). The disk is made by Ximeta, and needs a special driver to work.  The only catch is that they only explain how to install it on RPM based distros, and I  don't know how to build a deb from binaries.

This is the only thing stopping me from using Ubuntu as my daily machine (have a ton of shared files on the Ximeta disk I need to access).

Ximeta has written a Linux driver, and provides binaries see here:
[http://code.ximeta.com/cgi-bin/trac.cgi](http://code.ximeta.com/cgi-bin/trac.cgi)

Can anyone give me (or tell me where to to find instructions (that a noob like me would understand) for doing this?

Any help GREATLY appreciated...

-Nathan Hill

P.S.
I tried posting questions to the following thead numerous times with out any luck:
[http://www.ubuntuforums.org/showthread.php?t=31135](http://www.ubuntuforums.org/showthread.php?t=31135)

---

### Post by mlomker on 2005-09-10
From the command line:

[b]
su
apt-get install alien
alien -D somepackage.rpm
dpkg -i somepackage.deb
[/b]

I've used alien to convert a couple packages and it's worked great.

---

### Post by cwaldbieser on 2005-09-10
[QUOTE=nathanhill]I could really use a hand...
I have a NAS disk with Tons of files I want to access from my Ubuntu machine (over ethernet). The disk is made by Ximeta, and needs a special driver to work.  The only catch is that they only explain how to install it on RPM based distros, and I  don't know how to build a deb from binaries.

This is the only thing stopping me from using Ubuntu as my daily machine (have a ton of shared files on the Ximeta disk I need to access).

Ximeta has written a Linux driver, and provides binaries see here:
[http://code.ximeta.com/cgi-bin/trac.cgi](http://code.ximeta.com/cgi-bin/trac.cgi)

Can anyone give me (or tell me where to to find instructions (that a noob like me would understand) for doing this?

Any help GREATLY appreciated...

-Nathan Hill

P.S.
I tried posting questions to the following thead numerous times with out any luck:
[http://www.ubuntuforums.org/showthread.php?t=31135](http://www.ubuntuforums.org/showthread.php?t=31135)[/QUOTE]

Well, there are a couple things you could try.  You could see if the "alien" prgram can import the RPM for you.  You could also get the source tarball and use "checkinstall" to build and install it for you.  Search the forums for references to those programs and you will get many examples.

---

### Post by nathanhill on 2005-09-12
Hey - thanks for both of the replies! (I'm not alone after all  \\:D/ )

Alien won't work, as there is nowhere I can download an RPM (any longer, now Ximeta only provides a Tarball)

I gave it my best shot, but didn't really get anywhere...

I downloaded the Tarball, upacked it, and looked at the ReadMe file, which indicated that I must first download the Kernel source.
I did that (apt-get install linux-source-2.6.10)

Then the Tarball Readme indicated I should compile the kernel using:
#make oldconfig
I did that, but don't think it worked.  Got the following message:
*** Error during writing of the kernel configuration.
make: *** [oldconfig] Error 1

Anyhow after that, the Readme says to edit the Makefile (the Kernel makefile I assume)?  But I'm really not sure as they just indicate:
"Then make the whatever changes necessary to match the kernel version that you are running" - but as the do not provide any specific instructions for Debian distros, I'm was not sure what to do, so I skipped this part...

When I looked the files contained in the Tarball, I also took a look at the Makefile.  I do not know what script Makefiles are written with, but it looked like some kind of environment variables are referenced.  I checked if I had them using export, and I didn't, so I set the following:
#export NDAS_KERNEL_PATH=/usr/src/linux-source-2.6.10
#export NDAS_KERNEL_VERSION=2.6.10

After that I tried using CheckInstall.
First I CD'ed to the location I packed out the tarball to, and ran:
#sudo checkinstall 
This did not work either - got the following error:
make: *** No rule to make target `install'.

I also tried running:
#make install - same error

I also tried just running 
#make

This looked more promising.  Make seemed to run through the Makefile script, and output a bunch of files (among others an executable called <ndasadmin>)

I can not execute this executable however...

If someone could take the time to try this out on their system, and give me some newbee'ized instructions that would be really wonderful.

Until then, I'll keep on Googling and trying things, but I'm getting a bit frustrated 'shooting in the dark'...  ](*,) 

-Nathan

---

### Post by TwiceOver on 2005-09-12
I'd love to help you out.  I have the same Ximeta Netdisk but I am also an extreme newbie when it comes to Linux.  Hopefully someone can get this going.

---

### Post by mlomker on 2005-09-12
The general process for compiling things:

su (or run a root terminal)
./configure (if a file named that is in the directory, otherwise continue)
make
make install  (you could also use checkinstall if you want to make a .deb file of the package but it doesn't always work).

Sounds like you just need to **make install** in that directory.

If you need to start over for any reason, type **make clean** and it deletes everything that it's done so far.

---

### Post by nathanhill on 2005-09-12
Thanks for the feedback.

I did try that...

I get the same error (mentioned above) when running **checkinstall / make install** :(
-Irregardless of weather I have run Make first or not...

I went at it again (tried **make clean**) before, and still no joy...

I'm obviously going at it wrong - but am not sure what angle to take now...

---

### Post by mlomker on 2005-09-13
[QUOTE=nathanhill]I'm obviously going at it wrong - but am not sure what angle to take now...[/QUOTE]

I can't offer an opinion if you don't post the error messages.

---

### Post by nathanhill on 2005-09-13
Sorry mloker, I wan't clear in my answer...
The errors were the same as in my previous post above:

> After that I tried using CheckInstall.
First I CD'ed to the location I packed out the tarball to, and ran:
#sudo checkinstall
This did not work either - got the following error:
make: *** No rule to make target `install'.

I also tried running:
#make install - same error

I also tried just running
#make
 

After your last post I tried running make, and then **make install**, and I still get the same error as before (same error for both **make install** and **checkinstall**:
make: *** No rule to make target `install'.

Could you possibly try downloading the tarball and doing a test installation?
If you get to the point where you can successfully checkinstall the driver, you may more easily see where I'm going astray?

---

### Post by mlomker on 2005-09-14
[QUOTE=nathanhill]If you get to the point where you can successfully checkinstall the driver, you may more easily see where I'm going astray?[/QUOTE]

Let me get back to you on that.  The problem is that I run 64-bit Ubuntu and that is a 32-bit program.  I was thinking about installing 32-bit on another machine today just for such occassions.

---

### Post by mlomker on 2005-09-14
[QUOTE=nathanhill] you may more easily see where I'm going astray?[/QUOTE]

My guess is that you probably didn't have the linux source installed.  I built the executable and it's just a single file as far as I can see.  Send me a private message on here (or post your email address) and I'll just email the file to you.

---

