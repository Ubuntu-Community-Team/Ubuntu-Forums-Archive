---
title: "Too much Swap"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by herbertportillo on 2010-01-25
I replaced an old 160GB hard drive with a 500GB hard drive today. I did a clean install of Ubuntu 9.10 on it, and that plus downloading and installing all the updates and applications I had before took a little under 2 hours :)

I have a little problem, though. There's too much swap. 14 GB of swap. Why is there so much? I know I don't need that much; I only have 5 GB of RAM. Is there a way to reduce the amount of swap, or would I have to wipe the hard drive and do what I just did all over again, except this time, tweak some setting before the OS installs? Any and all help is appreciated. Thanks.

---

### Post by sandyd on 2010-01-25
the swap is double the amount of ram you have to allow you to hibernate.
about the extra 4GB, not sure why its there.

---

### Post by Temposs on 2010-01-25
If you pop in your Ubuntu LiveCD, you can open the GParted(Partition Editor) program through System->Administration. You can edit your partition sizes from there.

---

### Post by audiomick on 2010-01-25
Hallo.
you can reduce your swap without re-installing. I think you mght then have to correct your fstab, which I unfortunately don't know how to do.

---

### Post by herbertportillo on 2010-01-25
Here's the screenshot of Gparted.

---

### Post by tom.swartz07 on 2010-01-25
> **herbertportillo said:**
> Here's the screenshot of Gparted.

Just right click it and select 'swapoff', then you could change the size however you want

Make sure youre running in LiveCD- otherwise youll damage your computer.

---

### Post by Temposs on 2010-01-25
I think first you want to reduce the size of your swap(1-2 times the amount of RAM your have), and then increase the size of your main partition into the free space created.

---

### Post by herbertportillo on 2010-01-25
Right now I'm running off of LiveUSB.
I won't damage my computer, right? My hard drive isn't mounted.
Giggity.

---

### Post by herbertportillo on 2010-01-25
Well, if I never use the Hibernation feature, it's safe to turn the swap off, right? But just turning off the swap doesn't let you write to that space, or does it?

---

### Post by cascade9 on 2010-01-25
> **herbertportillo said:**
> I have a little problem, though. There's too much swap. 14 GB of swap. Why is there so much?

Let me guiess...you let ubuntu choose the sizes of partitions automatically? It always does something silly if I let it do that. :| 

Yeah, if you just turn swap off you wont be able to use that space.

---

### Post by matchett808 on 2010-01-25
and why is it too much swap? i think thats what i have (roughly, i think mines might be 12 but i have only 4 gig of ram....)

---

### Post by audiomick on 2010-01-25
No, you have to reduce the size of your swap partiton to re-assign the space to another.
As has been mentioned, if you want to hibernate, make the swap partition a fraction bigger than your RAM. If you don't, you can probably shrink it to 1GB without any trouble. I have 4GB of RAM, and barely even scratch the swap space. If you don't do anything extremely RAM intensive, you should see similar behaviour.
Bear in mind, I think, but am not sure, that if you change the size of your swap, you will have to correct your fstab.

---

### Post by theozzlives on 2010-01-25
You've got 450+ GB of space with the swap? I wouldn't worry about it. I've got a 320 GB HD, 8 GB swap and still have 200+ GB in my /home partition.

---

### Post by audiomick on 2010-01-25
> **matchett808 said:**
> and why is it too much swap? 

That much swap wont break anything, and if you have enough drive space that you don't need the space, there is no real reason to change it.
It is just that it is more than you need for almost all situations.

---

### Post by herbertportillo on 2010-01-25
Yeah, when I installed the OS I told it to take up all of the new hard drive (which is what I wanted; I haven't had Windows on my computer for over 5 months, thank you, thank you very much).

Can I reduce the swap size and move the leftover space to /dev/sda1? If I can, how do I do that?

---

### Post by cascade9 on 2010-01-25
> **matchett808 said:**
> and why is it too much swap? i think thats what i have (roughly, i think mines might be 12 but i have only 4 gig of ram....)

Because its way to much swap space for that much RAM. You'll _never_ use it. Any bigger than 2xRAM for swap space is pretty crazy (in most cases, if you had 256MB or less then more than 2x might make sense)

---

### Post by Sef on 2010-01-25
If you want to use hibernation, then have [swap equal to your RAM]("https://help.ubuntu.com/community/SwapFaq").   If not, then 1 - 2 gb swap will be more than enough.

---

### Post by herbertportillo on 2010-01-25
Hmm. The consensus seems to be that it won't hurt to have that much swap.
Well, I guess I'll just let the gluttonous swap be. :)

---

### Post by JBAlaska on 2010-01-25
> **sef said:**
> if you want to use hibernation, then have [swap equal to your ram]("https://help.ubuntu.com/community/swapfaq").   If not, then 1 - 2 gb swap will be more than enough.

+1

---

### Post by audiomick on 2010-01-25
> **herbertportillo said:**
> Hmm. The consensus seems to be that it won't hurt to have that much swap.
Well, I guess I'll just let the gluttonous swap be. :)

Fix it next time you re-install. The day will come...:D

---

### Post by cascade9 on 2010-01-25
> **Sef said:**
> If you want to use hibernation, then have [swap equal to your RAM]("https://help.ubuntu.com/community/SwapFaq").   If not, then 1 - 2 gb swap will be more than enough.

I thought that you needed more swap than RAM for hibernation to work, not equal.

---

### Post by audiomick on 2010-01-25
> **cascade9 said:**
> I thought that you needed more swap than RAM for hibernation to work, not equal.

From what I have read,  equal. Hibernate writes the contents of the RAM to the swap space when it puts the computer to sleep.

I think it is easier to aim for a bit more than RAM when installing rather than trying to get it right on the nose.

---

### Post by matchett808 on 2010-01-26
so let me get this right, if you have plenty disc space then you can have as much swap as you want.....(as long as its more than your ram or equal....etc....)  

so there is no such thing as too much swap space (as long as you have enough disk space...) just anything over what is needed for hibernation becomes 'wasted'?

---

### Post by SuperSonic4 on 2010-01-26
> **matchett808 said:**
> so let me get this right, if you have plenty disc space then you can have as much swap as you want.....(as long as its more than your ram or equal....etc....)  

so there is no such thing as too much swap space (as long as you have enough disk space...) just anything over what is needed for hibernation becomes 'wasted'?

You can have as much or as little swap as you like. I have 12GiB swap because I have plenty of space

You can have no swap if you like but it means you can't hibernate and if you max your ram you'll lose performance. Generally if you have over 4gb RAM you don't need swap (I have 8GB and still swap)

Pretty much anything about 12gb is useless for hibernation purposes though.

---

### Post by audiomick on 2010-01-26
> **matchett808 said:**
> so let me get this right, if you have plenty disc space then you can have as much swap as you want.....(as long as its more than your ram or equal....etc....)  

so there is no such thing as too much swap space (as long as you have enough disk space...) just anything over what is needed for hibernation becomes 'wasted'?

Pretty much dead on the nose. If you were doing something like editing 5 feature length films simultaneously, you might find yourself using that much swap, otherwise it will most likely not see much use. However, it wont hurt you in any way, as long as you can spare the space.

---

### Post by philinux on 2010-01-26
I have 2 gig ram and swap partition is 2 gig. Hibernation works just fine.

Any more swap would be completed wasted.

---

