---
title: "Cannot read boot cd"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Aksha on 2008-12-21
I have did checksums and everything and i am pretty sure the disk burned right as it is my 5th try burning it at 4x. What should i do to install? wubi has worked for me but the normal way won't, is there a way i can use wubi and then switch over to a partitioned normal way?

---

### Post by Aksha on 2008-12-21
somebody help please

---

### Post by Aksha on 2008-12-21
Why no one respond to my questions?!?

---

### Post by Kareeser on 2008-12-21
Because you're impatient. :)

Boot into the BIOS, and make sure your computer tries to boot from the CD first, instead of the hard drive.

---

### Post by Aksha on 2008-12-21
> **Kareeser said:**
> Because you're impatient. :)

Boot into the BIOS, and make sure your computer tries to boot from the CD first, instead of the hard drive.

ok i test this then come back to tell u the outcome

---

### Post by Aksha on 2008-12-21
my cd drive is set to boot first on my bios and i still get same message once i click install

---

### Post by 2hot6ft2 on 2008-12-21
Computer specs, age of pc, does the cd drive boot with other bootable cd's (ie windows recovery cd/dvd), is it a laptop/desktop, does it do anything, does it just ignore the disc, does it freeze, how far does it get????????? More info than it don't work might help.

Seriously how are we supposed to know if you don't give any info so we can try and help?

---

### Post by 2hot6ft2 on 2008-12-21
> **Aksha said:**
> my cd drive is set to boot first on my bios and i still get same message once i click install
I gather that means you're getting to the desktop of the livecd. What exactly does it do when you click on the install icon? What message?

---

### Post by Aksha on 2008-12-21
yes it gets to intall desktop then once i click one of the options it freezes for awhile then pops up with message" can't read boot cd"

---

### Post by Aksha on 2008-12-21
> **2hot6ft2 said:**
> Computer specs, age of pc, does the cd drive boot with other bootable cd's (ie windows recovery cd/dvd), is it a laptop/desktop, does it do anything, does it just ignore the disc, does it freeze, how far does it get????????? More info than it don't work might help.

Seriously how are we supposed to know if you don't give any info so we can try and help?

amd 64 athlon, desktop, windows cds work i think, it freezes once i click install

---

### Post by 2hot6ft2 on 2008-12-21
When it gets to where you choose your language, after choosing the language I believe it's the F6 key for other options hit it and add noacpi to the end and hit Enter that may help.

---

### Post by teh_yodeler on 2008-12-21
Try burning it with another computer, and be patient!  Fiddle around with it and try to get it working.

Try to install directly from the main menu instead of going to the desktop first.  Do you know what I mean?

---

### Post by Aksha on 2008-12-21
> **teh_yodeler said:**
> Try burning it with another computer, and be patient!  Fiddle around with it and try to get it working.

Try to install directly from the main menu instead of going to the desktop first.  Do you know what I mean?

oh i don't get to the desktop only the main menu

---

### Post by 2hot6ft2 on 2008-12-21
It's an AMD 64 so it's not real old and it's reading the drive. But once you click on install it stops reading the cd. So you're making progress.

Now there is enough info for people to be able to offer solutions.

---

### Post by Aksha on 2008-12-21
yes it reads the cd until the main menu where it has the live and install option then when i click one of those i get "can't read boot cd" then a reboot button

---

### Post by 2hot6ft2 on 2008-12-21
> **2hot6ft2 said:**
> When it gets to where you choose your language, after choosing the language I believe it's the F6 key for other options hit it and add noacpi to the end and hit Enter that may help.

Did you try adding the noacpi option?

---

### Post by Aksha on 2008-12-21
> **2hot6ft2 said:**
> Did you try adding the noacpi option?

not yet, what does that do>>

---

