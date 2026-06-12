---
title: "I downloaded a .patch file..."
date: 2009-03-20
forum: New to Ubuntu
---

### Post by -LOC- on 2009-03-20
I downloaded a .patch file (grub-0.97-silent_succeed.patch) that I want to try out, but I don't know what to do with .patch files.  It's a text file on my desktop.  How can I make it do what it is supposed to do!?

BTW: I got it from here: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/131389](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/131389)

---

### Post by taavikko on 2009-03-20
You need to patch source with it.
But I'm sure you have no apparent need to apply it.

How does this bothers you when you see few text-messages before usplash starts?

And finally, which version of *Buntu you are using?

---

### Post by -LOC- on 2009-03-20
> **taavikko said:**
> You need to patch source with it.
But I'm sure you have no apparent need to apply it.

How does this bothers you when you see few text-messages before usplash starts?

And finally, which version of *Buntu you are using?

I'm using Ubuntu 8.10.

What do you mean, "patch source with it?"

I know there is no need for the patch, it's just that seeing the text really iritates me.  It looks unprofessional.

The wonderful thing about Ubuntu and Linux in gerneral is that if there is something that bothers you, you have the power to change it.  I thought I had found my solution with this patch thing but I don't know how to use it.

If you can help me use this, I'd be greatfull.

---

### Post by mikechant on 2009-03-20
I believe you have to install the 'build-essentials' package before you can compile stuff etc. on Ubuntu.

Next, here is the link for how to obtain grub source and build it:

[http://www.gnu.org/software/grub/manual/grub.html#Obtaining-and-Building-GRUB](http://www.gnu.org/software/grub/manual/grub.html#Obtaining-and-Building-GRUB)

See if you can get this to work before trying to patch.

If that's OK, then you need to use the 'patch' command to apply the patch file. I think if you make sure you are in the directory that contains the grub-0.97 directory created above, then the command
patch -p0 patchfilename
should do it.

Have a look at the patch manual (particularly the bit about the -p parameter) - online at [http://linux.die.net/man/1/patch](http://linux.die.net/man/1/patch)
and see if you think this is right

One the patch is applied, rebuild from source as before.

Notes:
I haven't done any of this myself. This is educated guesswork. Maybe someone else can confirm or correct.

You may need to uninstall the packaged version of grub first to avoid conflicts.

Because the boot loader is so crucial, if I was doing this I would want to try this process on a seperate test install of Ubuntu first.

Good luck!

---

### Post by lloyd_b on 2009-03-20
> **mikechant said:**
> I believe you have to install the 'build-essentials' package before you can compile stuff etc. on Ubuntu.

Next, here is the link for how to obtain grub source and build it:

[http://www.gnu.org/software/grub/manual/grub.html#Obtaining-and-Building-GRUB](http://www.gnu.org/software/grub/manual/grub.html#Obtaining-and-Building-GRUB)

See if you can get this to work before trying to patch.

If that's OK, then you need to use the 'patch' command to apply the patch file. I think if you make sure you are in the directory that contains the grub-0.97 directory created above, then the command
patch -p0 patchfilename
should do it.

Have a look at the patch manual (particularly the bit about the -p parameter) - online at [http://linux.die.net/man/1/patch](http://linux.die.net/man/1/patch)
and see if you think this is right

One the patch is applied, rebuild from source as before.

Notes:
I haven't done any of this myself. This is educated guesswork. Maybe someone else can confirm or correct.

You may need to uninstall the packaged version of grub first to avoid conflicts.

Because the boot loader is so crucial, if I was doing this I would want to try this process on a seperate test install of Ubuntu first.

Good luck!

Two notes.  First off, with 'buntu systems, you should ideally get the source from the repositories, rather than from off of the web:```
apt-get source grub
```will retrieve the sources for the grub package that's currently installed on your system.

Second, using the patch program requires some shell redirection:```
patch -p0 < patchfile
```

Lloyd B.

---

### Post by -LOC- on 2009-03-20
Hey, thanks for this.  I managed to patch it, but the patch doesn't work correctly.  It still appears but quicker with it installed. IDK.  I updated to GRUB2 now, and it has some options to get rid of things I don't like in it.  I'm playing around with those now to see how they work.  If GRUB2 doesn't work, I'll rewrite the source itself to remove the offending lines myself.  I don't want to do that, but it'll be a soultion.  And it'll give me something to do!  AH, self imposed busy work!

---

