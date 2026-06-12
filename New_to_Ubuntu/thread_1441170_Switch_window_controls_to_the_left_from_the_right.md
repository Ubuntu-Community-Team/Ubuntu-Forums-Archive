---
title: "Switch window controls to the left from the right?"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by Jimleko211 on 2010-03-28
I'm a ubuntu vet but I'm re-migrating from Mac OS X, and I've grown accustomed to having my window controls (close, maximize, minimize) to the left.  I used to know how to make this happen in Ubuntu, but I forgot how, and I don't know what to search in Google to find out how to.  Can anyone help me?

---

### Post by bluelamp999 on 2010-03-28
ALT-F2 to fire up the Run dialogue control.

Type in ```
gconf-editor
``` and select Run, this will bring up the Configuration Editor...

Then apps>metacity>general and look for the *button_layout* parameter and change the value to ```
close,maximize,minimize:menu
```

Then you should have Mac style window controls...

---

### Post by KdotJ on 2010-03-28
Ubuntu 10.04 (released next month) has this feature as default, with the window buttons on the left side

---

### Post by Jimleko211 on 2010-03-28
Thank you very much, Bluelamp.  It worked perfectly! :D

---

### Post by bluelamp999 on 2010-03-28
> **KdotJ said:**
> Ubuntu 10.04 (released next month) has this feature as default, with the window buttons on the left side

The buttons may be on the left but the order is not the same...

The 10.04 default layout is *maximize, minimize, close* whereas the Mac layout is *close, maximize, minimize*.

---

### Post by bluelamp999 on 2010-03-28
> **Jimleko211 said:**
> Thank you very much, Bluelamp.  It worked perfectly! :D

You're welcome!

Expect to see a lot more of similar requests popping up on the forums as folk realise that the new default button layout sucks!

---

### Post by Gray_uncle on 2010-05-12
Thank you! Worked great.

---

### Post by Theo L on 2010-05-13
> **bluelamp999 said:**
> 
Expect to see a lot more of similar requests popping up on the forums as folk realise that the new default button layout sucks!

You got that right :(

Since I updated my Ubuntu I'm constantly reaching for the controls in the wrong corner of each window. I was a Windows user before and the right corner controls have been etched in my memory permanently. 

Unfortunately I'm not able to migrate the controls from left to right using the method explained in this thread: When trying to edit the button_layout I get: " Currently pairs and schemas can't be edited. This will be changed in a later version."

Oh man!

If I had known about this I wouldn't have updated to the new version. Really.

---

### Post by Theo L on 2010-05-13
> **Theo L said:**
> 
Unfortunately I'm not able to migrate the controls from left to right using the method explained in this thread: When trying to edit the button_layout I get: " Currently pairs and schemas can't be edited. This will be changed in a later version."


Update: I had another look at the button_layout scheme and took a bold step: I " unset"  that scheme and close the editor.

Than I reopened the editor and saw the button-layout could now be edited, so I typed: menu: maximize, minimize,close

and hey, there are my right corner window controls again! What a relief. Sometime small things like this can make me day :)

---

### Post by pete_m on 2010-05-13
P.S.  i've downloaded the emerald window decorator and i can choose the left/right buttons  from there.
don't know what is the Lucid default decorator . .


thanks all for an enlightening thread.. first read a bit back n it helped me get stuck in with gconf

i''m an EEE PC user planning an imminent move to Ubuntu Lucid & Debian Sid . . .
 i look forward first to the performance improvements the move will make and to the luxury of choosing the position of those pesky buttons and the window menu.
hopefully configuring them in gconf-editor will be all that's needed to get my right-buttoned karmic stuff upgraded.

is there an easy way to create numbers of gnome-sessions( with different gnome  desktop schemes)  to  then access them at log-in screen ?
is there an easy way to create numbers of X-sessions s( with different windows managers ( ice, flux, kde ) and desktop schemes )to  then access them at log-in screen ?

what files do i need to manage to enable easy back-up and restore of Gnome and X sessions ?


i've put some work into my existing Ubuntu install based on 9.10 karmic nbr2 and am very happy with the results - full credit and thanks to all

screenshots of my work in progress at

[http://www.youtube.com/watch?v=YoI4wRVVjBs](http://www.youtube.com/watch?v=YoI4wRVVjBs)

writing on a live eb4 session from usb stick before heading back to my  9.10 main machine- which reminds me to attend to the dummy upgrade i've been performing from eb4

Hey i there[SIZE=5] **[SIZE=3]KdotJ[/SIZE]**[/SIZE] - yr helpful posts have been  in lots of threads i've  visited ..

... changed yr signature ? whose idea was that ...


googled you old signature ...
[http://www.google.co.uk/search?hl=en&client=firefox-a&hs=RHk&rls=org.mozilla%3Aen-GB%3Aofficial&q=%22I%27m+a+PC%2C+and+removing+the+Windows+partition+from+my+hard+drive+was+my+idea.%22+&btnG=Search&aq=f&aqi=&aql=&oq=&gs_rfai=]("http://www.google.co.uk/search?hl=en&client=firefox-a&hs=RHk&rls=org.mozilla%3Aen-GB%3Aofficial&q=%22I%27m+a+PC%2C+and+removing+the+Windows+partition+from+my+hard+drive+was+my+idea.%22+&btnG=Search&aq=f&aqi=&aql=&oq=&gs_rfai=")

---

