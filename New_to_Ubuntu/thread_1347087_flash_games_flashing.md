---
title: "flash games flashing"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by pleasantashes on 2009-12-05
I updated Jaunty to Karmic and am now having flash game problems in Mozilla.
The flash games are actually flashing. I can play them but it gets irritating.
YouTube vids work fine. Is there a solution?

---

### Post by Anuovis on 2009-12-05
I have the same problem. This is my first Ubuntu though...
Not only my tested flash games flicker, but some heavy flash websites as well. 

Example: *[http://www.markmorganmusic.com/](http://www.markmorganmusic.com/)* 
(Bio or Music sections of the site)

---

### Post by Psumi on 2009-12-05
When you mean that the flash movie flashes black and whatnot?

That's... actually normal.

If you switch to gnash/swfdec though, this does not happen. However, you sacrifice stability and features.

---

### Post by Anuovis on 2009-12-05
I am sorry, if this will become the thread hijack.
I just assumed the OP has the same issue as me. The flash runs fine but it has white flickers, it blinks, some weird lines appear for a fraction of the second, etc. Hard to describe, it is a blinking screen, more or less... Works fine in YouTube but not in the site that I gave a link to, this also happens in all the flash games I have tried. This is definitely not normal.

---

### Post by The_Pirate_King on 2009-12-05
I have had a similar problem.  I assumed it was my graphics card, and tried installing a different graphics driver, and that broke my Xorg and... well that's a different story. 

But now I think this might be a problem with Flash Player itself...

---

### Post by pleasantashes on 2009-12-05
> **Anuovis said:**
> I am sorry, if this will become the thread hijack.
I just assumed the OP has the same issue as me. The flash runs fine but it has white flickers, it blinks, some weird lines appear for a fraction of the second, etc. Hard to describe, it is a blinking screen, more or less... Works fine in YouTube but not in the site that I gave a link to, this also happens in all the flash games I have tried. This is definitely not normal.

exactly the same!

---

### Post by Anuovis on 2009-12-05
There is a**_ [similar thread ]("http://ubuntuforums.org/showthread.php?t=1313427")_**without any final answer.
I am not sure if anything can be done with this.

---

### Post by l-x-l on 2009-12-05
> **pleasantashes said:**
> exactly the same!

Same problem here.

---

### Post by pleasantashes on 2009-12-05
Hopefully it's just a hiccup that if not already fixed will be fixed soon.

---

### Post by sportsdude81 on 2009-12-15
Same problem here.  Never happened to me in Jaunty, but with Karmic 64 bit it happens on all flash games and the commercials on hulu.  The videos work fine though

---

### Post by Psumi on 2009-12-15
> **sportsdude81 said:**
> Same problem here.  Never happened to me in Jaunty, but with Karmic 64 bit it happens on all flash games and the commercials on hulu.  The videos work fine though

Try xfce with the newest flash from adobe (10.0.4x.xx or something, which was recently released.)

For some odd reason, XFCE has little of this flashing issue now, only gnome has it the worst it seems.

---

### Post by sportsdude81 on 2009-12-23
Not really looking for a new desktop, just a patch or hack to maybe fix it.  Honestly don't play flash games ever (thank you xbox) but my 2 year old does and he gets frustrated that he can't play on my computer. haha

---

### Post by danbh on 2010-01-02
hey guys, I found some answers for the flash flickering

I posted my findings here: [http://chogydan.blogspot.com/2010/01/flashy-flash-flashin-ubuntu-karmic.html](http://chogydan.blogspot.com/2010/01/flashy-flash-flashin-ubuntu-karmic.html)

---

### Post by Anuovis on 2010-01-02
> **danbh said:**
> hey guys, I found some answers for the flash flickering

I posted my findings here: [http://chogydan.blogspot.com/2010/01/flashy-flash-flashin-ubuntu-karmic.html](http://chogydan.blogspot.com/2010/01/flashy-flash-flashin-ubuntu-karmic.html)
 
Is it a good idea changing the kernel?

---

### Post by TBABill on 2010-01-03
This has been documented back to other versions of Ubuntu and other distros as well. As far as I have found doing searches many times, the problem remains unresolved. 

I found SUCCESS with this problem with both Mandriva 2010 and OpenSUSE 11.2. I assume it's the kernel that is different between them and ubuntu. I know OpenSUSE uses a different kernel for certain and I am now running SUSE because of this problem on Ubuntu (and Mint because it is based on Ubuntu). 

If there is a tweak that cures the problem I have not found it in countless searches. Switching distros to one using a different kernel is the only fix that worked for me. My flash games, videos, scrolling within any browser, etc. are excellent now.

I was forced to find the solution because my wife and kids use Facebook and other apps that have flash based games....almost unusable within Ubuntu but excellent in other distros. Most don't want to switch, as I did not, but that's all that has worked. If 10.4 has resolved this issue I'll be back on Ubuntu!

---

### Post by J V on 2010-01-03
64 bit karmics don't play well with the flashplugin in the repositories (32 bit) its better to get the alpha 64 bit from adobes website, it fixed similar flickering issues for me... As well as non-responsivness

---

### Post by tilixibr on 2010-01-03
I have this problem with both Adobe and Gnash...

---

### Post by zaphodbblx on 2010-01-03
Wont HTML 5 eliminate this problem(and hopefully flash)That is when it finally gets full adoption(I'm not holding my breath!)

---

### Post by Psumi on 2010-01-03
> **zaphodbblx said:**
> Wont HTML 5 eliminate this problem(and hopefully flash)That is when it finally gets full adoption(I'm not holding my breath!)

Internet Explorer doesn't even support HTML5 at all, so... there.

---

### Post by zaphodbblx on 2010-01-03
> **Psumi said:**
> Internet Explorer doesn't even support HTML5 at all, so... there.

Internet explorer...who uses that?:lolflag:

---

### Post by TBABill on 2010-01-05
Just an update to my earlier post. I decided after all the flash frustration to give a 64-bit distro a shot. I chose Mint because I like it's interface better, but it's pretty much Ubuntu with a different face so I suspect you'd have similar results with Karmic 9.10 x64. 
 
I had really good success with the 64-bit Mint 8 install and flash performance was greatly improved. Unfortunately I didn't check which flash version was automatically installed because it worked well without worrying about it. If you have the ability to run 64-bit, maybe running Live to see if drivers work and performance improves would be a possibility (although it'd be inherently slow because of running from a LiveCD). When it worked for me I installed side by side with 32-bit OpenSUSE (KDE), which runs flash apps great automatically (but I am not loving the difficulty of navigating the OS in SUSE). For right now Mint 64 seems great and feels faster, but I don't have data to support whether it really is or not....but flash works well!

---

### Post by krzynool on 2010-11-06
Hi I have found a workaround that works for me for now. But still waiting for a fix to that issue.
[http://mintytux.blogspot.com/2010/11/workaround-for-flickering-flash-player.html](http://mintytux.blogspot.com/2010/11/workaround-for-flickering-flash-player.html)

---

### Post by magowiz82 on 2011-04-29
I have the same problem here with natty

---

### Post by magowiz82 on 2011-04-29
I solved installing 64-bit version of flash plugin :
```

sudo add-apt-repository ppa:sevenmachines/flash
sudo apt-get update
sudo apt-get install 
sudo apt-get remove flashplugin-installer
sudo apt-get install flashplugin64-installer

```

---

### Post by djbacon on 2011-05-12
Thank You. This fixed this problem for me too on Ubuntu 11.04 (64bit).

---

