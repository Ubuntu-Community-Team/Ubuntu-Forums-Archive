---
title: "Using Terminal To move files"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by brian242r on 2010-07-29
Hey Guys... Well I was sorta an idiot and installed some programs that clashed with others, so i removed them. Bad Idea... I deleted something that was very important and now my Ubuntu 10.04 runs in low graphics mode -.- Its basically a huge terminal now....

Any way... After trying a lot of different methods that just didn't work through a live CD I have decided to try and move my ENTIRE home folder onto an external hard drive...

User name: "brian"
Hard drive name: "Storage"
Is this possible?
If so can i please get a step by step list of commands to use... other lists just are confusing :( 
Do I have to mount "Storage?"

Thanks Brian

---

### Post by jesseafrantz on 2010-07-29
> **brian242r said:**
> Hey Guys... Well I was sorta an idiot and installed some programs that clashed with others, so i removed them. Bad Idea... I deleted something that was very important and now my Ubuntu 10.04 runs in low graphics mode -.- Its basically a huge terminal now....

Any way... After trying a lot of different methods that just didn't work through a live CD I have decided to try and move my ENTIRE home folder onto an external hard drive...

User name: "brian"
Hard drive name: "Storage"
Is this possible?
If so can i please get a step by step list of commands to use... other lists just are confusing :( 
Do I have to mount "Storage?"

Thanks Brian
Curious, can you give us specifics to what the program was? you may be able to reverse it. As for it being a giant terminal, it's what's there when GDM/X-server isn't engaged.

---

### Post by slooksterpsv on 2010-07-29
I'll advise caution with the terminal, but I assume you're going to reformat correct? And depending on if you've booted from the Live CD or from the HDD itself, you'd do the following:

If booted off hard drive:
```

ls /media

```

Make sure the external is mounted there, it should show /media/Storage:

Type in the following next: (I'm using cp cause you're probably going to wipe the drive, also so you can verify all your data came over)
```

mkdir /media/Storage/brian
cp -R /home/brian/ /media/Storage/brian

```

Now if you're booting off the live cd, it depends on if the home directory was its own partition, on the root / partition or what not, in which you will need to mount the drive first before we can move any data.

If your drive is /dev/sda1 we need to create a directory and mount it in media:
```

sudo mkdir /media/HDD1
sudo mount /dev/sda1 /media/HDD1

```

Then make sure it's the right drive:
```

ls /media/HDD1

```

Then make sure the other drive is mounted:
```

ls /media/

```

If it's not we'll need to figure out what drive it is set to and mount it like we did above with mount /dev/sda1... which it could be sdb1 etc.
Now once we have all that taken care of do the following:
```

sudo mv /media/HDD1/home/brian /media/Storage

```

I did sudo in case it reads permissions from it in which case your regular ubuntu user may not be able to copy/move the data.

---

### Post by brian242r on 2010-07-30
> **jesseafrantz said:**
> Curious, can you give us specifics to what the program was? you may be able to reverse it. As for it being a giant terminal, it's what's there when GDM/X-server isn't engaged.
 
Yea It was a different login thingy..... I have tried to reinstallxserver with no avail... if u have any programs I should try and reinstall to fix it that would be greatly apriceated... I will be able to give you the exact program when i get home.... 
 
Also I am booting from the hdd as my home folder is encrypted and 10.04 is being a pain because Iforgotmy pass phrase.... Again if you know anything that would be really nice.

---

### Post by brian242r on 2010-07-30
> **slooksterpsv said:**
> I'll advise caution with the terminal, but I assume you're going to reformat correct? And depending on if you've booted from the Live CD or from the HDD itself, you'd do the following:

If booted off hard drive:
```

ls /media

```Make sure the external is mounted there, it should show /media/Storage:


[/code]I did sudo in case it reads permissions from it in which case your regular ubuntu user may not be able to copy/move the data.

Yea.... I got up to here and no list came back.... Tried on live cd and results popped up :(

I dont think its mounting properly..... any ideas? 

When I plug my hard drive in some numbers and writing comes up like:

[000.000.000] sdf...... (Number example not actual) <- Whats going on... please really new to ubuntu....

Also.... If i try from the live cd.... that will keep the encryption im trying to work around because descriptors arnt working for me 0_o

---

### Post by jesseafrantz on 2010-07-30
> **brian242r said:**
> Yea It was a different login thingy..... I have tried to reinstallxserver with no avail... if u have any programs I should try and reinstall to fix it that would be greatly apriceated... I will be able to give you the exact program when i get home.... 
 
Also I am booting from the hdd as my home folder is encrypted and 10.04 is being a pain because Iforgotmy pass phrase.... Again if you know anything that would be really nice.
If it's broken, have you tried going into recovery mode and try repairing the package?

---

### Post by Miyavix3 on 2010-07-30
Does your external drive mount automatically?

If not, type:
```
sudo fdisk -l
```

It should tell you what's what.

/dev/sda1 (or something similar)

Then just look under 'blocks' and compare that size to your hard drive size. (if your hard drive is 120GB, then it will be like 116499223, basically listing it in bytes, instead of gigabytes)

Whichever blocks matches your external, that's the /dev/insertyourhddhere is.

Just be careful with fdisk though. Only use the -l option here.

Then you should know which one to mount.

---

### Post by brian242r on 2010-07-30
> **jesseafrantz said:**
> If it's broken, have you tried going into recovery mode and try repairing the package?

No I havnt Tried that because I dont know what im doing and are just trying to make things as simple as possible so i can get my data back and reformat

If your able to tell me what commands I can use I'll give it a shot

---

### Post by jtarin on 2010-07-30
> **brian242r said:**
> No I havnt Tried that because I dont know what im doing and are just trying to make things as simple as possible so i can get my data back and reformat

If your able to tell me what commands I can use I'll give it a shotWhen your Grub boot prompt appears choose (recovery mode)

---

### Post by brian242r on 2010-07-30
> **jtarin said:**
> When your Grub boot prompt appears choose (recovery mode)

Okay, will try in a minute but how do i get to grub mode? I have no boot promp it just show the splash screen and off it goes....

also i think im copying the files atm but i typed in the comand and thn its looks something like this

$brian$brian$: cp -R /home/brian/ /media/hardrive/brian

-

^ and it keeps flasshing that... it sounds as if the computer is doing work... is it?

---

### Post by jtarin on 2010-07-30
You have to have a Grub Boot screen....it is the DOS-like screen you first see upon boot.

---

### Post by jtarin on 2010-07-30
> **brian242r said:**
> Okay, will try in a minute but how do i get to grub mode? I have no boot promp it just show the splash screen and off it goes....

also i think im copying the files atm but i typed in the comand and thn its looks something like this

$brian$brian$: cp -R /home/brian/ /media/hardrive/brian

-

^ and it keeps flasshing that... it sounds as if the computer is doing work... is it?You have issued the command to copy files from one location to another, its a safe assumption that it is following your instructions.Depndent on the number of files you have and the speed of your hardware it could take some time. Always try to do a test file before you issue commands that could affect files irretrievably.

---

### Post by brian242r on 2010-07-31
Thanks Guys.... Just finished copying all my stuff... ended up having to mount it to a different name for   some reason 0_o just reformatted an know have to change everything back :( 

Definitely not encrypting the home folder this time... that was a pain...

---

### Post by brian242r on 2010-07-31
> **jtarin said:**
> You have issued the command to copy files from one location to another, its a safe assumption that it is following your instructions.Depndent on the number of files you have and the speed of your hardware it could take some time. Always try to do a test file before you issue commands that could affect files irretrievably.


Thanks will keep that in mind for next time... it was copying after all

---

