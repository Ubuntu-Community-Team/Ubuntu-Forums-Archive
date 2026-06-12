---
title: "Mouse going haywire, touchpad control dissapears, keyboard too!"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by BastardNamban on 2009-08-30
My mouse has the opposite problem addressed in many threads about mouse issues, where people can't get clicks to register. My mouse is going haywire, and clicking & holding at random times, sometimes very fast! It's driving me nuts.

Sometimes, it then switches to the opposite- no clicks register no matter what I try, yet the cursor still moves in both cases.

I think this may have something to do with my touchpad? A while ago I asked how to enable the touchpad through terminal, here: [http://ubuntuforums.org/showthread.php?t=1200140]("http://ubuntuforums.org/showthread.php?t=1200140")

Using this command, ```
gnome-mouse-properties
```, I had a tab under the mouse settings to enable/disable the touchpad. Now I don't have that tab at all, and can't figure out why! 

I had used this sugguestion from another page to try initially to turn off my touchpad, forgetting about earlier post.
```
sudo rmmod psmouse          # Turns the touchpad OFF
sudo modprobe psmouse     # Turns the touchpad ON

``` After trying both of those several times and checking the mouse settings tabs, still no touchpad tab. And my mouse is still going nuts.

Did I mention yet my keyboard is ignoring a bunch of what I type at times? When I type REALLY SLOW it registers-at the same time the mouse skips- I'm not hitting the touchpad either, this is peck typing to make sure of that.

I'll check back tonight- this is unexpected, & I have to leave early this morning.

Using 8.04 Ubuntu. Please help?:(

---

### Post by tgeer43 on 2009-08-30
Something tells me that this is a wireless mouse and keyboard.

Am I correct?

tgeer

---

### Post by BastardNamban on 2009-08-31
Nope. This is a Dell Inspiron 9300 laptop, so keyboard is not wireless, and I'm using a corded Buffalo mouse.

---

### Post by tgeer43 on 2009-08-31
Well, so much for that idea.

As far as the missing touchpad tab in mouse preferences, try reinstalling 'xserver-xorg-input-synaptics' to see if that restores it. If it doesn't and you need to disable the touchpad correctly to troubleshoot your other issues, you can install 'gsynaptics' which is a standalone GUI touchpad control app.

tgeer

---

### Post by bregnernice on 2009-08-31
I have similar problems, though im not using a mouse but a laptop touchpad.
Going absolutely ballistic at times. Randomly registering clicks often without physically touching the mousepad. Often making it impossible to meaningfully work with the cpu.

Was working fine with hardy and in the beginning with jaunty too, but then went haywire in ways op describes, though no problems with the keyboard, so i tried the karmic upgrade (clean install) but still same issues.

Im hoping to find a solution and will regularly check the forums for any hints to as what might cause this trouble.

---

### Post by BastardNamban on 2009-09-02
Ok, feedback- I got a new Logitech MX Anywhere mouse today, and plugged it in- it seems to have fixed all my problems like a box of magical Lucky Charms or something.

Since plugging in that mouse's receiver, not only has the touchpad option reappeared under my mouse menu (and so I shut it off), the keyboard and mouse click problems have gone as well!

I don't know what happened, I changed nothing, just bought this new Logitech mouse, plugged it in, and all 3 issues are fixed! And I gotta say, this things' pretty impressive too- it really DOES work on glass! I have a 5 mm thick blue glass computer desk, it works perfectly on it, all controls work right out of the box except side scrolling. Awesome!

---

### Post by BastardNamban on 2009-09-13
ARRRRRGGG!!!!! :mad::](*,):

Now it's happening AGAIN! So far, it's just the mouse. Even with a BRAND NEW logitech mouse, the issue was fixed only for a few days.

I mentioned the new mouse brought back the touchpad option, and I turned it off. Well guess what? The touchpad is active AGAIN, and there is no way to shut it off, AGAIN!- the touchpad tab under mouse has magically dissapeared, AGAIN!!!

:](*,):

Now my mouse is selectively holding down button 1 on my computer- I know it's not the mouse, it's something with linux- the mouse is BRAND NEW.

This problem refuses to go away, and no one with any clout seems to know why, or what the heck is going on. I'm f*@king fed up with this. Can someone tell me how to fix this, please, for the love of someone's god!

We need an :AAARRRRRGGH! HULK SMASH!!!: emoticon for events like this.

---

### Post by BastardNamban on 2009-09-14
Can anyone PLEASE help? I'll try anything at this point, it's getting worse.

Isn't there any way to fix this?

---

### Post by desperado665 on 2009-09-14
I'm assuming it's a USB mouse and not a PS2 type. Please post output of ```
lsusb
```

Also, does the touchpad work properly without the mouse being plugged in?

---

### Post by BastardNamban on 2009-09-14
> **desperado665 said:**
> I'm assuming it's a USB mouse and not a PS2 type. Please post output of ```
lsusb
```

Also, does the touchpad work properly without the mouse being plugged in?

Here's the output of "lsusub":```
shogun@Valhalla:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
shogun@Valhalla:~$ 

```

And yes, the touchpad works without the mouse plugged in. It is a USB wireless mouse, microreceiver.

What I can't figure out is why the touchpad option is gone again, what is making it appear/dissapear in the first place, and why the mouse is randomly registering clicks, both hold type and single click.

---

### Post by BastardNamban on 2009-09-15
Anyone?

---

### Post by desperado665 on 2009-09-16
You might want to check your BIOS and see if USB mouse support is enabled. I think you might have some sort of conflict between your touchpad and mouse.

---

### Post by Kauliukzmogis on 2010-09-01
Hello,

I have similar problem. Mouse is not working and also "killing" keyboard and touch pad after fresh install of Ubuntu 10.04.

Everything is working just fine if I start the laptop without wireless mouse connected. All goes crazy after I connect the mouse. First pointer starts to run through screen, later no buttons is working on mouse or touch pad, keyboard is not working too (except Ctrl Alt Del combination). The only thing that is possible is to move the pointer.

After connecting the mouse for first time I saw some king of error message that mouse could not be "taken" by system. Sorry, I can't tell more precise, because message was in my native language.

Could you help me?

---

