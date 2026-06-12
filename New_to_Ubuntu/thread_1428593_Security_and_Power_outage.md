---
title: "Security and Power outage"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by mvalviar on 2010-03-13
What's the point of having all these security stuff when linux presents a root shell then the power was cut of abruptly on a power outage or when someone pulls the plug or when someone turned off the unit improperly?

If someone wants to do an rm -rf / on my machine all they need to do is turn the unit on, pull the plug, plug it back in, boot it up, wait for the shell and type it in.

Something's terribly wrong with this picture.

---

### Post by asmoore82 on 2010-03-13
This is a simple law of existence.

There is no protection against anyone who has physical access to your computer.
For Ubuntu, you can pick a recovery boot option.
For Linux, you can pass init=/bin/bash to the kernel at boot.
For Mac, you can hold Apple+S at boot to get a root prompt. ("S" is for "Single User Mode")
For Windows XP, you can boot a Win2000Pro Disc and pick "Recovery Console"

For Windows, Mac and/or Linux, you can just boot any Linux Live CD :razz:.

Encryption schemes only defend against the clueless or unmotivated ~ a waste of time IMO.
All encryption can be broken in just a matter of time. If anyone had unsupervised,
physical access to your computer, they could just make a bit for bit copy of your whole
drive, encrypted or not, and take it with them. You would have no way to know they got it
and they would have 24/7 access to your data forevermore, for review and
analysis and cracking if necessary.

