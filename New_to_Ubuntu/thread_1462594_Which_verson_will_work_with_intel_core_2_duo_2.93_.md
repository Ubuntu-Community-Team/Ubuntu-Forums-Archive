---
title: "Which verson will work with intel core 2 duo 2.93 ghz"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by nappyd on 2010-04-25
I am trying to install a copy of Ubuntu studio on my PC which has an intel core 2 duo 2.93Ghz processor. I currently have a working copy of Ubuntu Studio 9.10 which hangs up either in the checking hardware step or the installing programs step. ANy help would be greatly apprecited. I have sucessfully installed a copy on my laptop using the same DVD.

---

### Post by Temposs on 2010-04-25
The installation problems are not likely due to processor. Basically any processor will work with Ubuntu. You should give complete specs for your system so we can help more.

---

### Post by abyssius on 2010-04-25
your processor configuration is commonly used successfully with ubuntu. it will probably not provide a clue to your problem. it could be a motherboard bios setting or an installed  hardware device. can you boot successfully with the live CD (without trying to install)?

---

### Post by sandyd on 2010-04-25
from the livecd,
run in the terminal
```

sudo lshw >> ~/Desktop/lshw.txt
```

there should now be a file called lshw.txt on the desktop.

attach it to your post.

---

### Post by nappyd on 2010-04-25
The motherboard is an ASROCK P45XE ( i think) All of the harddrives are WD SATA. the raid is on the motherboard I have two removeable harddrive bays installed but i don't know anything about them. 

I don't know what else you need to know so please ask if you need anything else. 

I have tried to dual boot with vista and tried to install on a freshly formated drive and neither have worked. I have also tried unhooking the removable bays and installing with only one WD 400 GB hard drive.

---

### Post by 3rdalbum on 2010-04-25
Use 10.04.

---

### Post by nappyd on 2010-04-25
Why 10.04?

---

### Post by nappyd on 2010-04-25
> **carlee said:**
> from the livecd,
run in the terminal
```

sudo lshw >> ~/Desktop/lshw.txt
```there should now be a file called lshw.txt on the desktop.

attach it to your post.


I do not think that ubuntu studio has a live cd, i will try to burn one and do what you asked.

---

### Post by sandyd on 2010-04-25
nvm.
3dalbum is telling you to use 10.04, because it has support for the p45 chipset, while 9.10 doesnt.

---

### Post by 3rdalbum on 2010-04-25
> **carlee said:**
> nvm.
3dalbum is telling you to use 10.04, because it has support for the p45 chipset, while 9.10 doesnt.

I actually didn't know that, but I do know that 10.04 has fixed a lot of bugs and it has later hardware support than 9.10. Also, if you installed 9.10 now you'd be kicking yourself in three days when 10.04 comes out!

You don't need to wait three days; you can download the current build of Ubuntu 10.04 from [www.ubuntu.com](www.ubuntu.com) and just keep it updated with the Update Manager program. Come April 29th, when you run the Update Manager you'll have the final release.

---

### Post by nappyd on 2010-04-25
So i should download a version of ubuntu 10.04 and then add the programs that ubuntu studio has?

---

### Post by sandyd on 2010-04-25
> **3rdalbum said:**
> I actually didn't know that, but I do know that 10.04 has fixed a lot of bugs and it has later hardware support than 9.10. Also, if you installed 9.10 now you'd be kicking yourself in three days when 10.04 comes out!

You don't need to wait three days; you can download the current build of Ubuntu 10.04 from [www.ubuntu.com]("http://www.ubuntu.com") and just keep it updated with the Update Manager program. Come April 29th, when you run the Update Manager you'll have the final release.
actually i take that back, I dont think it will work, or rather it hasn't worked since 1 week ago.
see [http://ubuntuforums.org/showthread.php?t=1455885&page=3](http://ubuntuforums.org/showthread.php?t=1455885&page=3)

---

### Post by nappyd on 2010-04-25
So 10.04 won't work?

---

### Post by sandyd on 2010-04-25
give it a try, you will oficially be the first to try it this close to the beta release.

if it doesn't work, just go out to the local computer store, buy a graphics card, stick it in, set the option in the bios (if any) and it should work. most people who have a external (non-integrated/on-motherboard) graphics ([such as this dude]("http://ubuntuforums.org/showthread.php?t=919619")) run their p45s fine.

---

### Post by nappyd on 2010-04-25
Alright i will download tonight and post what happens.

---

### Post by oldfred on 2010-04-26
You mentioned raid. Not sure about 10.04 but older versions did not work with the LiveCD desktop installs. Raid was more typical for servers so the text install or the server install has the extra features to support raid.

---

### Post by nappyd on 2010-04-27
I was able to successfully install and run Ubuntu Studio 10.04 last night. I dual booted with Vista already installed with no problems. 

10.04 was the right choice thanks to everyone who helped.
I hope to become a linux enthusiast and totally forget about windows soon enough.

---

