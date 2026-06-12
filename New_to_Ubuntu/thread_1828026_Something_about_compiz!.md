---
title: "Something about compiz!"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by the-new-x on 2011-08-18
Well, first of all, I do not have a problem this time, it is just that I need an extremely time saving tip. When you go into compiz, and then want to edit the animations, instead of grabbing each item by it's own, isn't there a code that would just apply the setting to everything in the system. (I.E. the open application, close application, minimize application, etc... settings).
Here is a picture that will clarify my point:

[IMG]http://i1236.photobucket.com/albums/ff445/iareX/Screenshot-11.png[/IMG]

---

### Post by beew on 2011-08-18
I don't understand where the time saving would come from. Presumably it is not a frequent thing to edit your animations so basically you do it only once or maybe a couple of times at most. It would take more time to write a script or to find one and then to install it and run it.

---

### Post by the-new-x on 2011-08-18
> **beew said:**
> I don't understand where the time saving would come from. Presumably it is not a frequent thing to edit your animations so basically you do it only once or maybe a couple of times at most. It would take more time to write a script or to find one and then to install it and run it.
No this is not what I meant, what I want to do is apply the same animation to all of the windows instead of grabbing each type of windows by it's own. (Let us say I want to choose the explode animation as my exit animation, so instead of applying it to each type of windows by it's own (eg: the terminal, the explorer, firefox, etc...), is there something that I could type in the box below that will automatically choose all of the types of windows?

[IMG]http://i1236.photobucket.com/albums/ff445/iareX/Screenshot-12.png[/IMG]

Thanks in advance!

---

### Post by CatKiller on 2011-08-18
Those settings are just GConf entries. Assuming you know what you want to do, you can use gconf-tool to change them. You could, for example set it up how you want it, export those values and import them on another machine, or include that function in another script.

---

### Post by the-new-x on 2011-08-18
> **CatKiller said:**
> Those settings are just GConf entries. Assuming you know what you want to do, you can use gconf-tool to change them. You could, for example set it up how you want it, export those values and import them on another machine, or include that function in another script.
Well, I have only installed Ubuntu 10 days ago, so honestly, I do not know some of the things that I do on Ubuntu, it is my first Linux distro, been using windows all my life!
So here is my question again, can I type something in the boxes where I wrote in the above pictures in order to make the animation apply to all types of X windows? I hope this clarifies my point a little more!

---

### Post by CatKiller on 2011-08-18
> **the-new-x said:**
> 
So here is my question again, can I type something in the boxes where I wrote in the above pictures in order to make the animation apply to all types of X windows? I hope this clarifies my point a little more!

Ah, gotcha. On my phone rather than my computer so looking at pictures isn't that great. You can just put *any* to have it apply to all windows. You can get more technical than that if you want to tweak it; the grab function is quite useful for that.

Also, I hadn't seen your second post when I posted mine.

---

### Post by the-new-x on 2011-08-18
> **CatKiller said:**
> Ah, gotcha. On my phone rather than my computer so looking at pictures isn't that great. You can just put *any* to have it apply to all windows. You can get more technical than that if you want to tweak it; the grab function is quite useful for that.

Also, I hadn't seen your second post when I posted mine.
Don't worry about it, thanks a lot, I tried it, and it works just great, thanks again!

(P.S, I already use the grab function, the terminal deserves to be different after all!)

Again, thanks!

---

### Post by the-new-x on 2011-08-18
> **CatKiller said:**
> Ah, gotcha. On my phone rather than my computer so looking at pictures isn't that great. You can just put *any* to have it apply to all windows. You can get more technical than that if you want to tweak it; the grab function is quite useful for that.

Also, I hadn't seen your second post when I posted mine.
And outside of this thread, can you tell me how I can insert the images as thumbnails, so that they look much better!

---

### Post by CatKiller on 2011-08-18
No idea, I'm afraid. Glad you're sorted on your window selection, though.

---

### Post by the-new-x on 2011-08-18
OK, thanks again, looks like I will have to make a new thread about it tomorrow, good night (yeah it is only 11:30pm over but I got courses to attend!)

---

