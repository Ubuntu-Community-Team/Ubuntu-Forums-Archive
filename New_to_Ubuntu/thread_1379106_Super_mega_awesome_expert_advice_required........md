---
title: "Super mega awesome expert advice required......."
date: 2010-01-12
forum: New to Ubuntu
---

### Post by danwosere2007 on 2010-01-12
Hey computer dudes/dudettes. I'm using a samsung n130 netbook (go me=P) with ubuntu 9.10NBR. Randomly every so often (although often enough for me to be in here posting this message) the system stalls for about 10-30 seconds. Coincidentally the system monitor icon at the top of the screen  turns dark blue as opposed to the light blue it usually follows the cpu% with. Any ideas why? Sometimes i would be running an app and it would freeze, othertimes im just chilling my beans navigating around the sub menu netbook launcher jobbit on the left hand side. It is fairly annoying though. Could it be something to do with hyper-threading maybe? *shrugs. Any suggestions would be appreciated. Thanks! - Danildinho.

---

### Post by warfacegod on 2010-01-12
Sounds like you are running something fairly processor intensive. You didn't, by any chance, install the Ctrl-Fox addon into Firefox did you?

---

### Post by warfacegod on 2010-01-12
You done breaking your system yet?

---

### Post by nothingspecial on 2010-01-12
Open a terminal and type top

That should tell whats using all your cpu/memory

---

### Post by warfacegod on 2010-01-12
> Linux assumes you know exactly what you`re doing 

Whereas Windows assumes you are an idiot.

---

### Post by sxmaxchine on 2010-01-12
run system monitor system>administration>system monitor then chosse the processes tab then find wat is using the most cpu and right click it and click kill proces

---

### Post by anaconda on 2010-01-12
> **danwosere2007 said:**
> Hey computer dudes/dudettes. I'm using a samsung n130 netbook (go me=P) with ubuntu 9.10NBR. Randomly every so often (although often enough for me to be in here posting this message) the system stalls for about 10-30 seconds. Coincidentally the system monitor icon at the top of the screen  turns dark blue as opposed to the light blue it usually follows the cpu% with. Any ideas why? Sometimes i would be running an app and it would freeze, othertimes im just chilling my beans navigating around the sub menu netbook launcher jobbit on the left hand side. It is fairly annoying though. Could it be something to do with hyper-threading maybe? *shrugs. Any suggestions would be appreciated. Thanks! - Danildinho.

My acer aspire one (with 8.9" display) has a really really really slow SSD-disk, and it causes the whole machine to hang for 10-30s every now and then.. when the machine tries to read something from the hd...

I didn't check the specks of your machine, but does it have a cheap  SSD-disk?

My Acer almost flies, if I boot it from an external hd...

---

### Post by warfacegod on 2010-01-12
> **sxmaxchine said:**
> run system monitor system>administration>system monitor then chosse the processes tab then find wat is using the most cpu and right click it and click kill proces

Doing that to just any old process is unwise. Be careful in deciding which process to kill.

---

### Post by danwosere2007 on 2010-01-12
Yo dudes thanks for the suggestions, don't think i've added any firefox plugins man other than flash maybe =P. It just hangs completely outta the blue, cant really tell what app is caning the cpu because it has usually stalled and thus i cannot access the system monitor =P. I do know upon looking at the system monitor scrolling blue icon at the top that the cpu seems to turn dark blue and go all the way to the top which is weird.No its not a solid state its a 160gb regular internal HD, so im guessing thats probably not the reason. It does it when no apps are running, only every so often and it has been o.k(ish) of late. I'll try and collate some more info so next time i post back you might have a bit more to go on=). Cheers - Dan.

---

### Post by FCS tech on 2010-01-12
I have a acer 9402wsmi (4-5 years old) laptop running 9.04 with a clean install from disk. I was having that problem and more so i wiped it and did the clean install. i still get this one. Just wanted you to know your not the only one.

---

### Post by warfacegod on 2010-01-12
danwosere2007

Just backup your stuff, do a clean install, and leave the Configuration Editor alone until you make a backup of a fresh install.

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by danwosere2007 on 2010-01-12
Hmmm, its not that annoying a problem that i would go about partitioning/formatting and reinstalling ubuntu again man haha. I did check the md5sum when i installed this version though, so i know its all funkydory and all ;). It was playing silly buggers slightly before i touched anything config wise, and i have returned anything i've meddled with there to nominal values, so its not really that i dont think. The curious thing is when it starts stalling it doesn't show 100 per cent cpu usage anywhere (*on the processes screen) (it shows as having 2 processors even though it only has one, something to do with hyper-threading or something i think). One of the cpu's registers as 100 per cent the other is 50% or something (thus being able to still look at system monitor). I know im about to have fun and games because the system monitor shows a dark blue rather than light blue. Rather than reinstalling im thinking theres bound to be a way of analysing possible causes and determining a fix surely? It's more fun that way anyways haha ;). 

On an unrelated topic i'm trying to get pSX working. It's proving rather troublesome. I've managed to disable pulseaudio via autospawn = no function, then the kill pulseaudio stylee. Not a problem. But then i have no sound man. Do i need alsamixer or something in order to get it working? Tar! - ObiDan

P.s cheers for that top tip in terminal nothing special, i just tried it on ym desktop looks like a useful little function, i might use it on my netbook in a bit and see if i can't ascertain what could be causing my netbook such heinous grievance. ;)

---

### Post by warfacegod on 2010-01-12
> **danwosere2007 said:**
> Hmmm, its not that annoying a problem that i would go about partitioning/formatting and reinstalling ubuntu again man haha. I did check the md5sum when i installed this version though, so i know its all funkydory and all ;). It was playing silly buggers slightly before i touched anything config wise, and i have returned anything i've meddled with there to nominal values, so its not really that i dont think. The curious thing is when it starts stalling it doesn't show 100 per cent cpu usage anywhere (*on the processes screen) (it shows as having 2 processors even though it only has one, something to do with hyper-threading or something i think). One of the cpu's registers as 100 per cent the other is 50% or something (thus being able to still look at system monitor). I know im about to have fun and games because the system monitor shows a dark blue rather than light blue. Rather than reinstalling im thinking theres bound to be a way of analysing possible causes and determining a fix surely? It's more fun that way anyways haha ;). 

On an unrelated topic i'm trying to get pSX working. It's proving rather troublesome. I've managed to disable pulseaudio via autospawn = no function, then the kill pulseaudio stylee. Not a problem. But then i have no sound man. Do i need alsamixer or something in order to get it working? Tar! - ObiDan

P.s cheers for that top tip in terminal nothing special, i just tried it on ym desktop looks like a useful little function, i might use it on my netbook in a bit and see if i can't ascertain what could be causing my netbook such heinous grievance. ;)

Hyper Threading is basically extra pathways in your processor to create what is called a logical core. My Pentium 4 2.8 GHz is Hyper Threaded so my System Monitor and hardware apps all see it as two cores, they have no choice. Hyper Threading isn't a true dual core but nor is it a single core either. Consider it 1.5.

Start a seperate thread for your PSX woes.

---

### Post by danwosere2007 on 2010-01-12
Haha nah no need. I think ive found what im looking for with regard to pSX dillema after a bit of scoping around the forums. Gonna go try it out in a bit. Cheers for the advice peoples. 

- Case closed. (Unless some professional computer dudes can tell me why my computer is sketching out! ;) I'll try running top on it next time and see if i can see any abnormal happenings (might have me a ghost in the shell haha ;). 
- Dan ;)

---

### Post by warfacegod on 2010-01-12
There is *always* a ghost in the machine.

---

