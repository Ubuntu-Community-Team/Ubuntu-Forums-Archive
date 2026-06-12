---
title: "Is there a way to coax a little more volume from my system?"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-11-03
Sometimes my integrated speakers in my monitor are sufficient ............. sometimes not! Is there anything to do about it?

Thanks guys!

---

### Post by jeeth_viglug on 2009-11-03
Increase the master volume .Try out VLC media player as well.

---

### Post by tahitiwibble on 2009-11-03
I have already done both. :) I seem to have so many devices in the volume control panel, are all of them necessary?

---

### Post by danastasio on 2009-11-03
right click the volume icon, then go to "sound preferences" and crank up the output volume!

---

### Post by tahitiwibble on 2009-11-03
^^^ thanks for the suggestion but no go. All I get is the "volume control preferences" window with a drop-down box and all my devices but no way to adjust anything.

---

### Post by kansasnoob on 2009-11-03
> **tahitiwibble said:**
> Sometimes my integrated speakers in my monitor are sufficient ............. sometimes not! Is there anything to do about it?

Thanks guys!

What version of Ubuntu? Post the output of:

```
cat /etc/issue
```

---

### Post by tahitiwibble on 2009-11-03
```
dad@dad-desktop:~$ cat /etc/issue
Ubuntu 8.10 \n \l
```

---

### Post by Xatolos on 2009-11-03
Depends what you are using them for?
Are the sound issues with video files? If so you can alter the sound options with the program and the master volume. Managed to find a volume 'enhancer' once on I think it was totem player but it made a static-y noise with the movie (a sign I was starting to blow the speakers).
Also be careful with over-ridding the sound, too loud and you can blow them. If its getting shrill and crackley with being loud then you might be asking for problems.

---

### Post by NickJones on 2009-11-03
Have you ever had more volume coming out of the speakers? If it is a laptop then cranking the volume higher will just cause the sound to clip, and possibly damage the speakers.

---

### Post by batterybaby on 2009-11-03
are you sure your soud setting is ok?you are luckier than me.since my HP LAPTOP was bought,its soud is very small.

---

### Post by kansasnoob on 2009-11-03
> **tahitiwibble said:**
> ```
dad@dad-desktop:~$ cat /etc/issue
Ubuntu 8.10 \n \l
```

Install gnome-alsamixer:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video, pay special attention to the VIA toggles to the far right.

I generally need to set the VIA toggles to about 90%+!

---

### Post by tahitiwibble on 2009-11-03
> **kansasnoob said:**
> Install gnome-alsamixer:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video, pay special attention to the VIA toggles to the far right.

I generally need to set the VIA toggles to about 90%+!

No VIA toggles in sight

---

### Post by kansasnoob on 2009-11-03
That's odd. I still have them in Jaunty but not Karmic.

You can see the comparison here:

[http://ubuntuforums.org/showthread.php?t=1291507](http://ubuntuforums.org/showthread.php?t=1291507)

---

### Post by tahitiwibble on 2009-11-03
Hmmmm. This is all I have

[IMG]http://i221.photobucket.com/albums/dd79/wibble_01/Screenshot-GNOMEALSAMixer.png[/IMG]

---

