---
title: "Can't play dvd's on the movie player"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by lance23dillon on 2011-02-05
When ever I try to play a dvd it comes up saying that "No packages with the requested plugins found". I'm not sure where to find the package that has the plugins I need.

---

### Post by Autodave on 2011-02-05
> **lance23dillon said:**
> When ever I try to play a dvd it comes up saying that "No packages with the requested plugins found". I'm not sure where to find the package that has the plugins I need.


Open a terminal window and type this into it:

sudo apt-get install ubuntu-restricted-extras

Hit ENTE and put your password in when prompted.  Hiw ENTER again and let it do its thing.

---

### Post by lance23dillon on 2011-02-05
Ok I did that and now its coming up with "could not read form resource".

---

### Post by 3177 on 2011-02-05
funny, ive had this problem for a while, but actually just took care of it after seeing your thread.    well, here you go, I just did it and tested a dvd, works fine.
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by lance23dillon on 2011-02-06
Its still coming up with the "could not read form resource". Any new suggestions?

---

### Post by Soulcage on 2011-02-06
If you haven't already add the medibuntu repository
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
Then install libdvdcss2.
```
sudo apt-get install libdvdcss2
```

---

### Post by lance23dillon on 2011-02-06
I tried entering that in and this is what it gave me.


lance@Du-****:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss2' has no installation candidate
lance@Du-****:~$ 

I don't know what to do with that.

---

### Post by mick8985 on 2011-02-06
I'm stuck on a windows machine right now, but iirc libdvdcss2 was superseded with libdvdcss3

---

### Post by JRV on 2011-02-06
Install libdvdcss2 in Ubuntu 10.10 (Maverick Meercat)

If you are using a different version change "maverick" to the correct version name.

You need to add the following lines to /etc/apt/sources.list file or 
you need to make sure you have enabled Universe and multiverse repositories Using GUI.

   gksudo gedit /etc/apt/sources.list

Make sure you have the following two lines save and exit your file.

    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe multiverse

Now update the source list

    sudo apt-get update

    sudo apt-get install medibuntu-keyring

    sudo apt-get update

For i386 Users install Codecs using the following command

    sudo apt-get install w32codecs libdvdcss2

For amd64 Users install Codecs using the following command

    sudo apt-get install w64codecs libdvdcss2

It's also a good idea to install vlc media player:

    sudo apt-get install vlc

---

### Post by 3177 on 2011-02-06
> **lance23dillon said:**
> Its still coming up with the &quot;could not read form resource&quot;. Any new suggestions?

 can you post your terminal output when you try the link I gave you?

---

### Post by odysseusjak on 2011-02-06
This is what I do after I have installed Ubuntu Restricted from the Software Center:

Install DVD playback codecs:
01.  Applications > Accessories > Terminal
02.  cd /usr/share/doc/libdvdread4
03.  sudo ./install-css.sh

Works for me.

---

### Post by lance23dillon on 2011-02-06
So got it working. Stupid error on my part, I'm miss one of the steps. 

Thanks for all the help everyone!

---

### Post by lance23dillon on 2011-02-06
Got it working! I missed a step last time. thanks for all the help!

---

### Post by 3177 on 2011-02-06
glad to hear it.

---

### Post by odysseusjak on 2011-02-09
That's great to hear! Can you marked this thread as solved, please? Thanks!

---

