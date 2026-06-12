---
title: "Major sound issues...."
date: 2009-09-16
forum: New to Ubuntu
---

### Post by dreadbuntu on 2009-09-16
ok, so I have no sound what so ever since I switched from windows xp.  I've tried everything I could find in the forums and in troubleshooting.  I could be messing it up though as I am a complete beginner on ubuntu.  Please help me someone... I've been at this for twenty hours now.....  (not in a row :P)
thanks

---

### Post by Dermot Doyle on 2009-09-16
This may be of limited help, but I have had huge sound problems as well. I have a Dell preloaded with Ubuntu 8.04. Every time I upgraded to a new kernel the sound never worked no matter what I did or what thread I followed, mine or someone elses. Finally I stuck with the original kernal which is 2.6.24-19 and the sound works perfectly. Maybe an older kernal will work for you.
Also you may want to add to your thread title the computer you have and the version of Linux you are using in case someone with a similar problem has managed to solve it.
Good luck

---

### Post by dreadbuntu on 2009-09-17
aaaaaaaaahhhhhhhhh!!!!   I'm just gonna start over!   thanks for your help....  the problem may be that I have a very ancient sound card......  blah.   I don't really understand this whole kernel thing....   this is a bit frustrating... lol

---

### Post by sydbat on 2009-09-17
What version of Ubuntu are you using? 8.04 (Hardy)? 8.10 (Intrepid)? 9.04 (Jaunty)? Knowing this will help us help you.

Also, what are the specs for your computer? Is it a desktop or laptop? What processor, ram, sound device(s)?

The more info we get from you, the easier it is to diagnose and assist.

---

### Post by dreadbuntu on 2009-09-17
ok, so I'm using 8.04.....  it is a desktop.... very old computer but other then the sound it is working ok.... a teeny bit slow though....  it's an IBM  pentium 3...  and I'm not sure about the ram......  I just got this computer as a hand me down.   the sound card is allegro  something.  forgive my lack of knowledge, sometimes I think I know more then I do.....

---

### Post by sydbat on 2009-09-17
OK. Go to System > Preferences > Sound. On the Devices tab there are options to choose your sound software (ALSA, OSS, PulseAudio, etc). There are also Test buttons next to each choice.

The default is Autodetect, but I have found that it does not always work the best (it is *supposed* to choose the best one). I use the ALSA option on my Hardy (8.04) install and it seems to work pretty good.

Let us know what happens.

---

### Post by dreadbuntu on 2009-09-17
ok, so I have already done that.....  all I hear when I run the tests is a very faint humming noise.....

---

### Post by shae on 2009-09-17
Could you open a terminal and use the following command:

```
lspci
```

and past the output for us?

---

### Post by Maheriano on 2009-09-17
Upgrade to 9.1 and it should work. It has Pulse Audio fixes that 8.04 never did.

---

### Post by LewRockwell on 2009-09-17
just find a new box...

or find new/newer parts to put in the box...

used equipment is cheap/free/found-at-the-curb around here...

.

---

### Post by LewRockwell on 2009-09-17
craigslist

+ 1

.

---

### Post by dreadbuntu on 2009-09-17
ok, this is what I got.....  when i typed lspci...

00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:02.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 12)
00:02.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:02.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 08)
00:02.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 20)
00:0e.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
00:12.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

---

### Post by LewRockwell on 2009-09-17
also...since we're talking about sound...

remember that there is a difference between amplified and un-amplified outputs

sometimes a soundcard will have BOTH

in that case there will be an amplified speaker output

and an un-amplified signal output

in some cases the un-amplified output can still produce sound in headphones and small/micro speakers

as always, your mileage may vary, buyer beware, and buyer be aware

we now return you to your regularily scheduled programming

.

---

### Post by LewRockwell on 2009-09-17
> 00:12.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)we've dealt with those before and honestly don't remember if we ever got one working

.

---

### Post by shae on 2009-09-17
Check out this post: [http://ubuntuforums.org/showthread.php?t=147576](http://ubuntuforums.org/showthread.php?t=147576)

---

### Post by dreadbuntu on 2009-09-18
Thanks for all of the help.  It appears my sound works when I put in a cd and play it... but no other times....  maybe it's just a problem with my codecs for my media player........  any insight on this?   I checked out that post... I had already tried that one.  
thanks again!

---

### Post by dreadbuntu on 2009-09-18
Success!!!  I don't know what fixed my problem.....  maybe it fixed itself overnight.... or  I turned up ALL of the sounds on alsamixer..... or I removed one of my media players cause apparently I had 2 totem players....  or when I originally installed flash player it screwed it up so, I removed it......   but now it works.... so who knows what fixed it... maybe one of you do?

---

