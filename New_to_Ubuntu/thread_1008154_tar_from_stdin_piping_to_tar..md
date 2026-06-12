---
title: "tar from stdin: piping to tar."
date: 2008-12-11
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-12-11
I want to do something like this
```

# dd if=/dev/sdX | tar -cvz /location/of/harddiskimage.tar.gz

```

I am currently using the following
```

# dd if=/dev/sdX | gzip > /location/of/harddiskimage.img.gz

```
However I would like to be able to add other things into the archive, not just compress the image.
Any help is appreciated

---

### Post by cmnorton on 2008-12-11
What about:

dd if=/dev/sdX | tar -cvzf /location/of/harddiskimage.tar.gz

z is supposed to compress on create and decompress on extract.

---

### Post by JohnGalt131 on 2008-12-11
> **cmnorton said:**
> What about:

dd if=/dev/sdX | tar -cvzf /location/of/harddiskimage.tar.gz

z is supposed to compress on create and decompress on extract.

```
# dd if=/dev/zero | tar -cvzf /home/user/Desktop/imag.tgz
tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.

```

---

### Post by glennric on 2008-12-11
Why not first do
```
dd if=/dev/sdX > filename
```
Then
```
tar czvf harddiskimage.tar.gz filename
```

??

---

### Post by Duck2006 on 2008-12-11
Some of this may help

[http://ubuntuforums.org/showthread.php?t=633232](http://ubuntuforums.org/showthread.php?t=633232)
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

---

### Post by JohnGalt131 on 2008-12-11
> **glennric said:**
> Why not first do
```
dd if=/dev/sdX > filename
```
Then
```
tar czvf harddiskimage.tar.gz filename
```

??

Isn't that two operations? dd is very slow as is and if you add to that time the time needed to tar it, that makes for two long operations when I'd rather it just be 1 long operation.

---

### Post by glennric on 2008-12-11
I don't think that tar accepts data from standard input the way you are trying to do.  It needs a list of files to work on, not data like that output by dd.  So you may be stuck with two commands.

---

### Post by glennric on 2008-12-11
Why are you trying to do this?

---

### Post by cmnorton on 2008-12-11
> **JohnGalt131 said:**
> ```
# dd if=/dev/zero | tar -cvzf /home/user/Desktop/imag.tgz
tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.

```

Mea culpa. Sorry about the mis-information. 

You can certainly dd from the device and pipe it into gzip. I just tried it.

sudo dd if=/dev/sdb1 | gzip -9 > temp.gz    

This works, where /dev/sdb1 is my unmounted external USB drive.

Else, I believe you would have to dd out to a file, and then run that through tar.

Edit:
-----------

Are you trying to image a disk?

---

### Post by JohnGalt131 on 2008-12-11
> **cmnorton said:**
> Mea culpa. Sorry about the mis-information. 

You can certainly dd from the device and pipe it into gzip. I just tried it.

sudo dd if=/dev/sdb1 | gzip -9 > temp.gz    

This works, where /dev/sdb1 is my unmounted external USB drive.

Else, I believe you would have to dd out to a file, and then run that through tar.

Edit:
-----------

Are you trying to image a disk?
Yes I periodically create compressed images. But I would like to be able to append files to the archive (usually text files) such as a list of instructions for a restore, the contents of the image, etc. gzip only compresses, it does not (I don't think) archive.

---

### Post by caljohnsmith on 2008-12-11
double post, sorry about that, see below.

---

### Post by caljohnsmith on 2008-12-11
> **JohnGalt131 said:**
> I want to do something like this
```

# dd if=/dev/sdX | tar -cvz /location/of/harddiskimage.tar.gz

```

I am currently using the following
```

# dd if=/dev/sdX | gzip > /location/of/harddiskimage.img.gz

```
However I would like to be able to add other things into the archive, not just compress the image.
Any help is appreciated
I believe Glennric is right, if you send standard output to tar, it needs to be a list of files to tar together; when you use "dd" to create an image, you are creating one, single huge "file" of your entire drive, so tar "cowardly" refuses to tar a single file. If you want to append files to your cloned HDD image that you create with dd, the only way I know of to do it is if the HDD image is decompressed, and then you can mount a partition (sda6 in the example below) in the HDD image by doing:
```
sudo losetup -o $((512*$(sudo sfdisk -luS [COLOR="Red"]harddiskimage.img[/COLOR] 2>/dev/null | grep [COLOR="Red"]sda6[/COLOR] | awk '{print $2}'))) /dev/loop0 [COLOR="Red"]harddiskimage.img[/COLOR]
sudo mount /dev/loop0 /mnt
```
And then your sda6 partition is mounted on /mnt, and you can add files to it. Essentially the code above is the same as manually doing:
```
sudo sfdisk -luS harddiskimage.img
```
And then using that output to know the starting sector of your sda6 partition as "start_sector" (sda6 is just an example), then you can do:
```

sudo losetup -o $((512*[COLOR="Red"]start_sector[/COLOR])) /dev/loop0 harddiskimage.img
sudo mount /dev/loop0 /mnt
```
And that's the same thing.

---

