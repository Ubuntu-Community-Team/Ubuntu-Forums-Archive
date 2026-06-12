---
title: "Modifying window resizing"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by jtsc on 2009-03-01
Hello, I find it inconvenient to resize windows (using intrepid and gnome). I spend a lot of time slowwwwly moving the mouse to hit the, I don't know, one pixel where I can resize. Ideally there would be a setting somewhere that would allow me to increase the size of that zone... anyone know?

---

### Post by Bradtek on 2009-03-01
Would also love to know if such a setting exists

---

### Post by bela42 on 2009-03-01
Thats a window manager setting. If you use "borderless" window decorations, you may be left with just one pixel to resize. You rely on the resize handle at the lower right corner of each window.

You may also want to try a different win deco, which has a wider border.

---

### Post by Zunino on 2009-05-10
Hello, there.

Here's another user who also feels frustrated by this deficiency. I don't believe one should have to increase border widths just to be able to do something as ordinary as resizing a window horizontaly or verticaly with the mouse. I've just written a [post about this issue]("http://blog.zunino.eti.br/?p=44").

I hope this problem gets some deserved attention soon. It's the kind of problem that can affect many different kinds of users. I'd hate to hear a Windows user complaining about not being able to do a task as simple as resizing a window with the mouse.

Regards.

---

### Post by CatKiller on 2009-05-11
Windows users don't get anywhere near as much flexibility with their theming as Linux users. They can't change the properties of their windows because they only have one fairly limited window manager to choose from. It doesn't really seem that surprising that if you choose a theme with a narrow window border that you end up with a narrow window border. It's not like you can't change it.

Besides, Alt-middle-click will resize most windows. It's not really that difficult.

EDIT:

> Resizing must not be related to nor depend on the visual characteristcs of the windows. Put another way, one should not have to cope with heavy, ugly 10px-wide borders just to be able to grab them more comfortably. Ideally, window borders should be left as thin as the user likes and the window manager should be the one responsible for &#8220;seeing&#8221; a virtual, say, 10px-wide border that would serve as a hot spot for the resizing cursor. Is that really hard to accomplish?That's a pretty pointless suggestion. The whole point of the WIMP method is that you interact with things that you see. Not some arbitrary invisible halo that you can't. What if you've got two windows next to each other and you want to resize one? You can't, because these invisible haloes would overlap and you'd have no idea which window you were resizing, and no way to select the other one instead. Your problems seem to stem from two things; poor control of a mouse pointer, and resenting taking any steps to mitigate against your lack of skill. Either pick window controls that you can interact with or get better with a mouse. Blogging about your own poor choices isn't going to help you to interact with your computer in a way that makes you any happier.

---

### Post by mcduck on 2009-05-11
like Catkiller suggested, windows can be resized from any point inside the window by holding Alt and dragging with the middle mouse button.

In a similar way, Alt+Left mouse button allows moving the window.

Apart from that, it's really just a question of what kind of window border theme you use. Thicker borders make things easier, but on the other hand they waste screen space.

---

### Post by Zunino on 2009-05-11
> **CatKiller said:**
> Windows users don't get anywhere near as much flexibility with their theming as Linux users.
There's no doubt about it. And, from what I could gather, [OS X users have even more limitations]("http://www.xvsxp.com/interface/moveresize.php"). Viva the Linux's flexibility!

> **CatKiller said:**
> Besides, Alt-middle-click will resize most windows. It's not really that difficult.
It sure isn't. I don't find it difficult at all and neither did I say so. But I don't think you'd get the same impressiom from the average, non-techie user who has once struggled to learn the basics of windows manipulation and now wonders why it is so hard to "grab" the window border on this new system, like he'd been doing for years. 

Think of a Linux newcomer who has finally decided to see for himself what's up with this free Ubuntu operating system that so many people talk about. So this new user decides to try out the cool New Wave theme that he had seen on screenshots. As he has a hard time trying to resize windows the "usual" way, he is bound to feel that there's something wrong with the system.

Please, don't overestimate the average user. Don't expect him to infer that the behavior he's seeing is a consequence of the theme he has chosen or, more specifically, the border width setting thereof. Even more importantly, don't expect that same user to convince himself that *he* is the one who lacks the necessary precision skills for resizing windows. Given enough interest, that user might even give it a shot at a community forum such as this in an attempt to find out what's going on. But, most likely, that deficiency (yes, he will see it as a problem) will just get added to the list of "reasons why I should consider going back to my previous OS". Good riddance? Well, I, for one, don't think that would be the best attitude to have.

