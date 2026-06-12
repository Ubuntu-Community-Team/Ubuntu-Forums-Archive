---
title: "USB mount points? I need help please."
date: 2010-02-25
forum: New to Ubuntu
---

### Post by ericeclifford on 2010-02-25
Hey guys,

I am trying to find out how if possible to change the way ALL USB sticks are mounted.

I want them to all have the name media/disk and then media/disk-1 etc...

I have a diesel USB stick, and it is /media/DIESEL, same with some other types of USB sticks.

but some of them come up as /media/disk, but not all, is there a way I can tell it to name it the way I want it.

This is for a program, that will save bookmarks on my customized live dvd.

It is like a selected persistence but on 8.04.2 and my own code/programming.

---

### Post by Kakers on 2010-02-25
Try this...

```
e2label /media/disk /media/diesel
```

[http://linux.about.com/library/cmd/blcmdl8_e2label.htm](http://linux.about.com/library/cmd/blcmdl8_e2label.htm)

I have only really used this for hard drives, never really USB sticks so it would be interesting to know the result

---

### Post by ericeclifford on 2010-02-26
I was actually looking for away to do it for me. Like a way to automatically change the name upon connecting the device to the PC.

---

### Post by ericeclifford on 2010-03-01
So there is no way to have a config file or something to automatically name a USB stick the name I want, no matter what the name is by default?

---

### Post by undecim on 2010-03-01
You mean like change the "disk" part?

i.e., the first non-labeled USB drive will be "/media/foo" and the second will be "/media/foo-1"?

---

### Post by ericeclifford on 2010-03-01
Well since USB dev ID's are /dev/sda1 etc..

can I just tell fstab to put all /dev/sda1 to /media/disk

and /dev/sda2 to media/disk-1   etc...

---

### Post by ericeclifford on 2010-03-03
Bump still need info if this is possible using fstab.

---

### Post by Lord Stig on 2010-03-04
I would like this info, too. Can anyone help?

---

### Post by HermanAB on 2010-03-04
You need to define the file system Volume Labels of the schticks, then they will be mounted as /media/LABEL.

---

### Post by ericeclifford on 2010-03-04
> **HermanAB said:**
> You need to define the file system Volume Labels of the schticks, then they will be mounted as /media/LABEL.

Could you give me an example of how I would label a disk by using the method /dev/sda1 /media/disk

I mean do I need to give it a  FS as well, like /dev/sda1 vfat /media/disk? and add that to fstab? sorry for being lost, never played with mount points before.

---

### Post by Paddy Landau on 2010-03-04
The name used is the label on the USB disk itself. So, if you change the label on the disk to [FONT=Courier New]foobar[/FONT], then it will mount as [FONT=Courier New]/media/foobar[/FONT]; if you change it to [FONT=Courier New]FooBar[/FONT], it will mount as [FONT=Courier New]/media/FooBar[/FONT]. Presumably your USB device currently has the label [FONT=Courier New]DIESEL[/FONT].

If two devices both have the same label, e.g. [FONT=Courier New]foobar[/FONT], then they will mount (in order) as [FONT=Courier New]/media/foobar[/FONT] and (I think) [FONT=Courier New]/media/foobar1[/FONT].

Remember that case is important; [FONT=Courier New]foobar[/FONT], [FONT=Courier New]FooBar[/FONT] and [FONT=Courier New]FOOBAR[/FONT] are all different.

It's a good idea anyway to change the label on a disk, as it helps you keep track of which one is which.

If you want to override this default, there are three different ways.

[LIST=1]
[*]Change the label (as just described) on each USB device. For example, make your first one [FONT=Courier New]foobar1[/FONT], your second [FONT=Courier New]foobar2[/FONT], etc. Or, better, the first is (say) [FONT=Courier New]Monday[/FONT], the second [FONT=Courier New]Tuesday[/FONT], the third [FONT=Courier New]Wednesday[/FONT], and so on (or whatever names make best sense for what you store on them).
[*]After the USB device has been mounted, right-click the icon on the desktop; select Properties > Drive > Settings > Mount Point, and type the required mount point there. (You'll probably have to unmount then plug it in again. I've never used this method, so I don't know how well it works.)
[*]Before mounting the USB device, add new lines to [FONT=Courier New]/etc/fstab[/FONT]. The front part should *not* have [FONT=Courier New]/dev/sdb1[/FONT] or whatever, but instead [FONT=Courier New]LABEL=*label*[/FONT], e.g. [FONT=Courier New]LABEL=foobar[/FONT]. Just be sure to give each device its own unique label, otherwise it will apply this to the wrong device! Again, remember that case is important.
[/LIST]
Option 1 is clearly the best option, as it puts the mount name onto the USB device itself. Option 2 is not so good, because it might confuse you if names change. Option 3 requires you to put the labels onto the USB device itself anyway, and then overwrite it, so it makes a messy solution.

HTH

---

### Post by ericeclifford on 2010-03-04
> **Paddy Landau said:**
> The name used is the label on the USB disk itself. So, if you change the label on the disk to [FONT=Courier New]foobar[/FONT], then it will mount as [FONT=Courier New]/media/foobar[/FONT]; if you change it to [FONT=Courier New]FooBar[/FONT], it will mount as [FONT=Courier New]/media/FooBar[/FONT]. Presumably your USB device currently has the label [FONT=Courier New]DIESEL[/FONT].

If two devices both have the same label, e.g. [FONT=Courier New]foobar[/FONT], then they will mount (in order) as [FONT=Courier New]/media/foobar[/FONT] and (I think) [FONT=Courier New]/media/foobar1[/FONT].

Remember that case is important; [FONT=Courier New]foobar[/FONT], [FONT=Courier New]FooBar[/FONT] and [FONT=Courier New]FOOBAR[/FONT] are all different.

It's a good idea anyway to change the label on a disk, as it helps you keep track of which one is which.

If you want to override this default, there are three different ways.

[LIST=1]
[*]Change the label (as just described) on each USB device. For example, make your first one [FONT=Courier New]foobar1[/FONT], your second [FONT=Courier New]foobar2[/FONT], etc. Or, better, the first is (say) [FONT=Courier New]Monday[/FONT], the second [FONT=Courier New]Tuesday[/FONT], the third [FONT=Courier New]Wednesday[/FONT], and so on (or whatever names make best sense for what you store on them).
[*]After the USB device has been mounted, right-click the icon on the desktop; select Properties > Drive > Settings > Mount Point, and type the required mount point there. (You'll probably have to unmount then plug it in again. I've never used this method, so I don't know how well it works.)
[*]Before mounting the USB device, add new lines to [FONT=Courier New]/etc/fstab[/FONT]. The front part should *not* have [FONT=Courier New]/dev/sdb1[/FONT] or whatever, but instead [FONT=Courier New]LABEL=*label*[/FONT], e.g. [FONT=Courier New]LABEL=foobar[/FONT]. Just be sure to give each device its own unique label, otherwise it will apply this to the wrong device! Again, remember that case is important.
[/LIST]
Option 1 is clearly the best option, as it puts the mount name onto the USB device itself. Option 2 is not so good, because it might confuse you if names change. Option 3 requires you to put the labels onto the USB device itself anyway, and then overwrite it, so it makes a messy solution.

HTH

So it would be like   LABEL=disk /dev/sda vfat /media   ??

---

### Post by Paddy Landau on 2010-03-04
> **ericeclifford said:**
> So it would be like   LABEL=disk /dev/sda vfat /media   ??
I presume that you are talking about option 3. Assume that you've labelled your USB drive as [FONT=Courier New]party[/FONT] but you wanted it mounted as [FONT=Courier New]/media/sleepy[/FONT].

Then, you would put into your [FONT=Courier New]/etc/fstab[/FONT] file something like
```
LABEL=party  /media/sleepy  vfat  *user,dev,exec,relatime*  0  0
```I'm sorry, I don't know the correct options (*italicised*); you'll have to look them up yourself and change them.

But, as I said, I do *not* recommend option 3. It's messy and inflexible. Rather use option 1: Just label your USB as [FONT=Courier New]sleepy[/FONT], and then it will automatically mount as [FONT=Courier New]/media/sleepy[/FONT].

I put in options 2 and 3 as, well, options; but really, I strongly advise that you go for option 1. That's what I do.

---

### Post by bodhi.zazen on 2010-03-04
I agree, the easiest way is to label your USD device.

Option #4, which is very easy as well, is to use pmount

[http://productivelinux.com/2009/01/31/how-to-automatically-mount-usb-drives-with-rox-filer-ivman-and-pmount/](http://productivelinux.com/2009/01/31/how-to-automatically-mount-usb-drives-with-rox-filer-ivman-and-pmount/)

This method is typically used when one is running a light weight window manager w/o gnome an ivman may conflict with gnome-mount, I am not sure (I do not use gnome enough).

---

### Post by ericeclifford on 2010-03-05
> **Paddy Landau said:**
> I presume that you are talking about option 3. Assume that you've labelled your USB drive as [FONT=Courier New]party[/FONT] but you wanted it mounted as [FONT=Courier New]/media/sleepy[/FONT].

Then, you would put into your [FONT=Courier New]/etc/fstab[/FONT] file something like
```
LABEL=party  /media/sleepy  vfat  *user,dev,exec,relatime*  0  0
```I'm sorry, I don't know the correct options (*italicised*); you'll have to look them up yourself and change them.

But, as I said, I do *not* recommend option 3. It's messy and inflexible. Rather use option 1: Just label your USB as [FONT=Courier New]sleepy[/FONT], and then it will automatically mount as [FONT=Courier New]/media/sleepy[/FONT].

I put in options 2 and 3 as, well, options; but really, I strongly advise that you go for option 1. That's what I do.

Well see here is the problem.

I want to use the /dev/sda1 option to be able to label it /media/disk, because it will be in a live DVD.

And users will use multiple kinds of USB stick, and wont know how to do it. Themselves, and the fact that the live dvd wont change at all( not including persistence).

So is there a way to label a usb stick based on the fdisk option of using the /dev/sda# method to label all incoming USB stick, no matter what their original name is?


EDIT: I tried to add this in the fstab file

/dev/sda1 /media/disk auto users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0

It saids, you dont have permission necessary to view the contents of *disk*.

---

### Post by Paddy Landau on 2010-03-05
> **ericeclifford said:**
> I want to use the /dev/sda1 option to be able to label it /media/disk, because it will be in a live DVD.

And users will use multiple kinds of USB stick, and wont know how to do it. Themselves, and the fact that the live dvd wont change at all( not including persistence).
Right, that's more information than I had before. That changes things.

> **ericeclifford said:**
> So is there a way to label a usb stick based on the fdisk option of using the /dev/sda# method to label all incoming USB stick, no matter what their original name is?
No, I don't think so. That's because each new device gets a new ID. The first hard drive will be [FONT=Courier New]/dev/sda[/FONT] (or it could be [FONT=Courier New]/dev/hda[/FONT] or something). The next USB would be [FONT=Courier New]/dev/sdb[/FONT]. The next external hard drive would be [FONT=Courier New]/dev/sdc[/FONT]. And so on.

So, you can't predict the name for a specific USB, apart from that it will be [FONT=Courier New]/dev/sd*x*[/FONT] (where *[FONT=Courier New]x[/FONT]* could be any letter). That's why an entry in [FONT=Courier New]/etc/fstab[/FONT] won't work. (I had understood that you were in control of your own computer and your own USB drives, which is very different from multiple users with any USB on any computer.)

To handle this programmatically, you would have to disable automatic mounting (sorry, I don't know how to do that); set up something to listen for new devices being added (again, sorry, I don't know how to do that, but it probably involves looking at [FONT=Courier New]/dev[/FONT]); and when you find a new device, mount it according to your desired standards.

So -- *if* I've understood you correctly this time -- you really have three new questions:

[LIST=1]
[*]How do I prevent auto-mounting USB devices?
[*]How do I tell when a new USB device has been inserted into the computer, and...
[*]What is its device name?
[/LIST]
One further comment: Will this apply only to USB sticks, or also to other USB devices such as external hard drives? If the former, then you need a way to distinguish between the two, and allow auto mounting (or your program must mount) the latter.

---

### Post by ericeclifford on 2010-03-08
> **Paddy Landau said:**
> Right, that's more information than I had before. That changes things.


No, I don't think so. That's because each new device gets a new ID. The first hard drive will be [FONT=Courier New]/dev/sda[/FONT] (or it could be [FONT=Courier New]/dev/hda[/FONT] or something). The next USB would be [FONT=Courier New]/dev/sdb[/FONT]. The next external hard drive would be [FONT=Courier New]/dev/sdc[/FONT]. And so on.

So, you can't predict the name for a specific USB, apart from that it will be [FONT=Courier New]/dev/sd*x*[/FONT] (where *[FONT=Courier New]x[/FONT]* could be any letter). That's why an entry in [FONT=Courier New]/etc/fstab[/FONT] won't work. (I had understood that you were in control of your own computer and your own USB drives, which is very different from multiple users with any USB on any computer.)

To handle this programmatically, you would have to disable automatic mounting (sorry, I don't know how to do that); set up something to listen for new devices being added (again, sorry, I don't know how to do that, but it probably involves looking at [FONT=Courier New]/dev[/FONT]); and when you find a new device, mount it according to your desired standards.

So -- *if* I've understood you correctly this time -- you really have three new questions:

[LIST=1]
[*]How do I prevent auto-mounting USB devices?
[*]How do I tell when a new USB device has been inserted into the computer, and...
[*]What is its device name?
[/LIST]
One further comment: Will this apply only to USB sticks, or also to other USB devices such as external hard drives? If the former, then you need a way to distinguish between the two, and allow auto mounting (or your program must mount) the latter.

Well if I knew that i just wanted say /dev/sda 1 - 4, cant I just label /dev/sda 1 - 4 like /media/disk -1   - 4??

---

### Post by Paddy Landau on 2010-03-08
> **ericeclifford said:**
> Well if I knew that i just wanted say /dev/sda 1 - 4, cant I just label /dev/sda 1 - 4 like /media/disk -1   - 4??
Sorry, I didn't understand that question. Remember that you label the device itself, so to use that method, your users would have to label their USB disks --  as you say, not likely to happen!

However, a new thought occurred to me.

You can mount a device in two places. I'll work through an example to explain it.

[LIST=1]
[*]Your user enters a device into the USB port. That device just happens to be labelled 'Jim' and has exactly one partition.
[*]The system automatically adds the device as [FONT=Courier New]/dev/sda[/FONT] and its first partition as [FONT=Courier New]/dev/sda1[/FONT].
[*]The system also automatically mounts [FONT=Courier New]/dev/sda1[/FONT] as [FONT=Courier New]/media/Jim[/FONT].
[*]Your program is listening for new devices. You can do it in two places: Either in [FONT=Courier New]/dev[/FONT] or in [FONT=Courier New]/media[/FONT] -- you decide which is easier for you.
[*]Your program can then look at the output of the mount command to find out which device is mounted where, e.g.:```
**/dev/sda1** on **/media/Jim** type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
```
[*]Suppose that you want your device to be mounted as [FONT=Courier New]/media/disk1[/FONT]. Then you can duplicate [FONT=Courier New]/media/Jim[/FONT] to [FONT=Courier New]/media/disk1[/FONT] as follows.```
sudo mount --bind /media/Jim /media/disk1
```
[/LIST]
I don't know whether this idea would help you.

---

### Post by ericeclifford on 2010-03-08
I still dont get why I cant name /dev/sda to /media/disk

everytime, no matter what the original label is.

And it should be automatic, btw I have to be able to do this in 1 big swoop, I cant let the users do it.

It has to be done automatically and not knowing the original name of the USB device, just what the device name(/dev/sda) is to a label like (/media/disk) then I can call /dev/sdb /media/disk-1

Something like that is what I am looking for.

---

### Post by anewguy on 2010-03-08
You don't seem to be understanding the naming conventions for device mounts, as Paddy Landua explained quite well in his 2nd latest post.  You cannot guarantee what devices others may have, so you cannot gaurantee you will be using /dev/sda for example.  Please re-read his post and if you still have questions as to why you can't do this, please post back and perhaps he'll try again to explain this to you.

Dave ;)

---

### Post by ericeclifford on 2010-03-08
> **anewguy said:**
> You don't seem to be understanding the naming conventions for device mounts, as Paddy Landua explained quite well in his 2nd latest post.  You cannot guarantee what devices others may have, so you cannot gaurantee you will be using /dev/sda for example.  Please re-read his post and if you still have questions as to why you can't do this, please post back and perhaps he'll try again to explain this to you.

Dave ;)

Well here is the scoop, I am making a customized 8.04.2, and I want a selected persistence on this, it will look for the first usb stick( normally /dev/sda).

Even if I have to put instruction in saying that no other USB devices should be in, and that will pretty much guarantee the device will be /dev/sda, so I could change a file to make /dev/sda mount to /media/disk everytime right?

---

### Post by Paddy Landau on 2010-03-08
Unfortunately, you simply cannot guarantee that.

If the computer has a hard drive, that may well become [FONT=Courier New]/dev/sda[/FONT]. If it has two hard drives (quite common), they will be [FONT=Courier New]/dev/sda[/FONT] and [FONT=Courier New]/dev/sdb[/FONT]. Perhaps the user already has an external hard drive that he's kept plugged in, which could be [FONT=Courier New]/dev/sdb[/FONT] or [FONT=Courier New]/dev/sdc[/FONT]. Whatever. You have a huge number of possibilities.

If it were me, I would take the approach that something like CloneZilla takes, which is this:

[LIST=1]
[*]Ask the user to put in the USB device if he hasn't already, and to press Enter (or OK or whatever) when done.
[*]Search for all the devices *and their partitions*. Ignore any partitions that don't have a format compatible with your needs.
[*]List all the partitions -- *not the devices* -- remember that the user may insert a USB device with more than one partition! (For example, I purchased a 2Gb USB stick that came, by default, with two partitions; how many users would even realise this?)
[*]If there is more than one suitable parition, let the user choose which partition he intended.
[*]In any case, confirm that you're about to use that partition, and return to step 1 if not confirmed.
[/LIST]
Of course, you'll have to fiddle your wording to use non-technical jargon as far as possible (e.g. avoid using "partition") unless you intend your users to be familiar with it.

If you're *absolutely sure* that it will *always* be the first USB device and that there are no other devices, then it will be [FONT=Courier New]/dev/sda[/FONT]. But from what you've said, I don't believe that you can be sure.

There may be a way to "change a file" to set the mount point; thinking about it, you may get some luck with [FONT=Courier New]/etc/fstab[/FONT].

But...

... To make an entry into [FONT=Courier New]/etc/fstab[/FONT] you would have to make some assumptions about the file system. I'm not sure that '[FONT=Courier New]auto[/FONT]' would work every time; it might work, but you'll have to test several different USB devices on several different hardware makes and configurations. I don't recommend that, because Ubuntu already has this kind of flexibility built in. You'd be reinventing a few spokes from the wheel.

Rather make use of what Ubuntu already gives you.

I've already given you one way to query Ubuntu about what's attached ([FONT=Courier New]/dev[/FONT]) and mounted ([FONT=Courier New]/media[/FONT]). There are almost certainly other ways, but I don't know about them; try Google.

By the way, with 10.04 LTS coming out in just two months, why don't you wait for that instead of using 8.04?

---

### Post by ericeclifford on 2010-03-08
> **Paddy Landau said:**
> Unfortunately, you simply cannot guarantee that.

If the computer has a hard drive, that may well become [FONT=Courier New]/dev/sda[/FONT]. If it has two hard drives (quite common), they will be [FONT=Courier New]/dev/sda[/FONT] and [FONT=Courier New]/dev/sdb[/FONT]. Perhaps the user already has an external hard drive that he's kept plugged in, which could be [FONT=Courier New]/dev/sdb[/FONT] or [FONT=Courier New]/dev/sdc[/FONT]. Whatever. You have a huge number of possibilities.

If it were me, I would take the approach that something like CloneZilla takes, which is this:

[LIST=1]
[*]Ask the user to put in the USB device if he hasn't already, and to press Enter (or OK or whatever) when done.
[*]Search for all the devices *and their partitions*. Ignore any partitions that don't have a format compatible with your needs.
[*]List all the partitions -- *not the devices* -- remember that the user may insert a USB device with more than one partition! (For example, I purchased a 2Gb USB stick that came, by default, with two partitions; how many users would even realise this?)
[*]If there is more than one suitable parition, let the user choose which partition he intended.
[*]In any case, confirm that you're about to use that partition, and return to step 1 if not confirmed.
[/LIST]
Of course, you'll have to fiddle your wording to use non-technical jargon as far as possible (e.g. avoid using "partition") unless you intend your users to be familiar with it.

If you're *absolutely sure* that it will *always* be the first USB device and that there are no other devices, then it will be [FONT=Courier New]/dev/sda[/FONT]. But from what you've said, I don't believe that you can be sure.

There may be a way to "change a file" to set the mount point; thinking about it, you may get some luck with [FONT=Courier New]/etc/fstab[/FONT].

But...

... To make an entry into [FONT=Courier New]/etc/fstab[/FONT] you would have to make some assumptions about the file system. I'm not sure that '[FONT=Courier New]auto[/FONT]' would work every time; it might work, but you'll have to test several different USB devices on several different hardware makes and configurations. I don't recommend that, because Ubuntu already has this kind of flexibility built in. You'd be reinventing a few spokes from the wheel.

Rather make use of what Ubuntu already gives you.

I've already given you one way to query Ubuntu about what's attached ([FONT=Courier New]/dev[/FONT]) and mounted ([FONT=Courier New]/media[/FONT]). There are almost certainly other ways, but I don't know about them; try Google.

By the way, with 10.04 LTS coming out in just two months, why don't you wait for that instead of using 8.04?

There is no hard drive, just a live dvd.

I will upgrade to newer versions once I finish this version, your support has been great, I will reread your posts and try it, but everything needs to be done auto, this is due to the fact it is a live dvd of  ubuntu.

Which is why I want a selected persistence, and which is why I need the dev/sda to be /media/disk everytime on every "1st" plugged in USB device.

---

### Post by Paddy Landau on 2010-03-09
> **ericeclifford said:**
> There is no hard drive, just a live dvd.
So you have control over the type of hardware. That will help.

> **ericeclifford said:**
> Which is why I want a selected persistence, and which is why I need the dev/sda to be /media/disk everytime on every "1st" plugged in USB device.
I've given as much knowledge as I have, sorry I have no further suggestions.

If this is a commercial venture, and you need more knowledge, then you may want to [purchase professional support from Canonical]("http://www.ubuntu.com/support/services"). It's not expensive for a single year, and I would imagine (though I've never tried it) that their people would have intimate knowledge of the system.

---

### Post by ericeclifford on 2010-03-12
> **Paddy Landau said:**
> So you have control over the type of hardware. That will help.


I've given as much knowledge as I have, sorry I have no further suggestions.

If this is a commercial venture, and you need more knowledge, then you may want to [purchase professional support from Canonical]("http://www.ubuntu.com/support/services"). It's not expensive for a single year, and I would imagine (though I've never tried it) that their people would have intimate knowledge of the system.

Again thanks for the support, Im sure I will find out sooner or later if at all possible.

Maybe I have to write a program to do it myself or have someone write me one in C or something.

---

