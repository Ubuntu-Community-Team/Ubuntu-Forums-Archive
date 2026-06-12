---
title: "[SOLVED] New LINUX User | Add-on Firefox Installation Problem | .ttf Fonts"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Valtiel on 2008-12-02
I'm a new LINUX user. My first experience was with Fedora 10 and after 48+ of hands-on hours with it, I ended up making the switch to Ubuntu.

After educating myself about LINUX OS as mush I have thus far, I came to find that Ubuntu is more of my flavour in: integration with my hardware, user-friendly, installation & update system are a lot more straight forward and to the point, etc... . So you get an idea, what I did in Fedora in 48 hours I have been able to do and more in Ubuntu is around 6 hours.

Anyways, I'm here to ask about two things that have been bothering my internet experience in LINUX.

**1- Font & size on some websites**

   [INDENT] Some websites font look very small in Firefox. And example of this is [www.lifehacker.com](www.lifehacker.com) I know I can fix this by playing araound with the font selection that Firefox uses to render some sites, but while that will fix the way fonts look in [www.lifehacker.com](www.lifehacker.com) for example, it will mess the way fonts look in other websites.[/INDENT]
[INDENT]
    I read something about being able to install .ttf fonts in unbuntu. I wonder, how do I do this and would this fix my font problem?[/INDENT]

**2- Firefox keep resetting my interface setup every time I install an add-on**

    [INDENT]For Firefox I use TinyMenu so I can minimize firefox UI. Once I installed TinyMenu then I move all buttons and text bards in the Navigation bar to the Menu bar and then hide the Navigation bar as well as bookmarks bar. Anyways, everytime I install an add-on for Firefox, and the browser re-starts, all the Navigation buttons are removed from the Menu bar and back to the Navigation bar [the Navigation bar still hidden and so is the Bookmark bar.

    Has anybody else experienced this? Any idea on how I can fix this? I was able to do this no problem when I was in Windows XP and also a few hours ago in Fedora 10
[/INDENT]

Any help/suggestion will be greatly appreciated.

---

### Post by Valtiel on 2008-12-02
Help anybody?

---

### Post by luckydeveloper on 2008-12-02
I can help you with your First problem about FOnts.

If you feel that fonts in some website are small, you can always do Ctrl++  this will zoom in to the page for you to see them big

---

### Post by luckydeveloper on 2008-12-02
For you second problem, every time you install any addon in firefox, the normal procedure will be to restart the browser inorder to see those addons into action... i dont see the restarting as a problem, thats just to enable those addons to work.
besides this,
i dont have experience with TinyMenu... so i cant comment on that particularly.

---

### Post by Tilex on 2008-12-03
> I read something about being able to install .ttf fonts in unbuntu. I wonder, how do I do this and would this fix my font problem?

You can install fonts by going in Systems Settings and clicking on "Fonts".  There you can easily install fonts.

---

### Post by Valtiel on 2008-12-03
> **luckydeveloper said:**
> For you second problem, every time you install any addon in firefox, the normal procedure will be to restart the browser inorder to see those addons into action... i dont see the restarting as a problem, thats just to enable those addons to work.
besides this,
i dont have experience with TinyMenu... so i cant comment on that particularly.

The problem isn't that Firefox needs to be restarted so the installation of add-ons can be complited. I know this is the way it should be and I have nothing against it.

>>Let me re-state my problem with some images to aid my description of the problem as well as you guys better understanding. 

TinyMenu is a minimalist oriented add-on for Firefox. The idea behind TinyMenu is to hide all the menu items in the Menu-bar in one single list-type menu.

Once I install Tiny Menu I proceed to move all the items in the Navigation-bar to the to the Menu-bar so I can minimize the Firefox interface [**See attached Image1.png**]

Now everything is good from that point on till I install another add-on to Firefox. Everytime I do this, Firefox interface get reset.

-All the native Navigation-bar items are set back to the Navigation-bar thus leaving Tiny Menu by itself on the Menu-bar [**See Image2.png**]

**NOTE**: I have this same setup in windows and never had a problem with it. I even had it in Fedora 10 without this issue I have in Firefox/Ubuntu

**---Something I have notice**

I came to track down the problem to Tiny Menu itself. When I uninstall Tiny Menu from Firefox, then move items around from the Navigation-bar to the Menu-bar the re-setting of items doesn't take place when I install and add-on

Now I wonder, why does this happen in Firefox/Ubuntu but not in Firefox/Fedora 10?

---

### Post by Valtiel on 2008-12-03
> **Tilex said:**
> You can install fonts by going in Systems Settings and clicking on "Fonts".  There you can easily install fonts.

I'm sorry but I'm just fresh out of the water here. I very new to LINUX. 

There is no **System Settings >>> Fonts** location

nor

**System >>> Settings >>> Fonts**

I did look under **System >>> Preference** and **System >>> Administration** without any luck.

Notice that hardly understand the file structure of LINUX systems much-less ubuntu but I did do some digging in the **HOME FOLDER** and also couldn't come up with anything -no FONT folder. I even tried to search for: *FONT, FONTS, .fonts and .font* without any luck either.

If you could be more specific it would be Outstanding and very appreciated. 


>>>Also, yesterday I found some documentation for Windows users moving to LINUX. Very good stuff, but I was wondering if there is documentation that talks about the equivalence of locations/terms/folder structure/etc of windows in LINUX/Ubuntu?

ex. In windows ______ the equivalent in Ubuntu is ______

---

### Post by Kellemora on 2008-12-03
Hi Val

To install the Mickey$oft core fonts go to System, Administration, Synaptic Package Manager, let it load and then scroll down the list for msttcorefonts and place a checkmark in the box, then say APPLY in the pop-up, then APPLY again up in the menu bar.
This will install those font's!

If you have other True Type fonts you would like to install, it's best to install them where they belong (which is NOT in a hidden fonts folder in your home directory, which you will see mentioned quite often here).  The correct place to put True Type fonts is in the True Type folder located at /usr/share/fonts/truetype I usually make a separate folder inside of the truetype folder for each of my font sets and makers.
EG:  ttfBitstreamArrus and put the whole set of Arrus fonts in that folder, keeps them all together that way.  Also helps you remember WHAT they are since many fonts have numeric file names.
Oh, you DO NOT have to INSTALL fonts as in windows, just copy n paste them into your truetype folder is all.

TTUL
Gary

---

### Post by Kellemora on 2008-12-03
Hi Again Val

Forgot about your font size issue in Firefox.

Hold down your control key and use the scroll wheel on your mouse.  Only move it ONE click at a time and wait, Firefox is SLOW to know you did this.

I'm 61 years old so this is the first feature I looked for, hi hi.........

And FWIW the web browser OPERA, besides being much faster at everything, the fonts enlarge instantly with no delay using control scroll wheel.
I still like Firefox better though.  Don't crash as often.

TTUL
Gary

---

### Post by Valtiel on 2008-12-03
Thank you very much for your help and taking the time to express the steps are clear as you did. That was a lot easier than what I thought.

---