Did you drink the bitlocker kool-aid?? Don't:
[quote="Wikipedia"]In cryptography, a cold boot attack (or to a lesser extent, a platform reset attack)
is a type of side channel attack in which **[COLOR="Red"]an attacker with physical access to a computer[/COLOR]**
is able to retrieve encryption keys from a running operating system after using a cold
reboot to restart the machine from a completely "off" state[emphasis added].[/quote]
[http://en.wikipedia.org/wiki/Cold_boot_attack](http://en.wikipedia.org/wiki/Cold_boot_attack)

Any motivated individual, with physical access to your computer,
can just steal the whole thing, or burn your house down, etc.

---

### Post by marshmallow1304 on 2010-03-13
What he said ^.


Think of it this way.  If I'm a malicious stranger inside your house, the least of your worries is that I'm going to wipe your hard drive (while cackling maniacally, of course).

---

### Post by ankspo71 on 2010-03-13
I asked a similar question about the potential risks of leaving live cds laying around. The best advice given to me was to change the boot order in the bios (so the cd doesn't boot first) then set a password in the bios. This way a password would have to be entered before anything could happen. This is not guaranteed security, but it could help.

---

### Post by Paddy Landau on 2010-03-13
> **asmoore82 said:**
> Encryption schemes only defend against the clueless or unmotivated ~ a waste of time IMO.
Modern encryption systems with a "strong" key are impervious to attack with today's technology. If you have a strong passphrase and you use the new encryption in Ubuntu, or perhaps use something like [TrueCrypt]("http://www.truecrypt.org/"), then your data will be safe from prying eyes.

The TrueCrypt manual explains it in layman's language.

It does mean, of course, that you must tell no one your passphrase, and not write it down anywhere, and of course all your backups must be encrypted, too. You must lock your computer screen while you are away from it. People will only get your passphrase through force (e.g. torture, blackmail or threat) or [social engineering]("http://en.wikipedia.org/wiki/Social_engineering_%28security%29").

But to protect against data loss, you need proper off-site backups.

---

### Post by 3rdalbum on 2010-03-13
> **mvalviar said:**
> What's the point of having all these security stuff when linux presents a root shell then the power was cut of abruptly on a power outage or when someone pulls the plug or when someone turned off the unit improperly?

Er... it doesn't, unless there's **bad** filesystem damage.

---

### Post by mvalviar on 2010-03-13
> **3rdalbum said:**
> Er... it doesn't, unless there's **bad** filesystem damage.

Thanks for the insight from all the above post. How do fix the filesystem damage.

---

### Post by Paddy Landau on 2010-03-13
> **mvalviar said:**
> How do fix the filesystem damage.
What version of Ubuntu?

Do you have ext2, ext3, ext4 or some other type of file system? If you're not sure, post the results of this command:
```
sudo parted /dev/sda print
```

---

### Post by mvalviar on 2010-03-13
> **Paddy Landau said:**
> What version of Ubuntu?

Do you have ext2, ext3, ext4 or some other type of file system? If you're not sure, post the results of this command:
```
sudo parted /dev/sda print
```

the '/' partition is ext4 my /home partition is ext3. I couldn't reformat the home partion size I don't have any other drive big enough to fit the contents.```
Model: ATA ST3160215A (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      32.3kB  21.5GB  21.5GB  primary  ntfs            boot
 2      21.5GB  148GB   127GB   primary  ext3
 3      148GB   159GB   10.7GB  primary  ext4
 4      159GB   160GB   1124MB  primary  linux-swap(v1)

```

---

### Post by mcduck on 2010-03-13
> **mvalviar said:**
> What's the point of having all these security stuff when linux presents a root shell then the power was cut of abruptly on a power outage or when someone pulls the plug or when someone turned off the unit improperly?

If someone wants to do an rm -rf / on my machine all they need to do is turn the unit on, pull the plug, plug it back in, boot it up, wait for the shell and type it in.

Something's terribly wrong with this picture.

The security stuff assumes that you handle the most important part of security, restricting physical access to your machine, yourself. Because no software can do that for you. Regardless of what operating system you are running.

Alternatively you can encrypt your hard drive, which is pretty much the only way to protect files on a computer if somebody gets unrestricted physical access to it.

Recovery mode is not sen as a security problem because if it wasn't there anybody could still edit the grub boot options, boot a live system form CD or thumb drive, or simply open your computer, take your hard drive and access all your stuff on another computer. (BIOS passwords are pretty much pointless, they can be reset in about ten seconds on a desktop machine and even quicker on most laptops). Considering all this it makes no difference if there's an option to boot into recovery mode or not, while having the option makes recovering from many problem situations a lot easier.

(Besides, if somebody just wanted to destroy with your files a hammer would do the trick even easier and wouldn't even require booting the machine... ;))

Anyway, there are two basic rules considering computer security (on local level, not through networks):

1. Restrict access to the machine itself.
2. If that's not possible, encrypt your data.

Every other security measure that exists is geared towards network security and security between different users on the same system.

---

### Post by Paddy Landau on 2010-03-13
If you boot off a Live CD, you can use the following commands (in any order). They can take a while to run.
```
sudo fsck -CMf /dev/sda1
sudo fsck -CMf /dev/sda2
sudo fsck -CMf /dev/sda3
```You don't need to check the swap partition.

A word of warning: I've never used this with an NTFS partition, so I'm not entirely sure that it will work on sda1. Please make a backup first, and perhaps check on the forum for using this with NTFS. If it's Windows, then do it from Windows instead.

An alternative way is to boot off the Live CD, start GParted, right-click each partition and select "Check". Again, you don't need to check the swap partition, and I don't know whether it will work on NTFS.

The last time I had a computer giving these problems was when the hard drive had started to fail. I hope that's not the case with you!

Good luck.

---

### Post by mvalviar on 2010-03-13
ubuntu@ubuntu:~$ sudo fsck -CMf /dev/sda2
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda2: 125449/7733248 files (7.0% non-contiguous), 25327164/30932992 blocks
ubuntu@ubuntu:~$ sudo fsck -CMf /dev/sda3
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda3: 261783/655360 files (0.2% non-contiguous), 1310673/2621440 blocks

Is there anything wrong with this or is my drive failing and I need to replace it?

Regards,

Marco

---

### Post by Paddy Landau on 2010-03-13
> **mvalviar said:**
> Is there anything wrong with this or is my drive failing and I need to replace it?
Everything looks fine. What problems do you still have? Please be specific, because (obviously) we can't see your computer.

---

### Post by spectralblue on 2010-03-13
Great answers above guys.

The first thing people should note about security is that you may have the best passwords, the best encryption technologies, the best safes, security personnel. You may even have the best CIA operatives working for you, but you are still vulnerable - the human element of security is always vulnerable. 

Think about your car, you may have a club there, a state of the are security system, but people can still steal it, because they can access your car while you're not guarding it. 

Ever heard of people stealing whole ATM's? It has happened. Anyone can break through anything in time, so as long as they have access to the item itself. 

A computer is no different.

---

### Post by 3rdalbum on 2010-03-13
> **mvalviar said:**
> Thanks for the insight from all the above post. How do fix the filesystem damage.

Run fsck manually:

```
fsck /dev/sda1
```

That's why it drops to the root console, to tell you to run fsck manually.

---

### Post by asmoore82 on 2010-03-14
> **Paddy Landau said:**
> Modern encryption systems with a "strong" key are impervious to attack with today's technology.
Go ahead and drink the kool-aid...

If it would take a desktop computer, working around the clock, *worst case scenario*,
1 million years to brute force your passphrase, how long would it take a botnet army
of 10 million desktop PC's working together to do it?

Answer: approx. 36.5 days, *worst case scenario*

It's a good thing no unscrupulous individuals have been able to build a botnet that large yet, right?
Oh wait, **_they have_**: [http://www.defintel.com/mariposa.shtml](http://www.defintel.com/mariposa.shtml)

How long would it take Pixar's render farm to brute force it?

Do you believe those Treacherous Platform Module(TPM) chips can lock your data up safely... :lolflag:
> Infineon said it knew this type of attack was possible when it was
testing its chips. But the company said independent tests determined
that the hack would require such a high skill level that there was a
limited chance of it affecting many users.
[http://www.nzherald.co.nz/technology/news/article.cfm?c_id=5&objectid=10625082&pnum=0](http://www.nzherald.co.nz/technology/news/article.cfm?c_id=5&objectid=10625082&pnum=0)

---

### Post by Paddy Landau on 2010-03-14
> **asmoore82 said:**
> Go ahead and drink the kool-aid...
Thank you, those were most interesting. I guess if I stored state secrets, I should be worried. Oh wait, the state stores state secrets...

---

### Post by mvalviar on 2010-03-14
Well I just experienced another power outage (it's pretty common here since there's a power crisis, if I had Windows I'm pretty sure my files has long been fried) earlier. When the power came back and I booted up. I saw a message saying one of the partition cannot be mounted (or waiting to be mounted I'm not sure) and telling me to press Esc to enter a maintenance shell. I didn't have the chance to press it since it proceeded to boot anyway.

---

### Post by Paddy Landau on 2010-03-14
> **mvalviar said:**
> Well I just experienced another power outage...
Yeah, I lived for a couple of years in a place like that. Terribly frustrating.

Have you tried a simple reboot? What happens when you do?

Ext3 and ext4 have 'journalling', which in theory is supposed to protect against that sort of problem; in theory, you shouldn't lose more than a few minutes of work. Of course, theory is one thing and reality another...

Let us know what happens when you simply reboot.

---

### Post by mvalviar on 2010-03-14
On a simple reboot all is fine it boots normally. If I boot the computer after it was turned off due to the power being cut off I get the message in the splash screen saying something failed to me mounted and that I need to press escape to enter a recovery shell. 

I'll give you the exact message when it happens. It should happen soon enough.

---

### Post by Paddy Landau on 2010-03-14
> **mvalviar said:**
> I'll give you the exact message when it happens. It should happen soon enough.
The exact quote is not necessary. The computer recognises that it suffered a catastrophic failure. The reboot succeeds, so all is fine.

As long as you have power failures, you will have to put up with this.

If it's within your budget, I would suggest a UPS (Uninterruptible Power Supply), at least a cheap one to give you a few minutes to shut down normally.

---

