---
title: "Why won't Lucid Lynx play DVDs?"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by FormatSeize on 2010-05-30
Title says it all.
I can not get DVDs to play at all. It says that it needs to search for a plugin that can make MoviePlayer play from a 'DVD Source', but it never finds it. I just get a message that says that it was not found.

I could play DVDs on Ubuntu 9.x (forgot at the moment), but now all of a sudden Ubuntu doesn't play DVDs anymore.

Any help?

---

### Post by Ozymandias_117 on 2010-05-30
You probably need libdvdcss2 [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by sandyd on 2010-05-30
> **FormatSeize said:**
> Title says it all.
I can not get DVDs to play at all. It says that it needs to search for a plugin that can make MoviePlayer play from a 'DVD Source', but it never finds it. I just get a message that says that it was not found.

I could play DVDs on Ubuntu 9.x (forgot at the moment), but now all of a sudden Ubuntu doesn't play DVDs anymore.

Any help?
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-get install libdvdcss2

```

during an upgrade, the ubuntu upgrade thingy disables medibuntu, which has your dvd support.

The above commands will reenable it.

---

### Post by scottishbloke on 2010-05-30
If i was you mate id move to Linux Mint as it comes preinstalled with all the codecs to play dvds, Its what ive done, Lucid Lynx Suck's.

---

### Post by Ozymandias_117 on 2010-05-30
> **scottishbloke said:**
> If i was you mate id move to Linux Mint as it comes preinstalled with all the codecs to play dvds, Its what ive done, Lucid Lynx Suck's.

Linux Mint is just Lucid Lynx with ubuntu-restricted-extras and libdvdcss2 installed. Also, it wouldn't be "Suck's" because "Suck" doesn't own anything, and since "Suck" isn't a noun, it would be "sucks".

---

### Post by sandyd on 2010-05-30
> **Ozymandias_117 said:**
> Linux Mint is just Lucid Lynx with ubuntu-restricted-extras and libdvdcss2 installed. Also, it wouldn't be "Suck's" because "Suck" doesn't own anything, and since "Suck" isn't a noun, it would be "sucks".
win :D

---

### Post by FormatSeize on 2010-05-30
> **carlee said:**
> ```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-get install libdvdcss2

```during an upgrade, the ubuntu upgrade thingy disables medibuntu, which has your dvd support.

The above commands will reenable it.
I've tried this, and the following is what I get
```
Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.

Please install the necessary plugins and restart Totem to be able to play this media.
```It still seems to be missing something...

---

### Post by philinux on 2010-05-30
Lets keep on topic and civil guys.

---

### Post by proggy on 2010-05-30
> **FormatSeize said:**
> I've tried this, and the following is what I get
```
Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.

Please install the necessary plugins and restart Totem to be able to play this media.
```It still seems to be missing something...
Have you tried with an other media player like Vlc for instance

---

### Post by xaegis on 2010-05-30
...

---

### Post by germanix on 2010-05-30
copy paste the following. The first command in one line:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list
Did you remember the enter key? Good, then let's continue with this line:&#8232;
 sudo apt-get --quiet update
Followed by this line here: (then enter key)&#8232;
 sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring
And finally this important step (four more after this):&#8232;
 sudo apt-get --quiet update
Starting with the next line we'll be installing the actual playback codecs:&#8232;
 sudo apt-get install non-free-codecs
Let's not forget about DVD playback support:&#8232;
 sudo apt-get install libdvdcss2
Some needed Windows related codecs:&#8232;
 sudo apt-get install w32codecs
And finally, installation of codecs into the multimedia players:&#8232;
 sudo apt-get install vlc mplayer

---

### Post by FormatSeize on 2010-05-30
> **proggy said:**
> Have you tried with an other media player like Vlc for instance
No.
Where do I find it? I'm willing to give it a try.

---

### Post by Guitar John on 2010-05-30
> **carlee said:**
> [

the ubuntu upgrade thingy 

:mrgreen:

---

### Post by clhsharky on 2010-05-30
FormatSeize

Have you also installed ( ubuntu-restricted-extras )?

Sharky

---

### Post by blagosphere on 2010-05-30
ozymandias had the fix that worked for me.

---

### Post by FormatSeize on 2010-05-30
vlc works for me.

Thanks everyone!

---

### Post by Rocko262c on 2011-01-15
Dear Everyone,

I have the same problem with more than one computer after fresh installs of Ubuntu 10.10.  I have followed all the advice of installing everything in here except to install Linux Mint.

I can't play any DVD's from any region on my computers.  Again, I have followed all the advice above.

Anyone else suggest anything?

Cheers,
Rocko262c

---

### Post by Brad55 on 2011-01-15
> **Rocko262c said:**
> Dear Everyone,

I have the same problem with more than one computer after fresh installs of Ubuntu 10.10.  I have followed all the advice of installing everything in here except to install Linux Mint.

I can't play any DVD's from any region on my computers.  Again, I have followed all the advice above.

Anyone else suggest anything?

Cheers,
Rocko262c
 Try this,

First, open your terminal: put this into it **sudo apt-get install ubuntu-restricted-extras**

Next, put this in the terminal **sudo apt-get install libdvdcss2**

Next, put this in the terminal **sudo /usr/share/doc/libdvdread4/install-css.sh**

---

### Post by Illustratedman45 on 2011-01-20
> **Brad55 said:**
> Try this,

First, open your terminal: put this into it **sudo apt-get install ubuntu-restricted-extras**

Next, put this in the terminal **sudo apt-get install libdvdcss2**

Next, put this in the terminal **sudo /usr/share/doc/libdvdread4/install-css.sh**

Brad55 - you're the man! This did the trick for me. I recently installed Peppermint 10.10 and everything seemed to working fine until I tried a movie DVD and the players (Gnome player and VLC) would start to play then stop. I googled this problem and came across this thread and your solution. Much appreciated. :D

---

### Post by Brad55 on 2011-01-22
> **Illustratedman45 said:**
> Brad55 - you're the man! This did the trick for me. I recently installed Peppermint 10.10 and everything seemed to working fine until I tried a movie DVD and the players (Gnome player and VLC) would start to play then stop. I googled this problem and came across this thread and your solution. Much appreciated. :D


np glad to help. I know I have had a time getting DVD's and MP3's play in the past so I always find the easy way and the fastest.

---

