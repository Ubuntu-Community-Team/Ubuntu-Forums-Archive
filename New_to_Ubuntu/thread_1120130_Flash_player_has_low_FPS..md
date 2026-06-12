---
title: "Flash player has low FPS."
date: 2009-04-08
forum: New to Ubuntu
---

### Post by mmitt on 2009-04-08
I am using firefox, and for some reason, the flash player doesn't seem to like ubuntu. I usually play games, watch youtube, etc. but now, the low FPS has made many games unplayable and many videos unwatchable. I have another partition of Windows Vista and the flash player works perfectly... I have the flash player from adobe's website and everything. Can anyone help?

---

### Post by durand on 2009-04-08
Open a terminal (Applications > Accessories > Terminal) and run glxinfo. Post the output here within quote tags. ```
> 
```

It might be that it isn't accelerating your video with your graphics card. Do games still work properly?

---

### Post by mmitt on 2009-04-08
It was too large, so I attached a file with the output on it.

---

### Post by durand on 2009-04-08
Hmm, that's strange. It seems to be accelerated. I'm not really sure what the problem is :( Does your CPU usage spike when flash is running?

---

### Post by mmitt on 2009-04-08
> **durand said:**
> Hmm, that's strange. It seems to be accelerated. I'm not really sure what the problem is :( Does your CPU usage spike when flash is running?
I'm not really sure. How can I tell?

---

### Post by durand on 2009-04-08
Right click on the panel and click on "Add to panel" then find the system monitor applet and add it. You should see it spike when there is a lot of cpu usage. If you click on it, it will tell you what is using up the CPU.

---

### Post by mmitt on 2009-04-08
> **durand said:**
> Right click on the panel and click on "Add to panel" then find the system monitor applet and add it. You should see it spike when there is a lot of cpu usage. If you click on it, it will tell you what is using up the CPU.
Ok then, yes, it goes way up.

---

### Post by durand on 2009-04-09
If you click on that, it should tell you what program's using up the CPU. That will hopefully give us an insight into this.

---

### Post by freak42 on 2009-04-09
something else to try (even though usually that's not the problem):
in any flash content (e.g. a youtube video) rightclick on the video.. choose settings.. then from the tabs at the botom choose the most right one with a little monitor on it.. and check that the box is checked above the tabs that says "enable hardware acceleration", otherwise check it.

---

### Post by mmitt on 2009-04-11
Ok it says that mostly it is firefox.

---

### Post by Kosimo on 2009-04-11
> **mmitt said:**
> I am using firefox, and for some reason, the flash player doesn't seem to like ubuntu. I usually play games, watch youtube, etc. but now, the low FPS has made many games unplayable and many videos unwatchable. I have another partition of Windows Vista and the flash player works perfectly... I have the flash player from adobe's website and everything. Can anyone help?

I had a similar problem, and what it can happen is that flash player isn't accelerating your video. I could fix my problem by forcing flash to hardware accelerate the streams

```
$ sudo mkdir /etc/adobe
$ echo "OverrideGPUValidation=true" >~/mms.cfg
$ sudo mv ~/mms.cfg /etc/adobe/
```

---

### Post by mmitt on 2009-04-12
> **Kosimo said:**
> I had a similar problem, and what it can happen is that flash player isn't accelerating your video. I could fix my problem by forcing flash to hardware accelerate the streams

```
$ sudo mkdir /etc/adobe
$ echo "OverrideGPUValidation=true" >~/mms.cfg
$ sudo mv ~/mms.cfg /etc/adobe/
```
Thanks, I tried that but it didn't work... Nothing really changed.

---

### Post by pistonbroke on 2009-04-13
Hi, ):P 

new poster here, new to ubuntu and new to firefox so please be gentle with your answers. I am having the same problems as the original OP.

I have vista installed and flash runs fine through aol but whenever I try to play a game using ubuntu and ff it becomes that slow that its unplayable.

Would like to find a solution as its one of only two things left that are stopping me deleting vista totally.

---

### Post by TenPlus1 on 2009-04-13
I managed to stop 3d spiking by running nvidia-settings and turning ON the 3D Vsync option...  3D runs smooth and doesnt use all my processing power...

---

### Post by chriswyatt on 2009-04-13
I was going to suggest disabling some plugins in Firefox.

---

### Post by durand on 2009-04-13
You could also see if it works in another browser just to check that flash player is the problem and not firefox.

---

