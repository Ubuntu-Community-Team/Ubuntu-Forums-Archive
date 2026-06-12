---
title: "Not a complaint - just a lament....... still no movies"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by mistypotato on 2010-10-28
As of 9.10 I still can't put a DVD movie into my DVD drive and get it to play.

Unlike windowsXP which is now about a decade old...I put a DVD movie in the drive and it just plays.

By no means a deal breaker for me.  I love and USE ubuntu 85% of the time and it's stable as all get out.   But it would be nice.   Maybe someday :)

I wonder if this is still the case in 10.10 ????

---

### Post by krzysz00 on 2010-10-28
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) (look there)

---

### Post by Spice Weasel on 2010-10-28
Patent issues. When you pay for Windows part of the cost goes to the people that own the patents for DVD playing.

---

### Post by TriBlox6432 on 2010-10-28
If you don't mind having non-free software on your computer:

```

sudo apt-get install ubuntu-restricted-extras

```

Also, I recommend VLC for a media player.  It can play any format thrown at it, as long as proper codes are installed (ubuntu-restricted-extras will take care of that)

---

### Post by 73ckn797 on 2010-10-28
Follow the info on this link:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

It may help.

---

### Post by mistypotato on 2010-10-31
I ended up installing gxine and all the non-free plugins and now I can play movies with no problem.

VERY nice clarity and sound btw.

But...when does the bill arrive?  I didn't pay and yet it installed and works?

---

### Post by trikster_x on 2010-10-31
Well....

Some of the non-free bits and restricted stuffs can be a little on the less than legal side, depending on where your location is.  Most of the codecs and encryption keys are copyrighted and require licensed software or hardware for playback, which most of the programs available in Ubuntu's package list aren't, hence the "restricted" extras.  Even your lovely cd drive isn't actually licensed for playback of media, rather it is made specifically for accessing data.  That is why media player software is necessary to play music cd's.

---

### Post by 73ckn797 on 2010-10-31
> **mistypotato said:**
> But...when does the bill arrive?  I didn't pay and yet it installed and works?

I have not received any bills!

---

### Post by Chronon on 2010-10-31
> **mistypotato said:**
> I ended up installing gxine and all the non-free plugins and now I can play movies with no problem.

VERY nice clarity and sound btw.

But...when does the bill arrive?  I didn't pay and yet it installed and works?

You can purchase the Fluendo DVD Player app from the Software Center if you so desire.  Personally, I don't think this is necessary since I have already paid a license fee to play DVDs on my box by paying for Windows.  If your box doesn't have an associated Windows license then it's a tad more ambiguous (depending on locality).

I am not a lawyer and I do not offer legal advice.  I'm only telling you my thoughts regarding my own situation.

---

### Post by mikewhatever on 2010-10-31
> **TriBlox6432 said:**
> If you don't mind having non-free software on your computer:

```

sudo apt-get install ubuntu-restricted-extras

```

Also, I recommend VLC for a media player.  It can play any format thrown at it, as long as proper codes are installed (ubuntu-restricted-extras will take care of that)

Ubuntu-restricted-extras does not provide DVD decoding capabilities, nor does VLC.
One way of obtaining it is as follows:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Despite the above, I wouldn't be too surprised if some DVD still refused to play, since DVD makers has gone out of their ways to make decoding hard.

---

### Post by dizzle1234 on 2010-10-31
I thought VLC plays movies out-of-the-box... :confused:

---

### Post by Verbeck on 2010-10-31
i thought vlc had its own decoders...

> **mikewhatever said:**
> Despite the above, I wouldn't be too surprised if some DVD still refused to play, since **DVD makers has gone out of their ways to make it decoding hard**.

out of the topic:
too true.one time, a dvd i bought had a virus on it. r0something.exe. kept the machine restarting in every boot (until safe mode fixed it). AND the cover said they wont be responsible for what damage the dvd would cause to a computer system. who is to blame?

---

### Post by mikewhatever on 2010-10-31
> **dizzle1234 said:**
> I thought VLC plays movies out-of-the-box... :confused:

No, at least not in Ubuntu. The package needed to read encrypted (or as they call it, scrambled) DVDs comes from the unofficial Medibuntu repository. The restricted-extras package pulls in various gstreamer plugins as well as jave MS fonts, and other unrelated stuff.

---

