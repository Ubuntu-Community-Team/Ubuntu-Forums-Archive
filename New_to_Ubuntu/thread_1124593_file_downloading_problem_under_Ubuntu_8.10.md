---
title: "file downloading problem under Ubuntu 8.10"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Ubunser on 2009-04-13
Hello! I installed Ubuntu 8.10 a week ago, and one of many questions I've got is simply how to download files. When clicking on mp3 download link I was astonished to see it started to play it in browser. But firstly, I want to save a file, secondly, the playback was ugly: the playback was abrupt and the sound volume jittered up and down.

Then I typed in terminal 'sudo aptitude install gwget'. But yet it got no better. The download process stuck on zeroes, the modem indicator was blinking to say it's downloading, but the sound was same as in browser. 

After file extension .mp3 there goes "(invalid encoding)".  I hope there is somebody to help me with this. One more thing, this problem occurs only when downloading new .mp3, and they contain a lot of "%*%" or something like this and the url is very long. Those .mp3 that I already have (transmitted from Windows) work fine. Thanks if anybody knows.

---

### Post by mhh91 on 2009-04-13
try right-clicking on the link and choosing "save link as" :)

---

### Post by halitech on 2009-04-13
right click - save link as should work or you can use ```
wget url/to/file
``` in a terminal if that doesn't work. Just make sure you are on the right page to actually get the correct link.

---

### Post by Ubunser on 2009-04-13
Thanks that worked! Yet what's the problem using gwget, it is supposed to work.

---

### Post by halitech on 2009-04-13
its possible that gwget is having trouble with the spaces (all the 20% in the file name) so its not downloading. Not sure as I don't use gwget.

if you have a link I'm sure someone could give it a shot to see what happens.

---

### Post by Ubunser on 2009-04-13
here it is

