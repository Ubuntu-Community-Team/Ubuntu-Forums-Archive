---
title: "I bet some person out there is smart enough..."
date: 2009-08-19
forum: New to Ubuntu
---

### Post by ithinkitschad on 2009-08-19
Okay how do I merge sda5 with the unallocated partition? I've booted into ubuntu live and tried gparted but it didn't work. Sda5 is ubuntu. So can anyone help?

---

### Post by Grenage on 2009-08-19
Why 'did it not work'?

---

### Post by ithinkitschad on 2009-08-19
> **Grenage said:**
> Why 'did it not work'?

There was no option to merge the partitions

---

### Post by t0p on 2009-08-19
I think you can use gparted to increase the size of sda5 so it takes up the unallocated space.  If that doesn't work, please explain what gparted says about it.  Just saying "it didn't work" is not at all helpful.

---

### Post by Grenage on 2009-08-19
If it's 'unallocated' then you simply want to increase the size of sda5.

---

### Post by ithinkitschad on 2009-08-19
Sorry I didnt explain more. If I try to resize sda5 it wont let me expand it. As if the unallocated space wasn't there. I dont really know what other information i can give. Theres no option to "merge" the partitions, and I cant resize a partition to take up the unallocated space.

---

### Post by Grenage on 2009-08-19
Ah.

This is your system partition, and partitions need to be unmounted before modifying.  You'll want to boot from a live CD.

---

### Post by ithinkitschad on 2009-08-19
> **Grenage said:**
> Ah.

This is your system partition, and partitions need to be unmounted before modifying.  You'll want to boot from a live CD.

... Yes, as I said in the first post, I've tried booting into a live cd. But it didnt work. Thats where the confusion craps on my brain. I thought that would make it work.

---

### Post by mcduck on 2009-08-19
> **ithinkitschad said:**
> There was no option to merge the partitions

You can't merge them if you only have one partition and the rest is unallocated space (so it's not a partiton at all).

Instead you want to expand the partition you have to contain the currently unallocated space. ;)

edit: the point other people have made about unmounting the partition beforehands is also a valid one, you can't edit mounted partitions. Also your partton has to be located next to the unallocated space, since partition really is about physical management of data on your drive (so you can't combine partitions that have other data between them)

---

### Post by Grenage on 2009-08-19
Sorry, I missed that part.  Does it not give you the option to unmount?  Does it think the space is a partition?  Any chance of a screenshot?

---

### Post by howefield on 2009-08-19
Can you post a screenshot of gparted showing the disk ?

---

### Post by theozzlives on 2009-08-19
> **Grenage said:**
> Sorry, I missed that part.  Does it not give you the option to unmount?  Does it think the space is a partition?  Any chance of a screenshot?

sda5 is most likely swap, it would be a logical partition. You would have to resize the extended patition, then resize sda5. If that's not the case, post a screenshot of your gparted screen. Just hit Alt + PrntScrn at the same time.

---

### Post by ithinkitschad on 2009-08-19
Ok instead of quoting a few people, when I boot into a live cd... None of the partitions are mounted. (I've said a few times I'm booting in a live cd, thats the only way it would work) If I open gparted.. I've already moved the unallocated partition to ext3 or whatever you want. Look lets simplify it, if someone knows what thier talking about tell me what to do. I know I have to be on a live cd. I understand that my effing operating system cant be mounted while i merge it with another partition. My problem is that the live gparted in ubunted gave me no options to do it, and knoppix didnt work.

---

### Post by ithinkitschad on 2009-08-19
> **theozzlives said:**
> sda5 is most likely swap, it would be a logical partition. You would have to resize the extended patition, then resize sda5. If that's not the case, post a screenshot of your gparted screen. Just hit Alt + PrntScrn at the same time.

[]("http://ubuntuforums.org/member.php?u=420456")theozzlives, yes my homeboy. nah, sda5 is my logical, my swap is sda6. But damn you help out you seem smart. You thought me about the ubuntu symbol

---

### Post by oboedad55 on 2009-08-19
> **ithinkitschad said:**
> Ok instead of quoting a few people, when I boot into a live cd... None of the partitions are mounted. (I've said a few times I'm booting in a live cd, thats the only way it would work) If I open gparted.. I've already moved the unallocated partition to ext3 or whatever you want. Look lets simplify it, if someone knows what thier talking about tell me what to do. I know I have to be on a live cd. I understand that my effing operating system cant be mounted while i merge it with another partition. My problem is that the live gparted in ubunted gave me no options to do it, and knoppix didnt work.

Are you sure you're not trying to resize a logical partition inside an extended one?

Jon

---

### Post by ithinkitschad on 2009-08-19
[IMG]http://ubuntuforums.org/home/chunks/pics/Screenshot.png[/IMG]

---

### Post by theozzlives on 2009-08-19
> **ithinkitschad said:**
> []("http://ubuntuforums.org/member.php?u=420456")theozzlives, yes my homeboy. nah, sda5 is my logical, my swap is sda6. But damn you help out you seem smart. You thought me about the ubuntu symbol

Glad to help. :)

---

