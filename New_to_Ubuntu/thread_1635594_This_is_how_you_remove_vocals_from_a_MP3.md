---
title: "This is how you remove vocals from a MP3"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by suomalainen on 2010-12-02
Ubunteros,

Would anyone happen to know how you remove the vocals from a MP3???

MS-Windows enthusiasts need not apply!

Thanks

---

### Post by theDaveTheRave on 2010-12-02
A quick [google search]("http://www.google.com/search?client=ubuntu&channel=fs&q=remove+vocals+from+music&ie=utf-8&oe=utf-8") would have given you [this link]("http://www.labnol.org/software/tutorials/remove-vocals-song-mp3-music-instruments/1301/") as the first hit.


but I'm probably being overly nice to you.

---

### Post by suomalainen on 2010-12-02
Don't worry theDaveTheRave the Audacity program you pointed me to doesn't do what I need it to do.

By the way, you talk as if we have met before, but I don't know you at all? Do you usually get this way before a joyous holiday like Christmas and New Year? Normal people have a much more different feeling than that which you reflect.

I guess your anticipating a big lump of coal in your sock this year and feel real bad....

---

### Post by HermanAB on 2010-12-02
Sox of course.

Read the sox man page.  It is very easy to use.  Try a notch filter at 300Hz to 3kHz.

---

### Post by LowSky on 2010-12-02
Audacity is very versitile. suomalainen I would have another look at what theDave posted. Or completely explain what you need to do.

theDave is probably frustrated because people will often ask a question that is easily answered by asking the same question in a search engine. You were just as impersonal when you commented on it. Maybe theDave doesn't celebrate your holiday or maybe he had a bad day. We all get mad sometimes, including me, but don't take it out on the guy trying to help you no matter how snark their answer was.

---

### Post by mcduck on 2010-12-03
Now *that's* a great way to get people to help you.

Anyway, theDaveTheRave really did give you as good instruction for removing vocals as you can get, there really is no other way than using an equalizer to reduce the volume of the frequencies of human voice or trying to use the difference between left & right channel to find what stuff is played on absolute center (where vocals are usually mixed). And Audacity will do both just fine.

Don't expect perfect results, you are not going to get that no mater what tool you use. Especially music with instruments that use lots of the same frequencies with human voice will be pretty much impossible. Any tool will only be able to see a bunch of sound frequencies, there is no magical trick that would allow a program to detect what stuff belongs to what instrument after they have been mixed together.

---

### Post by NightwishFan on 2010-12-03
*Chews :popcorn: as he reads this thread*

I say Audacity as well. It has everything you need and a GUI to do it. Center Panning works wonders on most studio albums between 1995-2000.

---

### Post by suomalainen on 2010-12-03
@mcduck

Excuse me but how would you know if they are good instructions or not??? Also, you can keep your comments to yourself if you don't know 110% all the behind the scenes information!

Seems like you didn't even bother to look the video, because if you had, even here you would see that the vocals are still audible! And following the instructions that you state are so fantastic!?"!? or is it Finntastic?

Anyway, I did look for online methods as well as Linux methods to achieve what I wanted. Then when I post my question I'm told by one user that:

"but I'm probably being overly nice to you." and another member who apparently is a mind reader stated "theDave is probably frustrated because people will often ask a question that is easily answered by asking the same question in a search engine"

To be perfectly frank, I really don't want help if it's offered in hostile environment and one in which people are belittled!

---

### Post by mcduck on 2010-12-03
Because I'm a multimedia designer and work with audio material all the time, and even get paid for it? And I *did* watch the video.

Like I told you, there is no perfect way to remove some instrument or vocals from audio track once they are mixed together. It's just a bunch of audio frequencies and no program will be able to make difference between which things belong to a certain instrument.

Much the same thing as with images, you can't have a magical tool that removes a person from an image automatically and makes whatever was behind him to appear. The image is just a bunch of pixels and whatever was behind the person isn't even included in the image file. You can use all kinds of tricks to edit the persona but and draw new stuff in his place but that's not what was actually there and the result will never be same as if you had taken the picture without the person standing there in the first place.

In the same way all you can do with audio is to filter out some frequencies, which *will* affect all those frequencies, no matter if the sound was caused by singer or a guitar or something else. It's up to you how much you wish to filter out, you can reduce the frequencies to the point where the singing is completely inaudible but you'll end filtering out some of the instrument sounds as well. Or filter a bit less, with less damage to instrument sounds but probably leaving some of the vocals audible as well.

You can only get perfect result if you have an audio file where none of the instrument sounds contain same frequencies as human voice.

Apart from that, it's either the imperfect ways already described here, or trying to get the original studio recordings that aren't yet mixed together.

(I don't really care at all about whatever hostility there might be between you and theDaveTheRave, I just wanted to point out that he actually gave you as good answer as you can get, regardless of the tone of his post. So you should be thankful for that and ignore the tone, as I'd imagine you actually came here for the answer, not for kind words. The "Now that's a great way to get people to help you." in my post was actually related to your "Blah Blah Blah" answer to LowSky, who gave you a very polite answer.)

---

### Post by howefield on 2010-12-03
> To be perfectly frank, I really don't want help if it's offered in hostile environment and one in which people are belittled!

And to be even franker, it works both ways.

If you want to get some help, try again in a new thread, with one post jailed, and the general tone, this one is closed.

---

