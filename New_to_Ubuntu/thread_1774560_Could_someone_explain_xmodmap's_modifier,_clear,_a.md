---
title: "Could someone explain xmodmap's modifier, clear, and remove features to me?"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by unagimiyagi on 2011-06-03
Hi,

Been reading alot about xmodmap, but I'm still a bit unclear.

My sole goal is to do the following on a macbook pro keyboard:

make the Alt_L key windows key (I think it's a Super_L)
make the left command key an Alt_L key.
make the right command key an Alt_R key.
make the Alt_R a Control_R key.

In other words, I want a standard keyboard layout.

I know that I need to either clear or remove something in my xmodmap.  What is the difference between these commands and how are they used, and what do they really do?  I don't understand what a modifier key is in terms of xmodmap's usage.  

I gather that the steps are to do something like this:

clear the modifiers in xmodmap (what does that even mean?)  
assign a keysymbol to a keycode.  (I understand this)
add back a modifier? (I don't get that at all)


I have seen a code snippet as follows:

```

! Swap Alt and Cmd keys. keycode 37 =    Control_L
 keycode 133 =   Alt_L Meta_L 
 keycode 64 =    Super_L
 keycode 108 =   Super_R 
keycode 134 =   ISO_Level3_Shift Multi_key 
keycode 105 =   Control_R       Multi_key

 clear Shift 
clear Lock 
clear Control 
clear Mod1
clear Mod2 
clear Mod3
 clear Mod4
 clear Mod5 

add    Shift   = Shift_L Shift_R 
add    Lock    = Caps_Lock
 add    Control = Control_L Control_R 
add    Mod1    = Alt_L 0x007D 
add    Mod2    = Num_Lock 
add    Mod4    = Super_L Super_R 
add    Mod5    = Mode_switch ISO_Level3_Shift ISO_Level3_Shift ISO_Level3_Shift

  ! Configure '=' key on numpad as '='.

 keycode 0x7D =  equal

```If someone can explain those lines in great detail I may have an idea about what's going on.  I am on Natty, for what it's worth.
Thanks!

---

### Post by idoitprone on 2011-06-03
If i am going to write a xmodmap file then I need the proper keycodes and the modifiers. I want your keyboard defaults


```
xmodmap -pke | grep -i "alt\|meta\|control"
xmodmap -pm

```
Or use xev to find the keys you need. It is a simple program to test your configurations, but i might still need xmodmap -pm

There are two ways to swap keys. First is by keysym and the other by keycode.
The good thing about keysym is that you do not need to know about each keycode to write a script, but logging out and loggin in will cause the keys to keep swapping. In your case, you may want to conside using keycode as a perment solution. I am writing write both just for you.

Modifiers are events interpreted by the xserver. Forgetting to remove a modifier can lead to strange behaviors in programs. btw understanding how modifier works is the most confusing part of xmodmap. 
[http://www.emacswiki.org/emacs/XModMap](http://www.emacswiki.org/emacs/XModMap)
[http://www.emacswiki.org/emacs/MetaKeyProblems#toc7](http://www.emacswiki.org/emacs/MetaKeyProblems#toc7)


To run it save this in a file and run ```
xmodmap wateveryounamedthefile
```
Here is an example on how to swap caps lock and left control. 
btw in xmodmap configuration files "!" are comments
```
!
! Swap Caps_Lock and Control_L
!
remove Lock = Caps_Lock
remove Control = Control_L
keysym Control_L = Caps_Lock
keysym Caps_Lock = Control_L
add Lock = Caps_Lock
add Control = Control_L
```
[http://www.acm.uiuc.edu/workshops/cool_unix/xmodmap.html](http://www.acm.uiuc.edu/workshops/cool_unix/xmodmap.html)

Here is a basic script i made to swap escape with caps lock
```

remove Lock = Caps_Lock
keycode 66 = Escape 
keycode 9 = Caps_Lock
add Lock = Caps_Lock

```

---

### Post by unagimiyagi on 2011-06-03
Hi, thanks alot for your help.  Here are my results:

I'm hoping to make the left alt key become a windows key (where windows + d minimizes everything in ubuntu; and windows w shows an 'expose' like function in ubuntu natty)
I'd also want the left command key (do meta and super refer to the same key?) to become the left alt key
I also want the right command key to become the right alt key
I want the right alt key to become a right control key.  (the mac only has one control key, and it's on the left.  I'd like to add a second one)

Here is a pic of what I am talking about:  [http://www.google.com/imgres?imgurl=http://nedbatchelder.com/pix/mackeyboard.jpg&imgrefurl=http://nedbatchelder.com/blog/200808/mac_keyboard_symbols.html&h=444&w=945&sz=76&tbnid=XETnnjIzLfWlHM:&tbnh=56&tbnw=119&prev=/search%3Fq%3Dmac%2Bkeyboard%2Bpicture%26tbm%3Disch%26tbo%3Du&zoom=1&q=mac+keyboard+picture&hl=en&usg=__aesPJNO1uHKE26MOVh0Y5pDuGzw=&sa=X&ei=noPpTayEIKnx0gG9rqihAQ&ved=0CDEQ9QEwBQ&dur=873](http://www.google.com/imgres?imgurl=http://nedbatchelder.com/pix/mackeyboard.jpg&imgrefurl=http://nedbatchelder.com/blog/200808/mac_keyboard_symbols.html&h=444&w=945&sz=76&tbnid=XETnnjIzLfWlHM:&tbnh=56&tbnw=119&prev=/search%3Fq%3Dmac%2Bkeyboard%2Bpicture%26tbm%3Disch%26tbo%3Du&zoom=1&q=mac+keyboard+picture&hl=en&usg=__aesPJNO1uHKE26MOVh0Y5pDuGzw=&sa=X&ei=noPpTayEIKnx0gG9rqihAQ&ved=0CDEQ9QEwBQ&dur=873)

Thanks! if this can be done, I think that alot of mac users will be happy.

```


keycode  37 = Control_L NoSymbol Control_L
keycode  64 = Alt_L Meta_L Alt_L Meta_L
keycode 105 = Control_R NoSymbol Control_R
keycode 108 = Alt_R Meta_R Alt_R Meta_R
keycode 133 = Control_L NoSymbol Control_L
keycode 134 = Control_R NoSymbol Control_R
keycode 204 = NoSymbol Alt_L NoSymbol Alt_L
keycode 205 = NoSymbol Meta_L NoSymbol Meta_L



xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69),  Control_L (0x85),  Control_R (0x86)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

```

---

### Post by idoitprone on 2011-06-03
```
xmodmap -pke | grep -i "super"

```
opps i made an mistake. I get meta and super mixed up.

type that command above to get the current super key

and cross check with the program xev. I do not know what key press mac put there
i will try to start writing the simple script. hope i do not make an mistake

---

### Post by idoitprone on 2011-06-03
double post on accident

---

### Post by idoitprone on 2011-06-03
```



!
! clean most of the modifiers
clear control
remove mod4 = Super_L
remove mod1 = Alt_L Alt_R

!
! left side
keycode  64 = Super_L
keycode 133 = Alt_L Meta_L
add mod4 = Super_L
add mod1 = Alt_L Meta_L
add control = Control_L

! right side
keycode 134 = Alt_R Meta_R
keycode 108 = Control_R
add mod4 = Alt_R Meta_R
add control = Control_R
```

try this script.```
 xmodmap "the stuff above in a file"
```
If it does not work then I have to do all those clear, add, remove whatever blah. I guess for the super keys, since it seems about the same as my keyboard

If the command key is wrong, use the program xev and give me the keycode or change this script accordingly. It should not be that hard

---

### Post by unagimiyagi on 2011-06-03
Here are my super keys:


keycode 133 = Super_L NoSymbol Super_L
keycode 134 = Super_R NoSymbol Super_R
keycode 206 = NoSymbol Super_L NoSymbol Super_L


Let me try your script and see what happens :>

---

### Post by idoitprone on 2011-06-03
when your done change the line 
```
remove mod1 = Alt_L Alt_R

```to 

```
clear mod1

```

---

### Post by unagimiyagi on 2011-06-04
Thanks alot. I think that we're almost there.  Everything works except my ALT keys.

It seems like I need to press both ALT keys in order for ALT to work at all.  So a traditional ALT + TAB must be ALT_L + ALT_R + TAB

Is the fix apparent to you?  Can you explain what the difference is between clear and remove?  Reading your script, things should be working, but they are not.

Is Natty to blame at this point?

I see that in post # 6, you added mod4 and mod1 for the left side, but readded mod4 on the right side.  But not mod1 again?
Also, my command key is supposed to be the super key.  I see a Super_L in the modifier table, but not a Super_R in post # 6, my original xmodmap.  Is that a problem?  The command keys are supposed to become left and right ALT keys.


My right command key is a windows key still.  Right command + w shows all my active windows on one screen.  

Here is my xmodmap after your script:

> 

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69),  Control_R (0x6c)
mod1        Alt_L (0x85),  Alt_L (0xcc),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x40),  Alt_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

Thanks

---

### Post by idoitprone on 2011-06-04
oh crap i made an mistake

my bad.

I usually dont like writing scripts all the time since i an error prone idoit lol. I always forget one small thing

the difference between clear and remove is that clear removes all the modifiers, while remove modifiers one at a time. xmodmap -pm will give you a visual. Since, I not a developer, I cannot tell you the internals on this program, but I can tell you that the keyboard is abstracted in the xserver. This means this change will not persist in the tty consoles

```

!
! clean most of the modifiers
clear control
remove mod4 = Super_L
clear mod1

!
! left side
! keycode 64 is right alt
keycode  64 = Super_L
! key code 133 should be the command key, if not check with the program xev
keycode 133 = Alt_L Meta_L
add mod4 = Super_L
add mod1 = Alt_L Meta_L
add control = Control_L

! right side
! key code 134 should be the command key. i not have a mac
keycode 134 = Alt_R Meta_R
! kdecode 108 is the right alt key
keycode 108 = Control_R
! change mod4 to to mod1 
add mod1 = Alt_R Meta_R
add control = Control_R


```
My script is made to your specifications in post 1

---

### Post by unagimiyagi on 2011-06-04
Hi, thanks alot!

OK, so after more investigating, the command keys are indeed now the ALT keys.  But ALT+TAB is still not working.  
But if in Firefox I press ALT+B I do get the bookmarks menu.  Same in the terminal window.  ALT+F will bring up the file menu.  

So ALT by itself is working.  Why not ALT+TAB, or in Firefox, ALT+ left arrow (which is used to go backwards to the previous web page visited).  

Any ideas :>

That doesn't make sense.  Coupled with the other general weird Natty boot problems, I may give 10.10 a try and see if it'll work there.

---

### Post by idoitprone on 2011-06-04
two things i can think of

I did mess up again or Natty shortcuts are conflicting the key presses

post the altered keys


```
xmodmap -pke | grep -i "alt"

xmodmap -pm

```

and make sure the computer is seeing alt+tab with xev

---

### Post by unagimiyagi on 2011-06-04
OK, here is my output.  Thanks

> 

keycode 133 = Alt_L Meta_L Alt_L Meta_L
keycode 134 = Alt_R Meta_R Alt_R Meta_R
keycode 204 = NoSymbol Alt_L NoSymbol Alt_L

xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69),  Control_R (0x6c)
mod1        Alt_L (0x85),  Alt_R (0x86),  Alt_L (0xcc),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x40),  Super_L (0xce)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)








---

### Post by unagimiyagi on 2011-06-04
HOLD THE PRESSES!

YOU'RE RIGHT! IT WAS A NATTY KEYBOARD SHORTCUT that was the source of the problem.

Basically, you go change the previous ALT+Tab shortcut.  I changed it to ALT+D temporarily.  Then I changed it right back to ALT+Tab.  I guess the old shortcut key combo was just "sticking" and redefining it unstuck it.  

We are all set now!

Hey I'm going to add this to the Ubuntu wiki since in my opinion alot of people will want to have this info.  I'll give full credit to you.

Thanks a bunch.  I'm actually satisifed that I did understand xmodmap by the end, and it was something about Natty that was the issue.

---

### Post by idoitprone on 2011-06-04
Did you use my updated script?

there shoudld not be 3 alt keys and 3 control keys in the modifier. That is probably what went wrong and the desktop is not reading the modifier properly i believe. I am not sure how to fix that. Never mind it added
 the keycode 204 = NoSymbol Alt_L NoSymbol Alt_L to the mix
I wondered why, but oh well it should be harmless

Oh well it works for you i guess this hack work
change the alt+tab is a hack. since the current keybindings is not exactly the same as the default. I am not sure why and it is beyond the scope of my knowledge.
marked the thread as solved. - now i feel like a forum troll


Here is a scenio if i do not change the modifiers properly

this is why we always add and remove modifier keys
```
$ xmodmap -pm
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x9)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  **Alt_R (0x6c)**,  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

$  xmodmap -pke | grep -i alt
keycode 64 = Alt_L Meta_L Alt_L Meta_L
keycode 108 = Alt_R Meta_R Alt_R Meta_R
keycode 204 = NoSymbol Alt_L NoSymbol Alt_L

$  xmodmap -e "keycode 108 = Control_L "

$ xmodmap -pke | grep -i "alt\|con"
keycode  37 = Control_L NoSymbol Control_L
keycode  64 = Alt_L Meta_L Alt_L Meta_L
keycode 105 = Control_R NoSymbol Control_R
keycode 108 = Control_L NoSymbol Control_L
keycode 204 = NoSymbol Alt_L NoSymbol Alt_L

$ xmodmap -pm
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x9)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  **Control_L (0x6c)**,  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)
```

---

