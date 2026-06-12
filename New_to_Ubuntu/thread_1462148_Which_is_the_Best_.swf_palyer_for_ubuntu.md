---
title: "Which is the Best .swf palyer for ubuntu"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by kannan.csea on 2010-04-25
History:
Hi friends, I am new to ubuntu. I have downloaded some tutorials about eclipse IDE which are in .swf format, I tried to play this files both in movie player of ubuntu and VLC player with no success. They didn't ask for any codecs or search for any plugins. But the videos are not playing properly in both of them. 

Questions:
Now how can I get my .swf files playing. Which is the best player available for it. And how can I get it. 

I am new to ubuntu and I am using ubuntu 9.04.

---

### Post by warfacegod on 2010-04-25
I use Gnome M-Player for all video and have no issues with flash files.

You may need to enable "Multiverse" in Software Sources and get all your updates.

Just for a goof, try deleting the .swf from the file name and then play it. If it still won't play, try making it .sfv instead. If that doesn't work, just rename it the way it was.

---

### Post by ajgreeny on 2010-04-25
Almost any of the ubuntu video players, certainly all I have used, will play those without problem provided you have all the codecs needed.

ubuntu-restricted-extras should provide everything normally needed, but I always also add the universe and multiverse gstreamer ugly and bad packages, and the w32codecs from medibuntu, w64codecs if yourun a 64 bit system.

Of all the players, VLC is definitely my favourite for just about everything multimedia.

---

### Post by kannan.csea on 2010-04-25
> **warfacegod said:**
> I use Gnome M-Player for all video and have no issues with flash files.

You may need to enable "Multiverse" in Software Sources and get all your updates.

Just for a goof, try deleting the .swf from the file name and then play it. If it still won't play, try making it .sfv instead. If that doesn't work, just rename it the way it was.


Tried removing the extension and also changing to .sfv. But it didn't work for me buddy. Now gonna try the Gnome M-player

---

### Post by kannan.csea on 2010-04-25
> **ajgreeny said:**
> Almost any of the ubuntu video players, certainly all I have used, will play those without problem provided you have all the codecs needed.

ubuntu-restricted-extras should provide everything normally needed, but I always also add the universe and multiverse gstreamer ugly and bad packages, and the w32codecs from medibuntu, w64codecs if yourun a 64 bit system.

Of all the players, VLC is definitely my favourite for just about everything multimedia.


How to install codes friend? I am very new to ubuntu can you give the terminal commands to do that.

---

### Post by kannan.csea on 2010-04-25
Downloading Gnome-Mplayer using:

```
sudo apt-get install gnome-mplayer
```

I will tell what happens with my .swf files with this new player once it gets installed.

---

### Post by ghostborg on 2010-04-25
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Medibuntu-follow the instructions for:
Adding the Repository
Playing Encrypted DVDs - with the entire Medibuntu repository
Playing Non-Native Media Formats - with the entire Medibuntu repository

Make sure you have installed ubuntu-restricted-extras with Synaptic Package Manager.

---

### Post by kannan.csea on 2010-04-25
Gnome-Mplayer installed still my .swf files are not playing good. The sound is playing nicely but the video is cluttered for some time then it turns black and no video is there only the audio keeps running.

---

### Post by warfacegod on 2010-04-25
Sounds like you need a better codec. I'd give ghostborg's link a try.

---

### Post by kannan.csea on 2010-04-25
> **ghostborg said:**
> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Medibuntu-follow the instructions for:
Adding the Repository
Playing Encrypted DVDs - with the entire Medibuntu repository
Playing Non-Native Media Formats - with the entire Medibuntu repository

Make sure you have installed ubuntu-restricted-extras with Synaptic Package Manager.

Now downloading the codes from medibuntu. Hope its not illegal:

```
sudo apt-get install w32codecs
```

I will tell what happens once its finished.

---

### Post by warfacegod on 2010-04-25
Not if you're using it for Research. :P

---

### Post by kannan.csea on 2010-04-25
Codecs installed succefully

Setting up w32codecs (20071007-0medibuntu4) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kannan@kannan-laptop:~$ 

But still the .swf not working. Dont know why its always everything happens different for me. 

Friends any further help about this. ?

---

### Post by kannan.csea on 2010-04-25
After installing this codecs i tried to play the .swf files using the Gnome-Mplayer and now something pretty happens, it shows a Error message.

[IMG]file:///home/kannan/Desktop/Error.png[/IMG][IMG]http://lh5.ggpht.com/_xW3xw7ryJqs/S9RGW0b9qEI/AAAAAAAADFw/gAnJY-XNmMU/Error.png[/IMG]

---

### Post by cuberts on 2010-04-25
> **kannan.csea said:**
> History:
Hi friends, I am new to ubuntu. I have downloaded some tutorials about eclipse IDE which are in .swf format, I tried to play this files both in movie player of ubuntu and VLC player with no success. They didn't ask for any codecs or search for any plugins. But the videos are not playing properly in both of them. 

Questions:
Now how can I get my .swf files playing. Which is the best player available for it. And how can I get it. 

I am new to ubuntu and I am using ubuntu 9.04.I think that the best is the GNOME M swf, and I use it. It works great too.
You can get it by simply going to the Ubunbu software center, and searching for it

---

### Post by kannan.csea on 2010-04-25
> **cuberts said:**
> I think that the best is the GNOME M swf, and I use it. It works great too.
You can get it by simply going to the Ubunbu software center, and searching for it


Hi friend, I tried this out and now when I try to play the .swf file it plays. But only the video is running and there is no audio. And the video also is not properly running it just moves like snapshots in a slideshow.

---

