---
title: "How to Convert .img to .iso"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by Linyx on 2011-02-13
I have searched for a while and i install isodump but i don't know how to use it....:confused:

here it is > [http://www.t2-project.org/]("http://www.t2-project.org/")

I want to convert .img to .iso....

---

### Post by qyot27 on 2011-02-13
Mount the .img with CDemu ([https://launchpad.net/~cdemu/+archive/ppa](https://launchpad.net/~cdemu/+archive/ppa)), and then use ddrescue (which should be in the repositories) to copy the contents of the mounted device to an .iso.  Don't know if that will preserve autoboot features, though.

---

### Post by Hippytaff on 2011-02-13
[This post]("http://ubuntuforums.org/showthread.php?p=3115582") is quite old so there might be a better way to do it now, but it's worth a look.

---

### Post by Linyx on 2011-02-13
> **Hippytaff said:**
> [This post]("http://ubuntuforums.org/showthread.php?p=3115582") is quite old so there might be a better way to do it now, but it's worth a look.

I have seen this thread but their isn't a method of how to use it....!!!

Anyway, their is also an another tool called ccd2iso,

And when i use it by the given command in the above post i-e ccd2iso img_file iso_file

its shows me an error message i-e "**ccd2iso unrecognized sector mode 0 at sector 0**"

---

### Post by Hippytaff on 2011-02-13
Whats the img file called?

it should be as simple as
```

**ccd2iso *name-of-file*.img *name-of-file*.iso**

```

edit -> make sure your in the right directory too. ie if the .img file is in downloas CD Downloads/ etc

---

### Post by Linyx on 2011-02-13
> **Hippytaff said:**
> Whats the img file called?

it should be as simple as
```

**ccd2iso *name-of-file*.img *name-of-file*.iso**
**
```**

The image file name is "bsd.img", and i have typed it as

$ ccd2iso bsd.img bsd.iso
&
Output is > Unrecognized sector mode (0) at sector 0!

Also check out the Screen-Shot...

---

### Post by Hippytaff on 2011-02-13
That's odd
maybe have a look at an [alternative]("http://www.acetoneteam.org/")

Edit -> nice desktop btw

---

### Post by linuxsyst on 2011-02-13
$ sudo aptitude install ccd2iso
$ ccd2iso $img_file $iso_file

Try this

---

### Post by Linyx on 2011-02-13
> **Hippytaff said:**
> That's odd
maybe have a look at an [alternative]("http://www.acetoneteam.org/")

Edit -> nice desktop btw

thanks, 
i have installed it and now when i want to add that .img to it, it shows me the given error message > Scree-Shot

@linuxsyst:-

I have tried that commands & I have shown the error message i get from that in my above posts...

---

### Post by Hippytaff on 2011-02-13
try uninstalling and reinstalling ccd2iso.

Also do you think the .img file could be corrupted in any way?

---

### Post by Linyx on 2011-02-13
> **Hippytaff said:**
> try uninstalling and reinstalling ccd2iso.

Also do you think the .img file could be corrupted in any way?

I don't think so because i have tested it by making bootable BSD Flash.

I have re-installed it, same error..

i think Something is missing in the command but i can't Guess....

---

### Post by Hippytaff on 2011-02-13
Just found this on the man page
> 
**[B]LIMITATIONS**[/B]

       ccd2iso  currently only copies the first session of multisession discs,
       as well as outputting a harmless warning of **Unrecognized** **sector** **mode**.


it seems this is an issue for a lot of people. Maybe look for another tool, unless your sure it's a syntax thing, but I've got a feeling it's to do with the multisession limitations

---

### Post by Linyx on 2011-02-13
Hmmmm...

Actually i have Downloaded Free-BSD OS for Practice and i have it in .img which is specially for Flash-Drives,but now i want to have it in .iso so that i can test it on Virtual-Machine....Thats why i need to convert it...

---

### Post by Hippytaff on 2011-02-13
just [download the .iso]("http://www.freebsd.org/where.html") I say, save messing around...free-bsd aye! jumping in head first.

---

### Post by Linyx on 2011-02-13
> **Hippytaff said:**
> just [download the .iso]("http://www.freebsd.org/where.html") I say, save messing around...free-bsd aye! jumping in head first.

Good Idea, i was thinking about it but it would take a time and thus i won't be able to learn how to convert .img to .iso, if i need this in future....

---

### Post by Hippytaff on 2011-02-13
For some reason I think ccd2iso thinks the image is a multi-session disc (eventhough it might not be) if future the simple command you have been using should do the job.

I was thinknig of trying open-bsd in vmbox.

---

### Post by Linyx on 2011-02-13
> **Hippytaff said:**
> For some reason I think ccd2iso thinks the image is a multi-session disc (eventhough it might not be) if future the simple command you have been using should do the job.

I was thinknig of trying open-bsd in vmbox.

BTW ,I don't know what multi-session disc Means, Sorry for my ignorance,

Open BSD..?It will be better to know why to use Open-BSD Instead of Free-BSD in VM....

I think Open-BSD is specialized for Servers stuff

---

### Post by Hippytaff on 2011-02-13
Don't know that there's much difference between [openbsd]("http://www.openbsd.org/") and freebsd. not really looked into it. I was going to use a VM just to save messing around with actually installing it

---

### Post by jimwill on 2011-02-13
Can't help with a direct conversion, but maybe you could create an iso from the flashdrive?

---

### Post by audebruin on 2011-05-14
[workaround] rename .img to .iso [/workaround]

After this vlc opened the iso file without any problems.

---

### Post by Morpholinux on 2011-12-08
> **Linyx said:**
> Hmmmm...

Actually i have Downloaded Free-BSD OS for Practice and i have it in .img which is specially for Flash-Drives,but now i want to have it in .iso so that i can test it on Virtual-Machine....Thats why i need to convert it...

I am doing almost the same ....Debian 6.0.3 instead of Free-BSD

did >
```
ccd2iso debian-live-6.0.3-i386-gnome-desktop.img debian-live-6.0.3-i386-gnome-desktop.iso

Unrecognized sector mode (c0) at sector 0!

```


workaround suggested by audebruin
```
cp name.img name.iso

```
also didn't work (and why VLC? I am working with Virtual Box
.... I think there are different kind of img files)

---

### Post by Daughain on 2012-10-31
Has any solution to this issue been found yet? I can't locate an iso file of the img file I am using.

---

### Post by nospam2k on 2012-11-23
> **Daughain said:**
> Has any solution to this issue been found yet? I can't locate an iso file of the img file I am using.

I know this is kind of an old post but I wanted to offer a work around. You can write the .img file using USB image writer to a USB stick. If you still need an iso you can use:

dd if=/dev/sdX of=output.iso bs=4M

Where sdX is the whole usb device NOT a partition!

---

### Post by wildmanne39 on 2012-11-23
Old thread closed. Thanks for sharing.

---

