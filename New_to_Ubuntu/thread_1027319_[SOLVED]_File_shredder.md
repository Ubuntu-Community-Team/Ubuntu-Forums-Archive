---
title: "[SOLVED] File shredder"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by hoppyandy on 2009-01-01
when i was using windows i used to use a program to "shred" sensitive files supposedly to properly delete / over write them instead of reallocating space the were using.
Do i need anything like this for Ubuntu as i cant see any program of this sort around.
If yes can you please recommend a program to delete sensitive files properly.

Thanks

---

### Post by andrew.46 on 2009-01-01
Hi hoppyandy,

There is such a program called 'shred' believe it or not. It is a command line program which:

> NAME
       shred - overwrite a file to hide its contents, and optionally delete it

SYNOPSIS
       shred [OPTIONS] FILE [...]

DESCRIPTION
       Overwrite the specified FILE(s) repeatedly, in order to make it  harder
       for even very expensive hardware probing to recover the data.


This is a quote from the man pages for shred which of course can be accessed as follows:

```
man shred
```

Hope this is what you are looking for?

  Andrew

---

### Post by Sprut1 on 2009-01-01
What are you hiding? :P

One question - when you delete something by del button, do you just "reallocating space"? I know you can access things you have deleted until the HD is completely overwritten like 10 times (excuse my knowledge). Wouldn't that mean that they are actually still using space? :)

---

### Post by hoppyandy on 2009-01-01
> **andrew.46 said:**
> Hi hoppyandy,

There is such a program called 'shred' believe it or not. It is a command line program which:



This is a quote from the man pages for shred which of course can be accessed as follows:

```
man shred
```

Hope this is what you are looking for?

  Andrew

Many Thanks this is what i was looking for

---

### Post by Dedoimedo on 2009-01-01
You can also do this:

```

cat /dev/zero > file-you-want-to-delete

```

Or

```

cat /dev/random > file-you-want-to-delete

```

After that, delete it normally ...

Cheers,
Dedoimedo

---

### Post by hoppyandy on 2009-01-01
> **Sprut1 said:**
> What are you hiding? :P

One question - when you delete something by del button, do you just "reallocating space"? I know you can access things you have deleted until the HD is completely overwritten like 10 times (excuse my knowledge). Wouldn't that mean that they are actually still using space? :)

i think the reallocating of space just reallocates it to useable space which can be written on as needed, just like empty space.
i just got a habit of right clicking on files and using a program called tune up shredder which wrote over what you deleted, i personally like to think no one can see my "rubbish" not that i have anything to partically hide 

How do i allocate as SOLVED ? doi just edit first post ? sorry newbie

---

### Post by caro on 2009-01-01
> **hoppyandy said:**
> 

How do i allocate as SOLVED ? doi just edit first post ? sorry newbie

Use "Thread Tools" at the top of the thread.

---

### Post by Sprut1 on 2009-01-01
> **hoppyandy said:**
> i think the reallocating of space just reallocates it to useable space which can be written on as needed, just like empty space.
i just got a habit of right clicking on files and using a program called tune up shredder which wrote over what you deleted, i personally like to think no one can see my "rubbish" not that i have anything to partically hide 

How do i allocate as SOLVED ? doi just edit first post ? sorry newbie

Okay, maybe you can map del button to the shred command then :)

---

### Post by Dr Small on 2009-01-01
I set an alias for shred, which does this:
```
alias shred="shred -uvz"
```

It works quite nice :)

---

### Post by Ashin Sopaka on 2009-01-29
> **Sprut1 said:**
> Okay, maybe you can map del button to the shred command then :)

Now that sounds like a great idea! Did some searching around but couldn't find anything (probably using the wrong terminology!), but this would be a fantastic option to typing the shred command everytime.

Thanks in advance!

---

### Post by hyper_ch on 2009-01-29
I don't think shredding a file in a journaled filesystem is as simple as you think. I tend to think there will still be left-overs.

---

### Post by -kg- on 2009-01-29
> **hyper_ch said:**
> I don't think shredding a file in a journaled filesystem is as simple as you think. I tend to think there will still be left-overs.

You know, you might be right.  [Some of what I read here]("http://en.wikipedia.org/wiki/Journaling_file_system") concerns me just a bit.

Perhaps the writer of the shredding program took that into account when writing the software and the shredding program would overwrite any sensitive information contained in the journal as well as the file itself.

Not that I have anything to hide or that I wouldn't want to be gleaned from my hard drive.  All anyone would see from me is the Community I'm a member of, a whole bunch of scientific and research (mainly Linux) sites, and this forum.  Look away!  :)

But if someone were to do online banking or something, I could understand the concern.

---

### Post by hyper_ch on 2009-01-29
well, if you're really concerned about your data you should use (full disk) encryption instead... :)

---

### Post by les2 on 2012-06-01
A good use for the shred command is for when you have used a thumb drive to transfer a sensitive file (such as a tax return) from one computer to another.

I suppose the best solution would be to just store the file encrypted on the thumb drive in the first place. But just to be sure, you might still want to delete the encrypted file from the thumb drive (someone could just beat the decryption key out of you if the file is there).

If you use encryption to transfer the file and then shred it after access, you get the best of both worlds.

My question is whether shred is secure for a thumb drive formatted with FAT32 ?

---

### Post by nothingspecial on 2012-06-01
Please do not bump old threads to the top. Start a new one :)

---

