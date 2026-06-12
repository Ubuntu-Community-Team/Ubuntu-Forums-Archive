---
title: "No sound on laptop"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by gzav on 2010-12-08
Hi all,

I just installed Ubuntu 10.10 on my work laptop, but the only problem I ran into is I have no sound. There isn't even a speaker icon in my taskbar, what should I do?

Thanks in advance

---

### Post by tajiknomi on 2010-12-08
[SIZE=2]1st of all Go to > System > Preferences > Sound[/SIZE]...

[SIZE=2]If you find it, open and check whether it is muted...?

Also paste the output of 

                [/SIZE]```
[SIZE=3]lspci | grep audio[/SIZE]
```

---

### Post by gzav on 2010-12-08
Hi and thanks for the quick reply.

I found the sound and it wasn't muted

And as for lspci | grep audio, I pasted it in the terminal, but got absolutely no response

---

### Post by tajiknomi on 2010-12-08
> **gzav said:**
> Hi and thanks for the quick reply.

I found the sound and it wasn't muted

And as for lspci | grep audio, I pasted it in the terminal, but got absolutely no response

[SIZE=2]try [/SIZE]```
[SIZE=3]sudo lspci | grep audio[/SIZE]
```[SIZE=2]

Check whether the driver is install or not >[/SIZE]```
[SIZE=3]sudo lshw -C sound | grep driver
```[/SIZE][SIZE=2]

  [/SIZE][SIZE=2]Set the volume for Headphones/Speaker[/SIZE]
```
[SIZE=3]alsamixer[/SIZE]
```[SIZE=2] ...
[/SIZE]

---

### Post by gzav on 2010-12-08
I'm still getting nothing with lspci

With lshw, this is what appears:
follebouckt@XF-HPProbook:~$ sudo lshw -C sound | grep driver
[sudo] password for follebouckt: 
       configuration: driver=HDA Intel latency=0

and alsamixer works, i can set the volume but I still don't have any sound

---

### Post by tajiknomi on 2010-12-08
> **gzav said:**
> I'm still getting nothing with lspci

With lshw, this is what appears:
follebouckt@XF-HPProbook:~$ sudo lshw -C sound | grep driver
[sudo] password for follebouckt: 
       configuration: driver=HDA Intel latency=0

and alsamixer works, i can set the volume but I still don't have any sound

[SIZE=2]Have you tried your sound with other OS..?[/SIZE]

---

### Post by gzav on 2010-12-08
Yep, and it works without fail

---

### Post by tajiknomi on 2010-12-08
> **gzav said:**
> Yep, and it works without fail

[SIZE=2]I am not sure what the problem is, but you can go to system > Administration > Additional Drivers, and check, whether a driver for sound is available...?[/SIZE]

---

### Post by gzav on 2010-12-08
I tried that already and there's nothing there

---

### Post by tajiknomi on 2010-12-08
> **gzav said:**
> I tried that already and there's nothing there

[SIZE=2]Moreover, check out the output option in System >Preferences >SOUND.....[/SIZE]

[SIZE=2]Have a look at the pics,

Also check out my ***alsamixer*** pic, this is ***default***..
[/SIZE]

---

### Post by gzav on 2010-12-08
Thanks, it works! I don't quite know what I did, but I fiddled around some more with the profiles in Sound and now everything works

---

### Post by tajiknomi on 2010-12-08
> **gzav said:**
> Thanks, it works! I don't quite know what I did, but I fiddled around some more with the profiles in Sound and now everything works

[SIZE=2]Glad to see the issue is solved :p

Please mark the ***thread-as-solved*** in ***thread-tools*** above..
[/SIZE]

---

