---
title: "driver for ancient compaq keyboard ?"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by henry cow on 2010-07-26
Go ahead, start scoffing at this pathetic old fart and his absurd request.

I have a keyboard that I adore. Actually, I have 3 or 4 of them that I bought at yard sales and thrift stores as backups, because I love them so much. I have owned and used a whole lot of keyboards since I started personally computing on an Apple II in 1984, and I believe that the Compaq SK-2800 is the perfect keyboard.

It came with Presarios vintage 2000-01-02, somewhere along in there, before the HP takeover. It is a large heavy beige keyboard, with tall clicky keys. It is an "internet" keyboard with a series of buttons at the top that launch your half-dozen favorite programs or sites with one touch, along with a full array of music controls like volume, mute, fast forward, next track, etc. Best of all, those extra keys are "rubbery" which I love (and especially on calculator keypads).

So, under Linux (ie now) the standard keys work fine, but the extra keys don't. I have the drivers including .exe and .ini (difficult but not impossible to find and download for XP) and I would love to get this lovely and useful function to work in the Linux Universe.

Will ndiswrapper, or something like it, do the trick? I do not want to go to the aggravation of Wine or anything on that level. Is there just something simple that will make my beloved keyboard work to its fullest?

And lastly, since this has a PS2 plug, is there also a way to plug it into a USB port in the future? I would love to use these keyboards for decades, or until something better comes along (not likely). 

Thanks!

---

### Post by egalvan on 2010-07-26
Laptops have extra keys that work under Linux...

I would suggest using Google to search for any info on this,
if none is forthcoming here,...


Also, PS/2 /USB adapters are available..
I have several in my took kits...
I use them to plug in my PS/2 keyboard and mouse into "modern" machines that only have USB, 
or into laptops that only have one PS/2 plug

I bought some at Fry's, and got a few on eBay...
search for "ps2 usb", or try other combos...
also, local "mom&pop" computer repair shops may have them.

*edit*

found this via Google

