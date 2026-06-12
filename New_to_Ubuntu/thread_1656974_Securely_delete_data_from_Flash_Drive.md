---
title: "Securely delete data from Flash Drive"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by Prince Valiant on 2010-12-31
Hello,

I'm wondering how to securely delete data from a USB Flash Drive, and still leave the drive intact and usable.  :-D

I've heard about writing zeroes, and that (at least on a disk-type HD) the previous data can still be read.  I'm not paranoid, but curious: how can one completely remove all traces of data on a flash drive in such a way that absolutely no one could ever recover it?

Thanks for indulging a curious Ubuntu user!
-Val

---

### Post by Verbeck on 2010-12-31
```
dd if=/dev/urandom of=/dev/sd**X**
```would overwrite all data on a drive

source : [http://en.wikipedia.org/wiki/Dd_%28Unix%29]("http://en.wikipedia.org/wiki/Dd_%28Unix%29")

edit: didn't work - post #6

---

### Post by Prince Valiant on 2010-12-31
Thanks!

But my curiosity was in a slightly different question:

Could someone, with the right tools, recover whatever I overwrote?

---

### Post by JKyleOKC on 2010-12-31
> **Prince Valiant said:**
> how can one completely remove all traces of data on a flash drive in such a way that absolutely no one could ever recover it?
-ValProbably is not possible while leaving the drive usable, although overwriting with random data will make the remaining traces so tiny that only an organization like the National Security Agency would be able to find them.

Actually a flash drive might not retain any traces of older data; the traces that are left on magnetic media result from mechanical tolerances in the write and erase heads but a flash drive stores data in the form of persistent electrical charge.

Still the recommended method for removing "all traces" of data so that "no one could ever recover it" remains physical destruction of the drive. Grinding it to dust is usually effective...

---

### Post by Prince Valiant on 2010-12-31
> **JKyleOKC said:**
> Actually a flash drive might not retain any traces of older data; the traces that are left on magnetic media result from mechanical tolerances in the write and erase heads but a flash drive stores data in the form of persistent electrical charge.

That's what I thought is so interesting.  Is there any way for previous charges to be read?  Otherwise, like I read elswhere ([http://ask-leo.com/comments_003670.php?page=2]("http://ask-leo.com/comments_003670.php?page=2")), would an absolutely secure deletion be nothing more than overwriting the entire drive?

Thanks for your time!
-Val

---

### Post by Verbeck on 2010-12-31
> **Verbeck said:**
> ```
dd if=/dev/urandom of=/dev/sd**X**
```would overwrite all data on a drive

source : [http://en.wikipedia.org/wiki/Dd_%28Unix%29]("http://en.wikipedia.org/wiki/Dd_%28Unix%29")
just now i accidentally did that to the harddisk the the os is on (small typo - meant to do the flash disk) :mad:
but (after a kernel panic), testdisk from a live cd was abe to recover the /home \\:D/
could be new years luck\\:D/

---

### Post by s3a on 2010-12-31
You can use shred with lots of iterations (Do man shred in terminal).

---

### Post by frostschutz on 2010-12-31
> **Prince Valiant said:**
> I've heard about writing zeroes, and that (at least on a disk-type HD) the previous data can still be read.

No, that's wrong, a hoax, paranoia, etc. Data can only still be read if it wasn't actually overwritten (due to errors in hardware or software). There is no way to actually recover data from an overwritten sector.

It makes sense if you think about it: Modern storage media work use a ton of tricks to achieve a high data  density, you're lucky you can even reliably read your data back under  normal conditions... if you could recover overwritten data, you'd have doubled the data capacity of any storage media - just like that. (Un)fortunately things don't work that way. Storage media just don't have the redundancy that would be necessary to retain data after it's overwritten.

More scientific explanations:
[http://www.nber.org/sys-admin/overwritten-data-guttman.html](http://www.nber.org/sys-admin/overwritten-data-guttman.html)
[http://computer-forensics.sans.org/blog/2009/01/15/overwriting-hard-drive-data/](http://computer-forensics.sans.org/blog/2009/01/15/overwriting-hard-drive-data/)

TL;DR: Overwriting with random data, several passes, is a huge waste of time; physically destroying media that is in perfect working order, is a waste of resources. In some cases you may be legally obligated to do so, but if you're not, save yourself the trouble and just overwrite it with zeroes once. No one can recover any data from that.

---

### Post by zaikreign on 2010-12-31
Shred is far easy enough. You can erase a content of a certain partition or even an entire drive. You don't have to worry if you mess up the whole drive and never recover anything, you can create partitions again and start anew. I suggest you read the manual first for you to know what you'll be doing..

I already have tried this, "sudo shred -zvn 3 /dev/sdb", and used a certain recovery software. Deep scan did show nothing..

---

### Post by Joshun on 2010-12-31
Using a program like 'gparted' to erase the flash drives partition should ensure that it is fully erased. You can then create a new partition and should find that there isn't a single trace of data left behind.

---

### Post by zaikreign on 2010-12-31
Gparted only erases volume information, not the data itself. When we do delete a file from a device, only the reference to the data is altered. Same goes in deleting a partition or even formatting the drive. It isn't still safe to say that the data can no longer be recovered unless the data portion in the media has been overwritten..

---

### Post by Digital_Resistance on 2011-06-05
> **JKyleOKC said:**
>  Actually a flash drive might not retain any traces of older data;[...]

Actually...

[Flash drives dangerously hard to purge of sensitive data]("http://www.theregister.co.uk/2011/02/21/flash_drive_erasing_peril/")

> When secure wiping isn't
 
In research that has important findings for banks, businesses and security buffs everywhere, scientists have found that computer files stored on solid state drives are sometimes impossible to delete using traditional disk-erasure techniques.[...]> **Prince Valiant said:**
> [...]like I read elswhere ([http://ask-leo.com/comments_003670.php?page=2](http://ask-leo.com/comments_003670.php?page=2)), would an absolutely secure deletion be nothing more than overwriting the entire drive?[...]

The most recent comment posted to the "Ask Leo" piece linked above contains a link to what appears to be a similar article to the Register one I linked on the problems of securely deleting data from flash media. 

Leo really should update his answer.

---

### Post by 3602 on 2011-06-05
Do you have access to a Windows machine? I believe that C.O.M.O.D.O. has a software that completely destroys and fills the data (you can choose zero-fill, random-fill and NSA-fill, I believe) and make it fill repeatedly for 16 times. When I left a company this is what I did to my post.

---

### Post by Digital_Resistance on 2011-06-11
> **3602 said:**
>  [...]I believe that C.O.M.O.D.O. has a software that completely destroys and fills the data [...]

Please see my previous post. The problem is that such overwriting utilities* may not be effective for **flash** media the way they are for traditional mechanical hard disks.
 
(*Of which there are quite a few available. **DBAN** for wiping *entire disks* and **Eraser** for overwriting *individual files* (in MS Windows) may be the most popular and are both free and open source. )

---

### Post by Paqman on 2011-06-12
> **s3a said:**
> You can use shred with lots of iterations (Do man shred in terminal).

A single pass with shred is all you need. A USB flash drive is a pretty dumb device, there's no wear levelling logic involved that would get in the way of writing to the actual blocks the data is on, and there's no need to do a second pass. Actually there's no need to do a  second pass on magnetic storage either, the ability to recover data after a single pass on magnetic storage has been highly overstated. It can't be done using software tools, and nobody is going to put your drive in a scanning electron microscope.

If you want to securely wipe an SSD (which is what that article seemed to be on about) then you have to fill the drive up, for which you can use sfill. It's part of the same package as shred.

---

### Post by Digital_Resistance on 2011-06-13
> **Paqman said:**
> A USB flash drive is a pretty dumb device, there's no wear levelling logic involved that would get in the way of writing to the actual blocks the data is on, 

From the [article]("http://www.theregister.co.uk/2011/02/21/flash_drive_erasing_peril/"):

(All emphasis mine- DR)

> The difficulty of reliably wiping SSDs stems from their radically different internal design. Traditional ATA and SCSI hard drives employ magnetizing materials to write contents to a physical location that's known as the LBA, or logical block address. **SSDs, *by contrast***, use computer chips to store data digitally and employ an FTL, or flash translation layer, to manage the contents. When data is modified, the FTL frequently writes new files to a different location and updates its map to reflect the change.

In the process **left-over data** from the old file, which the authors refer to as digital remnants, **remain**.> and there's no need to do a second pass.Not the issue here; even after *multiple-pass* methods were used on the media, the researchers were able to recover data.

> **Paqman said:**
> If you want to securely wipe an SSD (which is what that article seemed to be on about) then you have to fill the drive up, for which you can use sfill.

1.) Again, to quote just a brief excerpt from the article:

> [...]Whole-disk wiping techniques faired only slightly better with SSD media.[...]Much more in the article- linked above. 

And here's a link to a PDF of the [actual paper the article is based-on]("http://www.usenix.org/events/fast11/tech/full_papers/Wei.pdf") 

2.) Peter Gutmann, who himself uses only *one pass* for overwriting *magnetic* media, nonetheless writes the following regarding **solid state** or **flash** media:

> To erase **SSD**s.... well, you're on your own there.

(emphasis mine. Source: [http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html#recommendations](http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html#recommendations) )

---

### Post by Digital_Resistance on 2011-06-15
Further to my previous posts, I came across this:

[http://www.schneier.com/blog/archives/2011/03/erasing_data_fr.html](http://www.schneier.com/blog/archives/2011/03/erasing_data_fr.html)

Pages of comments containing much substantive, informative content. 

An excerpt from just one of the many fascinating comments posted:

[quote=Clive Robinson]For most of us just wrapping a faulty thumb drive up in a used babies nappy and chucking it in the trash is the most security precaution we need.

However for some who's activites may be less socialy acceptable for whatever reason you might want to consider the following,

Using a hammer to open and remove any metal screening etc from the PCB and knocking off the bigger protection component would make a good first step.

Chucking the PCB into the microwave for a minute (remember the half glass of water to protect the microwave) would make a good second step.

Then carefully grinding down the chip packages so as not to tear them out of the mountings before you grind down the silicon would make a good third stage.

Finally toss the remains in a used nappy etc.
Even *physical destruction* of solid state media appears much less simple than one would have thought. Even fire does not always destroy the chips sufficiently to prevent recovery of the data that was on them.[/quote]
..........................................

Putting aside the specific question of SSD/flash media for a moment and moving to the question of the various overwriting utilities and commands available in GNU/Linux *in general*, such as **dd**, **shred**, **sfill**, etc.:  

Perhaps someone could post a link to something that explains (in a manner suitable for "absolute beginners") the differences between each option and gives some guidelines for choosing which to use for a given task (especially for wiping an entire drive or partition)

Such a reference should include an explanation and comparison of the options **urandom**, **random** and **zero**,  and offer some guidelines for choosing between them.

I would also like to see discussion on using **hdparm** commands to activate **ATA Secure Erase** (built into most hard drives manufactured since 2001)

---

### Post by Prince Valiant on 2011-06-16
Digital Resistance,

You've compiled some really interesting information there.  Thanks!  It's exactly the kind of information I was looking for.

I agree- an understandable overview of methods for securely erasing magnetic drives and flash drives would be useful.  

-Val

---

### Post by Prince Valiant on 2011-06-16
Oh- and though more comments would be welcome, I'll go ahead and mark the thread as solved.  Thanks everyone! :-D

-Val

---

### Post by crispy_420 on 2011-06-18
I have a flash drive that I used through four years of school. Between classes I would remove my data, erase and then fully format. When I did a class on forensics I was able to image the drive a recover documents from my first year. I couldn't recover everything I had ever done but I did get a decent amount documents that were readable.

---

### Post by eliasrio on 2011-07-24
hi I came across this :
[http://www.jonathanmoeller.com/screed/?p=2450](http://www.jonathanmoeller.com/screed/?p=2450)
where we find the **srm **command
[B]sudo apt-get install secure-delete
[/B][B]srm FILENAME
[/B]The **srm **command  (for secure-remove) overwrites files 38 times while deleting them.

---

### Post by eliasrio on 2011-07-24
[COLOR=Black]Adding a secure deletion option to nautilus file manager in ubuntu:
[http://techthrob.com/2010/07/07/adding-a-secure-delete-option-to-nautilus-file-manager-in-linux/](http://techthrob.com/2010/07/07/adding-a-secure-delete-option-to-nautilus-file-manager-in-linux/)

[/COLOR]

---

### Post by Rytron on 2012-09-24
Hello all.

If I was to shred a pen drive - Would I select **sdf1** or just **sdf**? Both show up in the terminal.

e.g.
```
sudo shred /dev/**sdf** -f -v -z --iterations=6
```
or
```
sudo shred /dev/**sdf1** -f -v -z --iterations=6
```

---

