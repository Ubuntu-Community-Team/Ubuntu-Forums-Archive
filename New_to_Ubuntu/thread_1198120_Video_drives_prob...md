---
title: "Video drives prob.."
date: 2009-06-27
forum: New to Ubuntu
---

### Post by koyakishore on 2009-06-27
hello mates..

i'm unable to play videos in my players..

and i'm even unable to enable my desktop effects..

i thnk the prob is with video drivers..

how to recover the problem..???

plz...guide me...

---

### Post by prvteprts on 2009-06-27
Please post details as much as you can so we could have a clue to what your problem is. Details like:

- your video card chipset
- the movie player you are using
- the file formats of the movies
- what happens when you try to play movies (description of scenario)

---

### Post by ~sHyLoCk~ on 2009-06-27
> **koyakishore said:**
> hello mates..

i'm unable to play videos in my players..

and i'm even unable to enable my desktop effects..

i thnk the prob is with video drivers..

how to recover the problem..???

plz...guide me...
Which video card?

---

### Post by mhgsys on 2009-06-27
Agree with the posters above to have more info, 
Guiding you:

please open up a terminal and typ:
```

lspci | grep VGA

```

to let us know which card you are using.

---

### Post by mal1958 on 2009-06-27
If your chipset is Nvidia, you can try to go to:

 System>Administration>Hardware Drivers

Nvidia driver are a proprietary driver that Ubuntu cannot ship with it's disk.  However I have found that Nvidia folk are a lot faster at getting drivers out and ones that work with the system.

Mike

---

### Post by koyakishore on 2009-06-27
yaa guys...
will give enuf info from now onwards..

coming to my prob..

1.my graphics card is INTEL rev02

2.I have 2 players VLC and tottem movie player...so, when i open a video file..both players first try to start the video playing.. but immediately the player gets terminated..

3.rite now...i'm using avi file format to be played.. but as VLC can play any file..i think i really has a prob..

---

### Post by LewRockwell on 2009-06-27
> **koyakishore said:**
> hello mates..

i'm unable to play videos in my players..

and i'm even unable to enable my desktop effects..

i thnk the prob is with video drivers..

how to recover the problem..???

plz...guide me...

G'day Mate!

see below...

---

### Post by koyakishore on 2009-06-28
anyone..?? plzz..

---

### Post by 3rdalbum on 2009-06-28
It's not a graphics driver problem. You already have the Intel driver, it's preinstalled. It wouldn't cause the problem you described. Your problem, sir, is one of codecs.

Have you tried installing the "ubuntu-restricted-extras" package, and added the w32codecs package from Medibuntu.org? (click on Repository HOWTO on medibuntu.org and follow the instructions, and then you'll be able to install the w32codecs from Synaptic Package Manager).

Do you know what video codec is used in the file you are trying to play? Do other video files work fine?

---

### Post by prvteprts on 2009-06-28
What are the specifications of that video card? Sorry, I am not familiar with it. I tried googling it, and it seems to be a sound card chipset or something. I guess it's a motherboard with integrated sound and graphics.

How old is your machine? I hope your problem has nothing to do with your specs being outdated or anything. I experience those kinds of symptoms when I try to play videos on a very OLD machine. Right around the time the video starts to load, the player or web browser terminates.

Are you dual booting with another OS and are you experiencing the same problems?

---

### Post by DPJ93 on 2009-06-28
> **mal1958 said:**
> If your chipset is Nvidia, you can try to go to:

 System>Administration>Hardware Drivers

Nvidia driver are a proprietary driver that Ubuntu cannot ship with it's disk.  However I have found that Nvidia folk are a lot faster at getting drivers out and ones that work with the system.

Mike

Actually, it worked exactly the same for me with my ATI graphic card. But I still prefer Nvidia.

---

### Post by halitech on 2009-06-28
if you search the forum you will find numerous threads about 9.04 and intel chipsets. There seems to be an issue with the latest drivers where previous drivers worked fine. There is info on fixing the issue but too lazy to look things up right now.

---

### Post by koyakishore on 2009-06-28
well..

@3rdalbum
i do installed ubuntu-restricted-extras..but i never tried w32 codecs..
ya...the prob is with all video files, not just the particular file..

@prvteprts
ya...i dual boot with windows.. and videos are working well in windows..

---

### Post by koyakishore on 2009-06-28
hmmmm...
first of all..thanks alot for ur replies...

now i even installed w32 codecs from medibuntu... but still no progress..:(

3 days back...all my players worked well..

but...after i upgraded ubuntu9.04..
i started facing these probs..:(

now..i started using windows again due to this prob..
hmmm...but i really like ubuntu..i wanna use ubuntu..:)

but..oops..

---

### Post by QIII on 2009-06-28
I think  you may have gotten steered away from the real issue.

If you have an Intel graphics chipset that worked with a prior version of Ubuntu and does not work now, please take a look at

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

Take a look at the section titled "Performance regressions on Intel graphics cards"

---

### Post by koyakishore on 2009-07-01
thanks alot mate..:)

It solved my problem..

---

