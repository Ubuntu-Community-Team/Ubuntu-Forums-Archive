---
title: "DVD wont play/Microphone will not set up"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by bbynum on 2010-02-20
Hi I am a former Windows XP user and am trying something new. I am brand new to Linux/Ubuntu and have come a across an issue. After installing the 9.10 version of Ubuntu I am discovering that my DVD Videos will not play. Also my microphone will not register on the Karaoke websites that I absolutely love. It will take me through the sets up and recognize as Linux Microphone but when I try to do a test record you cannot hear anything. I have tried doing updates and going through the sound and video options but I am lost. I do not know what to do. Is there anything that I can do to correct these issues? Please help..Without my microphone and dvd player I feel like I have lost my life line:(. Thanks for taking the time to read my post.

Bbynum

---

### Post by Greenwidth on 2010-02-20
Did you check the input tab on the sound preferences (Right click the speaker icon > Prefs) to check it's not muted? Also on the Hardware tab is it set to Duplex (ie. in & out)?

For DVD you need to:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
or:
If you want all the other codecs (mp3 &c) as well, add the Medibuntu repo:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by bbynum on 2010-02-20
Thanks Greenwidth I will give this a try. I am still learning here. :D

---

### Post by bbynum on 2010-02-20
I am so embarrased but I must be doing something wrong when I go to the link it first tells me to install:

[LIST]
[*]Install the **libdvdread4** package (**no need to add third party repositories**) via Synaptic or command line: 
[/LIST]

 sudo apt-get install libdvdread4
Am I supposed to open a terminal and put that in there because it doesn't give me the option to just install, like a click here option?

---

### Post by Greenwidth on 2010-02-20
Yes that's right input that into a terminal and it will connect, download and install it for you. 

Synaptic (System > Admin > Synaptic) is the GUI version, it's often quicker to just use the terminal.

For a good set of tutorials see left pane of:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by switch10 on 2010-02-20
Here is another heads up.  You wont be able to play Mp3's flash video and many other non free formats.  open a terminal and type this as well:

```
 sudo apt-get install ubuntu-restricted-extras 
```

---

### Post by Ozymandias_117 on 2010-02-20
You may also need libdvdcss2 for some videos with newer protection methods. (Or at least you might for ripping, libdvdread4 may work fine for playing)

---

### Post by bbynum on 2010-02-20
Thanks everyone for all of this useful information...I am watching videos and singing again. Everything was most helpful

~~smiles,
bbynum~~

---