Don't get me wrong (as you seem to have so far); I'm all for keeping an open mind and learning new and better ways of doing things and I'd encourage the hypothetical user above to do just that. But for usability sakes, well-tried solutions (note that I said well-tried, not necessarily better) should not be sacrificed.

> **CatKiller said:**
> That's a pretty pointless suggestion. The whole point of the WIMP method is that you interact with things that you see. Not some arbitrary invisible halo that you can't.
The "invisible halo" would not be arbitrary. It would be a well-defined usability aid implemented by the window manager. On the other hand, I will concede that I could have been more specific about how I thought it should work. My point was that the visual aspects (the looks) of the selected theme should not hurt usability. At least not for basic actions such as moving, resizing, minimizing etc. So, no matter if I choose a theme with very thin or thick borders, resizing windows should be easy in both cases. And that would not hurt any principles. If users expect a thicker border to be easier to grab (rightly so), make it easier to grab. But also establish a **minimum**, **practical**, **effective** border width that may or may not correspond to the theme's actual border width.

> **CatKiller said:**
> What if you've got two windows next to each other and you want to resize one? You can't, because these invisible haloes would overlap and you'd have no idea which window you were resizing, and no way to select the other one instead.
Let's suppose a scenario where the theme's border width is 1px and the minimum effective border width value of the window manager is 5px. With what I am suggesting, it would be 5 times easier for a user to successfully resize a window than what you see on the present scenario. Those 5 (virtual) pixels could either be split in half around the actual window border (**|**) or placed inside the window (****|). In either case, the net effect is that the user would get the expected feedback (usually a double arrow mouse pointer) with much more ease. And without having to mess with theme configuration files.

As for the problems you've brought up, I see at least 2 possible solutions. 1) Assuming the "virtual" pixels would be placed inside the window, overlapping would no longer be an issue; 2) For the case where there might be actual overlapping (i.e., when the "virtual" pixels are split around the window border), I believe a simple z-order criterion would be enough to help resolve conflicts.

> **CatKiller said:**
> Your problems seem to stem from two things; poor control of a mouse pointer, and resenting taking any steps to mitigate against your lack of skill. Either pick window controls that you can interact with or get better with a mouse. Blogging about your own poor choices isn't going to help you to interact with your computer in a way that makes you any happier.
I'm sorry to disappoint you, but I have to inform you that I have absolutely no disability of any kind. Both my vision and fine motor skills are in order. I'm actually quite good with the mouse (been using one for at least 18 years and playing FPS games for the most part of them). Now, jumping to conclusions about my lack of physical abilities with a pointing device seems to suggest that you must possess some robot-like fine motor skills (think CPU-making robots with nano precision). So, yes, pinpointing a single pixel out of, say, 1600 or 1920 (assuming you wish to resize a window by one of its sides) must be a piece of cake. If that's the case, I'd seriously ask you to demonstrate your best Ubuntu spirit (humanity to others) and become a neurosurgeon. :)

OK, I got a little carried away on this last paragraph. No actual offense. But I must say I didn't appreciate the way you have jumped to conclusions about other people's abilities. Please, I propose we keep the discussion within the realm of the problem itself from now on.

Regards.

---

### Post by CatKiller on 2009-05-12
Sorry if it came off as a personal attack. It wasn't my intention. It was the tone of your blog post that made it seem like you were complaining about the fact that you personally couldn't grab the borders. Thank you for the clear response.

The deficiency, really, is in the theme creators. They go for a striking look without thinking about usability. There are usability guidelines for how the interface should be designed so that it can actually be used, but it's only really the "professional" outlets that follow them. I find a 3-pixel border to be very easy to hit, but less than that would certainly be difficult to hit, especially with a touchpad.

The point about interacting with visible objects stands, though. What might be nice is if, instead of a large invisible area to click on, the halo was visible. So the theme creator could still have their effectively non-existent window border, but then when the user wanted to resize the window the area they could click on would highlight. Something along the lines of AWN's spotlight effect. So a 10-pixel area, say, could glow around the window to give the user some feedback and something to grab on to. This could probably be themeable along with the other window decorations.

---

### Post by Zunino on 2009-05-12
Hi there.

Apologies accepted. I have just posted a [comment to my own post]("http://blog.zunino.eti.br/?p=44#comments") to add some remarks after the discussion we've had here.

Cheers! :)

---

