---
title: "Ubuntu 11.04 3d Effects and compiz"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by siretfel on 2011-05-01
Hi all,
So I upgradedto 11.04 and first thing ubuntu says is that my hardware doesn't support Unity.
So I continuned. Then I see that advanced desktop effects are not working.
So I installed compiz manager.
Nothing works.
No advanced effects.
How is this possible?At 10.10 I had my laptop configured so much with effects it could blow my mind!But it was working perfectly.
Now what's going on guys?

---

### Post by Hedgehog1 on 2011-05-01
Please run the **Additional Drivers** application from the **Control Center**:

[IMG]http://img820.imageshack.us/img820/7027/nattysystemsetting.png[/IMG]

Once the correct restricted drivers are loaded, you can use Compiz and Unity after your next reboot.

***The Hedge***

:KS

---

### Post by siretfel on 2011-05-01
I did when installed 11.04!!!:confused::confused:
Glxgears works perfectly!
I installed compizconfig settings manager,tried to enable cube,rotate cube ...nothing.Wobbling windows NO!
What's going on??

---

### Post by deepestblue on 2011-05-01
I have a Dell XPS L501X having a Nvidia Graphics card, with Optimus technology. I was running 10.10 without any issues, and compiz worked like a charm. Last night I upgraded to 11.04 and compiz doesn't work at all, despite enabling OpenGL. During installation I got a pop-up msg saying that my hardware does not support Unity, and I clicked OK and proceeded with the install. Changing the compiz settings have no effect at all.

Any help would be greatly appreciated

> **Hedgehog1 said:**
> Please run the **Additional Drivers** application from the **Control Center**:

Once the correct restricted drivers are loaded, you can use Compiz and Unity after your next reboot.


This solution doesn't work for me. I have the Nvidia driver activated, but I suppose it's due to the Optimus thingy, it's not being used (AFAIK, it's like an on-demand GPU, with the Intel HD Graphics enabled by default)


Cheers!

---

### Post by siretfel on 2011-05-01
So I am not the only one!
I also have Nvidia graph card in my laptop

---

### Post by Hedgehog1 on 2011-05-01
> **siretfel said:**
> I did when installed 11.04!!!:confused::confused:
Glxgears works perfectly!
I installed compizconfig settings manager,tried to enable cube,rotate cube ...nothing.Wobbling windows NO!
What's going on??

It is possible you have created a conflict of Compiz settings.  Desktop Cube and Unity don't mix so good (see  [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293") to see where Desktop Cube and Wobbly Windows ***are*** fine in Natty).

From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```

Logout and reboot...

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-01
I also have NVidia cards in both my desktop and laptop, and I am running Natty with functioning Compiz.  I get Unity when I select 'Ubuntu', and get the Desktop Cube and Wobbly Windows when I select 'Classic' (I set them up using ccsm like you did).

There are MANY different models of NVidia cards, however, I have have only tested 3 myself with Natty.


***The Hedge***

:KS

---

### Post by siretfel on 2011-05-01
> **Hedgehog1 said:**
> It is possible you have created a conflict of Compiz settings.  Desktop Cube and Unity don't mix so good (see  [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293") to see where Desktop Cube and Wobbly Windows ***are*** fine in Natty).

From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```

Logout and reboot...

***The Hedge***

:KS

First of all, thank you very much for your help!
I did what you advised, unity --reset.
What happed is that I saw the unity interface for the first time but then the laptop stuck.I tried to do it twice.Both times,although only the mouse worked(i.e. could move it around) the laptop was hanged and had to reset manually from the power button.
After i logged in the interface was reverted back to the usual ubuntu interface and not unity.
Again no 3d effects works.Back to square one.

Edit:
I installed compiz icon.Changed to Metacity and then back to compiz.
Unity appeared but my resolution is 1280x800 and coulndn't see date/time,and button to logout restart shutdown options.
Manualy reset.
Came back,change resolution to smaller and then again metacity and then compiz same thing.Could not press anything had to manually reset.
I will try a different driver for my nvdia and see what happens.

---

### Post by Hedgehog1 on 2011-05-01
Well - ***so close and yet so far***.

Those are all the ideas I have right now.

Hopefully another forum member will know what to try next.


***The Hedge***

:KS

---

### Post by siretfel on 2011-05-01
> **Hedgehog1 said:**
> Well - ***so close and yet so far***.

Those are all the ideas I have right now.

Hopefully another forum member will know what to try next.


***The Hedge***

:KS

I couldn't have said it better...so close so far!hahaha
Thanks A LOT again for your help!
):P

---

### Post by siretfel on 2011-05-01
:popcorn:hahahahahha
I cannot believe it. I changed the driver from recommended to the other one and it works
My head is going to explode.
Anyways,seems so far it is working.
Hopfuly this was the issue,the choice of driver.

---

### Post by siretfel on 2011-05-01
With much regret and after a lot of hours trying to make everything work I must admit that i found so many bags that I truly think to move back to u10.10.
For the moment i'll stay with 11.04 at the lovely,functional,easy,"old" gnome environment.
I hope the developers "listen" to our cries and make the improvements.
:frown::frown::frown::frown:

---

