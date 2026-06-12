---
title: "A few things I don't know how to fix"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by SaosinHax on 2011-04-02
Since I changed to Ubuntu there have been 3 things I wanted to fix and a big question I had.
<SOLVED>
The question is , where do programs install to?
aka the "Program Files" folder in Windows
</SOLVED>

the things i wanted to get fixed:
<UNSOLVED>
On windows, to get a @ I had to do CTRL + ALT + 2/é/@

but on Ubuntu that key is not working, I have to use Alt Gr + é/2/@ instead, which is quite annoying , definitely when I'm programming , then I have to use the { } and [ ] all the time
</UNSOLVED>

the second thing is:
<UNSOLVED>
When I press on the middle key on my mouse ( the scrolling wheel or whatever they call it , nothing happens , when in Windows it puts this round thingy on the page which allows me to scroll through my page very fast
</UNSOLVED>
<SOLVED>
the third thing is,  is there any way to get (like in windows) a dynamic desktop background? switching 10 pictures every hour?</SOLVED>

---

### Post by SaosinHax on 2011-04-02
Since I changed to Ubuntu there have been 3 things I wanted to fix and a big question I had.

The question is , where do programs install to?
aka the "Program Files" folder in Windows


the things i wanted to get fixed:

On windows, to get a @ I had to do CTRL + ALT + 2/é/@

but on Ubuntu that key is not working, I have to use Alt Gr + é/2/@ instead, which is quite annoying , definitely when I'm programming , then I have to use the { } and [ ] all the time


the second thing is:

When I press on the middle key on my mouse ( the scrolling wheel or whatever they call it , nothing happens , when in Windows it puts this round thingy on the page which allows me to scroll through my page very fast


the third thing is,  is there any way to get (like in windows) a dynamic desktop background? switching 10 pictures every hour?

---

### Post by Vaphell on 2011-04-02
programs in general are installed to /usr/bin and the very core system tools in /bin

scrolling with middle-click:
middle click is 'paste highlighted text' in linux, which is an extremely cool feature, much better than having to go ctrl-c, ctrl-v route (though that works too in ubuntu) Either way, in firefox (i assume you use it, even though you gave no info about browser or language you use) type about:config in address bar, find general.autoScroll key and set it to TRUE

wallpaper changer:
install drapes or wally

keyboard layout problem:
no language specified and i don't get what @ has to do with {[

---

### Post by 23dornot23d on 2011-04-02
> 
Since I changed to Ubuntu there have been 3 things I wanted to fix and a big question I had.

The question is , where do programs install to?
aka the "Program Files" folder in Windows
Slightly different to windows you rarely need to know where the programs are stored .....
To find them though ..... use the Software Center or Synaptic Package Manager.

> 
the things i wanted to get fixed:

On windows, to get a @ I had to do CTRL + ALT + 2/é/@

but on Ubuntu that key is not working, I have to use Alt Gr + é/2/@  instead, which is quite annoying , definitely when I'm programming ,  then I have to use the { } and [ ] all the time
Depending on the keyboard and layout you have set up this could change ..... so the easiest way is to[** look here **]("http://wiki.linuxquestions.org/wiki/Accented_Characters")

Also another answer is here [LINK]("http://ubuntuforums.org/showthread.php?t=1718526") for things like Open Office ...

> 
When I press on the middle key on my mouse ( the scrolling wheel or  whatever they call it , nothing happens , when in Windows it puts this  round thingy on the page which allows me to scroll through my page very  fast
The middle mouse scroll wheel should work just the same ......  there is a option to change the mouse control settings though in the ..... System preferences menu ... 

I have a USB mouse plugged into my Acer laptop and it picks up perfectly well .... what computer and how is it attached
USB or other connection ?


> 
the third thing is,  is there any way to get (like in windows) a dynamic desktop background? switching 10 pictures every hour?                                                           
There is .... [Desktop Drapes]("http://maketecheasier.com/desktop-drapes-another-gnome-wallpaper-changer/2008/07/29") ....

Hope this helps ...

---

### Post by matt_symes on 2011-04-02
Hi

> **SaosinHax said:**
> Since I changed to Ubuntu there have been 3 things I wanted to fix and a big question I had.

The question is , where do programs install to?
aka the "Program Files" folder in Windows

They can go in a number of places. Depending on what programs they  are.

/bin and /sbin for binaries and system binaries.
/usr and /opt for other programs.

> the things i wanted to get fixed:

On windows, to get a @ I had to do CTRL + ALT + 2/é/@

but on Ubuntu that key is not working, I have to use Alt Gr + é/2/@ instead, which is quite annoying , definitely when I'm programming , then I have to use the { } and [ ] all the time

Not sure about this one. What keyboard are you using ? Yoou can remap keys using xmodmap. Maybe you could remap it.

```
man xmodmap
```

> When I press on the middle key on my mouse ( the scrolling wheel or whatever they call it , nothing happens , when in Windows it puts this round thingy on the page which allows me to scroll through my page very fast

I am not 100% sure but i don't believe you can do that in Ubuntu. I don't have a middle scroll button. Others will correct me if i am wrong.

> the third thing is,  is there any way to get (like in windows) a dynamic desktop background? switching 10 pictures every hour?

[http://www.liberiangeek.net/2010/09/automatically-change-desktop-background-ubuntu-10-10-maverick-meerkat-wally/](http://www.liberiangeek.net/2010/09/automatically-change-desktop-background-ubuntu-10-10-maverick-meerkat-wally/)

EDIT: DOH. Beaten to it. And we both wrote novels :D

Kind regards

---

### Post by Razmear on 2011-04-02
re: #1, in addition to getting installed in /usr/bin, there are hidden directories in your home folder tha contain most of the configuration info. Hit show hidden files in the file browser and see the directorys that start with .'s. Only the executable gets droped in the /usr/bin folder (mostly).

No idea about the @, it's just shift-2 on my KB.

eb

---

### Post by 23dornot23d on 2011-04-02
> 
EDIT: DOH. Beaten to it. And we both wrote novels :grin:
Lols ...... but I think we almost covered everything between us ..... good answers too ..... was not sure whether or not to mention where the files are as there is not a lot you can do with them without using the Software Center and Package managers and it is confusing working out their storage  places even when you know the system . 

I just know that the majority can be run from the menus ...... other more obscure ones we run from a terminal window ..... but most users should rarely need to use these nowadays ....... and should never really need to access the /bin - /sbin - /usr/bin - /usr/sbin directories anyway .... messing with them manually would probably lead to a broken system ..... and you need root privileges to change them ..... not advised really .

Two [Threads Same thing here]("http://ubuntuforums.org/showthread.php?t=1719643")

---

### Post by matt_symes on 2011-04-02
Hi

> **23dornot23d said:**
> Lols ...... but I think we almost covered everything between us ..... good answers too ..... was not sure whether or not to mention where the files are as there is not a lot you can do with them without using the Software Center and Package managers and it is confusing working out their storage  places even when you know the system . 

I just know that the majority can be run from the menus ...... other more obscure ones we run from a terminal window ..... but most users should rarely need to use these nowadays ....... and should never really need to access the /bin - /sbin - /usr/bin - /usr/sbin directories anyway .... messing with them manually would probably lead to a broken system ..... and you need root privileges to change them ..... not advised really .

And that is excellent advice. :P

Kind regards

---

### Post by 23dornot23d on 2011-04-02
You have another thread same questions [LINK]("http://ubuntuforums.org/showthread.php?p=10628365#post10628365")

---

### Post by cbowman57 on 2011-04-02
Add DesktopNova to that list of wallpaper changers.

---

### Post by SaosinHax on 2011-04-02
> **23dornot23d said:**
> Slightly different to windows you rarely need to know where the programs are stored .....
To find them though ..... use the Software Center or Synaptic Package Manager.

Depending on the keyboard and layout you have set up this could change ..... so the easiest way is to[** look here **]("http://wiki.linuxquestions.org/wiki/Accented_Characters")

Also another answer is here [LINK]("http://ubuntuforums.org/showthread.php?t=1718526") for things like Open Office ...

The middle mouse scroll wheel should work just the same ......  there is a option to change the mouse control settings though in the ..... System preferences menu ... 

I have a USB mouse plugged into my Acer laptop and it picks up perfectly well .... what computer and how is it attached
USB or other connection ?


There is .... [Desktop Drapes]("http://maketecheasier.com/desktop-drapes-another-gnome-wallpaper-changer/2008/07/29") ....

Hope this helps ...

Thanks alot, however theres a few things I dont get atm

Depending on the keyboard and layout you have set up this could change ..... so the easiest way is to[** look here **]("http://wiki.linuxquestions.org/wiki/Accented_Characters")


I dont really understand what im supposed to do here :/
and my mouse is connected using USB

---

### Post by cariboo on 2011-04-02
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by SaosinHax on 2011-04-02
> **Vaphell said:**
> programs in general are installed to /usr/bin and the very core system tools in /bin

scrolling with middle-click:
middle click is 'paste highlighted text' in linux, which is an extremely cool feature, much better than having to go ctrl-c, ctrl-v route (though that works too in ubuntu) Either way, in firefox (i assume you use it, even though you gave no info about browser or language you use) type about:config in address bar, find general.autoScroll key and set it to TRUE

wallpaper changer:
install drapes or wally

keyboard layout problem:
no language specified and i don't get what @ has to do with {[

my browser is google chrome and about:config doesnt work in GC :/
also
Im from Belgium and here all windows computers use ctrl + alt + @ to press @,
ctrl + alt + [ to press [
ctrl + alt + { to press {

but now i have to use Alt Gr + } to press }

---

### Post by Vaphell on 2011-04-02
chrome? look at this then:
[http://www.chromeextensions.org/appearance-functioning/smoothscroll/](http://www.chromeextensions.org/appearance-functioning/smoothscroll/)

cheesus christ, this would be probably the last possible layout i'd think of using when coding, 3 keys to achieve basic programming characters? That's insane :D
Out of curiosity: what do @ and [ keys do when you press them with/without shift then? In Polish layout we get language specific letters basically with altgr+basic_char and the rest of standard keyboard layout is untouched and all keys do what they say they do :)

edit: wikipedia to the rescue
[http://en.wikipedia.org/wiki/File:Belgian_pc_keyboard.svg](http://en.wikipedia.org/wiki/File:Belgian_pc_keyboard.svg)
that sucks :-)

---

### Post by SaosinHax on 2011-04-02
> **Vaphell said:**
> chrome? look at this then:
[http://www.chromeextensions.org/appearance-functioning/smoothscroll/](http://www.chromeextensions.org/appearance-functioning/smoothscroll/)

cheesus christ, this would be probably the last possible layout i'd think of using when coding, 3 keys to achieve basic programming characters? That's insane :D
Out of curiosity: what do @ and [ keys do when you press them with/without shift then? In Polish layout we get language specific letters basically with altgr+basic_char and the rest of standard keyboard layout is untouched and all keys do what they say they do :)

edit: wikipedia to the rescue
[http://en.wikipedia.org/wiki/File:Belgian_pc_keyboard.svg](http://en.wikipedia.org/wiki/File:Belgian_pc_keyboard.svg)
that sucks :-)

Ive been using it since I was 10 so I'm pretty used to using 3 keys

So can anyone help? and System - Preferences- Mouse doesnt work :(

---

### Post by 23dornot23d on 2011-04-02
The keyboard ..... 

In the menu .....

System - Admin - Language Support
are you all set up with everything that you need for your country ......

**What computer do you have ..... can you post a link to it ..... **show the keyboard
layout ......  too

( Have you tried installing  Firefox 4 ..... you may find the mouse works ok in that ..... )
Does the scroll wheel work in any other applications ....

---

### Post by Kixtosh on 2011-04-02
I think I understand what SaosinHax means when he's talking about the @ character. I use a U.S. keyboard on two laptops, but I also have to type in French sometimes, so I switch keyboard layout frequently (and ignore what's actually written on the keys themselves). I also have one very old laptop with an actual French keyboard.

So, on a French (and apparently Belgian keyboard), you can use one hand, on the appropriate side of the keyboard, to hold the CTRL and ALT keys, and your other hand to type the numbers keys on the opposite half of the keyboard to produce what (I think) are refered to as "third level" characters. This makes it a fairly intuitive two handed operation with no contorting of the limbs (your hands never have to cross each other). 

Ubuntu does not allow for this, so you have to use the right side only AltGr (I think this is always right ALT on U.S. keyboards, not AltGr) with one hand, while typing the number required for the third level character intended as the result, with the other hand. You often have to cross your left hand to the "wrong" side of the keyboard to reach the right sided number keys.

It may seem like three keys instead of two for the same result, but actually, it's still just two hands whatever way you look at it, and it avoids crossing one hand to the "wrong" side of the keyboard for fast typing.

Basically, what he needs (and what I would also like) would be to use the left side CTRL and ALT keys together, to get the same result as the ride sided ALT key for third level characters (AltGr key on French and Belgian keyboards). 

SaosinHax, correct me if I explained it wrong.

**[COLOR="DarkRed"]And now, after some trials and testing (and all that verbage above), I think I have the solution:[/COLOR]**

1. Open the System menu in the "top panel".
2. From the drop down list, open the "Preferences" menu.
3. From that list, open "Keyboard".
4. From that window, choose the "Layouts" tab.
5. From there, click on the "Options" button (bottom left).
6. Then, look for "Key to choose 3rd level" and select it.
7. Check the box "Any Alt Key".
8. Click "Close" and try it out.
9. Rejoice and drink a beer (or glass of nice wine).
10. Call your girlfriend or wife and tell her she's gorgeous.

Hopefully that should do it the way you want it ... please also adjust point (10) for the appropriate gender in your particular case. Note that you won't need to use left CTRL at all, so in that respect, you get to have your cake and eat it too (it's as convenient as the default Windows operation, but requires one fewer keys to press).

Could anyone who thinks assigning the left ALT to access third level characters might cause other issues, please state their concern forthwith! It might, for example, restrict access to other special key functions that normally require a press of that left ALT key (possibly in combination with another key, such as Shift or CTRL), but I can't think of any important ones right now.

---

### Post by Kixtosh on 2011-04-02
Actually, after trying it myself ... this works great but ...

CTRL ALT DEL no longer brings up the shutdown "log out" menu. Not a problem if you use another method to get there (such as the mouse, or the power button press etc.) but otherwise, it might be an issue for some.

**[COLOR="DarkRed"]I advise checking keyboard shortcuts that include the ALT key (from the System/Preferences/Keyboard Shortcuts location) to check whether shortcuts you may be using will be not usable after the layout modification suggested by myself above.[/COLOR]**

Apart from CTRL ALT DEL, I can also think of:

1. CTRL ALT Home, to bring up the Home folder.
2. CTRL ALT and left or right arrow keys, to change between desktops.
3. ALT F1 to bring up the main Applications menu.
4. ALT TAB to change between open windows.
5. ALT F10 to maximize a window.
6. ALT F9 to minimize a window.

There are lots of others too, which probably explains why I never made the change before. Some could be replaced using the Super (Win) key combination, instead of ALT, but it might get too "messy" for some people to want to use it.

I'll be going back to the "old" way of doing things again ... and telling my wife that she's not gorgeous after all. I don't know what I'll do with the glass of wine though: it's already long gone!

Anyway, for what it's worth, there you have it ... sigh!

---

### Post by 23dornot23d on 2011-04-03
Another ways may be to use a applet or a [COLOR=Blue][character table]("http://www.google.com/images?client=ubuntu&channel=fs&q=character+table+linux&oe=utf-8&um=1&ie=UTF-8&source=og&sa=N&hl=en&tab=wi&biw=1198&bih=528") [/COLOR]if they are only used occasionally ..

[IMG]http://img84.imageshack.us/img84/1479/charska.jpg[/IMG]


On the top panel click on it and add applet - Character Palette ..... you can edit the lines in preferences
and add what characters you want to it ........

Then by clicking a character in it ....... it is then just a case of pasting into whichever document you need it in
just another alternative ..... Hope its useful



You could also search on [COLOR=Blue][custom keyboard layouts in Google]("http://www.google.com/search?client=ubuntu&channel=fs&q=keyboard+layout+editing+Linux+gnome&ie=utf-8&oe=utf-8")[/COLOR] ..... to see if one exists

---

### Post by Daniel0108 on 2011-04-03
> **SaosinHax said:**
> 
<UNSOLVED>
When I press on the middle key on my mouse ( the scrolling wheel or whatever they call it , nothing happens , when in Windows it puts this round thingy on the page which allows me to scroll through my page very fast
</UNSOLVED>


You can set special keys in System>Preferences>Keyboard Shortcuts.

I don't know if there's a function for scrolling very fast, but you can switch workspaces when clicking on this button, for example.

So your middle mouse button isn't useless anymore.

Yours,
Daniel

---

