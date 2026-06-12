---
title: "usb memory stick read only, files needed"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by mo-mentum on 2010-01-11
Please can anyone help. I have a 1gb usb memory stick which appears to be read only, and i cannot see the data on it. I'm not IT literate so please be gentle with me!
 
when i look at the stick properties I can see that I have used 908 MB and have some 7% free.
 
The only way i know it is read only is when i try to defragment it i get a warning saying cannot defrag a read only file.
 
The stick does not have anything physical on it to switch it to read only, and even if it did it makes no difference as i cannot see the files on it.
 
I've used 3 different computers and still have the same problem. all i want are my excel files back, so formating the stick will loose my valuable data.
 
Please help and don't worry about going right back to basics - i need it that way!

---

### Post by gabo.cr on 2010-01-11
You will have to use terminal.
Go to the address of the USB:

```
cd /media/USB
```

USB is the name of your USB device.
Once you are there, type this:

```
ls -l
```

Then post the results:

Edit: If you need more information on how to do this, let us know.

---

### Post by mgmiller on 2010-01-11
> The only way i know it is read only is when i try to defragment it i get a warning saying cannot defrag a read only file.

I know this does not really answer your original question, but it's important to note that you should never defragment a thumb drive.  This type of non volatile memory is capable of almost limitless reads, but can only handle a limited number of writes without degrading.  Defragging, causes a lot of write activity and will "use up" the thumb drive prematurely.   Since there are no moving parts to wait to get aligned, there is no performance improvement from "correcting" even a heavily fragmented thumb drive.

Your drive sounds like it's filled to capacity.  I suspect it may have a full trash bin that is preventing it from being read.  If you could post the output of the ls command from the previous post it would help.

---

### Post by mgmiller on 2010-01-11
You could also try installing testdisk from synaptic or with the command:
```
sudo apt-get install testdisk
```

It can recover files from corrupted partitions.

---

### Post by gabo.cr on 2010-01-11
> sudo apt-get install testdisk

That's interesting !

---

### Post by mo-mentum on 2010-01-17
Thanks for the speedy response guys!  I guess I didn't emphasize enough how basic my undersatnding of computers is!
 
When you say go to the address of the USB, I try to do this using Windows Explorer and cannot see it as you describe.  What application/program do i use to type in the code.

---

### Post by mo-mentum on 2010-01-17
> **mgmiller said:**
> You could also try installing testdisk from synaptic or with the command:
```
sudo apt-get install testdisk
```
 
It can recover files from corrupted partitions.
 
I ran testdisk and got the following results:
*current partition structure:*
*check_FAT: Unusual number of reserved sectors 4 <FAT>, should be 1.*
*Warning: incorrect number of heads/cylinder 16 <FAT>!=255<HD>*
*Warning: incorrect number of sectors per track 32 <FAT>!=63 <HD>*
*1*FAT16 LBA 0   0  33     125  15 18 2009056 [UDISK 2.0]*
 
*Warning: bad ending cyclinder <CHS and LBA don't match>*
 
I then did the quick search and got the following message:
*The following partition can't be recovered:*
*FAT16 >32M       START 0   0  33  END 125 15 18 SIZE IN SECTORS 2009056 [UDISK 2.0]*
 
Does that mean I'm stuffed?  Any advice on what i need to do next would be greatly appreciated.
 
Thanks for your advice so far.

---