### Post by beew on 2011-05-01
> **deepestblue said:**
> I have a Dell XPS L501X having a Nvidia Graphics card, with Optimus technology. I was running 10.10 without any issues, and compiz worked like a charm. Last night I upgraded to 11.04 and compiz doesn't work at all, despite enabling OpenGL. During installation I got a pop-up msg saying that my hardware does not support Unity, and I clicked OK and proceeded with the install. Changing the compiz settings have no effect at all.

Any help would be greatly appreciated



This solution doesn't work for me. I have the Nvidia driver activated, but I suppose it's due to the Optimus thingy, it's not being used (AFAIK, it's like an on-demand GPU, with the Intel HD Graphics enabled by default)


Cheers!


Can't use Linux on that model because of Optimus, but I am curious that you said 10.10 works. There are many threads on the Dell XPSL510x on the Ubuntu forum and the Nv forum. Linux doesn't work on it.

---

### Post by deepestblue on 2011-05-01
> **beew said:**
> Can't use Linux on that model because of Optimus, but I am curious that you said 10.10 works. There are many threads on the Dell XPSL510x on the Ubuntu forum and the Nv forum. Linux doesn't work on it.

Trust me, Ubuntu 10.04 and 10.10 works on L501X. In fact, the first thing I did after I made sure the laptop was working, once it was delivered, was to install Ubuntu. Of course, the Nvidia graphics cannot be used, but the Intel-HD is good enough to run the compiz effects.

Attaching a screenshot (scaled to 80%) of my desktop, a few hours before "upgrading" to Natty, showing the ripples on water effect:
[ATTACH]190704[/ATTACH]

Everything except the Nvidia graphics, works out of the box - Wi-Fi, Bluetooth, webcam, touchpad, Function buttons, Additional multimedia buttons...

---

### Post by beew on 2011-05-01
> **deepestblue said:**
> Trust me, Ubuntu 10.04 and 10.10 works on L501X. In fact, the first thing I did after I made sure the laptop was working, once it was delivered, was to install Ubuntu. Of course, the Nvidia graphics cannot be used, but the Intel-HD is good enough to run the compiz effects.

Attaching a screenshot (scaled to 80%) of my desktop, a few hours before "upgrading" to Natty, showing the ripples on water effect:
[ATTACH]190704[/ATTACH]

Everything except the Nvidia graphics, works out of the box - Wi-Fi, Bluetooth, webcam, touchpad, Function buttons, Additional multimedia buttons...

Well if you cannot use the Nvidia card that you paid for it is not "working". If you just want your graphic card for Compiz you can  get any cheap laptop with an intel card. Compiz works flawlessly even on my 6 year old Dell D410 laptop, Unity also works out of the box, it is not really that big a performance requirement. If I spend the kind of money on a performance laptop not being able to use the Nvidia card is unacceptable.

Also, with Optimus even though you cannot use the Nvidia card it would still suck power and generate heat so it is worse than an expensive paperweight. Those threads I mentioned are about how to turn off the Nvidia card to make it a  paperweight instead of a cancer.

---

### Post by deepestblue on 2011-05-02
> **beew said:**
> Well if you cannot use the Nvidia card that you paid for it is not "working". If you just want your graphic card for Compiz you can  get any cheap laptop with an intel card. Compiz works flawlessly even on my 6 year old Dell D410 laptop, Unity also works out of the box, it is not really that big a performance requirement. If I spend the kind of money on a performance laptop not being able to use the Nvidia card is unacceptable.

Also, with Optimus even though you cannot use the Nvidia card it would still suck power and generate heat so it is worse than an expensive paperweight. Those threads I mentioned are about how to turn off the Nvidia card to make it a  paperweight instead of a cancer.

Well, I agree to what you said. But my expensive laptop does run Win7 too, and I use it for gaming alone. So, it's not a paperweight :) Enough of OT there

Anyway, my question still remains unanswered - what is it that prevents running of Compiz effects that were working fine in 10.10?

---

### Post by siretfel on 2011-05-04
> **deepestblue said:**
> Well, I agree to what you said. But my expensive laptop does run Win7 too, and I use it for gaming alone. So, it's not a paperweight :) Enough of OT there

Anyway, my question still remains unanswered - what is it that prevents running of Compiz effects that were working fine in 10.10?


+1 for your question.
I'm back to 10.10 and my laptop is flying:guitar:!!!

---

### Post by eentonig on 2011-05-04
> **beew said:**
> Well if you cannot use the Nvidia card that you paid for it is not "working". If you just want your graphic card for Compiz you can  get any cheap laptop with an intel card. Compiz works flawlessly even on my 6 year old Dell D410 laptop, Unity also works out of the box, it is not really that big a performance requirement. If I spend the kind of money on a performance laptop not being able to use the Nvidia card is unacceptable.

Also, with Optimus even though you cannot use the Nvidia card it would still suck power and generate heat so it is worse than an expensive paperweight. Those threads I mentioned are about how to turn off the Nvidia card to make it a  paperweight instead of a cancer.

Regarding NVidia cards and Optimus. Upgrade your BIOS to the latest version and disable Optimus in there. (If you're dual booting, windows might complain and reinstal your drivers. This will be fine after a reboot).

And for Ubuntu, install the NVidia drivers from their website or any other version than the recommended one. After this, you will be able to use NVidia graphics and Unity.

I have a Dell 6520 with NVidia NVS4200M.

---