[http://www.tcciband.com/TCCI_Slow_Internet/%d3%f7%e5%ed%e8%e5%202009%20MP3%2024/%cc%e0%f2%e5%f0%e8%e0%eb%20%f1%ee%f1%f2%e0%e2%eb%ff%fe%f9%e8%e9%20%f7%e5%ec%ef%e8%ee%ed%e0.mp3](http://www.tcciband.com/TCCI_Slow_Internet/%d3%f7%e5%ed%e8%e5%202009%20MP3%2024/%cc%e0%f2%e5%f0%e8%e0%eb%20%f1%ee%f1%f2%e0%e2%eb%ff%fe%f9%e8%e9%20%f7%e5%ec%ef%e8%ee%ed%e0.mp3)

---

### Post by Ubunser on 2009-04-13
Also when download finished (using 'Save link as') it was of bad quality as before. Oops

and this is the major problem...

---

### Post by halitech on 2009-04-13
wget [http://www.tcciband.com/TCCI_Slow_Internet/%d3%f7%e5%ed%e8%e5%202009%20MP3%2024/%cc%e0%f2%e5%f0%e8%e0%eb%20%f1%ee%f1%f2%e0%e2%eb%ff%fe%f9%e8%e9%20%f7%e5%ec%ef%e8%ee%ed%e0.mp3](http://www.tcciband.com/TCCI_Slow_Internet/%d3%f7%e5%ed%e8%e5%202009%20MP3%2024/%cc%e0%f2%e5%f0%e8%e0%eb%20%f1%ee%f1%f2%e0%e2%eb%ff%fe%f9%e8%e9%20%f7%e5%ec%ef%e8%ee%ed%e0.mp3) 

worked for me, other then it having no idea what most of the chacarters were in the file name so I have a file called ???????? ???????????? ????????.mp3 on my desktop. When I highlight your link, I see a lot of characters that aren't in english so maybe thats where gwget is having the issue.

---

### Post by Jakey_TheSnake on 2009-04-13
The bad quality will be down to the file you download, nothing to do with Ubuntu, firefox or wget.

---

### Post by halitech on 2009-04-13
> **Ubunser said:**
> Also when download finished (using 'Save link as') it was of bad quality as before. Oops

and this is the major problem...

it looks like you are linking to a file in the "slow internet" folder so maybe they have a higher quality file for those with a higher speed connection that you can check for.

---

### Post by Ubunser on 2009-04-13
It think I didn't get what you meant but here what actually is in the link: %ed%e8%e5%202009%20MP3%2024/%c and more of this. There couldn't be characters other than latin.

---

### Post by Ubunser on 2009-04-13
wow that's wierd. Yes when I the the other variant for this file, which is offered for fast connections (I have typically 15-20 kb/s) it was of good quality and even doesn make pauses. Thanks

---

### Post by Jakey_TheSnake on 2009-04-13
[http://tcciband.com/TCCI_Fast_Internet/](http://tcciband.com/TCCI_Fast_Internet/)

Is the FTP site for you to download your song from. I would give you the link, but I don't speak Russian *shrugs*

---

### Post by halitech on 2009-04-13
> **Ubunser said:**
> It think I didn't get what you meant but here what actually is in the link: %ed%e8%e5%202009%20MP3%2024/%c and more of this. There couldn't be characters other than latin. 

check out my screenshot in the lower left corner

---

### Post by halitech on 2009-04-13
> **Jakey_TheSnake said:**
> [http://tcciband.com/TCCI_Fast_Internet/](http://tcciband.com/TCCI_Fast_Internet/)

Is the FTP site for you to download your song from. I would give you the link, but I don't speak Russian *shrugs*

is that the language its in?  would explain why my system doesn't recognize all the characters

---

### Post by Ubunser on 2009-04-13
halitech, yes I saw your screenshot. I have no idea why this is so

---

### Post by halitech on 2009-04-13
I'm thinking the file name is in something other then english so my system is guessing at what the letters are

---

### Post by Jakey_TheSnake on 2009-04-13
> **halitech said:**
> I'm thinking the file name is in something other then english so my system is guessing at what the letters are

I went to the main tcciband site, and used the page translate feature of Google, from Russian > English and it worked (first guess, I might add). I used to know a Russian at school, so I guess that helped.

---

### Post by halitech on 2009-04-13
that would work to read the site but I dont think a translation would work for doing the actual download but I could be wrong.

---

### Post by Jakey_TheSnake on 2009-04-13
You misunderstand me, I was merely navigating the site to try and navigate to the "Fast Internet" bit, as I guessed it wouldn't be as intuitive as merely changing the word "slow" to "fast" - and to do that I needed to translate the page; thus finding out what the language was.

---

### Post by halitech on 2009-04-13
ahh, got ya now :)

---

### Post by Ubunser on 2009-04-13
Although fast connestion work for me now, but I would preffer to use slow, cause it is less Megabytes. Under Windows I always used "slow"

---

### Post by Jakey_TheSnake on 2009-04-13
> **Ubunser said:**
> Although fast connestion work for me now, but I would preffer to use slow, cause it is less Megabytes. Under Windows I always used "slow"

It's less MB because the quality is lower. You can't have your cake and eat it!

[quote="halitech"]ahh, got ya now :)[/quote] 

Good good :) 

Also, what happened to the 'Thanks' and 'Solved' system, and why? I just came back and it had gone :(

---

### Post by Ubunser on 2009-04-13
> **Jakey_TheSnake said:**
> It's less MB because the quality is lower. You can't have your cake and eat it!
 :(

These are not songs, but pastor preaching, so I'm not bound to quality, I just need the essence.

---

### Post by Jakey_TheSnake on 2009-04-13
> **Ubunser said:**
> These are not songs, but pastor preaching, so I'm not bound to quality, I just need the essence.

Then, my good sir, I am with you.

---

### Post by halitech on 2009-04-13
> **Jakey_TheSnake said:**
> Also, what happened to the 'Thanks' and 'Solved' system, and why? I just came back and it had gone :(

I believe they took both offline as part of an upgrade but I haven't seen either come back as of yet.

---

