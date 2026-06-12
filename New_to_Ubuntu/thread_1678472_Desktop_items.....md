---
title: "Desktop items...."
date: 2011-01-30
forum: New to Ubuntu
---

### Post by woodcarver on 2011-01-30
I'm using 10.04 LTS, updated yesterday...
Hey all, I have a question. My granddaughter messed with my keyboard and now all of the folders and doc's on my desktop are gone! I did a search for one of the folders and it came back empty! Is there a way to restore them?
Thank You!!!!

---

### Post by dFlyer on 2011-01-30
Did you check you trash bin?

---

### Post by woodcarver on 2011-01-30
Yea, that was the first place I looked. Thanks....

---

### Post by sikander3786 on 2011-01-30
If you are sure that they have been deleted, you need to recover them using some data recovery software. I would recommend *testdisk* here. It would recover all your files that were deleted recently or previously. But, it won't recover the file names. Any files that were stored twice will be recovered twice. And preferably, you need to copy them to another HDD or if that is not possible, to another partition at least and not the same one from where they are being recovered.

So, install testdisk.

```
sudo apt-get install testdisk
```

Once install, start *photorec* by typing,

```
sudo photorec
```

Choose your HDD from where you want to recover files.

Continue.

Choose partition table type. Intel for a PC. Other options for MAC, Sun partition table etc.

Choose partition. If not sure, type sudo fdisk -l (lowercase 'L') in another Terminal.

Choose filesystem. ext2/ext3/ext4 in most cases.

Choose Free. It would scan the free sectors on your HDD and not those which have files on them.

Navigate to your destination directory where you want to save recovered files. If that is another disk, hit ".." twice, then go to Media and choose your drive. Press 'y' when ready.

Remember, your destination partition should have sufficient free space. At least that much that your source partition has got 'free'.

---

### Post by matt_symes on 2011-01-30
Hi

You could also try extundelete.

[http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

Kind regards

---

### Post by woodcarver on 2011-01-30
Thanks all. I don't know what happened to the files, as far as I know they weren't deleted. They just disappeared. My granddaughter is 2 years old, and I'm sure she doesn't know anything about Ubuntu or deleting files.
(grandpa isn't too far ahead of her with Ubuntu!)

---

### Post by ianp5a on 2011-01-30
Did you check under Desktop in the Nautilus File manager? It is possible that they are still there but not shown on the desktop. There is an option to display a desktop clear of icons. I don't remember where it is though.

---

### Post by sikander3786 on 2011-01-30
> **woodcarver said:**
> Thanks all. I don't know what happened to the files, as far as I know they weren't deleted. They just disappeared. My granddaughter is 2 years old, and I'm sure she doesn't know anything about Ubuntu or deleting files.
(grandpa isn't too far ahead of her with Ubuntu!)
Can you please post the output of this command from Applications > Accessories > Terminal to make sure that your files are there or not.

```
ls ~/Desktop
```

---

### Post by woodcarver on 2011-01-30
> **sikander3786 said:**
> Can you please post the output of this command from Applications > Accessories > Terminal to make sure that your files are there or not.

```
ls ~/Desktop
```

Here's the output from the command:
john@john-laptop:~$

So If I'm reading it right, there are no files there. 
I used to do some programming in MS-DOS, many years ago, so I'm not completely lost with some terminal commands....if that helps any?

---

### Post by sikander3786 on 2011-01-30
Yes there don't seem to be any files in your Desktop directory. To look for all files including hidden one's, repeat this command.

```
ls -a ~/Desktop
```

If it still doesn't list any files, the files are not there. And if they are not even in Trash, you don't have any option other than to recover them. As I posted intructions on how to use photorec in my above post, I wrote a post related to photorec on my blog with screenshots. If you want to recover, this might be helpful.

[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by woodcarver on 2011-01-30
> **sikander3786 said:**
> Yes there don't seem to be any files in your Desktop directory. To look for all files including hidden one's, repeat this command.

```
ls -a ~/Desktop
```

If it still doesn't list any files, the files are not there. And if they are not even in Trash, you don't have any option other than to recover them. As I posted intructions on how to use photorec in my above post, I wrote a post related to photorec on my blog with screenshots. If you want to recover, this might be helpful.

[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Thanks! All there is is a .pdf file that I purposely have hidden. 
I'll read through your blog and see what I can do. 
One of these days soon I'm going to have to dig-up the terminal command listing and get back into it....Thanks for your input....:)

---

### Post by hakermania on 2011-01-30
Hey, my solution is the following:
1) Become root
2) give updatedb
3) give locate NAME
where NAME is a name of a folder/file in our desktop that was disappeared (prefer to be special, like 'hello_mother' or '1234_is_my_name' and not 'hi', in order to list less results)
4) You'll end up with the output of where the files are, if they haven't been deleted.

---