[http://www.linuxquestions.org/questions/linux-hardware-18/drivers-for-compaq-keyboards-73206/](http://www.linuxquestions.org/questions/linux-hardware-18/drivers-for-compaq-keyboards-73206/)


further, found this on Google's Cache Farm

[http://webcache.googleusercontent.com/search?q=cache:ns_LNx3IGZYJ:linux.omnipotent.net/article.php%3Farticle_id%3D12340+Compaq+SK-2800+linux&cd=10&hl=en&ct=clnk&gl=us&client=firefox-a](http://webcache.googleusercontent.com/search?q=cache:ns_LNx3IGZYJ:linux.omnipotent.net/article.php%3Farticle_id%3D12340+Compaq+SK-2800+linux&cd=10&hl=en&ct=clnk&gl=us&client=firefox-a)

---

### Post by Res2216firestar on 2010-07-26
System>Prefs>Layout tab. Try clicking on the model name to find the layouts menu and try compaq layouts.

---

### Post by egalvan on 2010-07-26
And I'm not about to scoff at your choice of keyboards...

that's a very personal choice... some keyboards just "work" better than others.

My personal choice for heavy typing is one of the ancient (circa 1984) IBM "Cliky" keyboards...
the ones that were clones of the Selectric Typewriter's keyboard.
These had IBM's quality, and were priced to match...$250 in 1980" $$$
but they last forever. (IIRC, they were rated at 100,000,000 strokes)

I had to solder in a small circuit to make them compatible with USB.

They are still clicking.


( But I **will** scoff at your "ancient circa 2000" statement...
that's only 10 years old... still wet-behind-the-ears :) )

---

### Post by Zeike on 2010-07-26
I know how you feel.  I adore my Sun keyboard but all my friends think I'm crazy.

Are the keys sending signals at all?  Have you tried setting shortcuts in the "Keyboard Shortcuts" dialog?  What happens if you run 'xev' and press the keys in quesion?

---

### Post by henry cow on 2010-07-26
Firestar - WOW - thanks!

It simply never occurred to me that "Compaq 18" would be on the option list, waiting for me to find it.

The audio buttons work fine, but I can't seem to find a way to make the assignable buttons take an assignment, even the supposedly "pre-assigned" ones.

Got any ideas?

ps - I read the Warriors and the Seekers with my kids, and they are really first-rate books. I am very curious to see where the Seekers end up, and what the deal is with Ujarak.

---

### Post by Zeike on 2010-07-26
> **henry cow said:**
> The audio buttons work fine, but I can't seem to find a way to make the assignable buttons take an assignment, even the supposedly "pre-assigned" ones.

Go to the keyboards shortcuts dialog in system->preferences.  Click add.  Type the command you use.  Click Ok. Click where is says "disabled" in the list next to your newly created shortcut.  Press the key you wish to assign.

---

### Post by henry cow on 2010-07-26
Zeike - 

Thank you. What format is the command asking? For instance, to get a Word Processor, I typed "Open Office.org Writer" but that did not seem to work.

I am a newbie. In Microsoft, I would go to "C:\Program Files\Microsoft\Office\Winword.exe" or something similar.

What is the equivalent in Linux? Please forgive my ignorance.

And, in the same line of questioning, how would I list my email client account at gmail.com? I tried "https://myaccount@gmail.com", and copying and pasting what I found in the slot at the top of the screen, to no avail.

Thank you so much.

---

### Post by Zeike on 2010-07-26
To see the command needed to run any program that you find in your main menu, you can go to "System->Preferences->Main Menu" and look at the properties for that menu item.

for example, OO Writer is 'ooffice -writer'.

To open a webpage you can use the 'gnome-open' command followed by the url you wish to open.  This will open it in whatever happens to be your default browser.  To open gmail try: 'gnome-open [https://mail.google.com](https://mail.google.com)'

---

### Post by SoFl W on 2010-07-26
> **henry cow said:**
> Go ahead, start scoffing at this pathetic old fart and his absurd request. !

And no one scoffed at you!

I know a few people that have favorite keyboards, I had one that had the old fat circle connector, I think it was a DIN-5 Type.  Used the PS/2 to DIN5 connector until the USB keyboards came out.  Some of the letters on that ole keyboards letters were worn off.

Glad you got it working.

---

### Post by anewguy on 2010-07-27
The older keyboards are from a time right before everything got "light" in order to make the price of a PC fall so much.  I'm a big fan of the older keyboards or of a new one when it's heavy, has a lot of tactile feedback, etc. (but they cost more ;) ).  We've got 2 of those old keyboards, including 1 that had the built in page scanner.  I haven't really tried to use them in Linux.  I'm sure everything else is a matter of knowing what the key is sending, then assigning an action to that string.

As far as using ndiswrapper - ndiswrapper is only for network drivers.

Best of luck!
dave ;)

---

### Post by henry cow on 2010-07-31
I appreciate all the suggestions that you all have offered, but it is still not working.

The CD buttons like fast forward and mute work, but the main 7 "internet" buttons are dead. I would like for them to activate my browser, gmail client, spreadsheet, writer, gimp, and other websites or programs that I change from time to time.

I used System/Preferences/Keyboard Shortcuts, then chose ADD. I typed in my request and pushed the desired button, then APPLY. I also tried switching the order of some of these actions in case I missed something.

It added whatever I wanted to the list, but the keys remained dead. 

Can you give me any other specific, step by step instructions?

Thanks a lot.

---

### Post by Windows Nerd on 2010-07-31
> **Zeike said:**
> To see the command needed to run any program that you find in your main menu, you can go to "System->Preferences->Main Menu" and look at the properties for that menu item.

for example, OO Writer is 'ooffice -writer'.

To open a webpage you can use the 'gnome-open' command followed by the url you wish to open.  This will open it in whatever happens to be your default browser.  To open gmail try: 'gnome-open [https://mail.google.com](https://mail.google.com)'
Wouldn't it be
```
oowriter [file_to_edit]
```?

And also, you can open any webpage with both Google Chrome or Firefox by:

```
firefox [url]
```
```
chromium-browser [url]
```

---

### Post by walt.smith1960 on 2010-08-01
for the "nonstandard" keyboards, here are a couple choices:

[http://pckeyboards.com/](http://pckeyboards.com/)

[http://pckeyboards.stores.yahoo.net/ind.htm](http://pckeyboards.stores.yahoo.net/ind.htm)

---

### Post by henry cow on 2010-08-01
Thanks folks, but it is still not working. Walt, were you pointing me toward instructions or places to buy additional keyboards?

I think there must be something a little off in post #7 by Zeike.

I have followed those instructions, and slight variations of them, a couple of dozen times, and everything seems to work except the actual working of the buttons. My new assignment gets added to the list, the proper entries are found in the "name" and "command" fields, but it never seems to "take" ....

When I do System/Preferences/Keyboard Shortcuts, and click "add" I get a Keyboard Shortcuts dialogue box that has blanks for "name" and "command" and selections "cancel" or "apply"

After filling in the blanks and clicking "apply" I am sent back to the main list with my item highlighted in blue and listed as "disabled"

That stays listed as "disabled" and when I click (right or left) on it, I get the previous box with my entries still filled in. I can click on my desired button, and/or "apply" but nothing ever changes.

It seems like there is another step that I am missing to actually assign the action to the key (or the key to the action, whatever)

The Windows driver has a wizard that works in a vaguely similar way, so I don't think I am too far off.

Thank you again for your help.

---

### Post by lkraemer on 2010-08-01
Have a look here:
[http://www.linuxquestions.org/questions/linux-hardware-18/drivers-for-compaq-keyboards-73206/](http://www.linuxquestions.org/questions/linux-hardware-18/drivers-for-compaq-keyboards-73206/)

```

Normally you dont need drivers for a keyboard , it's more about
finding out the keycodes that each multimedia key produces
and remapping it.

[http://www.tldp.org/HOWTO/Intkeyb/index.html](http://www.tldp.org/HOWTO/Intkeyb/index.html)
[http://www.tldp.org/HOWTO/Keyboard-and-Console-HOWTO.html](http://www.tldp.org/HOWTO/Keyboard-and-Console-HOWTO.html)

also has some usefull info
use xev to get your keycode
use xmodmap or xbindkeys to map them

```

Look into a program called "lineak"
[http://lineak.sourceforge.net/index.php?nav=docs](http://lineak.sourceforge.net/index.php?nav=docs)
[http://lineak.sourceforge.net/](http://lineak.sourceforge.net/)

Also, you can run "xev" and press the key you want to use and get its keysim, exemple of a xev output :
KeyRelease event, serial 26, synthetic NO, window 0x3e00001,
root 0x46, subw 0x0, time 521316987, (205,196), root:(209,222),
state 0x50, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
XLookupString gives 0 bytes: ""

FocusOut event, serial 26, synthetic NO, window 0x3e00001,
mode NotifyNormal, detail Notify

Then run this command to map the key : xmodmap -e "keycode xx = less greater"

Add this command in the "startup session commands" or in your .bashrc to do it automatically.

REF:
[http://ubuntuforums.org/archive/index.php/t-106209.html](http://ubuntuforums.org/archive/index.php/t-106209.html)


Also,
You may want to try "xkeycaps".


lk

---

