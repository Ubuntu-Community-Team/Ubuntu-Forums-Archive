---
title: "Display Question"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Tux_2009 on 2009-06-02
Hi, 
I am using Linux on a laptop, and wonder how I should go about making an external CRT monitor work?
I would like to use the external monitor instead of the laptop's screen, as the laptop's screen is quite small, and slightly hard to read.

When I plug in the CRT monitor, nothing happens, it will stay in standby mode as if it was not receiving ny signal? I appreciate any help!

Sorry for not so good English.

-Tux_2009

---

### Post by nandemonai on 2009-06-02
There is likely a key combo for your laptop that enables the external screen. Usually Fn - "one of the F keys". For example on my ancient Toshiba it's Fn-F5.

---

### Post by wpshooter on 2009-06-02
Have you gone into the BIOS to make sure that the video display mode is set to **BOTH** and not just LCD ?

Yes, or F key combination as stated above.

---

### Post by Yvan300 on 2009-06-02
Yeah mines is fn+f8, usually dell prints the fn keys in a blue colour. Lool for one marked crt/lcd.

---

### Post by Tux_2009 on 2009-06-02
Hello, and thanks to you for the replys!

Unfortunately, this did not solve the problem.:(

The laptop is quite old too, about 4 years or even more? HP ze4400. In the BIOS there is no setting for display, only some rather basic functions.

The functions keys does not work, I tried the command (fn + f5 in this case) and some others too (like volume, screen brightness). 

Strange thing I noticed: during startup (or shutdown), during when the computer is in textual based mode, the external display will show the text on the screen of the laptop. But when the operating system in itself starts (during start, when the login screen will appear), the external display 'disconnects'.


Great thanks for any further ideas?:)

-Tux_2009

---

### Post by Yvan300 on 2009-06-02
Are you using the free or proprietary drivers. You may need them in order to enable the use of a secondary display. If your running jaunty jackalope and your card is ATI then most likely support for it has been dropped by the ATI team and you'll have to revert to intrepid Ibex where there are propietary drivers available for most cards.

---

### Post by Tux_2009 on 2009-06-03
> **Yvan300 said:**
> Are you using the free or proprietary drivers. You may need them in order to enable the use of a secondary display. If your running jaunty jackalope and your card is ATI then most likely support for it has been dropped by the ATI team and you'll have to revert to intrepid Ibex where there are propietary drivers available for most cards.

Hi, thanks for the reply!

I searched for the correct drivers (I have an integrated ATI card), and i have find [THESE]("http://support.amd.com/us/gpudownload/Pages/linux-radeon-prer200.aspx").
They are from 2006 though.:-? And they will not install due to me having so much newer X.org version.

Can I do anything to make them install?

Thank you for further help!

-Tux_2009

---

### Post by blackened on 2009-06-03
If your machine recognizes that the monitor is plugged in, then you should be able to make it work using the **System -> Preferences -> Display** program. Usage is pretty self-explanatory.

---

### Post by Yvan300 on 2009-06-03
I \'m sorry, but the only way to make the drivers install, as far as i know, is to revert to the previous version of Ubuntu which is intrepid Ibex. I had to do this myself due to the poor drivers available in jaunty.

---

