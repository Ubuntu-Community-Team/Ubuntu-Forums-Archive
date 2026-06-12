---
title: "[SOLVED] convert"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by DarinB on 2008-12-15
How do i convert a wmv to mov or something that a friend can view a clip on her mac.
i have winff gui for ffmpeg, but i don't have an option to convert wmv to anything except wmv2??????

---

### Post by BlackS3th on 2008-12-15
Quick replie plz.... Random question ... How do i create a thread ... I would thank youu if yo told me

---

### Post by howefield on 2008-12-15
Why doesn't your friend download VLC (media player) and use that to play the WMV ?

PS.
Come to think of it, isn't there a Windows Media Player for Mac ?

---

### Post by Sarmacid on 2008-12-15
I have converted from many formats to avi using mencoder. I would guess that either you can use it to convert to .mov or she can watch .avi

---

### Post by DarinB on 2008-12-15
Where do i get mencoder.
And regarding the post that she download vlc. she is totally unable to do that and i in noway want to cross that bridge of helping her to mess things up.

---

### Post by Michael.Godawski on 2008-12-15
> **Re: convert**
 		Quick replie plz.... Random question ... How do i create a thread ... I would thank youu if yo told me 	

hey, 
while being at the absolute beginner talk main page, with all the treads look for a gray square button, with new thread on it. :p left upper side of the screen.

---

### Post by Sarmacid on 2008-12-15
> **DarinB said:**
> Where do i get mencoder.
Easy
```
sudo apt-get install mencoder
```

---

### Post by albinootje on 2008-12-15
Installing vlc on the mac sounds like a good plan :)
I know several macosx users and almost all of them they tell me (before i even start about open source software) about vlc and how much they like it!

---

### Post by howefield on 2008-12-15
> **DarinB said:**
> And regarding the post that she download vlc. she is totally unable to do that and i in noway want to cross that bridge of helping her to mess things up.

Yeah, I hear you :)

It might be an issue for the same reason, but it is really easy these days take control remotely and do the install yourself. eg TeamViewer is a great app with which is free for home use, and seems break through all routers and configurations with ease, and doesn't even need to be installed. Great way to help novice users.

Just putting it forward, not just for you but for anyone reading.

---

### Post by silverglade00 on 2008-12-15
I second the [Teamviewer]("http://www.teamviewer.com") recommendation. We use it here at my work to troubleshoot all over campus. It works great and they just came out with version 4. The free version is identical to the paid version. The only difference is the paid version comes with support. You don't get a crippled home version. In my experience, it always runs faster than Remote Desktop. Best of all, it runs in Wine with zero extra configuration. It's fun moving someone's Windows desktop around with wobbly windows :)

---

### Post by FakeOutdoorsman on 2008-12-15
> **DarinB said:**
> How do i convert a wmv to mov or something that a friend can view a clip on her mac.
i have winff gui for ffmpeg, but i don't have an option to convert wmv to anything except wmv2??????
You can just skip WinFF and try ffmpeg itself:
```
ffmpeg -i input.wmv -sameq output.mov
```
The sameq option will adjust the bitrate of the output video to relatively match the same quality as the input video.

---

