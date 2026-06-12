---
title: "help me get off the mouse!"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by fertileneutrino on 2011-06-21
hey,

i just put ubuntu on my netbook and i've been trying to learn how to use the terminal exclusively over using the UI. so far i installed xdotool to take care of moving windows around. 

is there anything else to help me get started even further?

also, i think this is a dumb question, but whenever an application is brought to the front and it comes time to actually use the application (like browsing a website or using thunderbird), I default to using the mouse. 

do people actually only use the keyboard (no mouse!!) to use applications like skype and stuff?

thanks!

Fertile Neutrino

---

### Post by idoitprone on 2011-06-21
[https://addons.mozilla.org/en-us/firefox/addon/pentadactyl/](https://addons.mozilla.org/en-us/firefox/addon/pentadactyl/)

here to help with the webbrowser problem
it behaves like vim

I recommand making a xmodmap file since you will be using escape alot

```
! xmodmap file
! for me only linux blah
 
! Swap Caps_Lock and Escape
 
 
remove Lock = Caps_Lock
remove Mod1 = Escape
keysym Escape = Caps_Lock
keysym Caps_Lock = Escape
clear Lock
add Lock = Caps_Lock
add Mod1 = Escape
```

---

### Post by LowSky on 2011-06-21
I'm a mouse user. I can't stand the need of a keyboard to do simple tasks like web browsing or open an application that in my menu.

I find it funny that when I started using a PC nearly 20 years ago there was a rush of people trying to design more mouse friendly environments, and get away from typing. Now we are going back to keyboards for what exactly?

---

### Post by fertileneutrino on 2011-06-21
> **idoitprone said:**
> [https://addons.mozilla.org/en-us/firefox/addon/pentadactyl/](https://addons.mozilla.org/en-us/firefox/addon/pentadactyl/)

here to help with the webbrowser problem
it behaves like vim

I recommand making a xmodmap file since you will be using escape alot

```
! xmodmap file
! for me only linux blah
 
! Swap Caps_Lock and Escape
 
 
remove Lock = Caps_Lock
remove Mod1 = Escape
keysym Escape = Caps_Lock
keysym Caps_Lock = Escape
clear Lock
add Lock = Caps_Lock
add Mod1 = Escape
```

hey! thanks a lot. is there a chromium-browser equivalent, or is that vim?

---

### Post by fertileneutrino on 2011-06-21
> **LowSky said:**
> I'm a mouse user. I can't stand the need of a keyboard to do simple tasks like web browsing or open an application that in my menu.

I find it funny that when I started using a PC nearly 20 years ago there was a rush of people trying to design more mouse friendly environments, and get away from typing. Now we are going back to keyboards for what exactly?

it's just that i have a netbook (bad trackpad) and it would be nice to not carry around a mouse if not needed :D.

---

### Post by idoitprone on 2011-06-21
> **LowSky said:**
> I'm a mouse user. I can't stand the need of a keyboard to do simple tasks like web browsing or open an application that in my menu.

I find it funny that when I started using a PC nearly 20 years ago there was a rush of people trying to design more mouse friendly environments, and get away from typing. Now we are going back to keyboards for what exactly?

vrome is more powerful but vimium is simpler. I use vrome
[https://chrome.google.com/webstore/detail/godjoomfiimiddapohpmfklhgmbfffjj](https://chrome.google.com/webstore/detail/godjoomfiimiddapohpmfklhgmbfffjj)
or
[https://chrome.google.com/webstore/detail/dbepggeogbaibhgnhhndojpepiihcmeb](https://chrome.google.com/webstore/detail/dbepggeogbaibhgnhhndojpepiihcmeb)

> I'm a mouse user. I can't stand the need of a keyboard to do simple tasks like web browsing or open an application that in my menu.

I find it funny that when I started using a PC nearly 20 years ago there was a rush of people trying to design more mouse friendly environments, and get away from typing. Now we are going back to keyboards for what exactly?

because a clicky clicky environment will become a bottleneck compared to shortcuts and command line. There is only so much stuff a screen can hold before it becomes an issue

---

### Post by snowpine on 2011-06-21
Ratpoison (available in the Ubuntu repositories) is a windows manager that requires no mouse: 

[www.nongnu.org/ratpoison/](www.nongnu.org/ratpoison/) 

I've been messing around with it for a few days; it is very fast and minimalistic, and it really, truly requires zero mouse interaction.

I'm using Firefox with vimperator plugin, as well as a lot of terminal apps like moc for music, mc for files, wicd-curses for network management, and crawl for fun. :)

LowSky, I respect your opinion... I was not part of any "pro-mouse movement 20 years ago" so I don't feel like a flip-flopper. :) Personally I suffer from some repetitive motion issues and I find it quicker and less stressful on my hands to simply press Super+W (my shortcut for Web browser) on the keyboard than to move my hand from the keyboard to the touchpad, accurately move the touchpad cursor all the way to the top left of the screen from wherever it happens to be, drop down the Applications menu, move the cursor down to Internet, move the cursor over to Firefox, and click the left touchpad button. Your Mileage May Vary. :)

---

### Post by noshelter on 2011-06-21
I use [cmus]("http://cmus.sourceforge.net/") to play music, it's a lot easier than you'd think

---

### Post by snowpine on 2011-06-22
I received a PM about "how do I use ratpoison?" and I'm quoting the info here in case it's helpful to others:

There are good instructions in the ratpoison manual:

[http://www.nongnu.org/ratpoison/doc/](http://www.nongnu.org/ratpoison/doc/)

Basically for most commands, you press Control+t (abbreviated C-t) followed by another key.

If you press C-t ? you'll see a list of commands.

For example to launch firefox you'd type C-t ! firefox (enter)

All configuration is done through the text file ~/.ratpoisonrc

Ratpoison isn't for everybody but I like it! I've only been using it about a week so I don't want to pass myself off as some kind of ratpoison-guru. :)

---

### Post by fertileneutrino on 2011-06-24
in vrome, has anyone had trouble navigating mail on gmail.com? when I use the 'f' quick hint mode, the numbers are optimized to highlight check boxes, not open emails directly. 

i also find myself highly dependent on the quickhint 'f' mode. do most people do this as well?

---

### Post by Paqman on 2011-06-24
> **fertileneutrino said:**
> i've been trying to learn how to use the terminal exclusively over using the UI

What's your actual objective? To avoid using the mouse, or to use the terminal more?

The reason I make the distinction is that there's a lot of ways you can control apps without the mouse, that also doesn't mean using the terminal. Unity has a lot of keyboard shortcuts available, and IIRC the accessibility system contains features to push this even further.

---

### Post by fertileneutrino on 2011-06-24
> **Paqman said:**
> What's your actual objective? To avoid using the mouse, or to use the terminal more?

The reason I make the distinction is that there's a lot of ways you can control apps without the mouse, that also doesn't mean using the terminal. Unity has a lot of keyboard shortcuts available, and IIRC the accessibility system contains features to push this even further.

my objective is to avoid using the mouse. i made that comment when i was confused, before people suggested other ways of helping such as vrome and ratpoison.

---

### Post by idoitprone on 2011-06-24
> **fertileneutrino said:**
> in vrome, has anyone had trouble navigating mail on gmail.com? when I use the 'f' quick hint mode, the numbers are optimized to highlight check boxes, not open emails directly. 

i also find myself highly dependent on the quickhint 'f' mode. do most people do this as well?


javascript is harder to detect which links are clickable. The behavior is polished in firefox but not in chrome. Sorry, there is nothing i can do, since i am not a vrome or vimperator developer.

---

