---
title: "Incompatible programs (i386)"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by snout71 on 2009-03-19
Have just installed UBUNTU

am a complete beginner, wanted to use my old DELL GX270 for something the kids can learn on, so i thought why not, windows slowed it down too much

it is great, the only thing is that most of the better software like the draw and paint and other educational software seems to be incompatible (i386) message appears

what is this? have yet to install my BELKIN adapter to connect to internet on it

any ideas?

---

### Post by mlentink on 2009-03-19
What versions of 'draw' and 'paint were you trying to install? Did you try and install them from the "Add/Remove Software"option in your applications menu?

---

### Post by philinux on 2009-03-19
> **snout71 said:**
> Have just installed UBUNTU

am a complete beginner, wanted to use my old DELL GX270 for something the kids can learn on, so i thought why not, windows slowed it down too much

it is great, the only thing is that most of the better software like the draw and paint and other educational software seems to be incompatible (i386) message appears

what is this? have yet to install my BELKIN adapter to connect to internet on it

any ideas?

You'll need to get connected to the net to download apps from ubuntu's servers or repo's as they are known.

---

### Post by snout71 on 2009-03-20
geeez

i wasnt expecting a reply straight away :)

thought i would switch off and check the next day and it turns out i have 2 replies as soon as i had posted the question :)

was looking at Gcompris, KTurtle and Tuxpaint

they came on the install disc that i downloaded (8.10)Ubuntu

They all say same message "cannot be installed on your computer type (i386)"

in reply to the other reply, i shall try and get my belkin adapter to work on it as there is a thread i found in the forums as my system hasnt recognised my installed wireless card

---

### Post by t0p on 2009-03-20
> **snout71 said:**
> 
was looking at Gcompris, KTurtle and Tuxpaint

they came on the install disc that i downloaded (8.10)Ubuntu

They all say same message "cannot be installed on your computer type (i386)"

I don't understand what you mean.  When exactly are you seeing this message about incompatibility?

Have you downloaded the .iso for 64-bit machines or something?  I don't get why you'd be getting messages about apps not being compatible with your i386 machine.

:confused:

---

### Post by snout71 on 2009-03-20
it is the message i received trying to install using the add/remove function

Solved. have just downloaded Edbuntu and installed programs i wanted. they look great, kids will love them

pity the desktop remains the same though, would be nice to have it a little child friendly

thanks

---

### Post by mlentink on 2009-03-20
> **snout71 said:**
> pity the desktop remains the same though, would be nice to have it a little child friendly

But the ubuntu desktop is configurable to your hearts delight. Have a look at [http://www.gnome-look.org/](http://www.gnome-look.org/) for starters

---

### Post by snout71 on 2009-03-23
thank you MLENTINK,

i followed that link and now have a great desktop for the kids

looking at Ubuntu, i like, think i will dual boot my main desktop so i can have the best of both worlds till i get more confident with ubuntu. dont know why i didnt try it before now

much appreciated

---

### Post by baw4h on 2009-05-20
> **snout71 said:**
> geeez

i wasnt expecting a reply straight away :)

thought i would switch off and check the next day and it turns out i have 2 replies as soon as i had posted the question :)

was looking at Gcompris, KTurtle and Tuxpaint

they came on the install disc that i downloaded (8.10)Ubuntu

They all say same message "cannot be installed on your computer type (i386)"

in reply to the other reply, i shall try and get my belkin adapter to work on it as there is a thread i found in the forums as my system hasnt recognised my installed wireless card

I'm having this same problem (the problem was never solved in this thread).  I first installed Ubuntu 9.04 a few days ago (64-bit version since I have an amd64 system) and I got the error "cannot be installed on your computer type".  I thought it must be because I was running 64-bit and most programs are still built for 32-bit.  So I installed Ubuntu 9.04 32-bit over the 64-bit and now I get the error "cannot be installed on your computer type (i386)" for everything in the add/remove programs that isn't already installed.

---

### Post by ibuclaw on 2009-05-20
If you do run into that problem, can you post the output of
```
uname -m
```
and
```
dpkg-architecture
```

Regards
Iain

---

### Post by durand on 2009-05-20
Try Qimo. [http://www.qimo4kids.com/](http://www.qimo4kids.com/) I've been told that it's a great kid friendly linux distro.

---

### Post by baw4h on 2009-05-20
Ran uname -m
i686

had to run sudo apt-get install dpkg-dev before I could run dpkg-architecture. Results attached.

---

### Post by durand on 2009-05-20
I'd guess that you were using the x64 versions of the programs and you have x32 on your computer. They're incompatible. If it were the other way round, it would work. Just install the programs directly in ubuntu, without the cd. Look in Add/Remove programs or System > Administration > Synaptic Package Manager.

---

### Post by baw4h on 2009-05-21
> **durand said:**
> I'd guess that you were using the x64 versions of the programs and you have x32 on your computer. They're incompatible. If it were the other way round, it would work. Just install the programs directly in ubuntu, without the cd. Look in Add/Remove programs or System > Administration > Synaptic Package Manager.

I'm not sure what you mean.  I installed 32-bit Ubuntu over 64-bit on a 64-bit system. That much I know.  But I'm installing off the 32-bit disc.  Should I just re-format it all and re-install 32-bit?  

I can't install over the internet yet, because I need to install MySQL before I can use the 'replace' command and install my wireless driver ([http://ubuntuforums.org/showthread.php?t=1155941](http://ubuntuforums.org/showthread.php?t=1155941)).  My computer is too far from the fios adapter to connect with a cable.  I don't have a wire long enough.

---

### Post by durand on 2009-05-21
Yeah you should probably reinstall. From what I can tell, you installed over a 64bit installation without formatting it so it has a mixture of 32 and 64bit. You should probably just install 64bit if you can.

---

### Post by rob2uk on 2009-05-21
> **durand said:**
> Yeah you should probably reinstall. From what I can tell, you installed over a 64bit installation without formatting it so it has a mixture of 32 and 64bit. You should probably just install 64bit if you can.

Hmmm, I'd probably give the opposite advice -

Reformat, install the 32 bit version.

I stuck with Ubuntu x64 for 2 months before I got fed up with 'wrong architecture (i386)' errors

---

### Post by durand on 2009-05-21
> **rob2uk said:**
> Hmmm, I'd probably give the opposite advice -

Reformat, install the 32 bit version.

I stuck with Ubuntu x64 for 2 months before I got fed up with 'wrong architecture (i386)' errors

You're not supposed to get wrong architecture errors unless something bad is happening...I've had 64 bit for 2 months now and I've never had that error.

---

### Post by baw4h on 2009-05-21
When I first installed Ubuntu, I went 64-bit.  I was getting architecture errors in add/remove which is why I installed over 64 with 32.  I'll try reformatting when I get off work and post results late tonight.

---

### Post by rob2uk on 2009-05-21
> **durand said:**
> You're not supposed to get wrong architecture errors unless something bad is happening...I've had 64 bit for 2 months now and I've never had that error.

hmmm, interesting.

I had the 32 bit compatibility libs installed, but I just figured it was that I had made a bad choice for a know-nothing n00b, so figured I'd be better off backing up my docs and starting from scratch

---

### Post by durand on 2009-05-21
> **rob2uk said:**
> hmmm, interesting.

I had the 32 bit compatibility libs installed, but I just figured it was that I had made a bad choice for a know-nothing n00b, so figured I'd be better off backing up my docs and starting from scratch

I dunno. I didn't have to install any 32bit compatibility libs. If I ran a 32 bit application, it just worked but almost all applications have a 64bit version these days.

---

