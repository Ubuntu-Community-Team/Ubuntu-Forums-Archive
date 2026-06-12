---
title: "A problem and a Few questions..."
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Evilhugbear on 2009-04-27
Hello people, yet another problem this time. 

First, I will start with the problem and later ask you a question or two. :P?
Ok, my problem is a very strange problem... This has been happening off and on and has started yesterday. What will happen is I will have just logged into ubuntu and done a couple little things and then I will go into FireFox. I then want to go to this website so I will press the letter "u" for ubuntuforums.com into the address bar and then everything will freeze, except for the mouse pointer. I can move it around all I want but when I click something, nothing will happen. This has also happened when I type the first u for hulu.com, it will freeze. And this will only happen in the address bar, as you can see, I have typed the letter u alot on this post. The only way I can get to this site is that I earlier bookmarked a post and I click it and then click the home pic in the top left corner.
Does anyone know how to fix this? It is getting annoying :(

Now for my  other questions. I have been looking at a guide/post here on the forums and it said something about emerald. I decided I would try it so I got it from the Synaptic Package Manager. I then went to deviantart and found a theme I would like to try. So I opened Emerald and imported the theme, and here comes my dumb question. 

How do I enable this theme?
And it also says how to set emerald to start up on the startup of ubuntu. (I'm guessing this will enable the theme once I log in). It says to go to System>Preferences>Sessions and then type something. My only problem is... I don't have a thing that says "sessions".

Is this not here in 9.04?

And is there a different way to run this at start up?

Again this is all in Ubuntu 9.04.

EDIT : 
I just went to check my gmail and when I typed "gm" everything froze. It appears to be getting worse. :(

---

### Post by llamabr on 2009-04-27
Just to be sure, every time you press the 'u' button, it freezes your firefox?

---

### Post by Evilhugbear on 2009-04-27
No everything, all of Ubuntu freezes. Sorry if I was unclear on that.  The only way to turn of my computer is to hold the power button till it goes off. Which I understand can be bad? Or is that just windows? Sorry I am very new...

And it appears to be getting worse. :(

---

### Post by Evilhugbear on 2009-04-28
Should I just download hardy heron and install over jaunty? Because I have seen slot of people with problems in jaunty. And hardy seems more stable

---

### Post by 3rdalbum on 2009-04-28
Are you running the latest graphics card drivers?

Have you tried another browser such as Flock or Epiphany to determine whether it's a problem with Firefox alone? Have you installed any new Firefox extensions lately?

---

### Post by Evilhugbear on 2009-04-28
> **3rdalbum said:**
> Are you running the latest graphics card drivers?
 
Have you tried another browser such as Flock or Epiphany to determine whether it's a problem with Firefox alone? Have you installed any new Firefox extensions lately?
 No I haven't and I guess I should try that lol. I haven't done anything to firefox besides change the homepage and add bookmarks.
How do I check for the drivers? Just go to Nvidia's site and download it?

---

### Post by SentientFluid on 2009-04-28
I also suggest creating a new profile *in Firefox *and see if it happens there.

To create one run ```
firefox -profilemanager
``` in Terminal.  The rest should be self-evident.  Create a profile called TEST and see how it works there.

If it works fine then it may be an add-on or corrupted something or other that you have installed. Run Firefox with your normal profile and disable all the add-ons and test again.

If it works then enable the add-ons one by one until you find the culprit.

May also be a corrupt font so try adjusting the fonts Firefox is using.  Also try clearing everything in the privacy settings one at a time.

Of course, if the same thing happens in the Test profile then you could also test it in a new Ubuntu user. Maybe the issue stems from your home folder.

FYI, if it is only happening in one program it's probably not going to be something system-wide like the video drivers.

---

### Post by Evilhugbear on 2009-04-28
Thanks it appears to just be firefox. I can't believe I forgot about trying a different browser.

---

### Post by oldos2er on 2009-04-28
"And it also says how to set emerald to start up on the startup of ubuntu. (I'm guessing this will enable the theme once I log in). It says to go to System>Preferences>Sessions and then type something. My only problem is... I don't have a thing that says "sessions".

Is this not here in 9.04?"

 In Jaunty, it's System, Preferences, Startup Applications.

---

### Post by SentientFluid on 2009-04-30
> **oldos2er said:**
> "And it also says how to set emerald to start up on the startup of ubuntu. (I'm guessing this will enable the theme once I log in). It says to go to System>Preferences>Sessions and then type something. My only problem is... I don't have a thing that says "sessions".

Is this not here in 9.04?"

 In Jaunty, it's System, Preferences, Startup Applications.

You'll find "Sessions" in System > Preferences.

If you don't find it there right click the Ubuntu logo and select Edit Menus. This will open the Main Menus window.  In the left sidebar make sure "System" is open and select Preferences underneath it.  In the list on the right look for Sessions and put a check mark next to it. Click Close and then try looking in System > Preferences again.

---

