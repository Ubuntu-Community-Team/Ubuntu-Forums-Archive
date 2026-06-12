---
title: "2 dvd's unreadable/mountable"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by Vege 4wd on 2011-01-30
Hi I have been running Lucid since it first came out. 
Have had no problems with and dvd related activity.

Not though I got two burnt dvd from a friend. They will not play or mount. I have a Matshita dvd drive. 
I have searched google and forums. All I can work out is they are burnt using the udf format. As a result I can not change the permissions. 

Any help or suggestions are welcomed and appreciated.

---

### Post by fabricator4 on 2011-01-30
What makes you think it's a permissions problem?

Put it in your commercial DVD player.  Will it read it?

Chris

---

### Post by Vege 4wd on 2011-01-30
Thanks for the reply. It play in my small portable dvd player. 

I can find the file in mnt that says samsung udf but if I try and open in a media player it comes up with an error saying no permission. I tried to manually change the permissions and will not let me. 

Now I am wondering if it is a region code issue?

---

### Post by albert s on 2011-01-30
I have had udf dvd's in the past with permission problems too.
I dont know why but I was able to get alternatives done,
AFAIK its some kind of photoshop thing......

---

### Post by Vege 4wd on 2011-01-30
Do you know of any workarounds for movies?

---

### Post by sandyd on 2011-01-30
Ubuntu normally mounts discs with iso9660 i think
so
```

sudo mkdir /mnt/cdrom
sudo mount -t udf /dev/sr0 /mnt/cdrom
```

---

### Post by Vege 4wd on 2011-01-30
Thanks for the reply sandyd.
I ran the code and got this error:mount: block device /dev/sr0 is write-protected, mounting read-only
  Any ideas?

---

### Post by fabricator4 on 2011-01-30
> **Vege 4wd said:**
> Thanks for the reply sandyd.
I ran the code and got this error:mount: block device /dev/sr0 is write-protected, mounting read-only
  Any ideas?

Read only should be fine.  You just won't be able to add anything to the disk.

Chris

---

### Post by Vege 4wd on 2011-01-30
Yes that would be ok but I can not play it. When I click on the folder in media it is empty.
Although I know there should be something in it because it plays in the portable dvd player. That is what makes me suspect region code?

---

### Post by sandyd on 2011-01-30
> **Vege 4wd said:**
> Yes that would be ok but I can not play it. When I click on the folder in media it is empty.
Although I know there should be something in it because it plays in the portable dvd player. That is what makes me suspect region code?
this is my bad.
point towards 
```

/mnt/cdrom

```instead. I use gentoo, so I end up mounting everything in /mnt, where ubuntu mounts it in /media....
and also, vlc should be able to play the dvd video without mounting.

---

### Post by Vege 4wd on 2011-01-30
Thanks Sandyd.
  Progress has been made. I can now play it vlc.

  Anyone know of a way to mount it though as I would like to rip it. Or can I rip without mounting? I would try vlc but I would like a little more quality.

Thanks for the input thus far.

---

### Post by sandyd on 2011-01-31
> **Vege 4wd said:**
> Thanks Sandyd.
  Progress has been made. I can now play it vlc.

  Anyone know of a way to mount it though as I would like to rip it. Or can I rip without mounting? I would try vlc but I would like a little more quality.

Thanks for the input thus far.
HandBrake

---

### Post by Vege 4wd on 2011-01-31
I'll give handbrake a go this evening. Ogg rip has been working well for me however will handbrake work even if the disc does not mount?

---

