---
title: "How to install VideoLan manually?"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by bilbo.san on 2010-09-22
Hello everyone!
I have a problem trying to play a WMV video, for it doesnt reproduce any sound. Ubuntu Movie Player says that it requires Windows Media Audio 9 codec to reproduce, the version 1.0.x of VLC says the same thing... 

I was hoping that the latest version of VLC would reproduce it. But VLC's site says that to have the latest version, it should be installed manually (??).

Any help is greatly appreciated!
e.

---

### Post by Jesus_Valdez on 2010-09-22
Try installing the codecs.

sudo apt-get install ubuntu-restricted-extras

---

### Post by bilbo.san on 2010-09-22
> **Jesus_Valdez said:**
> Try installing the codecs.

sudo apt-get install ubuntu-restricted-extras

Thanks... but still didnt work. Should I restart the system perhaps?

---

### Post by chewearn on 2010-09-22
You possibly need medibuntu repository to get some MS Windows codec.

[https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats](https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats)

---

### Post by bilbo.san on 2010-09-22
> **chewearn said:**
> You possibly need medibuntu repository to get some MS Windows codec.

[https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats](https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats)

thanks... but it couldnt be installed!

---

### Post by jtarin on 2010-09-22
Did you follow these instructions about adding VLC to your repositories?
> If you wish to install VLC 1.0.6 anyway, please refer to the instructions above for _Ubuntu 10.10_. Note that there will be some bugs; you are on your own.
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by chewearn on 2010-09-22
> **bilbo.san said:**
> thanks... but it couldnt be installed!

Could you be specific about the steps you did and the error message you encountered?

Saying it couldn't be install does not help to understand your issue, as I have no problem installing and playing WMV files.

---

### Post by bilbo.san on 2010-09-22
> **jtarin said:**
> Did you follow these instructions about adding VLC to your repositories?

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Yes... I did and it installed the 1.0... but it doesn't provide the latest 1.1.x version.

---

### Post by bilbo.san on 2010-09-22
> **chewearn said:**
> Could you be specific about the steps you did and the error message you encountered?

Saying it couldn't be install does not help to understand your issue, as I have no problem installing and playing WMV files.

Hi,
Thanks for your help!
This is that returned
>>>
[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate[/I]

<<<

---

### Post by chewearn on 2010-09-22
> **bilbo.san said:**
> Hi,
Thanks for your help!
This is that returned
>>>
[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate[/I]

<<<

Okay, this mean you have not added the medibuntu repository.  Scroll to the top of the wiki page to see the command to add the medibuntu repository, then re-run:
```
sudo apt-get install w32codecs
```

---

### Post by andrew.46 on 2010-09-22
Hi bilbo,

> **bilbo.san said:**
>  Ubuntu Movie Player says that it requires Windows Media Audio 9 codec to reproduce, the version 1.0.x of VLC says the same thing...

A complicating factor is that the audio files can be one of 4 different types: wma, wma pro, wma lossless and wma voice. If you are running a *32 bit* installation the good news is that a recent copy of MPlayer along with the w32codecs from Medibuntu will play *all* of these variants. vlc is not quite so versatile, it depends very much on which version of libavcodec it has been compiled against and if it has been compiled with the *--enable-loader* option.

Andrew

---

