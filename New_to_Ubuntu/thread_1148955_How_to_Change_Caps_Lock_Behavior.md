---
title: "How to Change Caps Lock Behavior"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by bernardolopes on 2009-05-04
Hello,

Every Ubuntu version that I have installed so far (or nay other Linux distribution for that matter) has a Caps Lock behavior that does not suits my typing style.

I learned how to type using Caps Lock to capitalize sentences. And intend do continue doing so.

Contrary to others OSes, in Linux, the Caps Lock key toggles the capitalization only when I *release* the key (i.e. key up). Instead of toggling the capitalization when I simply press the key (key down).

I've tried many Linux flavors and that seems the defult pattern.

Is there any way to change this?

I've messed with Gnome and KDE keyboard settings but none fixed my issue.

I know that the majority of people prefer the Shift key for such job. But I'd have learn how to type again.

I've searched this forum and other places and found people reporting the same question, but not a solution.

Thanks.

---

### Post by Sef on 2009-05-04
> Contrary to others OSes, in Linux, the Caps Lock key toggles the capitalization only when I *release* the key (i.e. key up). Instead of toggling the capitalization when I simply press the key (key down).

When I hold the caps key down, it capitalizes the letters.   Of course, the letters stay capitalized unless I repress the caps button.

---

### Post by bernardolopes on 2009-05-04
Thanks for the quick reply and wiliness to help.

With your post in mind, would you be kind to follow the below steps to try to reproduce my situation?

On any empty document:

1) With the capitalisation off, press and release the Caps Lock key to activate the upper case (the corresponding keyboard led should light, if that is the case);

2) Now press and hold any character key like "A" for example;

3) While holding the character key and with upper case activated, press the Caps Lock key without releasing it. So at this moment both character key and Caps Lock key are being pressed down.

The output so far as step 2 will be obviously a trail of upper case letter.

On step 3 the letter will continue to be capitalised even when the Caps Lock led (at least on my machines) is off and by implication the capitalisation is supposed to be set to lower case.

But it's only when I release the Caps Lock key is that the capitalisation effectively changes to lower case.

Do you have this behaviour also?

I would like to change this pattern so that the caps toggle occurs in the event of the Caps key press and not the Caps key release.

---

### Post by blueridgedog on 2009-05-04
I have the same behavior, but what real world typing method would produce the capslock key being held down rather than released (not sarcasm, but curiosity).  Perhaps on-handed typing or data entry?

---

### Post by bernardolopes on 2009-05-04
@blueridgedog: I don't think any real world typing method does that as you said. And I don't do that either. It's just that for a fraction of time, while typing fast, I tend to hold the Caps key a little longer causing the undesirable effect under Linux.

Some of my sentences looks like this: "THis IS AN EXample SEntence".

---

### Post by blueridgedog on 2009-05-04
OK, I see now.  You type very fast and use capslock a great deal (versus shift).  I have access to a few more designs of keyboards at my work and I will see if they reproduce the same behavior.

---

### Post by bernardolopes on 2009-05-04
Thanks blueridgedog.

Anyway I tried Ubuntu on 3 different machines and all yielded the same results.

Interesting enough, on a guest Windows on Sun's VirtualBox the Caps key behaves to my likings.

Again: isn't there a way to change that on Ubuntu?

---

### Post by blueridgedog on 2009-05-05
> **bernardolopes said:**
> 
Again: isn't there a way to change that on Ubuntu?

I do not know, but will search as well.

---

### Post by blueridgedog on 2009-05-06
I do not have a solution, but in searching for one I found this site:

