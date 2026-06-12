---
title: "Making devilspie work"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by TideMan on 2009-04-17
I've generated the following code in ~./devilspie/firefox.ds using gdevilspie
```
( if 
( and 
( is ( application_name ) "firefox" )
) 
( begin 
( maximize )
( set_workspace 3 )
( println "match" )
)
)

```

gdevilspie tells me the daemon is running and I can see it running in my Conky display.

Now, when I open firefox either in a terminal by typing firefox, or by clicking the icon in the top bar, it opens it but in my current desktop, not desktop 3.

What am I missing?

---

### Post by unutbu on 2009-04-17
Try:

```
( if 
    ( is ( application_name ) "Firefox" )
    ( begin 
      ( set_workspace 3 )
      ( println "match" )
      )
  )

( if 
    ( is ( window_name ) "Mozilla Firefox" )
    ( begin 
      ( maximize )
      ( println "match" )
      )
  )
```

I believe the reason why your devilspie rule did not work is that devilspie is case sensitive: "firefox" and "Firefox" are not the same.

Secondly, you may not want all windows associated with Firefox (such as the save dialog) to be maximized. 

That is why I suggest splitting off the maximize rule to only affect the "Mozilla Firefox" window.

---

### Post by TideMan on 2009-04-18
I've played around with various spellings of Firefox and nothing makes devilspie work for me.

I wonder if I have a basic misunderstanding of how to make it work?

Having got a .ds file and set the devilspie daemon running, how should one start an application like Firefox?

I've tried opening a terminal and typing firefox.  This results in Firefox opening, but in my current desktop.
I've also tried clicking Firefox in the upper taskbar and this opens Firefox, but in my current desktop also.

---

### Post by unutbu on 2009-04-18
Open a terminal and type

```
pkill devilspie       # kill any devilspie process that is currently running
devilspie             # start a fresh one that will print output to the terminal
```

Launch firefox. You should see a lot of warning messages, among which should be:

```
** (devilspie:2230): CRITICAL **: e_sexp_eval: assertion `f->tree != NULL' failed
Window Title: 'Mozilla Firefox'; Application Name: 'Firefox'; Class: 'Firefox'; Geometry: 843x1024+0+25

```
Please post the output.

---

### Post by TideMan on 2009-04-18
I followed these instructions:
```
pkill devilspie
devilspie
```
Then, I clicked Firefox and it works!!

Something must have been screwed up before.
Re-setting devilspie made it work.

Thanks unutbu

---

