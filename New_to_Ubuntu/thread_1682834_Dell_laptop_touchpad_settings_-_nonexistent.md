---
title: "Dell laptop touchpad settings - nonexistent"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by quik_lives on 2011-02-06
Hi folks! I just bought a Dell Inspiron N4030, installed Ubuntu to dual boot with Win7, everything went pretty smoothly and I was able to find fixes for everything but one thing by searching the forums. I'm still more or less a noob, despite the fact that I've used Ubuntu on my netbook for a year, because the netbook was so limited, I didn't actually *try* to do much with it. If that makes sense.

Anyway, my touchpad works ok. Moving the cursor, right and left click. But I don't have settings anywhere, so I have no way that I can find to set up scrolling. I don't care if it's two finger scrolling or right-side scrolling, but I really do need one or the other. I'd also like to be able to turn off tap-to-click so I can stop jumping my cursor all over the screen while I type.

Under System>Preferences>Mouse, there is no Touchpad tab. So I installed gsynaptics, and now I have System>Preferences>Pointing Devices, but it just lists the touchpad as PS/2 Generic Mouse, and the settings there don't *seem* to do anything, or at least I don't really understand how to make them do anything.

As mentioned, I did do some searching, but I was unable to find a solution, so I was hoping someone might be able to help me. Thanks for reading!

---

### Post by quik_lives on 2011-02-06
I know it's SB Sunday, and I'm terribly impatient, but - anyone?

---

### Post by migs73 on 2011-02-08
Try this guide;

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

NB if you have 10.04 installed I don't think multitouch is available. The guide for 10.04 and earlier is here;

[https://help.ubuntu.com/community/SynapticsTouchpad/PreMaverick](https://help.ubuntu.com/community/SynapticsTouchpad/PreMaverick)

FYI I have a 3 year old Dell 1501, and the pad is recognised, side scrolling and two finger scrolling are both supported.

**Both these guides have links to debugging pages right at the bottom.**

---

### Post by waynefoutz on 2011-02-08
It should be in System/Preferences/Mouse there should be a "touchpad" tab that has all those settings. 

[IMG]http://debii.curtin.edu.au/~pedram/images/stories/Screenshot-Mouse%20Preferences.png[/IMG]

---

### Post by migs73 on 2011-02-08
> **quik_lives said:**
> 

Under System>Preferences>Mouse, there is no Touchpad tab. 



Waynefoutz;

That is the OP's problem!!!

---

### Post by A4orce84 on 2011-02-26
Bump I would also like to get scrolling working correctly on my Dell Touchpad.

Any help would be greatly appreciated. Thanks!

--Asif

---

### Post by buratti simone on 2011-06-21
For the (little) sake of others dell N4030 owners, at least to solve the headache of making jump the cursor when you have to type considerable amount of text:

This is a workaround, as I didn't find any post that could locate the real cause of the problem - I will check bug tracks - btw it worked for me, with a 11.04 64 bit installation. I followed the link suggested by migs73, looked at [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) and found that I could create two launchers, one with the command  to disable the touchpad:
```
xinput set-prop 15 "Device Enabled" 0
```where 15 was the id of the touchpad in my case, [FONT=Arial]and another one to get it back on[/FONT]:

```
xinput set-prop 15 "Device Enabled" 1
```I also  modified the icons to better recognize the two launchers, but this is even more off topic.

I guess that I will open a ticket, by the way.

---

### Post by jamesisin on 2012-02-28
buratti simone - How does one determine their device number so that I can test your workaround?

---

### Post by jmblock2 on 2012-03-08
Same problem but on a HP Pavilion DV7. Also on 12.04, but this was also a problem on 11.10. Left/Right click works fine, but there is no touchpad menu/scrolling doesn't work.

I've tried random things found on old posts/bug entries. Mostly I've been messing with adding options to my xorg.conf, but nothing changes it. For instance using the settings

```
  Option   "MinSpeed" "0.01"
  Option   "MaxSpeed" "0.01"
```
and
```
  Option   "MinSpeed" "0.90"
  Option   "MaxSpeed" "0.90"
```
has no noticeable difference in movement. My xorg.conf was originally blank and I've had to add bits and pieces to get things working, from dual screens to video crashing lightdm. But it's probably because it keeps finding my touchpad as a ps/2 mouse? I'm not sure... not very good at debugging OS stuff like this. I'd be happy to try anything or learn more about fixing my own problem. I've just browsed the debug Ubuntu pages, but it hasn't really helped me narrow it down.

I'm mostly just interested in making this damn mousepad move faster.

Thanks.

---

### Post by jamesisin on 2012-03-26
Can anyone help me test the above workaround?

---

