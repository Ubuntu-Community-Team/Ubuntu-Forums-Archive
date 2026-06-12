---
title: "Unresponsive Keyboard before login"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by rednano12 on 2009-07-06
About 1-2 months ago, I posted a help topic, but was very unclear about what the problem itself was. I have not been able to come back on because of school finals :mad: and travel :). Now that I am back, I am ready to tackle the issue. Here is what happened. 
[LIST]
[*]I wiped the partition which had 8.10 and installed 9.04 from the alt. CD
[*]I installed sucessfully. 
[*]When I reboot, the loading bar finishes loading, and I see the shiny new login screen. 
[*]I hover the mouse over the username box.
[*]I click the box.
[*]I hit any key on my keyboard and it freezes.
[/LIST]

After lots of uninstalling and reinstalling, I can confirm that the same problem exists for me in 8.10, which is strange as I used to run it without any problems. It does not seem to occur in 8.04

If I attempt to go to a tty terminal, it works, which tells me that the keyboard is functional. However, if I try to type in my username, it freezes.

To me, it seems like a keyboard problem. I don't have a fancy keyboard, just an old dell one that I got from school. The model is SK-8110, but the barcode has been halfway ripped off.

Thank you so much!

---

### Post by squaregoldfish on 2009-07-07
Not sure whether or not this is good news, but I can tell you that it's not your keyboard that's faulty.

I have very occasional lockups on my machine, and have seen exactly the same behaviour - X locks up completely, and when I switch to a tty to log in, it stops after I enter the username. I assume that some critical process has gone AWOL somewhere, but since it happens so infrequently for me I haven't bothered to investigate any further.

Steve.

---

### Post by rednano12 on 2009-07-07
The issue is that I've tried over 20 times, but no luck, not even once. It is just very frustrating.

---

### Post by LewRockwell on 2009-07-07
grab a LiveCD of "straight" Jaunty and give it a spin

let us know what happens

.

---

### Post by rednano12 on 2009-07-07
A very similar thing. The loading bar finishes loading, but then I just get a black screen. Nothing happens if I click or press anything, and as I waited for half an hour, I assumed nothing was going to happen.

---

### Post by LewRockwell on 2009-07-07
although I reread this thread several times I didn't see where you listed your equipment so I'll operate under the assumption that you've got a compatibility issue between your video device and Jaunty

you wouldn't be the first

it's possible that someone has figured it out so once you know what you've got you can probably find the solution with a simple search

keep us posted!

.

---

### Post by rednano12 on 2009-07-08
To be honest, I am not 100% sure of all the parts. It is a custom that a friend of a friend made. :\ However, I replaced the video card myself, so it is running a Geforce 6200. Is that not supported by Jaunty? And why does it still not work in Intrepid anymore?

---

### Post by CatKiller on 2009-07-08
The 6200 works fine in Jaunty (I have one myself). Do you have other bits that you can swap in to isolate the problem?

---

### Post by rednano12 on 2009-07-08
Unfortunately, I have no spare hardware that I can do anything on. My father recently threw out all of my old computer stuff. The only thing I have left are two 256mb sticks of ram. I have a gig, so it seems unnecessary.

---

### Post by rednano12 on 2009-07-10
So, from what I gather, X is failing. Is it possible to stop it from failing without a tty terminal?

---

