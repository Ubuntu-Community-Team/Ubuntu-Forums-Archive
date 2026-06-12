---
title: "Need help with game controller"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by OMR on 2009-01-24
:(Help, I am Running Ubuntu 8.04 and I can't get my logitech Dual action controller to work, is there a package to set up a controller to work on Ubuntu, with the controller plugged into a MOBO USB port the machine doesn't even know the controller exists, I want to use it for Alien Arena.
I would be VERY grateful if we could make this work.

---

### Post by dorkdork777 on 2009-01-24
Plug it in, then navigate to /dev/input. Is there a file named "js0"?

---

### Post by SunnyRabbiera on 2009-01-24
Huh, this controller should work by default.
It might be the game, some games dont have joystick options.
If you are using this on a game, what game is it?

---

### Post by OMR on 2009-01-24
No

---

### Post by OMR on 2009-01-24
I'm Trying to play Alien Arena, trying to play by Keyboard and trackball can get you killed FAST I am brand new to gaming.

---

### Post by OMR on 2009-01-24
> **dorkdork777 said:**
> Plug it in, then navigate to /dev/input. Is there a file named "js0"?

No
Sorry for double post forgot to Quote you, I'm pretty new on forums!

---

### Post by OMR on 2009-01-24
> **SunnyRabbiera said:**
> Huh, this controller should work by default.
It might be the game, some games dont have joystick options.
If you are using this on a game, what game is it?

Alien Arena


Sorry for double post forgot to Quote you, I'm pretty new on forums!

---

### Post by SunnyRabbiera on 2009-01-24
> **OMR said:**
> Alien Arena


Sorry for double post forgot to Quote you, I'm pretty new on forums!

Hmm, well there are ways to see if your controller works.
Try another game, one that I know works with a controller is supertux so you can test it out.
Dont base it on just one game, as I said some games dont have controller functions.
Alien arena I dont know, but I could give it a test real fast.

---

### Post by dorkdork777 on 2009-01-24
There's no "js0" file in /dev, though. By my experience, that means it's not being recognised as an input device at all - trying different games won't help.

Would it be possible for you to try it on a different computer, preferably one running Windows XP? If it doesn't work there, then it's fair to assume the controller is somewhat broken.

Also, note the "EDIT" button next to the "QUOTE" button - this lets you edit your posts after you've made them, so you don't need to double post. In other news, welcome to the Ubuntu forums :)

---

### Post by SunnyRabbiera on 2009-01-24
> **dorkdork777 said:**
> There's no "js0" file in /dev, though. By my experience, that means it's not being recognised as an input device at all - trying different games won't help.

Would it be possible for you to try it on a different computer, preferably one running Windows XP? If it doesn't work there, then it's fair to assume the controller is somewhat broken.

Its still worth a shot trying another game, never know.
And also I have seen in ubuntu that joysticks are located under /dev/input/

usually listed as js0

Edit:
Looks like alien arena DOESNT see my controller, this controller I have works in other games I have on here but not on AA

---

### Post by Arylon on 2009-01-24
A lot of the games that are in the official repositories don't support joysticks directly, or maybe I've just got bad luck. ;)

Frozen-Bubble does support joysticks, and is a lot of fun too.

Joy2key is a utility which lets you use a joystick with games that only support the keyboard, but I haven't figured out how to set it up yet.

---

### Post by dorkdork777 on 2009-01-24
> **SunnyRabbiera said:**
> Its still worth a shot trying another game, never know.

Correct me if I'm wrong, as I've only been using Linux since Ubuntu 7.10, but if something isn't listed anywhere in /dev, that means Linux thinks the hardware doesn't exist. I could be wrong, though. :)

> **SunnyRabbiera said:**
> And also I have seen in ubuntu that joysticks are located under /dev/input/

usually listed as js0


That's what I meant, sorry. See my first post in the thread :P

---

### Post by OMR on 2009-01-24
> **SunnyRabbiera said:**
> Hmm, well there are ways to see if your controller works.
Try another game, one that I know works with a controller is supertux so you can test it out.
Dont base it on just one game, as I said some games dont have controller functions.
Alien arena I dont know, but I could give it a test real fast.

Alien Arena does have a joystick option.

---

### Post by OMR on 2009-01-24
> **dorkdork777 said:**
> There's no "js0" file in /dev, though. By my experience, that means it's not being recognised as an input device at all - trying different games won't help.

Would it be possible for you to try it on a different computer, preferably one running Windows XP? If it doesn't work there, then it's fair to assume the controller is somewhat broken.

Also, note the "EDIT" button next to the "QUOTE" button - this lets you edit your posts after you've made them, so you don't need to double post. In other news, welcome to the Ubuntu forums :)

Opps, forgot to plug it back in, now shows js0, went into game direction pad and joystick do wiggle weapon side to side and up and down about 2-3 milimeters no player navigation or weapons at all! No I no longer have a Windows machine, THANK GOD.

---

### Post by OMR on 2009-01-24
> **SunnyRabbiera said:**
> Its still worth a shot trying another game, never know.
And also I have seen in ubuntu that joysticks are located under /dev/input/

usually listed as js0

Edit:
Looks like alien arena DOESNT see my controller, this controller I have works in other games I have on here but not on AA

UR right installed the game you spok of an controller works fine.:Dhttp://ubuntuforums.org/images/smilies/icon_biggrin.gif

---

### Post by OMR on 2009-01-24
Thank you all for your help, it is not the controller it works on the game I just installed, will have to go to the Alien Arena forum for this issue.

---