### Post by 2hot6ft2 on 2008-12-21
I'm not exactly sure but it's always the first thing they suggest. I think that acpi is in effect a hardware interrupt and it looks like your cd drive may be getting interrupted. There are a few other acpi options that can be used but someone else will have to chime in with those.

Using noacpi wont have any lasting effect it only disables it for the current session.

---

### Post by Aksha on 2008-12-21
i tried the noacpi and every mode that is there, still same message ;(

---

### Post by 2hot6ft2 on 2008-12-21
Since it's a desktop. You may want to try swapping the cd drive out with another one. I had a similar issue and took the drive out of my external dvd burner and put it in the pc and it worked perfectly.

Perhaps you have another one lying around or a friend that would let you borrow theirs for your install.

There's really nothing to swapping drives they just plug in and unplug like anything else just with different connectors. Have the pc off when swapping drives and touch the case first to get rid of any static electricity before handling them.

Beyond that someone else will have to try and help.

---

### Post by Aksha on 2008-12-21
> **2hot6ft2 said:**
> Since it's a desktop. You may want to try swapping the cd drive out with another one. I had a similar issue and took the drive out of my external dvd burner and put it in the pc and it worked perfectly.

Perhaps you have another one lying around or a friend that would let you borrow theirs for your install.

There's really nothing to swapping drives they just plug in and unplug like anything else just with different connectors. Have the pc off when swapping drives and touch the case first to get rid of any static electricity before handling them.

Beyond that someone else will have to try and help.

i've tried my 2 cd drives both pop up with same message.

---

### Post by mw2239 on 2008-12-21
i had the same problem for ages, make sure your using the most recent release of ubuntu!
and mine worked when i burnt it at the max speed i could, and i installed it not using teh live desktop, i just used the install ubuntu choice!
have you done the "check cd for defects" or simmiliar option??

---

### Post by Aksha on 2008-12-21
> **mw2239 said:**
> i had the same problem for ages, make sure your using the most recent release of ubuntu!
and mine worked when i burnt it at the max speed i could, and i installed it not using teh live desktop, i just used the install ubuntu choice!
have you done the "check cd for defects" or simmiliar option??

i can't click that option either, any option i click gives me the cannot read error i have tried burning at numerous speeds

---

### Post by Aksha on 2008-12-21
anyone else have pointers?

---

### Post by Aksha on 2008-12-21
waiting

---

### Post by IamReck on 2008-12-21
You may have to wait for a while, this is a volunteer thread, and you have not been exactly clear what your issue was or what platform you are running on.

We need PC specs, life your processor types, your video card, how much RAM you have, and the make and model of your computer.

And don't be so impatient, no one here is getting paid to do this, this is all individuals volunteering.

Be polite, user correct grammar, explain your problem clearly, and maybe someone will get around to helping you, I suggest you go back and edit your original post to more accurately describe the problem.

---

### Post by Kareeser on 2008-12-21
Try burning the .iso file from another computer with a CD burner. Your burner may be at fault, like my laptop's was.

---

### Post by az on 2008-12-21
Create a bootable USB ubuntu installation.

---

### Post by evilkastel on 2008-12-21
OK, so here is my recommendation
1. if you can not take a deep breath and chill, maybe GNU/Linux is not for you. 
2. Try burning the cd from a different pc.
3. try making a liveUSB from another PC.
4. are you using the x86_64 live cd? or the ix86 one?
Eitherway, you might try to use the other, since i believe you said you have a x64 processor.
5.stop doubleposting and bunping please. thats just anoyying and keeps people from trying to help you.

EDIT: lol i practically stole last posts, sorry, honest mistake. nevertheless, this may be the way to go.

---

### Post by Immolatus on 2008-12-21
try a different iso altogether. Maybe it just lost a peace during download. I would have done that before swapping drives.

---

### Post by evilkastel on 2008-12-21
> try a different iso altogether. Maybe it just lost a peace during download. I would have done that before swapping drives.

he said he checkes MD5 sums... so thats not it i believe.

---

