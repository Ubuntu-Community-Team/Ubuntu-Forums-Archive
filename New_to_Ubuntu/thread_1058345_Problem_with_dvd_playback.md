---
title: "Problem with dvd playback"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by unitedwefall on 2009-02-02
Hi

I dunno if there is something really obvious that i'm missing but whenever i stick a dvd into ubuntu it won't play. It comes up with the correct dvd title (eg 'princess mononoke') etc. But as soon as i try to load it in vlc or mplayer or any media player it'll just crash. This happens with any dvd. Could it be something to do with the codec packs i have down? i thought id got all the right ones. Also the videos which i have saved to my hard disc play fine and the dvd drive works fine when i boot vista. (also worth noting that audio cd's play fine on ubuntu). Thanks for the help

xx

---

### Post by shifty_powers on 2009-02-02
have you installed

```
sudo apt-get install ubuntu-restricted-extras
```

?

---

### Post by Crafty Kisses on 2009-02-02
Did you install the "ubuntu-restricted-extras" package?

---

### Post by theozzlives on 2009-02-02
First install ubuntu-restricted-extras, the go to the terminal and type:
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```
then
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by Jingle on 2009-02-11
I'm following this thread and am installing the ubuntu-restricted-extras from terminal as instructed.. however it's bringing up at license agreement for SUN Java, and not letting me move forward, I've tried ENTER, Y(es), O(k), SPACEBAR, ESC, Q(uit) and nothing is working.

---

### Post by rax_m on 2009-02-11
I think you have to use your down arrow key until the <ok> is highlighted. Then press enter.

---

### Post by Jingle on 2009-02-11
After much swearing found it to be TAB!

thanks though...now my terminal is sat stuck waiting for an HTTP response from sourceforge trying to download some microsoft fonts :S

All I want is a DVD player!  VLC did it automatically in windows xp

---

### Post by dca on 2009-02-11
And unfortunately unless you pay for 3rd party app like LinDVD to play encrypted DVDs or Fluendo G-Streamer pack to play MP3/WMAs then it's worth putting up with the nuances...

---

### Post by quietbear on 2009-02-12
> **theozzlives said:**
> First install ubuntu-restricted-extras, the go to the terminal and type:
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```
then
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

I as well am doing this, and it is working as yet.  But I was wondering, what exactly am I doing?  What I mean is, what do these codes do exactly?  What does this process do?

---

### Post by jbsongaku on 2009-03-07
The first one just installs libdvdread3 and totem(xine).
The second one is for reading through the dvd copy protection so you can play protected DVD's

---

### Post by doublewitt on 2009-03-08
I have followed all threads on dvd playback and still have problems with it. It seems to be somewhat complicated. Every dvd player seems to be missing vital parts and so "on with the goose chase"...

Despite that, I have found a dvd player that you simply download and install. Once you run it for the first time and without changing any settings in the program options, it plays all my dvd files without ANY problems! 

**[SIZE="6"]xine-Media Player[/SIZE]**
**Works like a charm...**

---

### Post by mcloser on 2009-03-10
this was very frustrating for a while.

I went through most of the instructions and installed probably about 100meg of stuff I didn't have to.

after each one of these steps I retried openning the movie and of course found it did not work. so I kept searching for a solution and loading more junk.

finally I used the thing between my ears and thought I wonder if Ubuntu is turning into Windoze and I  HAVE TO reboot ????

well guess what ladies and germs... yes you guessed right !

after rebooting the machine, the hollywood encrypted dvd now played perfectly in all player apps.

so a word to anyone else out there with the same issue:  load the non free libs and other stuff that you think you need and then

REBOOT   ala windoze ( up and down like a toilet seat )

next question:  is Tux the illegitimate love child of Bill Gates and Pingu the cartoon penguin....

oh almost forgot to say:   REBOOT !

---

### Post by mcloser on 2009-03-10
> **doublewitt said:**
> I have followed all threads on dvd playback and still have problems with it. It seems to be somewhat complicated. Every dvd player seems to be missing vital parts and so "on with the goose chase"...

Despite that, I have found a dvd player that you simply download and install. Once you run it for the first time and without changing any settings in the program options, it plays all my dvd files without ANY problems! 

**[SIZE="6"]xine-Media Player[/SIZE]**
**Works like a charm...**


yeah, well Xine didn't work for hollywood dvd upon install for me.  nothing did.

as above had to download the libs and non free stuff and then REBOOT

don't forget the w64 codecs ( 64 bit for me )

if Linus was dead he'd be rolling in his grave.

---

### Post by kansasnoob on 2009-03-10
Look here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

It's pretty much self explanatory. I don't bother with the full Medibuntu repo anymore I just skip to:

[https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)

and:

[https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats](https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats)

Then I choose the "with individual packages" option.

---