### Post by ithinkitschad on 2009-08-19
> **oboedad55 said:**
> Are you sure you're not trying to resize a logical partition inside an extended one?

Jon

Yeah, I'm not trying to do that. Can I post a screenshot of gparted just from my computer or do I have to upload it somewhere?

---

### Post by ithinkitschad on 2009-08-19
Someone knows what to do...

---

### Post by mcduck on 2009-08-19
> **ithinkitschad said:**
> Yeah, I'm not trying to do that. Can I post a screenshot of gparted just from my computer or do I have to upload it somewhere?

Yes, you can post it directly to the forums. Use the paperclip icon in the message formatting options to attach the image to your message.

And please, have a bit of patience. You shouldn't keep bumping your thread every ten minutes, the recommendation is to bump once per 24 hours and even that only if you aren't getting any answers.

---

### Post by ithinkitschad on 2009-08-19
> **mcduck said:**
> Yes, you can post it directly to the forums. Use the paperclip icon in the message formatting options to attach the image to your message.

And please, have a bit of patience. You shouldn't keep bumping your thread every ten minutes, the recommendation is to bump once per 24 hours and even that only if you aren't getting any answers.

[ATTACH]125463[/ATTACH]
I apologize. Am I bumping it when I respond to people? Because I havent once posted "bump"

---

### Post by Cheesemill on 2009-08-19
OK. First of all you need to expand your extended partition (sda2) to take up all of the free space, then move swap (sda6) all the way to the right, and only then will you be able to expand sda5.
 
You can only expand a partition if it has free space **next** to it.
 
You may have to right click on swap and unmount it as the Live CD automatically uses any swap space it can find.

---

### Post by 3rdalbum on 2009-08-19
> **Cheesemill said:**
> OK. First of all you need to expand your extended partition to take up all of the free space, then move swap all the way to the right, and only then will you be able to expand sda5.
 
You may have to right click on swap and unmount it as the Live CD automatically uses any swap space it can find.

I didn't think it was possible to expand an extended partition? Or does it work when the extended partition is at the beginning of the disk?

---

### Post by ithinkitschad on 2009-08-19
> **Cheesemill said:**
> OK. First of all you need to expand your extended partition to take up all of the free space, then move swap all the way to the right, and only then will you be able to expand sda5.
 
You may have to right click on swap and unmount it as the Live CD automatically uses any swap space it can find.

Thank you, I've never tried that I'll boot up into the live cd right now and and try that. I'll be back soon.

---

### Post by mcduck on 2009-08-19
Cheesemill is right, your problem is that sda5 is inside the extended partition, and that your swap partition is between the unpartitioned psace and sda5.

You'll have to first resize sda2 to contain the whole disk, and then move sda6 to get free space next to the sda5. After that you can grow sda5 to use the free space.

---

### Post by infinitejones on 2009-08-19
Have you tried extending sda2 into the unallocated space? Then you can move the swap partition to the end of the new larger partition, and expand sda5.

And yes, every time someone (including you) adds a new post to a thread, it "bumps" it. When a search for threads is run, it returns the threads with most recent postings first. Hence any new post in a thread will "bump" it to the top.

Edit - beaten to it!

---

### Post by mcduck on 2009-08-19
> **3rdalbum said:**
> I didn't think it was possible to expand an extended partition? Or does it work when the extended partition is at the beginning of the disk?

extended partiton is a partition just like any other, and can be resized in the same way.

(the only difference is that if you want to shrink extended partition you have to shrink or remove the contained partitions first, resizing the extended partition won't automatically resize the contained partitions)

---

### Post by howefield on 2009-08-19
> **ithinkitschad said:**
> I apologize. Am I bumping it when I respond to people?

No

> **ithinkitschad said:**
> Because I havent once posted "bump"

Post number 19

---

### Post by ithinkitschad on 2009-08-19
... I guess I'm bumping it. At least its late at night, so many people aren't seeing it. Heres a pic of gparted now. 

[ATTACH]125466[/ATTACH]

So.. Really what do I do now... ?

---

### Post by dmizer on 2009-08-19
When you boot a live cd, it automatically looks for a swap partition on the hard disk. If it's there, it mounts the swap partition. In order to resize your disk you'll have to unmount swap with the following command at the command line:
```
sudo swapoff
```
For good measure, I also suggest running the following command:
```
sudo killall hald
```
You should be able to resize at will then.

---

### Post by Cheesemill on 2009-08-19
Why have you created a new partition? You just need to follow what I posted earlier.
 
Delete sda7
Move sda6 all the way to the right.
Expand sda5
 
Easy :)
 
 
PS - It's not late at night it's 11 in the morning.

---

### Post by ithinkitschad on 2009-08-20
> **Cheesemill said:**
> Why have you created a new partition? You just need to follow what I posted earlier.
 
Delete sda7
Move sda6 all the way to the right.
Expand sda5
 
Easy :)
 
 
PS - It's not late at night it's 11 in the morning.

cheesemill, i forgot to say thanks. You were completely right. I dont know why i was having trouble because I tried it again that way and it worked perfect. Thanks

---

