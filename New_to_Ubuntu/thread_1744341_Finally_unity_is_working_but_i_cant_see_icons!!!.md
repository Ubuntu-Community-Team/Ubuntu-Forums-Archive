---
title: "Finally unity is working but i cant see icons!!!"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by ravi_buz on 2011-04-30
So finally unity is working on my pC ([http://ubuntuforums.org/showthread.php?t=1743319](http://ubuntuforums.org/showthread.php?t=1743319)) but now when i booted in i cant see the icons on the left panel. Can some help me with this. I have attached the screen shot of my current desktop. [ATTACH]190500[/ATTACH]

But i can see folders and other things

---

### Post by lidex on 2011-04-30
Try this in a terminal:
```
unity --reset
```
Reboot

---

### Post by ravi_buz on 2011-05-01
> **lidex said:**
> Try this in a terminal:
```
unity --reset
```
Reboot

In one way it helped. Suddenly i wasnt able to see any icons or tab or anything and your command brought all back.

But still i cant see the icons on the Unity Quick launch tab any other solution for it?

---

### Post by lidex on 2011-05-01
This perhaps - may need a reboot or logout:
```
unity --reset-icons
```

---

### Post by ravi_buz on 2011-05-01
> **lidex said:**
> This perhaps - may need a reboot or logout:
```
unity --reset-icons
```

Din help. as i said i can see icons everywhere except in the launcher

---

### Post by lidex on 2011-05-01
Did you reboot after that last one? And were you tweaking anything in compiz via ccsm? 
You may need to reset compiz. See the section 'Reset Compiz in Ubuntu 11.04' here:
[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)
Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/731578](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/731578)

---

### Post by ravi_buz on 2011-05-01
Yes. I tied changing things in ccsm but it created some major problem so reset it back, but still it had the problem. 
PS. from the time i installed 11.04 i was unable to see the icons in the launch bar.

---

### Post by David D. on 2011-05-01
Here is something else you can try/check.  Go to the Ubuntu Software Center (you can get to it by clicking on the BFB/Ubuntu button in the upper left and entering "Ubuntu" in the search).

In Ubuntu Software Center, enter "unity" in the search.  In the search results click on "Interface designed for efficiency of space and interaction".  When that opens, click on (select) "More Info".  Make sure all the Add-ons are checked.  If any are not, select them and install.

---

### Post by ravi_buz on 2011-05-02
> **David D. said:**
> Here is something else you can try/check.  Go to the Ubuntu Software Center (you can get to it by clicking on the BFB/Ubuntu button in the upper left and entering "Ubuntu" in the search).

In Ubuntu Software Center, enter "unity" in the search.  In the search results click on "Interface designed for efficiency of space and interaction".  When that opens, click on (select) "More Info".  Make sure all the Add-ons are checked.  If any are not, select them and install.

Yup all the addons are installed.

---

### Post by nava69 on 2011-05-02
hi
i have fx5200 too and i have this problem,cant see icons in unity launcher

---

### Post by ravi_buz on 2011-05-02
> **nava69 said:**
> hi
i have fx5200 too and i have this problem,cant see icons in unity launcher

Hmm.. may be this is a bug. Once i go home will try to post this in launch pad. Meanwhile you can try Unity 2D/

---

