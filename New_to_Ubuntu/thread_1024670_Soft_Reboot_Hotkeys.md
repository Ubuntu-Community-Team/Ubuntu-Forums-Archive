---
title: "Soft Reboot Hotkeys?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Gias Kay on 2008-12-29
Hello,

Is there any hotkeys or key combinations in Ubuntu that would do the soft reboot, just like the Ctrl+Alt+Delete Windows counterpart?

With many thanks,


Gias Kay

---

### Post by tech9 on 2008-12-29
Ctrl+Alt+BackSpace

---

### Post by stoogiebuncho on 2008-12-29
Ctrl+Alt+Backspace will restart X, which means it will force you to log out and take you back to the log in page - not actually reboot your computer.

It's good to start with Ctrl+Alt+Backspace, but it doesn't always work, depending on how frozen your system is.  If it doesn't work, you can always Raise the Skinny Elephants:

(Raising Skinny Elephants Is Utterly Boring) = 
Alt+SysRq+R
Alt+SysRq+S
Alt+SysRq+E
Alt+SysRq+I
Alt+SysRq+U
Alt+SysRq+B

More information on what this does can be found here:

[http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html]("http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html")

---

### Post by tech9 on 2008-12-29
> **stoogiebuncho said:**
> Ctrl+Alt+Backspace will restart X, which means it will force you to log out and take you back to the log in page - not actually reboot your computer.


This is a given, but I am sure the user does not need to reboot - restarting X will suffice - hence my post.

---

### Post by Gias Kay on 2008-12-30
> **tech9 said:**
> This is a given, but I am sure the user does not need to reboot - restarting X will suffice - hence my post.

I'd hope my Ubuntu is working as great as you'd put your trust in it -  it is indeed a reboot I was asking about.

My newly installed Intrepid on my newly bought HP notebook constantly goes dead while surfing with Firefox. When that happens, the cursor stays movable but everything else is just a simple-and-plain no reaction. Alt + F2, Ctrl + Alt + Backspace, both I've tried and not giving a response, and the REISUB method ain't working either, possibly due to the fact it requires 4 keys to perform on a notebook (Alt + Fn + SysRq + *) but most notebook keyboards like mine can only register a maximum input of 3 keys simultaneously. So I am currently only left with the hard rebooting option but I know that's extremely bad for my new toy. Any ideas?

---

### Post by stoogiebuncho on 2008-12-30
Yeesh, that doesn't sound good.  I don't know of any other way to do a soft reboot, so maybe we should try to figure out what's causing the freeze-up instead.

You say this happens when surfing the web with Firefox?  Is there any other information you can give about what is happening on your computer before the freeze?  Is there flash content on the sites you are visiting when you freeze up?

You could try running firefox from a terminal (Applications>Accessories>Terminal)
```
firefox
```

Right-click the top bar of your terminal window and check "Always On Top" (so you'll be able to see it even if your computer freezes up).  When your computer freezes, there's a chance the terminal will give you some more information about what is going on.

---