[http://geekhack.org/](http://geekhack.org/)

The forum/message boards there will probably get you a result.  My searching indicates that it should be possible to change the behavior with an edit to your X windows setup and I bet the people there can help.

---

### Post by darthmob on 2009-05-06
you may bind the shift function to capslock (might be possible with [xmodmap]("http://www.linuxmanpages.com/man1/xmodmap.1x.php"))?!

---

### Post by Paddy Landau on 2009-05-06
I've read this thread with extreme curiosity.

As a touch-typist (among my many other sins), I find it really unusual to use the Caps-Lock key to capitalise single letters. I've never before come across a situation where the method that you describe would pose a problem.

I guess it's different strokes for different folks, as the saying goes. Good luck in finding your solution; let us know if you find it, because the method may come in useful to someone else.

---

### Post by bernardolopes on 2009-05-06
> I do not have a solution, but in searching for one I found this site:Thanks, I didn't think you would keep searching about this subject... I'll search that forum. Thank you again.

> you may bind the shift function to capslock (might be possible with [xmodmap]("http://www.linuxmanpages.com/man1/xmodmap.1x.php"))?!I'll look that too, but I don't think it will result in what I'm looking for. Thanks.

> I find it really unusual to use the Caps-Lock key to capitalise single letters.I agree. The way I learned how to type is unusual. I have learned how to type when typewrites were all we've got. That's why I have this typying "vice".

I know that it's a commom conception that the Caps key is somewhat "evil". I am an odd typist.

If I have absolutely no means to work around this issue I'll have to re-learn how to type with the Shift key only.



I found another thread here where a person experiences the same issue:
[http://ubuntuforums.org/showthread.php?t=691265](http://ubuntuforums.org/showthread.php?t=691265)

And I crossed into another thread here also that were more descriptive of the situation, but I can't find it anymore.

---

### Post by Paddy Landau on 2009-05-06
> **bernardolopes said:**
> The way I learned how to type is unusual. I have learned how to type when typewrites were all we've got. That's why I have this typying "vice".
That's interesting.

I typed on typewriters too, even before my mother bought an electronic one. The "shift" key was so-called because it literally shifted the entire keyrack up, allowing the hammer to strike with the capital letter instead of the lowercase one.

A person needed quite strong fingers to type! It was a bit of a learning curve to progress to electronic typewriters, where I didn't have to bang away at the keys.

"Enter" used to be called "Return", because it mimicked the carriage-return lever in the early typewriters and text-only computers.

So, you must have had an unusual typewriter that didn't have the "shift" key!

By the way, I had a good look at *xmodmap*, and I think that it may do exactly what you're after. Replace the Caps Lock function with the Shift key function, and lo and behold, you have it.

---

### Post by bernardolopes on 2009-05-06
I hope I'm not coming out too obnoxious in my continued statements... I really appreciate all the help and time given to this topic.

I replaced the Caps-Lock key with the Shift key using xmodmap and as I anticipated it did not solved my issue.

Only because I don't want to have to hold the Shift (now Caps) to capitalise. I want to press it and lock the capitalisation. It's not about position or something similar. It's about locking the capitalisation modifier on a key press (or key down) event, rather than on a key release (or key up) event.

In other words: my problem is that the capitalisation-toggler&lock event only happens when I release the key. I would really prefer it to happen when I simply press the key, disregarding if I ever hold it down or release.

I hope it's more clear now.

If you guys have more info please do post.

Thanks.

---

### Post by mick8985 on 2009-05-06
My keyboard does lock on key down rather than key release, perhaps the issue is the keyboard?

---

### Post by bernardolopes on 2009-05-06
The Caps-Lock upper case lock does work on the key press alone, but switching it to lower case doesn't.

I have tried on 3 machines with different keyboard brands and with other Linux distributions.

One thing that they had in common was the keyboard model as Brazilian ABNT and the layout as Brazil.

So I changed the layout and model to US and tested without rebooting. It doesn't solves.

---

### Post by LowSky on 2009-05-06
here is the effect of me using Windows Word Pad

aaa -- of course no caps
AAA -- with CAPS
AAAAAAAAAAAz - HOLDONG DONWN CAPS HOLDING DOWN 'A' AND THEN LETTING GO OF CAPS, IT ACTUALLY STOPS TYPING THE A, UNTIL I HIT ANOTHER KEY. then its lower case. 

Personally I think you just have really bad touch typing habits, just learn to use the shift key.

---

### Post by mick8985 on 2009-05-06
Ahh yeah now I see, it won't switch to lower case on my keyboard until key release aswell (british keyboard)
I would definitely see that as a bug as it is inconsistent with switching to uppercase. Although one of very little importance to the developers I would imagine. As you're probably the only person in the world who cares you might want to see about making a patch yourself. 
Does anyone know would the bug be with X or the kernel or what?

---

### Post by bernardolopes on 2009-05-06
I posted this problem on another forum. The first reply summarises everything I've said so far but with better words:

[http://www.allegro.cc/forums/thread/600166/810085#target](http://www.allegro.cc/forums/thread/600166/810085#target)

I find fair that people think that my typing style is terrible. And I really don't expect that Linux OSes have any obligation towards the minority of people that type like me.

I'll learn to proper use Shift and forget Caps-Lock only if I'm out of all resources.

Until then I'll keep trying to fix my issues on this question.

---

### Post by mick8985 on 2009-05-06
I agree that it is a bug and should be fixed, I'm sure the fix is simple too. Just where to submit the bug report, X or kernel.

---

### Post by Paddy Landau on 2009-05-07
> **bernardolopes said:**
> I posted this problem on another forum.
I read the posts there, and I understand your problem better.

Obviously, the solution that will help you best in the long term is to learn the placement of your fingers for touch-typing, and adjust your typing to the keyboard (keyboards aren't natural, although some say that the Dvorak keyboard is easier). You can get touch-typing tutorials on the Internet, some free.

The only alternative that I've thought of is to place a request for a patch on a programming freelancer site. You may be lucky enough to find someone who can make this change for just a few dollars. However, I don't recommend this as a solution, because (1) as soon as you use someone else's computer, you'll be stuck with the same problem, and (2) it won't be "future-proof" against upgrades and updates.

Good luck.

---

### Post by bernardolopes on 2009-05-07
I agree with you Paddy Landau.

I'm taking a tutorial on proper touch-typing.

Thank you guys for the help and patience.

Case closed.

---

### Post by hellocatfood on 2009-09-22
I switched to Ubuntu around 6 months ago and that was my only complaint. I've since learnt to use Shift instead of CAPS but I do feel that people shouldn't have to change to suit the OS.

Out of curiosity was a bug ever filed for this?

---

### Post by hellocatfood on 2009-10-02
For anyone else with this problem I've registered a bug for it in Ubuntu [http://bugs.launchpad.net/ubuntu/+bug/438447]("http://bugs.launchpad.net/ubuntu/+bug/438447")

---

### Post by Paddy Landau on 2009-10-02
> **hellocatfood said:**
> I switched to Ubuntu around 6 months ago and that was my only complaint. I've since learnt to use Shift instead of CAPS but I do feel that people shouldn't have to change to suit the OS.

Out of curiosity was a bug ever filed for this?
I disagree. It's not a bug. Caps-Lock was never meant for a single capital in a sentence; the OS should not have to change to suit the people -- OK, I'm kidding.

But it's not a bug. The intended function (going right back to when keyboards were mechanical -- yes, I'm old enough to remember) was to press Caps Lock *and release* before pressing another key.

Thus, it seems that Linux's method is the correct one, and Windows and Mac are the ones with the bug! (Remember that Unix, the predecessor of Linux, came before Windows and Mac.)

---

### Post by hellocatfood on 2009-10-02
> The intended function was to press Caps Lock and release before pressing another key.

That may be so, but I feel technology should adapt to its users needs. Myself and the OP know that we have crap/uncommon typing styles but we shouldn't have to change to suit the OS.

I think the user should at least be given a choice in how it operates.

---

### Post by random turnip on 2009-10-02
I didn't even know you could do that with the caps lock button 0.0

---

### Post by blueridgedog on 2009-10-02
> **hellocatfood said:**
> 
I think the user should at least be given a choice in how it operates.

And that is true...I hope future versions allow you to customize how it operates.

---

### Post by RisingFalcon on 2011-03-05
Anyone who has this problem please file a bug or agree to the one already filed.I seriously want this to get fixed in the very next update :\

---

