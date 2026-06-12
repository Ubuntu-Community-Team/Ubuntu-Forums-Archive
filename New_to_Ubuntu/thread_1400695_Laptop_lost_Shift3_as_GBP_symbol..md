---
title: "Laptop lost Shift3 as GBP symbol."
date: 2010-02-07
forum: New to Ubuntu
---

### Post by colintivy on 2010-02-07
Hi folks,
Had a shock, after years of working OK, suddenly lost the GBP symbol when pressing Shift3 (only gives 3). Looked at Preferences, Keyboard layout but none of the options of 102, 104 ,105 UK will bring it back. Also tried to reconfigure xserver-xorg which did not help either. I hope that it is not a foul-up on the keyboard itself and that something lurking in a file somewhere needs amending. Any clues? Am still on Hardy/OOo/Firefox.

Regards,

colintivy :confused:

---

### Post by colintivy on 2010-02-22
No whizz kids out there seem to have spotted my plea to improve my ignorance. Very sad but I have not progressed any further with this despite intermittent attempts to find the bits of program that may have gone adrift.


colintivy :confused:

---

### Post by steve-shinn on 2010-02-22
Does any of the other shift num features work eg shift 5 = % or shift 6 = ^

---

### Post by colintivy on 2010-02-22
Hi Steve!

Thank goodness there is someone out there!! It seems that all the other Shift+ Numbers are fine which is the oddity. If you look at my post on the General Help Forum you will see a longer explanation which may help. The Error Signal panel seems to agree that there is a problem somewhere but I do not understand the information and precisely how I am to react to it. My feeble attempts have not made any significant progress. I know that I can always insert my pound sign but that is only available from OOo Writer Character Map which does not help in other modes. Hope you can elucidate.

colintivy :)

---

### Post by _khAttAm_ on 2010-02-22
I don't know if similar options exist on Hardy, but here is something I found that might be helpful. I'm using Lucid.

Goto Keyboard Preferences>Layout and then make sure you have layout corresponding to your language. I have my default set as USA and I get '#' with USA selected. Whenever I add United Kingdom and move it up, then I get '£'. You may want to try out USA and see if you get '#'.

---

### Post by colintivy on 2010-02-22
Hi _khAttAm_

Thanks for that,tried US but still getting 3. Error Meesage "Error activating XKB configuration" still present despite attampts to reconfigure. Forum posted by brennon80 in 30th Oct 2009 indicates it is not unknown problem without much idea of cure!!

colintivy :confused:

---

### Post by mikechant on 2010-02-22
This post
[http://www.linuxquestions.org/questions/linux-software-2/error-activating-xkb-configuration-368174/](http://www.linuxquestions.org/questions/linux-software-2/error-activating-xkb-configuration-368174/)

has two solutions for the
"Error activating XKB configuration" error which worked for somebody. I would try the solution described in the final post first, since this looks relatively harmless (i.e. unlikely to make things worse).

---

### Post by colintivy on 2010-02-23
Hi Mike!

Thanks for introducing me to LQ, I have registered & posted there and await responses. Many of their posts go back a long way and may not be relevant to today's build. Being USA-based I fear that my peculiar odditiy may not have appeared to them before.

colintivy still:confused:

---

### Post by steve-shinn on 2010-02-23
Have you tried booting the laptop from a live cd to see if the shift 3 (£) works ? If it doesn't then it would indicate a laptop keyboard fault, if it does, then it must be a software issue.

---

### Post by HermanAB on 2010-02-23
Howdy,

I have had a problem like this where the capital T disappeared.  This must a problem with Xorg.  I never got to the bottom of it (since I re-installed a new version of Linux), but you may be able to fix it using Xmodmap.  Some googling will find you some information.  

Basically, you got to put a .xmodmap file in your home directory with some lines in it to remove and redefine the offending key.  Note that each time after changing this file, you got to log out and log in again to restart X. So it may take a few hours of experimentation.

---

