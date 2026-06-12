---
title: "What is burning? and making device bootable?"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by eb3ha4el on 2011-05-19
Hi

I got a really basic but have ever been wondering question.
I just don't understand the difference between
burning a CD for example and copying files into a CD...

Also regarding bootable device. What do we mean by bootable?
What differences there between just having installation files 
in device and bootable? 


Do both burning a CD and making bootable device require special software?


thanks in advance...

---

### Post by dniMretsaM on 2011-05-19
Copying files store the file on the CD. Burning makes them 'work' from the CD. Like music. You could copy the files to a CD and then take them off later just by copy -> pasting them from the CD to a computer. Burning them however would make it so you could play the music directly from the CD in a CD player or a computer program. Same for an ISO. If you simply copy the .iso file to the CD, it will be stored on it but not be of any use for booting from. However, if you burn it, it allows it to be accessed directly from the CD with no copying needed. Hope that helped.

---

### Post by papibe on 2011-05-19
I think you're referring to the the case of burning an ISO image vs. just copying the files.

In short, there are different methods, although they may provide similar results if the image just contains regular files.

When you have an special ISO like the Ubuntu installation or Live CD, the ISO itself has been created so it can boot when burned. That way you don't need special software.

For more detail information read the section "Boot sequence on standard PC (IBM-PC compatible)" [here]("http://en.wikipedia.org/wiki/Booting").

I hope it helps.

---

### Post by eb3ha4el on 2011-05-20
Thank you both of you

now I understand the difference.. 
but I'm just little wondering how is it actually different between process of burning or making device bootable... (also are they the same process? can I use burning software to make Live USB?)

---

### Post by tapi0n on 2011-05-20
> **eb3ha4el said:**
> Thank you both of you

now I understand the difference.. 
but I'm just little wondering how is it actually different between process of burning or making device bootable... (also are they the same process? can I use burning software to make Live USB?)


burning  (like dniMretsaM mentioned) is making the disk usable. When making a disk bootable it's dependant on the files you are burning. If the distributer of the files allow (and coded accordingly) you to make a bootable disk, you can make a bootable disk from it. If not, you can't.

So every bootable disk is burned, but not every burned disk is bootable.

Hope this is all somewhat correct, but that's at least what I get from it. If someone has a 'more correct' explenation please say so and I'll know too from now on :)

---

### Post by astamaja on 2011-05-20
Yes, you make a bootable Ubuntu live-cd in exactly the same manner as you would burn any other .iso file to a cd. As papibe pointed out, the "bootable" part is already included in the iso.
Live USB is a little bit different, I have only made through ubuntus Live USB maker (or whatever it's called), but you use the same .iso file as i recall.

Hope that makes it clearer

---

### Post by mcduck on 2011-05-20
Actually, copying a file to optical media is always the same as burning a file to a optical media.

The term "burning" simply comes from the process of the CD/DVD/BluRay drive using the laser to write the data to the media.

So it's not related to what you burn or in what format you do it. If you save data to optical media, you are burning it. Simple as that.

(mastering a disc would be different thing, that's what you do when you create, say, a Video DVD disc playable on regular DVD players, or create an Audio CD playavble on normal CD players. but even when mastering a disc, the process where the data is written to the media is called burning.)

What comes to making a drive/device bootable, that's quite simple as well. As you may know, the process of starting a computer and loading an operating system is called "booting". To load the operating system, the computer must be told where to load it from. Your BIOS settings will tell the system what device to use, but it still needs the exact location of files it needs to load on that device. That information is located on the first sectors of a disc on an area called "boot sectors". So making a drive bootable (instead of just copying files into it) requires you to write all the information needed to boot from that drive into the boot sectors.

edit: I just wanted to add that the reason why bootable CD's, like the Ubuntu CD, come as disc images is that the image not only contains the files, but also the exact structure of the disc including the boot sectors in the beginning. If you just write the files to the disc you miss the boot sector so your computer has no way of knowing what it should read from the disc to start the operating system.

---

### Post by eb3ha4el on 2011-05-20
> **tapi0n said:**
> burning  (like dniMretsaM mentioned) is making the disk usable. When making a disk bootable it's dependant on the files you are burning. If the distributer of the files allow (and coded accordingly) you to make a bootable disk, you can make a bootable disk from it. If not, you can't.

So every bootable disk is burned, but not every burned disk is bootable.

Hope this is all somewhat correct, but that's at least what I get from it. If someone has a 'more correct' explenation please say so and I'll know too from now on :)



Yes, that sounds clear. 
Sorry I'm getting into more questions...

What about difference between burning and just copying files?
i mean what does burning software actually do?
or more precisely, why copying files become just storage,
and burning makes the device something like auto-running, or bootable?


and about the ISO, is it distinguishable from copying files from CD or DVD or whateveer, since it preserves data as burned itself? so that it can be used as if burned CD is there when used with virtual driver?

---

### Post by eb3ha4el on 2011-05-20
> **mcduck said:**
> Actually, copying a file to optical media is always the same as burning a file to a optical media.

The term "burning" simply comes from the process of the CD/DVD/BluRay drive using the laser to write the data to the media.

So it's not related to what you burn or in what format you do it. If you save data to optical media, you are burning it. Simple as that.

(mastering a disc would be different thing, that's what you do when you create, say, a Video DVD disc playable on regular DVD players, or create an Audio CD playavble on normal CD players. but even when mastering a disc, the process where the data is written to the media is called burning.)

What comes to making a drive/device bootable, that's quite simple as well. As you may know, the process of starting a computer and loading an operating system is called "booting". To load the operating system, the computer must be told where to load it from. Your BIOS settings will tell the system what device to use, but it still needs the exact location of files it needs to load on that device. That information is located on the first sectors of a disc on an area called "Master Boot Record". So making a drive bootable (instead of just copying files into it) requires you to write all the information needed to boot from that drive into MBR.



You were giving me an answer to the questions I was writing at the same time :D
Great answer thank you very much

I suppose mastering device (ex. playable audio CD) employs
process similar to writing MBR as it does in making bootable device, is that right?

---

### Post by mcduck on 2011-05-20
> **eb3ha4el said:**
> You were giving me an answer to the questions I was writing at the same time :D
Great answer thank you very much

I suppose mastering device (ex. playable audio CD) employs
process similar to writing MBR as it does in making bootable device, is that right?

yes, depending on what type of disc you are mastering, it might involve creating a boot sector for it. But it also includes creating a specific file system structure or naming the files using certain format, and other tasks like that. It all depends on what type of disc you are creating.

For example a Video DVD requires certain structure of files with certain names on it so that DVD players can read it. And an Audio CD doesn't even *have* files or directories in it, the audio data is written to disc in completely different way than when with data CD's.

(mastering a disc doesn't include burning it, you could just as well master it into an image file and burn it later, or send the image to a disc factory so that they can start printing discs based on it. So mastering is just the process of collecting all the data that should go to the disc and converting it into the specific format and structure that certain type of disc should have.)

---

