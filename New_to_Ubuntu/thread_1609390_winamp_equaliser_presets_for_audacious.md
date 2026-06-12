---
title: "winamp equaliser presets for audacious"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by dhiman33 on 2010-10-30
In ubuntu 10.04, I could easily install winamp equaliser presets for audacious using these steps---

**Step 1**: Download the Winamp equalizer presets using the following command in your terminal:


wget [http://www.beastwithin.org/users/wwwwolf/code/xmms/winamp_presets.gz](http://www.beastwithin.org/users/wwwwolf/code/xmms/winamp_presets.gz)

**Step 2**: Import the downloaded Winamp equalizer presets into Audacious, using the command as follows:


gunzip -c winamp_presets.gz > ~/.config/audacious/eq.preset

](*,)Now it doesn't work.The file is downloaded and no error message is shown. Still nothing shows in preset list of audacious.[-( 
Any solution?

---

### Post by dhiman33 on 2010-11-02
:evil:Why no one answered!!! I've solved it by the worst method. Went to windows,changed winamp presets one by one,saved them as eqf files,booted to ubuntu, opened audacious,installed all the files one by one as presets. It took a LOTS of time to do all these.Just try and see!:-\"

---

### Post by pedal2themedal on 2010-11-17
Could you upload the updated presets? I am having the same issue. It must have something to do with the updated Ubuntu. I had to spend hours getting my headphones to work yesterday. Oh well, that is what I get for updating before the bugs are worked out, but I guess maybe my bug will help somebody else out.

Thanks, Robert

---

### Post by dhiman33 on 2010-11-20
):PSorry for delay, pedal2themedal,actually for the last 2 days I'm seeing some "site down for maintenance" message whenever trying to enter ubuntuforums.org. Today that message still exists, but when I tried "ubuntuforums.org/index.php", it opened like a charm! Are u having same problems?

Ok, here I'm attaching eq.preset file of mine(compressed). U xtract it, and then overwrite .config/audacious/eq.preset with it, and enjoy!!:guitar:

Let me know if this works for u, and also inform if u someday find an easir way to do this.Bye bye!:lolflag:

---

### Post by pedal2themedal on 2010-11-20
> **dhiman33 said:**
> ):PSorry for delay, pedal2themedal,actually for the last 2 days I'm seeing some "site down for maintenance" message whenever trying to enter ubuntuforums.org. Today that message still exists, but when I tried "ubuntuforums.org/index.php", it opened like a charm! Are u having same problems?

Ok, here I'm attaching eq.preset file of mine(compressed). U xtract it, and then overwrite .config/audacious/eq.preset with it, and enjoy!!:guitar:

Let me know if this works for u, and also inform if u someday find an easir way to do this.Bye bye!:lolflag:

No problem!! I am not having problems getting in to Ubuntu, but I use specific links to get to the exact threads I am looking for. As for the presets, they still aren't working

---

### Post by pedal2themedal on 2010-11-20
Scratch that, It doesnt work trying to put it in to Audacious via the loader in the program, but if I manually put it in the /.config/audacious/ file as eq.preset, then it works like a charm. Thanks a lot!! I listen to a lot of rock, and I just cant seem to synthesize the correct sound. Thanks again, Robert

---

### Post by dhiman33 on 2010-11-21
:confused:Who is Robert!@#$!

---

### Post by pedal2themedal on 2010-11-22
> **dhiman33 said:**
> :confused:Who is Robert!@#$!

That is my name, lol, pedal2themedal is just my "handle."

---

### Post by Drone4four on 2012-03-18
I was trying to get Audacious to recognize Winamp equalizer presets following this guide [[COLOR="Red"]_here_[/COLOR]]("http://www.mytechguide.org/8210/how-to-import-winamp-equalizer-preset-into-linux-audio-players-like-audacious-xmms-etc/?utm_source=feedburner&utm_medium=twitter&utm_campaign=Feed%3A%20MyTechnologyGuide%20%28My%20Technology%20Guide%29"). However, I ran into this error: ```
Error importing Winamp EQF file file:///home/USER/eq.preset
```  Special thanks goes out to dhiman33 for kindly sharing the Winamp presets that he copied one by one and saved them as eq files and shared them here.  You solved my problem for me. Thanks again,dhiman33!

---

### Post by NHH on 2012-03-21
Just Reload de program... it works for me.

---

### Post by dlsym on 2012-03-24
Thanks for the effort and upload Diman33!!

---

### Post by legendavey on 2012-04-07
thank you dhiman33. worked for me. :KS

---

### Post by israsta on 2012-06-07
Muchas gracias [dhiman33]("http://ubuntuforums.org/member.php?u=1176117")  !!!

---

### Post by KayeNg on 2012-12-25
Hey guys. I did the overwriting already.  So how do I see the presets in audacious?

Edit: I get it. I should use the winamp skin to use the presets.  

How about scaling? Is there a way to make the winamp interface bigger? It's too small.

Thanks!

---

### Post by dvanzo on 2013-01-14
Worked like a charm!!! Thanks so much!

Daniel

---

### Post by acidpeople on 2013-01-26
**dhiman33**

:D:D Thank you so much! Work good in audacious in Kubuntu 12.10!!! Sorry for my bad English.

---

### Post by Merrattic on 2013-01-26
Not working here at all

---

### Post by mannu3081 on 2013-03-13
Great help Dhiman33..... works for me....:guitar:

---

### Post by aLeXoR on 2013-04-10
Great Thank's!
...Oh, guys! There are all works with no errors if one uses CORRECT decimal point delimeter in default PRESET file (~/.config/audacious/eq.preset), i.e. default may be dot (.) or comma (,) //as for me: Audacious ver.3.2.4 (.) ;)

---

### Post by faeyin on 2013-06-13
Thanks !  So far this workaround was the only thing that worked for me. 

> **dhiman33 said:**
> ):PSorry for delay, pedal2themedal,actually for the last 2 days I'm seeing some "site down for maintenance" message whenever trying to enter ubuntuforums.org. Today that message still exists, but when I tried "ubuntuforums.org/index.php", it opened like a charm! Are u having same problems?

Ok, here I'm attaching eq.preset file of mine(compressed). U xtract it, and then overwrite .config/audacious/eq.preset with it, and enjoy!!:guitar:

Let me know if this works for u, and also inform if u someday find an easir way to do this.Bye bye!:lolflag:

---

### Post by kurakura on 2013-09-12
i use ubuntu 12.04 lts,.. i was trythis menthod but nothing happen? how to sove it,.. please help

---

### Post by dhimas-25 on 2013-10-16
thanks bro... 

this thread is helping me so much :D

---

