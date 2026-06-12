---
title: "GIMPshop"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by Wovaki on 2009-02-28
I was just wondering if GIMPshop is any good?

I am used to Photoshop, and I don't like all the windows that open with normal GIMP. Will I lose any functionality with GIMPshop, is it supported, and most importantly is it safe?

Thanks!
Wovaki

---

### Post by dorkdork777 on 2009-02-28
It's a matter of taste. Yes, you will lose functionality, but you should be able to replicate most of what you do in Photoshop. Gimpshop is not in the repos and there is no Linux download on the site, besides the source code, so you could describe it as "community supported" (i.e. post questions and we'll try and help), but it's not supported directly by Canonical. And what do you mean by "safe"? If you mean "is it virus free", then to the best of our knowledge, it is.

But if you really need 100% of Photoshop functionality, you'll have to stick to Windows - for now, at least.

---

### Post by MarblePanther on 2009-02-28
Or you can try WINE with photoshop:
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

To install WINE:  ```
sudo apt-get install wine
```

---

### Post by satipera on 2009-02-28
I must first say I do not use it, but.. from what I have read photoshop is a better programme but only the more sophistocated users would even notice. What do you mean by is it safe?

---

### Post by dorkdork777 on 2009-02-28
[Photoshop only works perfectly up to CS](http://appdb.winehq.org/objectManager.php?sClass=application&iId=17). CS2 and CS3 work partially (silver rating) and CS4 doesn't work at all.

---

### Post by Wovaki on 2009-02-28
I didn't mean lose functionality between PS and GIMPshop, I meant between GIMP and GIMPshop, I like GIMP I just don't like the layout that much.

Sorry, by safe I pretty much mean virus free, I just switched to Linux, and I was always paranoid on Windows about viruses and stuff.

---

### Post by satipera on 2009-02-28
I think what dorkdork777 is saying is if you want to run photoshop in wine rather than run gimp natively then it is only okay in wine up to cs, after that there are more problems, sorry if I am stating the obvious but this is just the sort of thing that used to leave me , eh what?            Just been  checking is gimpshop up to date?  I may be wrong but gimpshop may be a dead project.

---

### Post by Kellemora on 2009-02-28
Hi Wovaki

Just curious what it is you're trying to accomplish?

We run a graphics studio here, the primary thing we design are those tri-fold brochures you pick at all the tourist traps.  Most are overly BUSY because that's what the customer wants.

When we switched from the Doze, that meant switching from Photoshop to Gimp and our production rates are higher than they ever were in the Doze.

Yes it took some getting used to, and we had about a 2 week learning curve where things were slow as each person learned the new software.  But once they did, they are smokin'.......  There were many things we could not do in Photoshop that required other stand alone programs to accomplish.  But Gimp seems to have it all!

I haven't looked at GimpShop yet myself, but a couple here have and went right back to Gimp, said it's much faster.

TTUL
Gary

---

### Post by Wovaki on 2009-02-28
@up

Thank you, that helps me alot.

I like GIMP, I really do, but I can't get used to having 2 windows + 1 window per image open it just makes everything feel cluttered.

@all

Thanks :D

Wovaki

---

### Post by bodhi.zazen on 2009-02-28
> **Wovaki said:**
> I was just wondering if GIMPshop is any good?

I am used to Photoshop, and I don't like all the windows that open with normal GIMP. Will I lose any functionality with GIMPshop, is it supported, and most importantly is it safe?

Thanks!
Wovaki

Linux is not a drop in replacement for windows.

The gimp is a very powerful tool, but is not a drop in replacement for photoshop.

You can install gimp for windows or install the gimp on Ubuntu and check it out.

But it is hard to guess what feature in photoshop you are wanting.

---

### Post by Wovaki on 2009-02-28
Its not Photoshops features I want, I find that GIMP has everything I need and more. Its the layout that I'm used to, and I find it hard getting used to GIMP's layout.

---

### Post by Xiong Chiamiov on 2009-02-28
You can move palettes around and put them in different windows, so it's fairly customizable.  I never keep all of the stuff open that you get by default, and put everything in tabs underneath the tools.

There are no in-the-wild viruses for Linux, and even running malicious code shouldn't be able to do anything more than wipe out your home directory, if you don't run it as root.

---

### Post by hatrack on 2009-02-28
> **Wovaki said:**
> @up

Thank you, that helps me alot.

I like GIMP, I really do, but I can't get used to having 2 windows + 1 window per image open it just makes everything feel cluttered.

@all

Thanks :D

Wovaki

Hi

I too am getting used to Gimp and I have found a little trick that may be useful --

Stretch the image window until it nearly fills the screen but leave the size such that the title bars of the other two windows are still showing. Then, to select a tool, click on the appropriate title bar. This brings this window on top. Select the required tool and then click anywhere in the image window to resume editing the image in a large window but with the others hidden.

I find that by working this way, the screen feels less cluttered ...

HTH ... best regards ...

---

### Post by Kellemora on 2009-02-28
Hi Wovaki

You can get rid of ALL the CLUTTER by using the TAB KEY!
Ctrl-Tab will shift between layers still.
And you can set up hot keys for your most used features if you would like.

This might help too, we save all of our work in .xcf format until it's completely finished, then only the final copy is saved in something else.  But we keep all the masters in .xcf format to preserve the layers.

Although this is a different topic, it might give you some insight into why we switched to Ubuntu.
Coming from the Doze, lets look at a program like msWORD.  
In msWORD you had to LEARN where each of the features were located, and they WERE NOT in a logical location. 
For example:  If you wanted to change the page margins, which is a Formatting Function, you had to hunt around forever (in the beginning) to find out where they HID that feature.  Only from usage did you learn to go to the FILE system area to do that Formatting function.
In Open Office, if you stop and think, where is the most LOGICAL place to put Page Formatting?????  Well doh, under the Format Tab of course!!!!!
Why msWORD has it located under File Systems I have no idea.
But my point is, if you never used msWORD and you went TO IT from Open Office Writer, it would be exponentially harder to learn than Open Office Writer ever was.

We have found GIMP to be so much more LOGICAL and User Friendly than any version of PhotoShop we have ever used.
If you knew how many times I blew a near finished image due to quirks in Photoshop doing what you least expected it to do.  The hours saved in redoing was better spent in learning the ins and outs of Gimp and once you do, you will see it is quite user friendly.  And provides a larger working area if you use the tab key to move between things.  Hot keys are even faster.  But you do need to remember to turn those on and off, else they might interfere with something else.

I don't do it, but some of the artists here do.  Not exactly sure how since I've never done it myself.  But they remap the Window Key for some features, the alt key for some features.  Like window key plus a,s,d or f or the alt key plus z,x,c or v.  This speeds up their work considerably too.

Me, I get lost if my name is not pinned to my shirt pocket around here!
Theres a sign outside my office door that says "If I'm not in here, please come find me and direct me back here, I must be lost AGAIN!"

Enjoy, you'll get the hang of it!  If I could, anyone could!

TTUL
Gary

---

### Post by bodhi.zazen on 2009-03-01
> **Wovaki said:**
> Its not Photoshops features I want, I find that GIMP has everything I need and more. Its the layout that I'm used to, and I find it hard getting used to GIMP's layout.

In that case, that is what GIMPshop is for. Again since I do not know what you want in terms of lay out I suggest you install it and check it out. Again, you  can install it on a live CD first if you like.

That I know of, gimpshop is basically a theme for gimp and does not affect function, just the lay out of gimp and the gimp menus.

---

