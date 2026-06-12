---
title: "Referencing a Windows directory from Ubuntu"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by necronom on 2010-09-24
I'm sharing some of my Opera browser directories (the email ones) between Ubuntu and XP, but the New Mail sound isn't playing as it's set to "E:\Apps\Opera\profile\WeGotSomethingHere.wav".  Is there a way in Linux to assign a file path to somewhere else?

I'm thinking of the way I could do this on my Amiga.  I could "Assign" a floppy disk to a directory on my Hard Drive, so if I could do the same thing with Linux I could point "E:\Apps\Opera\profile\WeGotSomethingHere.wav" to "\media\Software\Apps\Opera\profile\WeGotSomethingHere.wav" by assigning "E:\" to "\media\Software\"

The problem is that the file that holds this file reference is part of the mail settings on my NTFS XP partition, unlike the main Opera settings, which can be set differently in Linux, so I can't have a different one for each OS.

---

### Post by Land Rover Series 3 on 2010-09-24
> **necronom said:**
> I'm sharing some of my Opera browser directories (the email ones) between Ubuntu and XP, but the New Mail sound isn't playing as it's set to "E:\Apps\Opera\profile\WeGotSomethingHere.wav".  Is there a way in Linux to assign a file path to somewhere else?

I'm thinking of the way I could do this on my Amiga.  I could "Assign" a floppy disk to a directory on my Hard Drive, so if I could do the same thing with Linux I could point "E:\Apps\Opera\profile\WeGotSomethingHere.wav" to "\media\Software\Apps\Opera\profile\WeGotSomethingHere.wav" by assigning "E:\" to "\media\Software\"

The problem is that the file that holds this file reference is part of the mail settings on my NTFS XP partition, unlike the main Opera settings, which can be set differently in Linux, so I can't have a different one for each OS.


I would have thought that the simplest solution would be to just copy the .wav sound file across?

---

### Post by ddnev45 on 2010-09-24
I think you should be able to do it with a symbolic link.

[Create symbolic link]("http://www.techiecorner.com/105/how-to-create-symbolic-link-in-unix/")

In a terminal:

```
man ln
```

for all the link options.

---

### Post by bprins on 2010-09-24
Why don't you just mount your windows partition from ubuntu? then you can don't have to hassle with symlinks but just reference the same .wav from linux to your win partition.

If this doesn't make any sense, then I probably don't fully understand your problem ;)

---

### Post by marshmallow1304 on 2010-09-24
Like ddnev45 said, create a symbolic link.  I'm not sure what Opera considers to be its base directory, so you might try your home directory or the directory in which the Opera binary resides (hint: 'which opera').

This is just an example, but it would look something like this:

```

ln -s /media/Software/Apps/Opera/profile/WeGotSomethingHere.wav "E:\Apps\Opera\profile\WeGotSomethingHere.wav"
```
or
```
cd /path/to/opera/executable/
sudo ln -s /media/Software/Apps/Opera/profile/WeGotSomethingHere.wav "E:\Apps\Opera\profile\WeGotSomethingHere.wav"
```

---

### Post by necronom on 2010-09-25
> **marshmallow1304 said:**
> Like ddnev45 said, create a symbolic link.  I'm not sure what Opera considers to be its base directory, so you might try your home directory or the directory in which the Opera binary resides (hint: 'which opera').

This is just an example, but it would look something like this:

```

ln -s /media/Software/Apps/Opera/profile/WeGotSomethingHere.wav "E:\Apps\Opera\profile\WeGotSomethingHere.wav"
```


That worked!  Thanks.

I had already set up a link for some other Opera directories, but I didn't think I would be able to create a link for a Windows path in that way.  I guess Linux isn't looking at it as a path, but as a filename, so when I go to E:\Apps\Opera\profile\WeGotSomethingHere.wav, it's not trying to find an E drive, it's just looking at a string of characters that have a link to somewhere else.

I just put it in my home dir, and it worked first time.

Thanks everyone for the help.

---

