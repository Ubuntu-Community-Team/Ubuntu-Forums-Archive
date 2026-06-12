---
title: "[SOLVED] I lost the wifi icon on upper right panel"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by archer6 on 2008-06-13
I'm running Ubuntu 8.04 

I was customizing the panel across the top of the display. Adding some icons I clicked on Applications in the upper left of panel, hovered pointer over Accessories/ Dictionary right clicked on add this launcher to panel. All was going well. 

Then once I was done adding some of these, I noticed the 5 Blue vertical bars that I normally see on the right side indicating Wireless (WiFi) Signal Strength had disappeared. 

I have a good wifi connection, I simply must have done something to make the icon disappear. 

Where do I find this icon so that I can put it back in the panel? 

Thanks!

---

### Post by rlzyoner on 2008-06-13
Something along the lines of System -> Preferences -> Sessions
Now click the startup tab and enter nm-applet
Upon reboot, your icon should be there.

Alternatively, open a terminal and type nm-applet and press enter.
Icon is now back, but only until you close the terminal ;)

---

### Post by archer6 on 2008-06-13
> **rlzyoner said:**
> Something along the lines of System -> Preferences -> Sessions
Now click the startup tab and enter nm-applet
Upon reboot, your icon should be there.

Thank You!

I have it up and running and recovered from "User Error" that would be me......:)

For others that may read this later, as I did a search before posting and nothing was posted, here is what I did wrong to make it disappear. 

While adding icons to the panel, I must have accidentally "removed" the notification area. 

I followed your instructions accordingly, with one slight difference.
Here are the revised instructions for anyone that has this problem. 

1) System Preferences
2) Sessions / Startup programs tab, where all was fine.
3) Clicked on Current Session Tab / found filename nm-applet
4) Noticed in Style & State columns no icons appeared,  whereas other line entries had a preferences icon in the Style column, and a life preserver icon under the State column. 
5) Below the list of files window, was a button saying normal, I clicked on that and changed it to the preferences Icon.
6) Then I clicked on Apply & Close
7) Restarted to find my WiFi icon with all four bars lit up bright blue and when hovering, indicating that my WiFi strength was 93% which is excellent. 

So there is the revised instructions, via a joint effort from: rlzyoner and: archer6..... what a team!.....:)

Thanks Again rlzyoner, for your fast response, clear directions which enabled me to recover from the deadly USER Error - me again....:)

Cheers!

---

### Post by delizi on 2009-01-05
hi all,

i have the same problem as stated above. i've accidentally removed the wifi icon (the 4 bar) and can't put it back. I have done what proviosly stated but i restart the machine cant see the wifi icon.

any advice/help appriciated

ps: i am using ubuntu 8.04 for eee pc

---

### Post by argraff on 2009-02-17
After every install, I lose that icon in my futzing, and then I can't remember what it's called and I can't use my internet!!! Thank you for the instructions - now I can explore 8.10.

---

### Post by Flymo on 2009-02-18
Well, this did not solve my problem, sadly, but I found something that did - you see, I removed the wrong darn thing from my panel.  :oops:

...and the applet was gone.  Nothing said 'nm-applet' in the 'Add to Panel' dialogue.  Networking icon was not at all right....

I tried various things, items in this post, and ```
sudo nm-applet --sm-disable
```

...which did nothing that I could see, putting it in the background with '&' does the same...

[URL="http://www.linuxquestions.org/questions/linux-newbie-8/no-more-wireless-connection-in-mn-applet-ubuntu-7.10-598769/"]
Found this at Linux-questions which helped me.[/URL]

The relevant part there was :-
```
Check to see if nm-applet is a running (or sleeping)process. If so try this:
In the panel (toolbar) right click
- add to panel
- Notification area icon (scroll down under utilities)

```
...then added the Notification Area to the panel - Success!

Found that I had indeed started three instances of nm-applet, but I knew that already from trying ```
ps -ef | grep nm-applet
``` in the terminal.

All the while that my nm-applet display was missing, the WiFi was working fine.

Hope that something here was useful.

All the best, Ben

Ubuntu 804 on an Acer 4315, Celeron 540, intel 810 graphics
and Atheros WiFi using NDISwrapper, no problems with it until I did the deed.

---

### Post by dande on 2009-10-11
Thanks a lot for your info. This solved my issue too.
Thanks

---

### Post by Cold Man 1 on 2010-07-04
For ubuntu users on 10.04 and such all you have to do is right click on the upper bar, click on "add to panel" and scroll down till "notification area" add that and your done !!! it should be back instantly:popcorn:

---

