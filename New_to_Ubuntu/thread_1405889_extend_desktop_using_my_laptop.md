---
title: "extend desktop using my laptop"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by jmatta on 2010-02-13
hello,
I have been using ubuntu 9.10 (karmic koala) for a while
but when I try to extend the desktop to another monitor it just shows a black screen and only the mouse is visible

I used a few settings the maximum I could get was 1280*800 on my primary monitor and 640*480 on the secondary [which is bad] or 1024*768 on the primary [also bad] and 800*600 on the secondary
any more the blank black screen awakes :)

I'm using a HP 530c laptop with integrated 945 intel graphics card and I dual boot between windows 7 and ubuntu[ubuntu as primary]

after googling a lot all the posts show how to dual display with good display settings but by editing "xorg.conf" which shows my problem that I can't find this file ANYWHERE.

any help would be appreciated since I have a few presentations coming on... I can always use the windows  but I would like to learn this ..

---

### Post by ubunterooster on 2010-02-13
did you go to system/preferences/display and click on the "detect displays" button?

---

### Post by switch10 on 2010-02-13
dissable compiz to have full resolution.  Or stack the monitors on top of each other.

---

### Post by jmatta on 2010-02-16
whats compiz ??

---

### Post by Roger Allott on 2010-02-16
> **switch10 said:**
> dissable compiz to have full resolution.  Or stack the monitors on top of each other.

I'm running 9.10 with dual monitors right now, and I haven't had to disable compiz to get them working.

---

### Post by ubunterooster on 2010-02-17
> **jmatta said:**
> whats compiz ??

Compiz is what takes care of all extra desktop effects. There are three options available in a usuall install: none; normal; extra. You could try turning this to none.

---

### Post by ubunterooster on 2010-02-17
sorry, I forgot to give location: system/preferences/appearance
 go to the "visual effects" tab.

---

### Post by Dale61 on 2010-02-17
> **Roger Allott said:**
> I'm running 9.10 with dual monitors right now, and I haven't had to disable compiz to get them working.

Are you going to leave the OP hanging, or are you going to let him (us) know how you did it?  Even if you post a link, it should help more than just the OP.

C'mon, don't be selfish.  I bet you have received help from someone here, so now it's your turn to re-pay that favour.

---

### Post by Roger Allott on 2010-02-18
> **Dale61 said:**
> Are you going to leave the OP hanging, or are you going to let him (us) know how you did it?  Even if you post a link, it should help more than just the OP.

C'mon, don't be selfish.  I bet you have received help from someone here, so now it's your turn to re-pay that favour.

OK, here's my ten-point guide to getting a dual-monitor set-up working with Compiz.

1. Plug in second monitor.
2. Ummmm .......
3. Errrrr .......
4-9. Repeat steps 2 or 3 as required.
10. That's it.

---

### Post by Dale61 on 2010-02-18
Strange that.  I thought it would be as simple as that, but I was wrong.

My laptop monitor is 1366 x 768, whilst my external (desktop) monitor is 1440 x 900.  I adjust the laptop, the external is out of whack.  I adjust the external, the laptop is out of whack.

I overrode the command for the Catalyst Control Centre, and made some adjustments to the settings, and what do you think happened?  The graphics card drivers crashed and I lost both screens.

I'm currently in the middle or re-loading 9.10, and I'm going to have to get used to the out-of-sync screens.

---

### Post by Roger Allott on 2010-02-18
> **Dale61 said:**
> Strange that.  I thought it would be as simple as that, but I was wrong.

My laptop monitor is 1366 x 768, whilst my external (desktop) monitor is 1440 x 900.  I adjust the laptop, the external is out of whack.  I adjust the external, the laptop is out of whack.


My laptop is 1280x800 and my external monitor is 1440x900. Thus, both have the same aspect ratio, whereas yours don't. I've no idea whether that's relevant, but I don't think it should be.

---

### Post by Dale61 on 2010-02-18
I think the unmatched aspect ratios is the problem.  The external being 16:10, with the laptop at 16:9.

The best option for me is to mirror the screens at a resolution of 1280 x 768, which is a 16:10 aspect ratio.

---

### Post by ubunterooster on 2010-02-18
My guess: go w/ what switch10 said. It worked w/ compiz on for roger because his two screens had the same ratio. 
 If my guess is wrong just turn compiz (visual extra effects) back on.

---

