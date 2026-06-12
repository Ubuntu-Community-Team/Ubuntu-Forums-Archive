---
title: "After deleting EXT4 partition, I lost my files from NTFS partition.... ?"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by samsung3D on 2010-12-21
Okey, I'm absolute beginner and I have question:

I have dual-boot laptop (*Windows XP & Ubuntu 10.10*) and I wanted to replace the *Ubuntu 10.10* with the *Ubuntu 10.10 Notebook*.

Partitions on my hard drive: 
> [LIST]
[*]*Windows XP* --- C:\ [*]Documents and pictures ---- D:\ [*]*Linux 10.10* which I was replacing with *Linux 10.10 Notebook* --- unknown drive (it's hidden from *XP*)
[/LIST]


What I've done was:

- I put my Linux 10.10 Notebook via usb
- Go through the setup
- Go in the advanced menu
- Delete the ext4 partition and make another partition on the same free space
- I made "/" sign on that partition (which I think that the sign is something like flag for installing the OS on that partition, maybe I'm wrong)
- AND when I click the "next" button It shows me one message (something that will delete the other system files on that partition, but I'm not sure), but I click OK and setup continued.

After the setup, I wasn't able to start the [I]Ubuntu 10.10 Notebook
[/I] but that's not the problem, the problem is that **files from the NTFS partition was lost**. 

Any help will be appreciated, because I wait your response.
Thanks.

---

### Post by garvinrick4 on 2010-12-21
Were you running a WUBI install? A folder inside of Windows called Ubuntu?

---

### Post by samsung3D on 2010-12-21
> **garvinrick4 said:**
> Were you running a WUBI install? A folder inside of Windows called Ubuntu?

Sorry I don't know what is WUBI. Can you explain the question?

---

### Post by sffvba[e0rt on 2010-12-21
> **samsung3D said:**
> Sorry I don't know what is WUBI. Can you explain the question?

Did you install Ubuntu from within Windows, or did you boot from the Ubuntu disc/usb and install that way?

404

---

### Post by samsung3D on 2010-12-21
> **not found said:**
> Did you install Ubuntu from within Windows, or did you boot from the Ubuntu disc/usb and install that way?

404

I boot from the Ubuntu usb and from there I remove the partition first than I make new one.

---

### Post by sffvba[e0rt on 2010-12-21
> **samsung3D said:**
> Okey, I'm absolute beginner and I have question:

I have dual-boot laptop (*Windows XP & Ubuntu 10.10*) and I wanted to replace the *Ubuntu 10.10* with the *Ubuntu 10.10 Notebook*.



If all you wanted to do was try the Unity interface you simply had to run the following in terminal:

```
*sudo apt-get update && sudo aptitude install unity*
```Then you could log-out and when logging in you could choose to use the Unity interface or the standard Gnome interface...

> 
After the setup, I wasn't able to start the [I]Ubuntu 10.10 Notebook
[/I] but that's not the problem, the problem is that **files from the NTFS partition was lost**. 

So you are able to boot into Windows? Are all the files gone?  Some of the files?


404

---

### Post by oldfred on 2010-12-21
This should tell us what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by samsung3D on 2010-12-21
So you are able to boot into Windows? Are all the files gone?  Some of the files?


404[/QUOTE]

Good question, I forgot to write that. Windows files are OK, I boot the Windows XP without error, JUST the files in the D:\ partition are lost. That's why I'm confused.

---

### Post by samsung3D on 2010-12-21
> **oldfred said:**
> This should tell us what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

I will do that tomorrow and I will post the results, it's 2:30AM here :)

---

### Post by sffvba[e0rt on 2010-12-21
> **samsung3D said:**
> I will do that tomorrow and I will post the results, it's 2:30AM here :)
Good night ;)

---

### Post by samsung3D on 2010-12-22
I was wrong about this problem. My hard disk was empty before I tried to do anything! My documents which I was thinking that they are lost, they were on my other laptop. I reinstalled 3 laptops and I think I "forgot my head on the table" :) .... Sorry for this!

But I like to say that I didn't expect those "light-speed replies"

Thank you anyway.



(How can I delete this tread? I was searching but didn't found that. Or just to mark it as SOLVED tread?)

---

### Post by oldfred on 2010-12-22
Threads do not get deleted. Yours is best case as no data was lost.:) 

I would not post solved, just as those threads are where instructions worked to solve a problem and those searching forum can narrow down search. Even may solved threads do not get posted as solved.

---

### Post by sffvba[e0rt on 2010-12-23
> **samsung3D said:**
> I was wrong about this problem. My hard disk was empty before I tried to do anything! My documents which I was thinking that they are lost, they were on my other laptop. I reinstalled 3 laptops and I think I "forgot my head on the table" :) .... Sorry for this!

But I like to say that I didn't expect those "light-speed replies"

Thank you anyway.



(How can I delete this tread? I was searching but didn't found that. Or just to mark it as SOLVED tread?)

hehe... thanks for sharing the "solution", glad you didn't loose anything...

I would suggest marking the thread as solved (that way somebody else doesn't try and give advice to a non-existing problem, and others may see that they can use this thread to maybe solve there own problems (hey, somebody else might also forget which PC there data is on))...


Cheers
404

---

### Post by garvinrick4 on 2010-12-23
By the way from your post #1 the / means your file system like C: drive in Windows.
Anytime you install a new / it formats the partition to what ever you tell it (ext4) and
overwrites what ever was there before. So if you want to do a clean install just mark
to format ext4 and use as / and you do not have to do anything to partition before installing file system or now called "/"

---

### Post by samsung3D on 2011-01-31
> **garvinrick4 said:**
> By the way from your post #1 the / means your file system like C: drive in Windows.
Anytime you install a new / it formats the partition to what ever you tell it (ext4) and
overwrites what ever was there before. So if you want to do a clean install just mark
to format ext4 and use as / and you do not have to do anything to partition before installing file system or now called "/"

Thanks garvinrick4! Now I will know what is / for. 
The thread is now [SOLVED].

---

