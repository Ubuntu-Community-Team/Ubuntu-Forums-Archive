---
title: "DVD Playback issues"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Nuu on 2009-01-24
Before you vent your frustration for having to answer another one of these questions, yes I have searched, and yes I did find other topics about the same thing, but they all had different solutions or more often than not no solutions at all.

Now I am not exactly a technical user of Ubuntu, but I will try and explain my problem as well as I possibly can. I tried to run just your average DVD which you get from the shop on my computer with Totem, which gave me the error 'could not read from resource'. So I went to look on the Multimedia & Video How-to, and followed all the instructions in part 1 and part 4. I tried running the DVD on gxine and VLC, but the sound was broken and the video reduced to occasionally flashing up random frames and whatnot. I tried 'de-interlacing' it, but with no luck.

If you need more information then you'll have to explain to me how to get at it. ;)

Cheers.

---

### Post by taurus on 2009-01-24
Are you trying to play a movie (DVD)?

Maybe this link helps, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

---

### Post by starcannon on 2009-01-24
Can you please post your:
```

sudo lshw -html > ~/Desktop/hardware.html 

```output here?

Lets see if you have acceleration as well:
```

glxinfo | grep direct

```If you have not yet done so be sure to add the medibuntu repositories:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

After the medibuntu repositories have been added then be sure to run:
```

sudo apt-get install ubuntu-restricted-extras

```Hang in there, DVD playback is not to rough, and we can get you rolling.

P.S. Ack my bad I forgot the -html flag in that first command, rerun it now that it is fixed. Sorry :(

---

### Post by llamabr on 2009-01-24
Hello.  Sounds like you had a bad first experience here.  Most people will not attack you for asking noobie type questions, and those who do are eventually shown the door.

I like vlc, too, but I use xine for dvd's.  I'm not familiar with totem, or that error.  Have you tried a few different DVD's?  What error do you get from xine?

---

### Post by Dr Small on 2009-01-24
> **Nuu said:**
> Before you vent your frustration for having to answer another one of these questions, yes I have searched, and yes I did find other topics about the same thing, but they all had different solutions or more often than not no solutions at all.


We are here to help you, no matter how many times the question has been asked. Some people experience different problems, so if you can't find a solution by some research, then you are welcome to present the problem to the community. But, just because you don't get any responses doesn't mean we don't wish to help. Sometimes there are questions that we are not experienced with and have no solution ;)

Try taurus' suggestion with Medibuntu. You may need to install libdvdcss2 in order to get things to work. VLC should work quite well with all DVDs. Never had a problem yet that wasn't codec related. Ogle is also another great player, but generally the players are just the frontend to the decoding/video output, so choosing a player is just based on what you like. :)

---

### Post by kansasnoob on 2009-01-24
Well, first of all, I have a good idea!

Start by saying what you've tried!

For watching DVD's I use Totem-Xine.

Of course I have libdvdcss2 installed from Medibuntu:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by kansasnoob on 2009-01-24
> **Nuu said:**
> Before you vent your frustration for having to answer another one of these questions, yes I have searched, and yes I did find other topics about the same thing, but they all had different solutions or more often than not no solutions at all.

Now I am not exactly a technical user of Ubuntu, but I will try and explain my problem as well as I possibly can. I tried to run just your average DVD which you get from the shop on my computer with Totem, which gave me the error 'could not read from resource'. So I went to look on the Multimedia & Video How-to, and followed all the instructions in part 1 and part 4. I tried running the DVD on gxine and VLC, but the sound was broken and the video reduced to occasionally flashing up random frames and whatnot. I tried 'de-interlacing' it, but with no luck.

If you need more information then you'll have to explain to me how to get at it. ;)

Cheers.

I just realized I was doing this the wrong way! You'll have to forgive us when we forget where we started.

So go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you mentioned what version of Ubuntu you were using I forgot, just remember to add the gpg key!

Beyond that I personally prefer Totem Xine! You'll find that in Synaptic as totem-xine.

But you'll find as many different preferences as there are users!

---

### Post by Nuu on 2009-01-25
Ah...well, I have a new development. I tried two other DVDs which I have, and they both work perfectly. It seems there was something wrong with the DVD, not my computer. Shan't be going to that shop again.

So sorry, and thanks anyway.

---

### Post by starcannon on 2009-01-25
> **Nuu said:**
> Ah...well, I have a new development. I tried two other DVDs which I have, and they both work perfectly. It seems there was something wrong with the DVD, not my computer. Shan't be going to that shop again.

So sorry, and thanks anyway.

Nuu;

Sadly its not a matter of which shop you purchase from, its the RIAA's paranoid obsession with piracy (they figure since they screw everyone, that everyone will screw them); so, that said, the keys change every so often and it takes a little for the OSS solution to catch up. If you really want a seamless experience with your copyrighted media, do consider the commercial solution (I assume Canonical gets a piece of the action); you can find a nice Official Ubuntu Commercial Solution here:
[http://shop.canonical.com/product_info.php?products_id=244](http://shop.canonical.com/product_info.php?products_id=244)
A very nice Commercial DVD Player (Highly Recommended for Your Situation; and, again I hope Canonical gets a bit of the action) is here:
[http://shop.canonical.com/product_info.php?products_id=243](http://shop.canonical.com/product_info.php?products_id=243)
These are retail commercial solutions; that will cost real dollars/euros/pounds and since I'm not a Stallmanite I have no trouble at all recommeding them.

GL and have fun.
Rob aka starcannon

---

