---
title: "A question for the developers of ubuntu"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by mdraicch on 2009-01-28
I have been using 8.10 because 8.04 became unstable.  Recently 8.10 became unstable and the machine would turn itself off while encoding video, either with avidemux or devede.

So, I downloaded and installed linux mint, which is based on 8.10.

With 8.10, before it became unstable, i would get a frame rate of around 30 per second with avidemux.  With linux mint I now get around 80 fps.

Why is this so??

Regards
Muzza

---

### Post by igknighted on 2009-01-28
If you want to contact the devs, you should use launchpad.  Developers rarely (if ever) use the forums.

As for your question, there are way to many factors, but the most likely would be the video card driver used.  Any idea what card you have, and what driver you used in 8.10 and Mint?  Oh... and what version of Mint?

---

### Post by mdraicch on 2009-01-28
> **igknighted said:**
> If you want to contact the devs, you should use launchpad.  Developers rarely (if ever) use the forums.

As for your question, there are way to many factors, but the most likely would be the video card driver used.  Any idea what card you have, and what driver you used in 8.10 and Mint?  Oh... and what version of Mint?

Thanks igknighted i am using a gigabyte mobo with an integrated ati 3200, with the fglrx driver, on linux mint 6.

I think that might be the difference, the latest ati driver is 8.12, which I used with 8.10, but I think mint uses 8.5.

I think I'll reload 8.10, and load 8.5 or the oldest driver I can get and see what happens.

Regards
muzza

---

### Post by kestrel1 on 2009-01-28
Trying to encode video with an integrated Video card is not going to work.
You really need a good quality card with plenty of RAM on board.
I would think a minimum of 128mb on the video card & you need a good processor & a good amount of RAM 2gb or more.

---

### Post by hyper_ch on 2009-01-28
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by GepettoBR on 2009-01-28
> **kestrel1 said:**
> Trying to encode video with an integrated Video card is not going to work.
You really need a good quality card with plenty of RAM on board.
I would think a minimum of 128mb on the video card & you need a good processor & a good amount of RAM 2gb or more.

I have encoded video on a single-core, 1.3GHz Centrino laptop with an integrated ATI Radeon GPU that had only 32MB of video RAM and 768MB of regular RAM for five years until I upgraded just recently.  It took ages, but it was completely possible.

---

### Post by kestrel1 on 2009-01-28
> **GepettoBR said:**
> I have encoded video on a single-core, 1.3GHz Centrino laptop with an integrated ATI Radeon GPU that had only 32MB of video RAM and 768MB of regular RAM for five years until I upgraded just recently.  It took ages, but it was completely possible.
I have encoded video on similar spec to the above, but with a video card that had 64mb RAM. It will encode, but can be very slow & choppy.
Integrated video is no good for serious video encoding.

---

### Post by GepettoBR on 2009-01-28
> **kestrel1 said:**
> I have encoded video on similar spec to the above, but with a video card that had 64mb RAM. It will encode, but can be very slow & choppy.
Integrated video is no good for serious video encoding.

I agree that it isn't good. In fact, it's horrible. But you said it wouldn't work, and it will - albeit poorly.

---

### Post by kestrel1 on 2009-01-28
Yes, point taken. I meant to say it will not work very well.

---

### Post by mdraicch on 2009-01-28
Thankyou for your reply guys, but I must admit that I am confused.  I was under the impression that the video card was only useful in encoding if the encoding process could be offloaded to the gpu, otherwise I thought that the video card simply displays.

How is it that it matters what video card I have to the encoding process???

Regards
muzza

---

### Post by GepettoBR on 2009-01-28
> **mdraicch said:**
> Thankyou for your reply guys, but I must admit that I am confused.  I was under the impression that the video card was only useful in encoding if the encoding process could be offloaded to the gpu, otherwise I thought that the video card simply displays.

How is it that it matters what video card I have to the encoding process???

Regards
muzza

You are correct in your assumption. Modern encoders, however (H.264/MPEG-4 AVC, for example) offload to the GPU if possible. If not, they pound harder on the CPU, which can lead to instability and dramatically lowers speed. If you're encoding with older standards, however (XviD, MPEG-2, etc) then the very presence of a GPU is almost meaningless, unless you have some sort of wrapper that sends the encoder's calls to the GPU.

---

### Post by mdraicch on 2009-01-29
> **GepettoBR said:**
> You are correct in your assumption. Modern encoders, however (H.264/MPEG-4 AVC, for example) offload to the GPU if possible. If not, they pound harder on the CPU, which can lead to instability and dramatically lowers speed. If you're encoding with older standards, however (XviD, MPEG-2, etc) then the very presence of a GPU is almost meaningless, unless you have some sort of wrapper that sends the encoder's calls to the GPU.

Thankyou so much for your reply.

Best Regards
Muzza

---

### Post by jerome1232 on 2009-01-29
> **mdraicch said:**
> I have been using 8.10 because 8.04 became unstable.  Recently 8.10 became unstable and the machine would turn itself off while encoding video, either with avidemux or devede.


My first thought when reading this is your processor is overheating and your system is shutting itself down.

---

### Post by egalvan on 2009-01-29
> **jerome1232 said:**
> My first thought when reading this is your processor is overheating and your system is shutting itself down.

I totally agree, this waddles and quacks like a duck...

Open the case and check for dust-bunnies.
Remove any heat-sinks and check for properly-applied paste.
Remember the PSU; too often it is totally ignored.

I would run conky (or similiar) to check temps.

ErnestG

---

