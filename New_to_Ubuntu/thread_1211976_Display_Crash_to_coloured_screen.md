---
title: "Display Crash to coloured screen"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by allabouttowler on 2009-07-13
I've been using Ubuntu Hardy for about 6 months now as my only OS and am absolutely loving it.

However, I'm having a recurring issue with my display - at completely un-predictable intervals the screen simply crashes to a matt colour.

It seems to be a different colour every time and while I am still evidently able to send commands to the machine (ie stopping vlc by hitting the space bar) I have no option other than to do a hard reboot...

I'd originally assumed that the issue related to VLC, because the program seemed to be running the first few times i saw it, though that has since proved not to be the case.

Most often it happens when the computer is inactive for a while, be that while playing back video or sat overnight...

Any help would be greatly appreciated!

---

### Post by DaGrimReefah on 2009-07-13
> I have no option other than to do a hard reboot...

You can't restart X with Ctrl-Alt-Backspace?

Can you post more info, like your video card and/or your xorg.conf?

---

### Post by allabouttowler on 2009-07-20
No... Ctl Alt Backspace doesn't have any effect whatsoever...

I'm at work at the moment so I can't get you xorg info, I'll dig it out when I get home!

My IT guy and ubuntu guru recommended upgrading from hardy, so I may give that a go in the near future!

Thanks for your reply!

---

### Post by Cypher1101 on 2009-09-14
I'm actually having the same problem in jaunty-amd64, only my screen always goes to a dark blue. But that's my screen's default garbage signal color.

More specifically, I'm running jaunty-amd64 with an ati hd 3870 gfx card. I enabled proprietary drivers because even 2d effects didn't seem to show up well with the OSS driver.

I've been looking through the vlc forums, as well as ubuntuforums, for a fix, I just haven't found any solutions yet. I haven't found any promising suggestions yet either, for that matter.

I haven't tried the hotkey suggested yet, but I'll do it in a few minutes. it's pretty easy to trigger, as it happens everytime I switch to fullscreen too fast. There's a small lag in the switch and if I hit the hotkey too many times it seems to overload the display.

edit: the dark blue color is the same color that my screen turns when ubuntu goes into it's screensaver feature. However, alt-ctrl-backspace does has no effect on the loss of display,

I have found that switching between windowed and and fullscreen mode through the use of the 'f' hotkey seems to be more reliable and cause less crashes, if any. I'm not entirely sure what to make of the OP's display crashes since my machine stops responding entirely, as opposed to still running just without display.  update: the best fix I've found so far is to change video out on vlc to X11, since ATI's proprietary drivers have buggy support for whatever the default is. This seems, so far, to have fixed crashes for me while running vlc.

---

