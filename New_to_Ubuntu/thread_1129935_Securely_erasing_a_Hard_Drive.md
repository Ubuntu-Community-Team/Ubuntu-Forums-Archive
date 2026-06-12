---
title: "Securely erasing a Hard Drive"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Luke Marshall on 2009-04-19
There is a utility within Mac OSX that will erase the contents of a hard drive and allow the user to select whether or not "zeros" will be written to the disk to make the data harder to recover. It also allows you to choose how many times this will be done, the idea being that the more passes it takes burning zeros onto the drive the harder it will be for someone else to recover potentially sensitive data. 

Does Ubuntu have this facility? or maybe a 3rd party solution?

---

### Post by Peter09 on 2009-04-19
There is a utility called 'wipe' in the repositories which seems to suggest it will do something similar to your request - never used it though.

---

### Post by Luke Marshall on 2009-04-19
> **Peter09 said:**
> There is a utility called 'wipe' in the repositories which seems to suggest it will do something similar to your request - never used it though.

Thank you, I'll have a look and post back if its what I'm looking for.

---

### Post by halitech on 2009-04-19
You could get the Ultimate boot cd and use Dban

UBCD
[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

also available directly without UBCD
[http://www.dban.org/download](http://www.dban.org/download)

---

### Post by srt4play on 2009-04-19
[http://www.dban.org]("http://www.dban.org")

---

### Post by Luke Marshall on 2009-04-19
> **halitech said:**
> You could get the Ultimate boot cd and use Dban

UBCD
[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

also available directly without UBCD
[http://www.dban.org/download](http://www.dban.org/download)

Cheers mate, i think ill go down the Dban route, has anyone ever used this that knows what sort of options it gives when erasing?

---

### Post by halitech on 2009-04-19
welcome and not personally I haven't but from the awards its been given, it looks like it works good and shouldn't be too hard to use.

---

### Post by yeehi on 2009-04-19
Dban is good. It lets you try the following:

The Guttman wipe writes your disk over 30 times. It can take days to complete. 

The Dept of Defense short wipe writes 3 times, using different techniques. That is only medium secure!

What you really need is a sander to physically attack the surface of the hard disk, too. If you use a nail gun, the shards can still be read, and a huge amount of data can be held on a small piece of disk.

Also consider your memory. SDRAM holds data even when switched off, and you should think about wiping that, too.

There is a program for it in the repositories:

smem (1) - secure memory wiper (secure_deletion toolkit)
srm (1) - secure remove (secure_deletion toolkit)
sswap (1) - secure swap wiper (secure_deletion toolkit)

If you are in the business of wiping, you may need to consider getting secure, off site storage of media that you need for encryption, too. Are you encrypting your hard drives? You need the alternate install CD to set that up, in fthe first place.
And look into using TrueCrypt.

---

### Post by Luke Marshall on 2009-04-19
> **yeehi said:**
>  Are you encrypting your hard drives? You need the alternate install CD to set that up, in fthe first place.
And look into using TrueCrypt.

i haven't got them encrypted but now you mention it i most likely will, plus i see what you mean about physically damaging the HDD but most of the time i pass them on to friends etc to upgrade their machines. Oh....and i dont have a nail gun :D

---

### Post by Volt9000 on 2009-04-19
This may be a bit off-topic, but it's still somewhat related so I'll ask anyways...

I've always wondered: what's the point of writing 0s over the hard drive multiples times? Surely a single pass is enough-- after this the entire hard drive will be filled with 0s, including the partition. Is this not sufficient?

---

### Post by bmcclare on 2009-04-19
> **Volt9000 said:**
> This may be a bit off-topic, but it's still somewhat related so I'll ask anyways...

I've always wondered: what's the point of writing 0s over the hard drive multiples times? Surely a single pass is enough-- after this the entire hard drive will be filled with 0s, including the partition. Is this not sufficient?

I believe there are forensic techniques that can be used to get the value of the bits that were there before 0's were written. I don't know what kind of equipment it requires (tunneling electron microscope?). DBAN writes pseudo-random bits to prevent such techniques. 

I don't personally have data worth that kind of effort to recover, but lots of people do. DBAN is several levels more secure than I need but still convenient and easy to use.

---

### Post by Paddy Landau on 2009-04-19
> **Volt9000 said:**
> I've always wondered: what's the point of writing 0s over the hard drive multiples times? Surely a single pass is enough-- after this the entire hard drive will be filled with 0s, including the partition. Is this not sufficient?
My friend was able to go back 9 generations of data, and that was without fancy equipment.

Imagine a disk as a piece of paper, where you write on it in pencil. When you erase what's on the paper and write something new, you can still (if you look carefully) see what was written there before.

From what I remember, you need to write random data something like 23 times to be sure that no one can read the disk.

---

### Post by Luke Marshall on 2009-04-19
> **Paddy Landau said:**
> From what I remember, you need to write random data something like 23 times to be sure that no one can read the disk.

Yeah the option i used to have on my mac were a single pass, 7 passes, or 35 passes, it seemed excessive considering that 7 passes is the standard used by the Department of defence.

---

### Post by bodhi.zazen on 2009-04-19
You can probably just write 0 's to the HD with dd.

[http://16systems.com/zero.php](http://16systems.com/zero.php)

[Can Intelligence Agencies Read Overwritten Data?]("http://www.nber.org/sys-admin/overwritten-data-gutmann.html")

---

### Post by Luke Marshall on 2009-04-19
> **bodhi.zazen said:**
> You can probably just write 0 's to the HD with dd.

[http://16systems.com/zero.php](http://16systems.com/zero.php)

[Can Intelligence Agencies Read Overwritten Data?]("http://www.nber.org/sys-admin/overwritten-data-gutmann.html")

...wow... it's funny how we just take what were told to be a truth without ever questioning it, or even realise we should be questioning it. Consider me thoroughly informed :)

---

### Post by Volt9000 on 2009-04-19
> **Paddy Landau said:**
> My friend was able to go back 9 generations of data, and that was without fancy equipment.

Really? How did they accomplish this?
I'm not being sarcastic, I'd really like to know...

> Imagine a disk as a piece of paper, where you write on it in pencil. When you erase what's on the paper and write something new, you can still (if you look carefully) see what was written there before.

From what I remember, you need to write random data something like 23 times to be sure that no one can read the disk.

An interesting analogy, but I don't really understand how it applies to hard drives. AFAIK a bit is stored just with a magnetic field. If that magnetic field is replaced with a magnetic field that represents a 0, I don't see how you can "go back" and see what was written when there is no physical imprint left on the hardware.

Then again, I'm not hardware expert so I'm sure there's more at work than my basic knowledge of magnetic storage devices.

---

### Post by h4mx0r on 2009-04-19
This points me to consider why don't we have more space on our drives? Why aren't our drives more secure against data loss? Is it just people don't know how to code a proper file system? Perhaps a much larger conspiracy?

---

### Post by Paddy Landau on 2009-04-20
> **Volt9000 said:**
> [quote=Paddy Landau;7101185]My friend was able to go back 9 generations of data, and that was without fancy equipment.Really? How did they accomplish this?[/quote]
He told me that he had some fancy software that he used to use when it was part of his job. I know that he did take the drive out of the computer, so perhaps he did something with it; I didn't ask.

---

### Post by Paddy Landau on 2009-04-20
> **h4mx0r said:**
> This points me to consider why don't we have more space on our drives? Why aren't our drives more secure against data loss? Is it just people don't know how to code a proper file system? Perhaps a much larger conspiracy?
No conspiracy! The drives aren't designed with military security in mind. They're designed with price and efficiency in mind. That's all.

---

### Post by Paqman on 2009-04-20
> **yeehi said:**
> Dban is good. It lets you try the following:

The Guttman wipe writes your disk over 30 times. It can take days to complete. 

The Dept of Defense short wipe writes 3 times, using different techniques. That is only medium secure!


For all practical purposes, three writes is more than sufficient to prevent any software tool from recovering data. 

The so-called Gutman method of 35 wipes is massive overkill, and a complete waste of time and disk wear. In fact Gutman himself said:

> In the time since this paper was published, some people have treated the 35-pass overwrite technique described in it more as a kind of voodoo incantation to banish evil spirits than the result of a technical analysis of drive encoding techniques. As a result, they advocate applying the voodoo to PRML and EPRML drives even though it will have no more effect than a simple scrubbing with random data. **In fact performing the full 35-pass overwrite is pointless** for any drive since it targets a blend of scenarios involving all types of (normally-used) encoding technology, which covers everything back to 30+-year-old MFM methods (if you don't understand that statement, re-read the paper). If you're using a drive which uses encoding technology X, you only need to perform the passes specific to X, and **you never need to perform all 35 passes. For any modern PRML/EPRML drive, a few passes of random scrubbing is the best you can do**. As the paper says, "A good scrubbing with random data will do about as well as can be expected". This was true in 1996, and is still true now.

The technique he was describing was intended to counter the theoretical use of electron microscopy in data recovery. Even computer forensics labs only use software tools, and there's no reason even the most paranoid user should expect their disks to come under that kind of scrutiny. Unless you're expecting to get arrested, that is.

I just wiped a drive over the weekend for resale. What I did:

[list]
[*]Disconnect your normal drives to prevent horrible accidents
[*]Connect your drive to be wiped
[*]Boot into a LiveCD or LiveUSB
[*]Mount the drive and delete any partitions
[*]Install secure-delete
[*]sudo sfill -l -v /drive/name
[/list]

Even with only two passes, it takes a long time to write several hundred GB. I'd hate to think how long it would take if you were doing 35.

---

### Post by theozzlives on 2009-04-20
Big companies actually destroy their used HDs

---

### Post by Paqman on 2009-04-20
> **theozzlives said:**
> Big companies actually destroy their used HDs

Makes sense. It's probably cheaper than wiping them, and guaranteed 100% secure.

FWIW, number of overwrites will cease to be an issue in a few years. There aren't really any tools for recovering data from SSDs yet, and there's no reason to think that there will be any capable of recovering data after even one write.

---

### Post by Luke Marshall on 2009-04-20
> **h4mx0r said:**
> This points me to consider why don't we have more space on our drives? Why aren't our drives more secure against data loss? Is it just people don't know how to code a proper file system? Perhaps a much larger conspiracy?

A theory i was told, which im inclined not to believe, is that by slowly introducing slightly better HDD's in gradual improved states would mean the people selling could make more money by drip feeding the technology onto the market rather than giving you a massively improved product that could last a lifetime all in one go, it makes sense from a business point of view but it just seems a little paranoid to think its actually the case....or maybe thats what *they* want us to think :)

---

### Post by theozzlives on 2009-04-20
> **Luke Marshall said:**
> A theory i was told, which im inclined not to believe, is that by slowly introducing slightly better HDD's in gradual improved states would mean the people selling could make more money by drip feeding the technology onto the market rather than giving you a massively improved product that could last a lifetime all in one go, it makes sense from a business point of view but it just seems a little paranoid to think its actually the case....or maybe thats what *they* want us to think :)

The military has solid state HDs with no moving parts.

---

### Post by Luke Marshall on 2009-04-20
> **theozzlives said:**
> The military has solid state HDs with no moving parts.

I know, what i was getting at was the possibility that they may have had this knowledge for longer than we are aware but chose to make gradual improvements to existing tech before releasing the solid state drive, its not a theory limited to hard drives either, id like to point out though, that i don't think this is the case, i trust the man. :rolleyes:

---

### Post by whoop on 2009-04-20
Has anybody got some accurate information about microwaving your hd (for a short period)?
I've heard the following stories:
* It destroys your hd
* It erases all data
* It destroys your hd and erases all data
* It does nothing

---

### Post by Luke Marshall on 2009-04-20
> **whoop said:**
> Has anybody got some accurate information about microwaving your hd (for a short period)?
I've heard the following stories:
* It destroys your hd
* It erases all data
* It destroys your hd and erases all data
* It does nothing

From what i've seen on google search results the general idea is that microwaves just physically damage the HDD making it useless to use but don't actually erase the data at all, I'm not 100% sure but i don't think microwaves effect magnetic fields. So other than melting components in the drive, and probably setting fire to the microwave, it wont really accomplish much.

---

