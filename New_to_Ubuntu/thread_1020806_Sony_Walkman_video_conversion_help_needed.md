---
title: "Sony Walkman video conversion help needed"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by squid68 on 2008-12-24
I have a 4 gB Sony Walkman digital media player and am currently using Gusty. I know I will be upgrading the distro sometime  before April but in the meantime I need some advice on converting avi and mov files to mp4.  I have seen numerous posts and I am confused.  I tried to install ffmpeg and when I entered the mp4ize command I got an error with ruby in the message and something about not finding the file when I was in the folder where it was. I completely removed it with synaptic in case I need to start again. I followed the install instructions and gee they did not work. Probably assumed everyone knows what is going on.  

I saw that Winff seems to be popular but I do not think it supports Gusty and I do not know if it needs to have ffmpeg installed for it to work. 

I downloaded handbrake which seems to be the program that will probably work for me but when I clicked on the file I got an error that said "error: dependency is not satisfiable: libc6."  Probably does not support Gusty.  I may just have to wait to try this when I  update the distro to a newer version but stuff should work with Gusty which is not that old.

So ffmpeg failed to work, the Winff install instructions are for Hardy, Intrepid and Jaunty, and Handbrake 0.9.3 will not even let me install it. 0-3. I welcome the suggestions. Thanks.

---

### Post by billgoldberg on 2008-12-24
> **squid68 said:**
> I have a 4 gB Sony Walkman digital media player and am currently using Gusty. I know I will be upgrading the distro sometime  before April but in the meantime I need some advice on converting avi and mov files to mp4.  I have seen numerous posts and I am confused.  I tried to install ffmpeg and when I entered the mp4ize command I got an error with ruby in the message and something about not finding the file when I was in the folder where it was. I completely removed it with synaptic in case I need to start again. I followed the install instructions and gee they did not work. Probably assumed everyone knows what is going on.  

I saw that Winff seems to be popular but I do not think it supports Gusty and I do not know if it needs to have ffmpeg installed for it to work. 

I downloaded handbrake which seems to be the program that will probably work for me but when I clicked on the file I got an error that said "error: dependency is not satisfiable: libc6."  Probably does not support Gusty.  I may just have to wait to try this when I  update the distro to a newer version but stuff should work with Gusty which is not that old.

So ffmpeg failed to work, the Winff install instructions are for Hardy, Intrepid and Jaunty, and Handbrake 0.9.3 will not even let me install it. 0-3. I welcome the suggestions. Thanks.


Use the instructions for winnff for hardy.

It should work for Gutsy.

And yes, you'll need ffmpeg installed for winnff to work.

In a terminal, do

```
sudo apt-get install ffmpeg
```

Then install winff.

---

### Post by zeronothing on 2008-12-24
you could give OGMRIP a try. it should be in the gutsy repository. so you can use synaptic to install it. I know the program will rip DVD to a media format like XviD, MP4, etc. I'm not sure if you can select a file and encode it. I have used the program before to transcode DVD's to XviD.

---

