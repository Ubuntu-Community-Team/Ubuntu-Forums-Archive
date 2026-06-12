---
title: "Anyone know of any way to view a dvd ?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Mtrboat on 2009-09-02
Ok just put a dvd in and Movie Player has a problem with playing it. I also tryed Gstreamer and it failed as well. Anyone with any info on how to play a dvd please help . I had no idea this would be an issue .

---

### Post by gordintoronto on 2009-09-02
> **Mtrboat said:**
> Ok just put a dvd in and Movie Player has a problem with playing it. I also tryed Gstreamer and it failed as well. Anyone with any info on how to play a dvd please help . I had no idea this would be an issue .

Your best bet would be to search the forums before you ask a question.  This one has been answered many, many times -- including today.

---

### Post by 3rdalbum on 2009-09-02
That wasn't exactly the friendliest answer to your question, but it is a valid thing to say.

In short, add the Medibuntu repository ([www.medibuntu.org](www.medibuntu.org), click Repository Howto), install the libdvdcss2 and VLC packages in Synaptic Package Manager, and use VLC as your DVD player.

DVD decryption support can't ship out-of-the-box in any free operating system because of patents and legal restrictions in some parts of the world; but Medibuntu makes it simple to add.

---

### Post by kansasnoob on 2009-09-02
I prefer totem-xine but you need the Medibuntu repo also, so from terminal run these commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

then (after it's completed running you'll see the **"lance@lance-desktop:~$"** again - of course you're probably not lance :)) run:

```
sudo apt-get install libdvdcss2 w32codecs totem-plugins-extra totem-xine ubuntu-restricted-extras
```

If you want to try vlc:

```
sudo apt-get install mozilla-plugin-vlc  vlc-plugin-pulse
```

Restart Firefox after the changes. Then to play a movie look in Sound & Video, I prefer the Totem-Xine which will play under the native "Movie Player".

Some prefer mplayer - there are several front-ends to mplayer _ I find smplayer to be the best, but it's all a matter of choice.

Let us know how that works.

---

### Post by 3rdalbum on 2009-09-02
> **kansasnoob said:**
> 
```
sudo apt-get install libdvdcss2 w32codecs totem-plugins-extra totem-xine ubuntu-restricted-extras
```

Kansasnoob, when you're directing people to install the codecs from Medibuntu, you should tell them to install the "non-free-codecs" package rather than the "w32codecs" package.

w32codecs is not present on 64-bit - it's called w64codecs. The non-free-codecs package is present on 32-bit and 64-bit and will pull in the relevant w32/w64codecs package for your system.

Also, I tend to advise people to use Synaptic when they want to install ubuntu-restricted-extras, because then the Java license agreement comes up in a GUI dialog. If you just use apt-get, then the license agreement comes up in the text console, and a lot of people don't know that you have to press Tab to highlight the "I Agree" button.

Sorry to pick holes in your post, but we might as well make things as trouble-free for new users as possible :-)

---

### Post by kansasnoob on 2009-09-02
> **gordintoronto said:**
> Your best bet would be to search the forums before you ask a question.  This one has been answered many, many times -- including today.

So what? That's why they have an Absolute Beginners section.

I started out with Freespire and gOS, then converted to the KDE desktop on gOS, and finally found my beloved Gnome desktop in Ubuntu.

By then I was beyond confused, and totally frustrated, so even the most basic questions should be welcomed.

Sometimes I still need to have my hand held!

---

### Post by gognos on 2009-09-02
i followed the instructions for smplayer here

[http://ubuntuforums.org/showthread.php?t=1081070&highlight=mplayer+jaunty](http://ubuntuforums.org/showthread.php?t=1081070&highlight=mplayer+jaunty) 

was able to play/watch dvd's 

>  Your best bet would be to search the forums before you ask a question. This one has been answered many, many times -- including today.  

if you dont want to answer dont

---

### Post by kansasnoob on 2009-09-02
> **3rdalbum said:**
> Kansasnoob, when you're directing people to install the codecs from Medibuntu, you should tell them to install the "non-free-codecs" package rather than the "w32codecs" package.

w32codecs is not present on 64-bit - it's called w64codecs. The non-free-codecs package is present on 32-bit and 64-bit and will pull in the relevant w32/w64codecs package for your system.

Also, I tend to advise people to use Synaptic when they want to install ubuntu-restricted-extras, because then the Java license agreement comes up in a GUI dialog. If you just use apt-get, then the license agreement comes up in the text console, and a lot of people don't know that you have to press Tab to highlight the "I Agree" button.

Sorry to pick holes in your post, but we might as well make things as trouble-free for new users as possible :-)

Point well taken! I shouldn't have assumed that it was 32-bit.

I definitely agree that "we might as well make things as trouble-free for new users as possible".

Thanks for correcting me on that point!

---

